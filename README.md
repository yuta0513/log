# log

シンプルなログメモ Web アプリ。iPhone / Mac 両対応。

**URL**: https://yuta0513.github.io/log/

## 機能

- **テキスト入力** — Enter で送信（Shift+Enter で改行）。日本語 IME 対応済み
- **クロスデバイス同期** — Firestore にリアルタイム保存。iPhone で入力 → Mac で確認可能
- **オフライン対応** — localStorage にキャッシュ。オフラインでも過去ログ閲覧可
- **一括コピー** — 全ログをクリップボードにコピー
- **Obsidian 書き出し（Mac のみ）** — `inbox.md` に追記。書き出し後にクリア確認
- **クリア** — 全ログ削除（確認ダイアログあり）

## 技術構成

| 項目 | 詳細 |
|------|------|
| ホスティング | GitHub Pages |
| データベース | Firestore REST API（SDK 不使用、純粋な fetch） |
| オフラインキャッシュ | localStorage |
| Obsidian 連携 | File System Access API + IndexedDB（ファイルハンドル永続化） |
| ファイル構成 | `index.html` 1 ファイルのみ（CSS/JS インライン） |

## Obsidian 連携について

- Mac の Chrome / Edge でのみ表示される（File System Access API が必要）
- 初回クリック時にファイルピッカーで `inbox.md` を選択
- 2 回目以降はピッカー不要（IndexedDB にハンドルを保存）
- 書き出し形式: `- [MM/DD HH:MM] テキスト`
- 書き出し後、ログのクリアを確認

## Firestore

- プロジェクト: `logmemo-b0ad6`
- リージョン: asia-northeast1
- 無料枠: 読み取り 50,000/日、書き込み 20,000/日、ストレージ 1GB
