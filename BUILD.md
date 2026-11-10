# KP Astrology — Android build (Cordova)

1. Install Node.js LTS, Android Studio (with SDK 34), and Java 17.
2. npm install -g cordova
3. cd kpapp
4. cordova platform add android
5. cordova plugin add cordova-plugin-purchase
6. cordova plugin add cordova-plugin-geolocation
   cordova plugin add cordova-plugin-local-notification   (සඳු වෙනස් වේලා notification)
7. Copy the remaining web files into www/ (see MISSING below).
8. cordova build android --release
   - Output: platforms/android/app/build/outputs/apk/release/

MISSING (must be copied into www/ before build; not in this bundle):
- astronomy.browser.min.js
- en.js, en2.js
- manifest.webmanifest, sw.js
- favicon.png, icon-192.png, apple-touch-icon.png, og-image.png

Play Store: create non-consumable in-app product id "kp_premium".
Privacy policy URL is required (location + purchases).

## GitHub Actions (computer නැතිව, phone එකෙන් APK ගැනීම)
1. GitHub එකේ නව repository එකක් (private) හදන්න.
2. මේ ෆෝල්ඩරයේ ඇති සියලු ෆයිල් repo එකට upload කරන්න (`.github/` ෆෝල්ඩරය ඇතුළුව).
3. `www/` ඇතුළට `en.js`, `en2.js`, `astronomy.browser.min.js` එකතු කරන්න (පැරණි Netlify site එකෙන්).
4. Repo එකේ **Actions** tab එකට ගොස් "Build KP APK" → **Run workflow**.
5. ඉවර වුණාම run එක ඇතුළේ **kp-debug-apk** artifact එක download කරලා phone එකට install කරන්න.
