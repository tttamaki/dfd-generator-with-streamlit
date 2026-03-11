# マルチプラットフォーム用のビルド方法

## 新しい builder を作って有効化（最初だけ）

```bash
docker buildx create --name mybuilder --use
docker buildx inspect --bootstrap
```

## マルチプラットフォームでビルドして直接 Docker Hub に push

ここでは `linux/amd64 (x86_64)` と `linux/arm64` を作る例

```bash
docker buildx build \
 --platform linux/amd64,linux/arm64 \
 -t tttamaki/dfd-generator:latest \
 --push \
 .
```

## buildx のツールで確認（推奨）

```bash
docker buildx imagetools inspect tttamaki/dfd-generator:latest
```

または docker の manifest inspect

```bash
docker manifest inspect tttamaki/dfd-generator:latest
```
