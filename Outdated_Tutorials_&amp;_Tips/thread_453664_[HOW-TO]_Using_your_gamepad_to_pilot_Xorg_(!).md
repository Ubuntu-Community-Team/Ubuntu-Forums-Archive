---
title: "[HOW-TO] Using your gamepad to pilot Xorg (!)"
date: 2007-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by adam0509 on 2007-05-24
0) Verifiy your gamepad works with "joystick" (see [http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457) )

1) take debian's package (ubuntu-one don't work) :

[http://packages.debian.org/unstable/x11/xserver-xorg-input-joystick](http://packages.debian.org/unstable/x11/xserver-xorg-input-joystick)

2) Extrat with dpkg :

```

sudo dpkg -x xserve<tab> tempfolder
cd tempfolder
cd usr/lib/xorg/modules
sudo cp joy<tab> /usr/lib/xorg/modules

```

3) Configure Xorg :

```
Section "InputDevice"
    Driver        "joystick"
    Identifier    "joystick"
    Option        "Device"    "/dev/input/js0"
EndSection
```

and add this in    Section "ServerLayout" :

```
    InputDevice    "joystick"    "SendCoreEvents"
```


Restart X, eventually reboot.




If you don't wan't always your joystick to send informations :

1) Remove "SendCoreEvents"

2) use xsetpointer :

```

xsetpointer -l
xsetpointer joystick
xsetpointer "Configured Mouse"

```


TESTED WITH FEISTY

P.S: Will this works when Xorg 7.3 goes out ? Not sure :/

---

### Post by adam0509 on 2007-05-25
Corrected. The "dpkg --force" crashes apt and make it unusable. So you have to extract and copy the file to the main folder manually.



Unfortunaly this how-to don't work on my debian Etch :


```

(II) LoadModule: "joystick"
(II) Loading /usr/lib/xorg/modules/input/joystick_drv.so
(II) Module joystick: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.2.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(EE) module ABI minor version (7) is newer than the server's version (6)
(II) UnloadModule: "joystick"
(II) Unloading /usr/lib/xorg/modules/input/joystick_drv.so
(EE) Failed to load module "joystick" (module requirement mismatch, 0)

```

Very annoying, cause its on this PC I wanted to use this, and Feisty doesn't works (kernel crash...)

---

