# MS Tech EBook — Android App

Android application wrapper for the existing MS Tech EBook storefront at https://mstech-ebook.store.

**Source separation:** This Android project is maintained in `sidik11/Appebook`. The original `sidik11/ebook` repository is not modified by this app conversion.

## Build an APK

### Local build
1. Install JDK 17 and Android SDK platform/build tools for API 35.
2. From the repository root, run:

```bash
gradle assembleDebug
```

3. APK output: `app/build/outputs/apk/debug/app-debug.apk`.

### GitHub Actions
Push to `main) or manually run **Build Android APK** under Actions. The workflow builds a debug APK and uploads it as an artifact.

## App behavior
- Loads the live storefront in an Android WebView over HTTPS.
- Enables JavaScript, DOM storage, cookies, and third-party cookies required by the web checkout.
- Keeps HTTPS storefront and checkout pages in the app.
- Sends external app links such as UPI/payment intents to Android's app chooser.
- Supports Android back navigation and a retry screen when the network is unavailable.
- Does not embed server credentials or payment secrets.

## Important
This is a web-connected Android app: the storefront and API must remain deployed and reachable. For customer payments, test login, checkout, UPI handoff, payment return, and library access on a physical Android device before distributing the APK. A debug APK is for testing; Play Store distribution requires a properly signed release build.
