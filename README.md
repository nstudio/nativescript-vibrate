# NativeScript Vibrate

A vibrate NativeScript module for Android and iOS

## Installation

This is based off the project structure in the latest NativeScript release 1.0.0

Run `npm install nativescript-vibrate --save` from your project's `app` directory:

```
.
├── app <------------------------------ run npm install from here
│   ├── App_Resources
│   │   └── ...
│   ├── tns_modules
│   │   └── ...
│   ├── app.css
│   ├── app.js
│   ├── main-page.js
│   ├── main-page.xml
│   ├── main-view-model.js
│   ├── node_modules
│   │   └── nativescript-vibrate <-- The install will place the module's code here
│   │       └── ...
│   └── package.json <----------------- The install will register “nativescript-vibrate as a dependency here
└── platforms
    ├── android
    └── ios
```

As is, using npm within NativeScript is still experimental, so it's possible that you'll run into some issues. A more complete solution is in the works, and you can check out [this issue](https://github.com/NativeScript/nativescript-cli/issues/362) for an update on its progress and to offer feedback.

If npm doesn't end up working for you, you can just copy and paste this repo's vibrate.android.js and vibrate.ios.js files into your app and reference them directly.


## Permissions

### Android

To use the vibrate functionality on Android your app must request permission access the vibrator. To do so, add the following line to your project's AndroidManifest.xml

```xml
<uses-permission android:name="android.permission.VIBRATE" />
```

## Notes

### iOS

There is no API to vibrate for a specific amount of time, so it will vibrate for the default no matter what (the duration is ignored).

## Usage

To use the vibrate module you must first `require()` it from your project's `node_modules` directory:

```js
var vibrator = require( "./node_modules/nativescript-vibrate/vibrate" );
```

After you have a reference to the module you can then call its `vibration(milliseconds)` method.

```js
// my-page.js
var vibrator = require( "/path/to/node_modules/nativescript-vibrate/vibrate" );
vibrator.vibration(2000);
```

A sample barebones project is included with the repo (does not include the nativescript platforms folder). To use perform the following:

* Check out repo
* Switch to the Demo folder on your command line
* Add the platforms that you wish to use (tns platform add {android or ios})
* If you added Android as a platform add the appropriate permission to AndroidManifest.xml
* You should now be able to run the sample as usual (tns run {android or ios})