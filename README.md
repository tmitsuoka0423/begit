# begit

## 概要

Simple Git CLIは、プログラム初学者のためのGitを簡単に扱えるコマンドラインインターフェースツールです。
GitHubのアカウントがあれば、3コマンドでファイルをGitHubにアップロードすることができます。
詳しい手順はこちらの記事を参照してください。
⇢ [Gitをシンプルに使えるCLIツール作った - begit](https://zenn.dev/tmitsuoka0423/articles/b3af045e017b8efd2f61)

## インストール

```bash
$ npm install -g begit
```

## 使い方

以下の3コマンドを使います。

| コマンド | 説明 | 使うとき |
| --- | --- | --- |
| `begit init` | 初期設定を行います。 | 最初の1回のみ |
| `begit create <プロジェクト名>` | GitHub上にリポジトリを作成します。 | プロジェクトごとに1回 |
| `begit upload` | GitHubにファイルをアップロードします。 | アップロードしたいとき |

### 初期設定を行う

Gitがパソコンにインストールされているか確認します。

```bash
$ begit init
```

例

インストールされている場合、Gitのバージョンが表示されます。

```bash
$ begit init
初期設定を行います。

Git：確認しています...
Git：インストール済み git version 2.28.0
```

インストールされていない場合は、表示されるURLからGitをインストールしてください。

```bash
初期設定を行います。

Git：確認しています...

Git：インストールされていません。
以下のURLからGitをダウンロード、インストールしてください。
  https://git-scm.com/
```

### プロジェクトの準備を行う

`$ begit create`は、プロジェクトフォルダにつき1回実行してください。

```bash
$ begit create <プロジェクト名>
```

例

```bash
$ cd /path/to/project/folder
$ begit create sample-project
準備を開始します。
GitHubのユーザー名/メールアドレスを入力してください。
> {ここにユーザー名を入力してください}
GitHubのパスワードを入力してください。
> {ここにパスワードを入力してください}
準備しています...
準備が完了しました。以下のURLからアップロードしたファイルを見ることができます。
  https://github.com/{ユーザー名}/sample-project

新しいファイルをアップロードする場合は、以下のコマンドを実行してください。
  $ begit upload
```

同じプロジェクトフォルダに`create`コマンドを複数回実行した場合、以下のメッセージが表示されます。

```bash
$ begit create sample-project
このフォルダは準備済みです。
```

リポジトリはデフォルトでプライベートで作成されます。

### GitHubにコードをアップロードする

```bash
$ begit upload
```

省略コマンド
```bash
$ begit up
```

例
```bash
$ begit upload
ファイルをアップロードしています...
アップロードが完了しました。
```

内部的には以下のコマンドを実行しています。

```bash
$ git add .
$ git commit -m "{現在時刻}"
$ git push
```
