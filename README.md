# PayPayリンク式 Discord 自販機Bot 完全版

## 入っている機能

- Discord商品販売パネル
- 0円商品対応
  - PayPay入力なし
  - 「無料で受け取る」ボタン
  - DMへ自動納品
- 1円以上の商品
  - PayPay受け取りリンクの金額確認
  - 金額一致時にDMへ自動納品
- 商品作成時に在庫数指定
- `-1` = 無限在庫
- 無限在庫は販売パネルで `-` 表示
- `/shopadmin stock_set` で在庫数変更
- Discord自動再接続
- `main.py` クラッシュ時の自動再起動
- Render `/health` ヘルスチェック
- Windows用 `START.bat`

## 管理者コマンド

- `/shopadmin product_add`
- `/shopadmin stock_add`
- `/shopadmin stock_set`
- `/shopadmin panel`
- `/shopadmin orders`
- `/shopadmin product_delete`

### 在庫数

`product_add` の `stock`:

- `0` = 売り切れ
- `1` 以上 = 指定個数
- `-1` = 無限在庫

無限在庫は販売パネルで `-` と表示されます。

## GitHubへ置く構成

```text
main.py
start.py
requirements.txt
render.yaml
START.bat
.gitignore
RENDER_ENV.txt
data/
  products.json
  orders.json
  uploads/
    .gitkeep
```

## Render設定

Build Command:

```text
pip install -r requirements.txt
```

Start Command:

```text
python -u start.py
```

Health Check Path:

```text
/health
```

Environment Variables:

```text
DISCORD_TOKEN
GUILD_ID
ADMIN_USER_ID
ADMIN_CHANNEL_ID
```

`ADMIN_CHANNEL_ID` は省略可能です。

## 注意

`DISCORD_TOKEN` などの秘密情報はGitHubへ書かず、RenderのEnvironmentへ設定してください。

PayPayリンクの金額一致だけでは、実際にPayPay残高を受け取ったことの証明にはなりません。
このBotはPayPayアカウントへログインしたり、残高を自動受取したりしません。

Render Free Web Service自体のスピンダウンはBotコードだけでは防げません。
