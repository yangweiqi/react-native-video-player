# React Native Video Player

A React Native video player with a few controls. This player uses
react-native-video for the video playback.


![demo gif](https://raw.githubusercontent.com/cornedor/react-native-video-player/master/demo.gif "Demo GIF")

## Installation

```
npm install --save react-native-video-player react-native-video react-native-vector-icons
react-native link react-native-video
react-native link react-native-vector-icons
```

## Props

| Prop                    | Description                                                                                 |
|-------------------------|---------------------------------------------------------------------------------------------|
| video                   | The video source to pass to react-native-video.                                             |
| thumbnail               | An Image source to use as thumbnail before the video gets loaded.                           |
| videoWidth              | Width of the video to calculate the player size.                                            |
| videoHeight             | Height of the video to calculate the player size.                                           |
| duration                | Duration can not always be figured out (e.g. when using hls), this can be used as fallback. |
| autoplay                | Start the video automatically.                                                              |
| defaultMuted            | Start the video muted, but allow toggling.                                                  |
| muted                   | Start the video muted and hide the mute toggle button.                                      |
| controlsTimeout         | Timeout when to hide the controls.                                                          |
| disableControlsAutoHide | Disable auto hiding the controls.                                                           |
| disableFullscreen       | Disable the fullscreen button.                                                              |
| loop                    | Loop the video after playback is done.                                                      |
| resizeMode              | The video's resizeMode. defaults to contain and is passed to react-native-video.            |
| hideControlsOnStart     | Hides the controls on start video.                                                          |
| endWithThumbnail        | Returns to the thumbnail after the video ends.                                              |
| disableSeek             | Disable video seeking.                                                                      |
| pauseOnPress            | Automatically pause/play when pressing the video player anywhere.                           |
| fullScreenOnLongPress   | Automatically show video on fullscreen when doing a long press.                             |
| onStart                 | Callback for when the start button is pressed.                                              |
| onPlayPress             | Callback for when the play button is pressed.                                               |
| onHideControls          | Callback for when the controls are being hide.                                              |
| onShowControls          | Callback for when the controls are being shown.                                             |
| customStyles            | The player can be customized in this object, see customStyles for the options.              |

All other props are passed to the react-native-video component.

### customStyles

 - wrapper
 - video
 - controls
 - playControl
 - controlButton
 - controlIcon
 - playIcon
 - seekBar
 - seekBarFullWidth
 - seekBarProgress
 - seekBarKnob
 - seekBarBackground
 - thumbnail
 - playButton
 - playArrow
 - videoWrapper

## Methods

| Method                  | Props           | Description                                                               |
|-------------------------|-----------------|---------------------------------------------------------------------------|
| seek                    | time: float     | Seek the player to the given time.                                        |
| stop                    |                 | Stop the playback and reset back to 0:00.                                 |
| pause                   |                 | Pause the playback.                                                       |
| resume                  |                 | Resume the playback.                                                      |

## Future features

- [X] Make seek bar seekable.
- [x] Make player customizable.
- [ ] Add volume control
- [X] Add fullscreen button
  - [X] Add fullscreen button for Android
- [ ] Add loader
- [ ] Add video duration/play time

## Setting up fullscreen on Android

Step 1:

Copy 3 java files (FullscreenVideoPlayerPackage.java, FullscreenVideoPlayerModule.java, FullscreenVideoPlayerActivity.java) from this repo's ```android\app\src\main\java``` folder into android's app ```android\app\src\main\java\your\package\folder``` (same folder as ```MainApplication.java```, ```MainActivity.java```) and replace ```package com.my.package;``` (the first line in these 3  java files) with your package.

Step 2:

Open ```MainApplication.java``` file and add ```new FullscreenVideoPlayerPackage()``` into ```getPackages()```:
```
    @Override
    protected List<ReactPackage> getPackages() {
        return Arrays.<ReactPackage>asList(
            new MainReactPackage(),
            ...
            new FullscreenVideoPlayerPackage(),
            ...
        );
    }
```

Step 3:

Create ```layout``` folder in your ```android\app\src\main\res``` folder, then copy the ```player_fullscreen.xml``` from this repo's ```android\app\src\main\res\layout``` folder into new created folder.

Step 4:

Open ```AndroidManifest.xml``` and add this inside ```application``` tag:
```
    <application>
    ...
        <activity
            android:name=".FullscreenVideoPlayerActivity"
            android:configChanges="orientation|screenSize"
        />
    ...
    </application>
```    

And then your fullscreen should be working and ready to go!
