# opel-mobile-config
Install and run third party apps on the Opel Mobile Touch Flip

## Other Phone Models
these steps may work with other flip phones so long as they
1. can enable developer mode
2. are running Android 8 or higher


## Connecting to phone via USB
Android 8 only supports wired debugging, 

### 1. Enable Developer Mode
Go to `Settings -> Android System -> System -> About phone -> Build number`
rapidly click build number until developer mode is enabled

### 2. Enable USB Debugging
Go to `Settings -> Android System -> System -> Developer options`
Enable `USB debugging`

### 3. Install ADB
Click [here](https://developer.android.com/tools/releases/platform-tools), Click on  Download SDK Platform-Tools for Windows/Mac/Linux Depending on your platform

### 4. Check ADB Connection
Connect the phone to your computer, run:
```bash
adb devices
```
The response should look something like this, if not, ensure computer is added as a trusted device.
```bash
List of devices attached
0123456759ABCDEF	device
```

## Acquire Apps
Find whatever `apk`s you intend to run on this thing, keep in mind that:
1. the Touch Flip has very limited resources
2. [GPServices](https://en.wikipedia.org/wiki/Google_Play_Services) is not supported, at all. Nor are apps that require them
3. Most apps have questionable keyboard support
4. Most apps are designed with Material2/3, those elements are designed for huge screens with modern resolutions. Both the Opel lacks

These are the apps I use regularly on the Opel

| App  | Usability |  Purpose    |
|-------|-----|-------|
| [Apollo](https://f-droid.org/en/packages/org.nuclearfog.apollo/) | High  | Open source offline music client, looks great on the small screen |
| [UNLauncher](https://f-droid.org/packages/com.jkuester.unlauncher/)   | Medium  | Open source app launcher, because the Touch Flip doesn't come with one   |
| [Key Mapper](https://f-droid.org/en/packages/io.github.sds100.keymapper/) | Low | Create custom shortcuts for remapping your SOS button, or other features. There's no shortage of buttons on this phone! The app is open source, and difficult to use as it was made with Material |

## Install app
Use ADB to install the APK(s) you downloaded
```bash
adb install io.github.sds100.keymapper_288.apk
```

## Run app 
This part is difficult, the Touch Flip does not provide a way for you to run any application installed (hence why I downloaded UNLauncher), but I recommend against replacing the default launcher.
```bash
adb shell am start -n com.package.name/com.package.name.ActivityName
```
This is the command for running starting an app, but we don't know the activity name for the app we're running!
I recommend setting up Key Map first, from there you can launch UNLauncher, and then launch anything.
```bash
adb shell am start -n io.github.sds100.keymapper/io.github.sds100.keymapper.MainActivity
```

## Configure Key Map

Key Map has great documentation, and the app is easy enough to figure out through feel. Go [here](https://keymapper.app/user-guide/keymaps/) for documentation.

**Here's what I set up**
| Key  | Action | 
|-------|-----|
| SOS Button | Open UNLauncher  | From UNLauncher you can run any app installed |
| HOLD Volume Down   | Open Apollo  | Quick shortcut for my music player  |






