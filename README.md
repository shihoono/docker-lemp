# docker-lemp

- Laravel Welcomeページ
http://127.0.0.1:8080

- PhpMyAdmin トップページ
http://127.0.0.1:8081

 ### セットアップ手順

1. このリポジトリの main ブランチをチェックアウトする

2. docker-compose.yml があるディレクトリで下記のコマンドを実行する
```
$ docker compose up -d --build
```

3. 起動中の app コンテナの bash を実行する
```
$ docker compose exec app bash
```

4. vendorディレクトリへライブラリ群をインストール
```
[app] $ composer install
```

5. composer install 時は .env 環境変数ファイルは作成されないので、 .env.example を元にコピーして作成する
```
[app] $ cp .env.example .env
```

6. .envにAPP_KEY=の値がないとのエラーが発生するので、下記コマンドでアプリケーションキーを生成する
```
[app] $ php artisan key:generate
```

7. シンボリックリンクを貼る（適宜）
```
[app] $ php artisan storage:link
```

8. ファイル書き込み権限付与（適宜）
```
[app] $ chmod -R 777 storage bootstrap/cache
```

9. マイグレーション実行
```
[app] $ php artisan migrate
```
