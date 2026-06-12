---
title: "Fingerprint sensor on Samsung laptop not detected with Fingerprint GUI"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by bowfyre on 2019-01-28
The laptop is the [Samsung NP900X5T-K01US]("https://www.amazon.com/Samsung-NP900X5T-K01US-Notebook-Traditional-Laptop/dp/B078BDT7PZ?ref_=fsclp_pl_dp_12") and I am using Ubuntu 18.10 but I could switch to a different version of it if that would be easier.

---

### Post by yetimon_64 on 2019-01-28
Firstly open a terminal and run the code ...
```
lsusb
```
The output from this code will tell you the ID of the fingerprint sensor, for example from my HP laptop...
> ```
Bus 001 Device 003: ID **138a:0050** Validity Sensors, Inc. Swipe Fingerprint Sensor
```
The bold part of the output above (138a:0050) is the sensor ID number, you will need to check if the fingerprint GUI package supports your sensor.
Unfortunately the support for fingerprint sensors is not particularly good and not all units will work even with the fingerprint gui PPA.
[URL="https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui"][COLOR=#0000ff]
--Here--[/COLOR][/URL] is a link to the fingerprint gui PPA site for you to check compatible sensors etc.
Switching to a different Ubuntu version most likely won't help you out, though it is possible using the fingerprint gui ppa may improve your situation compared to the repository version, though even that is not guaranteed. As I note above not all sensors are supported in Linux/Ubuntu; it seems to be a bit of a lottery when buying hardware regarding fingerprint sensor support.

Depending on your sensor it may be possible to build a driver from source code and rebuild the fprint package from source to suit it. This is a very difficult route and **IS NOT** recommended for new starters to attempt. I mention it as that is what was required to get my sensor recognized and usable, though after some further research on security aspects of biometric identification I dumped the use of my fingerprint reader and no longer bother using it.

**Edit:** according to a further link to the freedesktop.org list, included in the ppa support list, my reader is now recognized by the ppa. 
Seems to be some improvement nowadays support wise. 
Make sure you also follow the link at the top of the ppa supported list to the freedesktop.org list; your sensor may also be listed there and as such may be supported by the PPA version of fingerprint GUI.

Good luck, regards, yeti.

---

