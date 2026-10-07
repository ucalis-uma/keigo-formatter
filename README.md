# Keigo Formatter

[![Made with pollinations.ai](https://raw.githubusercontent.com/pollinations/pollinations/main/packages/ui/src/brand/badge-made-with.svg)](https://pollinations.ai/?ref=badge)

ラフな日本語メモを敬語ビジネス文に変換する単一ページWebアプリです。

## 使い方

1. 公開URLを開く
2. 「Pollinationsでログイン (BYOP)」で自分のPollinationsアカウントを連携
   (または自分の `sk_` キーを直接入力)
3. メモを貼り付け → 文体を選択 →「敬語に変換する」
4. 結果をコピーして使う

## Pollinationsの利用箇所

- テキスト生成: `POST https://gen.pollinations.ai/v1/chat/completions`
  - 既定モデル `deepseek/deepseek-v4.1-flash` (公式・Tier無料枠可)
  - 予備: `deepseek/deepseek-v4-flash`、`community/MarcosFRG/deepseek-v4-flash-0731`
- 認証: BYOP OAuth (authorization-code + PKCE)
  - 仕様: `BRING_YOUR_OWN_POLLEN.md` (Connect User Wallets)
  - ユーザーのPollenを消費し、開発者はキーを保持しない
  - トークンは `sessionStorage` のみ (localStorage・URL・ログに置かない)

## 開発・公開

- ビルド不要。`index.html` 単体をGitHub Pages等で公開するだけ
- リポジトリに秘密鍵は含まない (`CLIENT_ID` は公開用の `pk_...` のみ。空でも手動キー入力で動作)
- エラー表示: 402 (残高不足) / 429 (レート制限) / 5xx (混雑) を区別

## 差別化

- 日本語特化の単機能 (敬語変換)。文体3種 (社内・社外メール・チャット)
- 英語圏の汎用変換アプリとの重複を避けている
