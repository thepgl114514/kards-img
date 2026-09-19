# KARDS 图床(jsDelivr)

本目录由 `scripts/prepare-gh-cdn.mjs` 生成,用来配合 jsDelivr 做免费 CDN。

- `thumb/` : 卡牌列表用的 300px 缩略图
- `img/`   : (可选)原图

## 用到的地址

jsDelivr 的规则是 `https://cdn.jsdelivr.net/gh/<用户名>/<仓库名>@<分支>/<路径>`,
例如仓库是 `yourname/kards-img`、分支 `main`,那么:

- 缩略图:`https://cdn.jsdelivr.net/gh/yourname/kards-img@main/thumb/1005th_rifles.jpg`
- 原图:  `https://cdn.jsdelivr.net/gh/yourname/kards-img@main/img/1005th_rifles.png`

## 接进本站

在 Cloudflare 里给 Worker 与 Pages 各加一个变量(不需要密钥):

```
IMG_CDN_BASE = https://cdn.jsdelivr.net/gh/yourname/kards-img@main/img
```

填好之后,`/img/<id>.png` 会优先从 jsDelivr 取,命中边缘缓存,不再消耗 KV 读额度。
详见 `docs/github-cdn.md`。
