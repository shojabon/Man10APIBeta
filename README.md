# Man10APIBeta
# APIキー取得

サーバー内にて順番にコマンドを実行してください
```
/mwa register
/mwa api
```
最後に出た「XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXX」フォーマットの英数字列がAPIキーとなります

# GET /v1/mshop/shop/list

このエンドポイントは、管理が可能なショップのリストを取得するために使用されます。

## HTTPリクエスト

`GET /v1/mshop/shop/list`

## ヘッダー

リクエストには以下の認証ヘッダーが必要です。

- `Authorization: Bearer <APIキー>`  
  または
- `Authorization: Basic Base64(<APIキー> + ":")`

ここで、`<APIキー>`は、ユーザーのAPIキーを表します。

## レスポンス

成功した場合、以下の形式でデータが返されます。

```json
{
  "status": "<ステータスコード>",
  "message": "<メッセージ>",
  "data": "<ショップリストデータ>"
}
```

## リクエスト例(curl)
```curl
curl -X GET \
  -u <APIキー>: \
  "https://api.man10.red/v1/mshop/shop/list"
# <API>キーの後には『:』をつけてください
```
```curl
curl -X GET \
  -H "Authorization: Bearer <APIキー>" \
  "https://api.man10.red/v1/mshop/shop/list"
```

## リクエスト例(Python)
```Python3
import requests

API_KEY = "<APIキー>"
request_result = requests.get("https://api.man10.red/v1/mshop/shop/list", headers={"Authorization": f"Bearer {API_KEY}"})
data = request_result.json()

for shop_data in data["data"]:
    print(shop_data["name"], shop_data["money"])
```
