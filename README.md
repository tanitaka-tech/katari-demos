# Katari デモ集

[Katari](https://github.com/tanitaka-tech/Katari) のホーム画面に並ぶデモ 9 本。
**Katari の拡張**として配っています（[ADR-0289](https://github.com/tanitaka-tech/Katari/blob/main/docs/adr/0289-demos-as-extension.md)）。

## 入れかた

ホーム画面の「デモ」タブで **「デモを取得」** を押すと、ここが取得されます。
手で入れる場合は拡張の管理ウィンドウで次を貼ってください:

```
git+https://github.com/tanitaka-tech/katari-demos
```

取得したあと**承認**すると、ホームのデモ一覧に 6 本が並びます。

## 中身

| パス | 中身 |
|---|---|
| `manifest.toon` | 拡張マニフェスト（`contributes.sample_projects`） |
| `demos/<id>.ktrtproj/` | プロジェクト本体（split 形式） |
| `media/<id>/` | ストアページの素材（`hero.jpg` / `shot-*.jpg` / `play.mp4`） |

## 手で直さないでください

この repo の中身は **Katari 本体から生成**しています。

```sh
# Katari のリポジトリで
node scripts/gen-demo-repo.mjs /path/to/katari-demos
```

デモの中身を変えたいときは Katari 側のビルダー（`src/lib/ipc/*-demo-project.ts`）を、
説明文や飾りを変えたいときは `scripts/gen-demo-repo.mjs` の `DEMOS` を直してから
生成し直してください。素材は `pnpm run capture:demo-store` が撮ります。
