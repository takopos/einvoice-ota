# 電子發票 App OTA

維護 `lursun.com.einvoice2` 的遠端更新檔。

## App 讀取的網址

| 用途 | URL |
|------|-----|
| 版號清單 | `https://raw.githubusercontent.com/takopos/einvoice-ota/main/einvoice-version.json` |
| APK | GitHub Release 資產（見 JSON 內 `apkUrl`） |

## 發版步驟

1. 在 App 專案升 `versionCode` / `versionName` 並打包 release APK。
2. 建立 Release（tag 建議 `v2.49`），上傳資產檔名固定為 **`einvoice.apk`**。
3. 更新本 repo 的 `einvoice-version.json`：

```json
{
  "versionCode": 49,
  "versionName": "2.49",
  "apkUrl": "https://github.com/takopos/einvoice-ota/releases/download/v2.49/einvoice.apk"
}
```

4. 將 JSON commit 並 push 到 `main`。

App 設定頁「下載更新」會比對 `versionCode`，較新則下載並安裝。

## 注意

- **不要**把大型 APK commit 進 git；只放在 Release。
- `versionCode` 必須嚴格遞增，否則已安裝的裝置不會更新。
