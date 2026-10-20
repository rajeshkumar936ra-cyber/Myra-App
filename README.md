# Myra Android Voice Assistant (starter project)

Native Kotlin Android project with a microphone UI, foreground listening service, speech recognition, text-to-speech responses, YouTube/WhatsApp launching, music-app launching, and optional device-admin screen locking.

## Build an APK

Requirements: Android Studio (current stable), Android SDK Platform 35, JDK 17.

1. Open this `Myra` folder in Android Studio and allow Gradle sync.
2. Build > Build APK(s) for a debug APK, or Build > Generate Signed Bundle / APK > APK to create a release APK signed with your own keystore.
3. Install the generated APK on your phone and grant microphone permission. For Android 13+, allow notifications. Tap **Enable screen lock** and explicitly activate Myra as a device administrator if you want voice screen-lock support.

## Voice commands

- “Open YouTube”
- “Open WhatsApp”
- “Play a song” / “Play music”
- “Lock the phone”
- “Stop listening”

## Important Android limitations

- The microphone foreground service must be started while the app is visible and after microphone permission is granted. Recent Android versions restrict starting microphone services from the background.
- Android's speech-recognition service may stop, need network access, or behave differently across devices. `START_STICKY` is a restart request, not a guarantee of uninterrupted listening after force-stop, reboot, or manufacturer battery management.
- Do not force-stop Myra if you want the service to continue. The persistent notification includes a Stop listening action.
- Battery optimization exemptions are user-controlled and are not requested automatically by this sample.
- Launching a music app does not guarantee it will start playback; this depends on the app, account state, and its playback integration.
- Device-admin activation is required for locking the screen. To remove that privilege, deactivate Myra in Android's device-admin settings before uninstalling.
- `QUERY_ALL_PACKAGES` is broad. If distributing publicly, replace it with narrowly scoped package visibility declarations and review Play policy requirements.

## Signing

No signing key is included. For security, create and protect your own keystore in Android Studio. Never share a private signing key.
