---
title: "Fingure print is not working"
date: 2016-04-26
forum: New to Ubuntu
---

### Post by bappy2 on 2016-04-26
I am a new ubuntu user. i have a hp probook laptop.
i just install ubuntu in my probook
but the fingureprint is not work in ubuntu

why?

---

### Post by Frogs Hair on 2016-04-26
Finger print reading software is not included with Ubuntu, but have a look here.  [https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui)

---

### Post by yetimon_64 on 2016-04-26
I am on a HP "envy 17" machine with a "Validity Sensors" unit, which I had to download some source code to build a driver for, not a real easy task. I found when setting up this HP unit a lot of sensor units are not supported by the fingerprint gui package or even the fingerprint ppa available for ubuntu.

 My first bit of advice would be to run the following code to identify which unit you have and check the supported devices in either the gui application or the ppa.

The code to run in terminal ...
```
lsusb
```
... and look for the line related to the reader. In my case the identifier needed for checking is "138a:0050", post back your identifier and we can check if your unit is supported or not.
> ```
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
```

Dependent on the device identifier it may be difficult or even impossible to get working, something to "think about" if that is the case is [[COLOR=#0000ff]--here--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2321901&p=13476928#post13476928"). A very interesting post by DuckHook and further down the thread a few good info links about the use of biometric readers.

Edit: just noted the list of supported readers is in the link Frogs Hair posted, at the very top. Check the lsusb code output against that list OP.

---

