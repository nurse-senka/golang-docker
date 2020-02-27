# golang-docker
[![dockeri.co](https://dockeri.co/image/nursesenka/go)](https://hub.docker.com/r/nursesenka/go)

Go言語用のDockerfileを管理する

`golang-alpine`をベースとし、Go言語で開発する際に必要なライブラリをインストールしています。

## Docker Hub

https://hub.docker.com/r/nursesenka/go

## Badge
以下で作成出来ます。

https://dockeri.co/

## 検証手順

ビルドが実行できることを確認してください。

```
docker build -t nursesenka/go .
```

`docker images` を実行し、 `nursesenka/go` というイメージが作成されていることを確認してください。

```
REPOSITORY     TAG       IMAGE ID       CREATED      SIZE
nursesenka/go  latest    7dff170c6565   2 hours ago  2.46GB
```

下記を実行し、コンテナが起動できることとgoがインストールされていることを確認してください。

```
docker run -it nursesenka/go go version
```

```
go version go1.13.5 linux/amd64
```

## 自動Buildについて

GitHub上でタグをPushするとDocker Hub上にも反映されます。

例えばこのようなタグを設定すると・・・

```bash
git tag -a v1.0.0 -m "release version v1.0.0"
git push origin tags/v1.0.0
```

Docker Hub上では `1.0.0` のタグが自動で作成されます。（`v1.0.0` のように `v` が必要なので注意）

## バージョニングについて

[セマンティック バージョニング](https://semver.org/lang/ja/) を採用します。

## バージョンアップのルール

- 初期バージョンは `1.0.0` からスタート
- グローバルで利用するgoのpackageを追加した場合、本Dockerfileはマイナーバージョンアップする
  - e.g `github.com/golang/protobuf/protoc-gen-go` を追加した場合 `1.0.0` から `1.1.0` となる
- goのマイナーバージョンが上がった場合、本Dockerfileはメジャーバージョンアップする
  - e.g `go1.13` 系から `go1.14` 系を利用するようになった場合 `1.1.0` から `2.0.0` となる
