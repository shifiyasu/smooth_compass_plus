# Smooth Compass Plus

[comment]: <> ([![Awesome Flutter]&#40;https://img.shields.io/badge/Awesome-Flutter-52bdeb.svg?longCache=true&style=flat-square&#41;]&#40;https://github.com/Solido/awesome-flutter&#41;)

Updated Version of the original Smooth Compass with latest Flutter SDK version, It's a Customizable flutter package to find direction using device motion sensors with ability to detect Qiblah.

| ![Image](https://github.com/alihadi5125/screenshots/blob/main/ezgif.com-gif-maker%20(3).gif?raw=true) | ![Image](https://github.com/alihadi5125/screenshots/blob/main/ezgif.com-gif-maker%20(1).gif?raw=true) |
|:-----------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------:|
|                              **SmoothCompassWidget** with default Widget                              |                              **SmoothCompassWidget** with custom Widget                               |

## Features

* Extensive, yet easy to use
* Preconfigured UI with customizable styling
* Custom builder
* Locale support
* Smooth Rotation
* Values in degrees

## Usage

Make sure to check out [examples](https://github.com/Ahmad-Ayman/smooth_compass_plus/blob/master/example)

### Installation

Add the following line to `pubspec.yaml`:

```yaml
dependencies:
  smooth_compass_plus: latest-version
```

Upgrade Kotlin version to latest version:

```gradle
ext.kotlin_version: latest-version
```

### Basic setup

*The complete example is available [here](https://github.com/Ahmad-Ayman/smooth_compass_plus/blob/master/example).*

**SmoothCompassWidget** requires you to provide `compassBuilder` which returns:
* `degrees` is the directional value.
* `turns` is the value for compass rotation.
* `compassAsset` the (default) widget for compass.

**SmoothCompassWidget** Optional Arguments `Height`, `Width`, `Duration` and `compassAsset`:
* `compassAsset` is the customizable widget for compass. if not provider default will shown.
  
**Default Widget**:
```dart
SmoothCompassWidget(
 rotationSpeed: 200,
 height: 300,
 width: 300,
// compassAsset:CustomWidget(),   you custom compass widget here
 compassBuilder: (context,AsyncSnapshot<CompassModel>? compassData,Widget compassAsset){
   return compassAsset;
    },
  ),
```

**Custom Widget**:
```dart
SmoothCompassWidget(
 rotationSpeed: 200,
 height: 300,
 width: 300,
  compassAsset:Container(
  height:200,
  width:200,
    decoration:BoxDecoration(
    shape:BoxShape.circle,
    image:DecorationImage(
    image:AssetImage("path for compass image"),
    fit:BoxFit.cover
   )
  ),
),
 compassBuilder: (context,AsyncSnapshot<CompassModel>? compassData,Widget compassAsset){
   return compassAsset;
    },
  ),
```

**Custom Widget with Qiblah**:
```dart
SmoothCompassWidget(
 rotationSpeed: 200,
 height: 300,
 isQiblahCompass: true,
 width: 300,
 compassBuilder: (context,AsyncSnapshot<CompassModel>? compassData,Widget compassAsset){
   return AnimatedRotation(
      turns: compassData?.data?.turns??0/360,
      duration: const Duration(milliseconds: 400),
      child: SizedBox(
        height: 200, 
        width: 200,
        child: Stack(
          children: [
          //put your compass here
            Positioned(
              top: 0,
               left: 0,
               right: 0,
               bottom: 0,
               child: Image.asset("Your Compass Asset Here",
                   fit: BoxFit.fill),
            ),

            //put your qiblah needle here
            Positioned(
              top: 20,
              left: 0,
              right: 0,
              bottom: 20,
              child: AnimatedRotation(
                turns: (compassData?.data?.qiblahOffset??0)/360,
                duration: const Duration(milliseconds: 400),
                child: Image.asset("Your needle asset here",
                  fit: BoxFit.fitHeight),
              ),
            )
          ],
        ),
      ),
   );
 },
),
```

#### Support

for any queries or issue contact at:
* aayman@turndigital.net


