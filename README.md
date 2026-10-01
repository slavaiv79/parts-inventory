# Parts Inventory (Android)

Data is saved on the phone with Capacitor Preferences (plus localStorage as a backup).
Scanning uses the phone camera (live) or Take photo.

## Option A: Build with GitHub (no Android Studio)
1. Create a free GitHub account and a new empty repository.
2. Upload ALL files from this folder, including the hidden `.github` folder (drag the folder contents into the repo on a computer).
3. Open the repo's Actions tab, run "Build APK" (it also runs on every upload).
4. When it finishes (about 5 minutes), open the run and download the artifact "parts-inventory-apk". Unzip it to get app-debug.apk.
5. Copy app-debug.apk to your Android phone, tap it, and allow "Install unknown apps" when asked.

## Option B: Android Studio (computer)
1. Install Node 20, Java 17 and Android Studio.
2. In this folder run:
   npm install
   cp node_modules/html5-qrcode/html5-qrcode.min.js www/
   npx cap add android
3. Open android/app/src/main/AndroidManifest.xml and add before </manifest>:
   <uses-permission android:name="android.permission.CAMERA" />
4. Run: npx cap sync android, then npx cap open android
5. In Android Studio press Run with your phone plugged in (USB debugging on), or Build > Build APK(s).

## Updating the app later
Edit www/index.html, then rebuild. Installing a new APK over the old one keeps your saved parts as long as the app ID (com.partsinventory.app) stays the same and the same build key is used. Debug builds from GitHub use a changing key on each run, so uninstall-and-reinstall may be needed. Use Copy as CSV before reinstalling.
