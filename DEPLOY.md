# デプロイ / ドメイン接続メモ

## 公開状況

- **リポジトリ**: https://github.com/weno-ms/cherry-moon （public）
- **仮URL（公開中）**: https://weno-ms.github.io/cherry-moon/
- **本番URL（DNS設定後）**: https://cherrymoon.jp
- **ホスティング**: GitHub Pages（main ブランチ / ルート）
- **独自ドメイン**: cherrymoon.jp（CNAMEファイル & Pages設定済み）
- **登録事業者**: お名前.com

更新フロー: ローカルで編集 → `git add -A && git commit && git push` → 数十秒で自動反映。

---

## 残作業：お名前.com でのDNS設定（ユーザー操作）

お名前.com の **［ドメイン Navi → DNS → DNSレコード設定を利用する → DNSレコード設定］** で以下を登録します。

### 1. apex ドメイン（cherrymoon.jp）用 — A レコード 4件

| ホスト名 | TYPE | VALUE |
|---------|------|-------|
| （空欄） | A | 185.199.108.153 |
| （空欄） | A | 185.199.109.153 |
| （空欄） | A | 185.199.110.153 |
| （空欄） | A | 185.199.111.153 |

### 2. IPv6対応（任意・推奨）— AAAA レコード 4件

| ホスト名 | TYPE | VALUE |
|---------|------|-------|
| （空欄） | AAAA | 2606:50c0:8000::153 |
| （空欄） | AAAA | 2606:50c0:8001::153 |
| （空欄） | AAAA | 2606:50c0:8002::153 |
| （空欄） | AAAA | 2606:50c0:8003::153 |

### 3. www もアクセス可能にする（任意・推奨）— CNAME 1件

| ホスト名 | TYPE | VALUE |
|---------|------|-------|
| www | CNAME | weno-ms.github.io. |

> 設定後、「確認画面へ進む」→「設定する」で反映。DNS反映は数分〜最大72時間（多くは1時間以内）。

---

## 反映後の確認

1. `dig cherrymoon.jp +short` → 上記の185.199.x.xが返ればOK
2. GitHub → リポジトリ Settings → Pages で「DNS check successful」表示を確認
3. 同画面の **Enforce HTTPS** にチェック（証明書自動発行後に選択可）
4. https://cherrymoon.jp にアクセスしてサイト表示を確認

DNS設定が終わったら教えてください。反映確認とHTTPS有効化までフォローします。
