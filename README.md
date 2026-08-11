# ATELIER Demo Page

ATELIER 行銷圖文生成器的介紹頁與三步驟操作手冊，透過 GitHub Pages 發佈。

**線上頁面：** https://wa-hsiang.github.io/ATELIER-DemoPage/

頁面上的「前往使用」與「立即前往使用」兩顆按鈕都指向 ATELIER 使用介面
（https://web-production-1a0c5.up.railway.app/ ，需以 @pressplay.cc 帳號登入）。

## 檔案

| 檔案 | 用途 |
|---|---|
| `index.html` | 整個頁面，單一檔案 |
| `.nojekyll` | 略過 GitHub Pages 的 Jekyll 處理 |

## 這個頁面的形態

`index.html` 是**完全自帶的單一檔案**：15 張圖片（12 張成品範例、3 張操作截圖）全部以
data URI 內嵌，沒有任何外部請求。除了 CTA 按鈕指向 ATELIER 之外，頁面不連任何外部資源，
所以不需要 build step，也沒有相對路徑會斷掉。

版面是固定 1280px 的桌機構圖（內含一列 1183px 的成品圖排列與 960px 寬的截圖）。頁尾一段
腳本會依視窗寬度對整頁做等比縮放，而不是重排——因為重排會拆掉成品圖那一列的固定寬度配置。
1280px 以上為 1:1，以下按比例縮小。

視覺沿用 PPA Design System 的 token 子集（`--pp-orange-*` 品牌橘、`--gray-*` 灰階、
`.t-*` 字級、`.ppa-btn` 按鈕），內聯在 `<style>` 中。

## 來源與重新產生

頁面源自 Claude Design（claude.ai/design）匯出的 handoff bundle，位於同層目錄：

```
../visual-generate-tool-demo/
```

那份 bundle 的 `project/Visual Generate Demo.dc.html` 是設計原稿，依賴四支 design token
CSS、`ppa-btn.css`，以及 `image-slot.js` 這個 custom element；12 張成品圖並不在磁碟上，
而是存在 `project/.image-slots.state.json` 裡。`index.html` 是把這些依賴全部解掉、內聯成
單檔的結果。

要修改內容，請改設計原稿或直接編輯 `index.html`，commit 後 GitHub Pages 會自動重新發佈。
