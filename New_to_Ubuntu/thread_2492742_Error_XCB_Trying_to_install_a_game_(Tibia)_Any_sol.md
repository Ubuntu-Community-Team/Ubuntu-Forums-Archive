---
title: "Error XCB Trying to install a game (Tibia) Any solution?"
date: 2023-11-21
forum: New to Ubuntu
---

### Post by davidmichu on 2023-11-21
[FONT=verdana][SIZE=4]Hello guys, im trying to install Tibia (a game) but it is unpossible to install it because im gettint an error about XCB. Do you recommend any possible solution for it?
[/SIZE][/FONT]


```
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.

This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.


Available platform plugins are: xcb.


Abortado (`core' generado)
```

---

### Post by #&amp;thj^% on 2023-11-21
Could you provide the link your following, it seems to be working fine here.
And what version Ubuntu are using currently? Details help.

---

### Post by davidmichu on 2023-11-21
> **1fallen said:**
> Could you provide the link your following, it seems to be working fine here.
And what version Ubuntu are using currently? Details help.


Description:	Ubuntu 22.04.3 LTS
If I do double click on launcher it doesnt open... on terminal the message is:

[HTML]av@av-Inspiron-N4010:~/Documentos/Tibia$ sh start-tibia-launcher.shqt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.
Available platform plugins are: xcb.
Abortado (`core' generado)
[/HTML]

---

### Post by MAFoElffen on 2023-11-22
I have a hunch... 

Please post the output from the following
```

uname -r
lsb_release -d
apt list qt* --installed

```

---

### Post by #&amp;thj^% on 2023-11-22
Did we loose the OP??
if davidmichu is still aroiund, try and run it as root ie:
```
sudo '/home/me/Downloads/Tibia/Tibia' 
```
My return looks like:
```
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
[ 2023-11-22 14:27:32,625 ] Loading main configuration from "https://static.tibia.com/launcher/tibiametadata.json"
[ 2023-11-22 14:27:32,989 ] Finished download of main configuration from  "https://static.tibia.com/launcher/tibiametadata.json"
[ 2023-11-22 14:27:33,107 ] Loading launcher package configuration "LAUNCHER" (Linux/x86_64) from "https://static.tibia.com/launcher/launcher-linux-current/package.json"
[ 2023-11-22 14:27:33,108 ] Loading package configuration for "Tibia" (Linux/x86_64) from "https://static.tibia.com/launcher/tibiaclient-linux-current/package.json" / "https://static.tibia.com/launcher/assets-current/assets.json"
[ 2023-11-22 14:27:33,108 ] Loading package configuration for "Tibia External Test" (Linux/x86_64) from "https://static.test.tibia.com/launcher/tibiaclient-linux-current/package.json" / "https://static.test.tibia.com/launcher/assets-current/assets.json"
[ 2023-11-22 14:27:33,185 ] Finished downloading package configuration for "LAUNCHER" (Linux/x86_64) from "https://static.tibia.com/launcher/launcher-linux-current/package.json"
[ 2023-11-22 14:27:33,185 ] Package configuration for "LAUNCHER" (Linux/x86_64) loaded completely
[ 2023-11-22 14:27:33,278 ] Finished downloading package configuration for "Tibia" (Linux/x86_64) from "https://static.tibia.com/launcher/tibiaclient-linux-current/package.json"
[ 2023-11-22 14:27:33,539 ] Finished downloading package configuration for "Tibia External Test" (Linux/x86_64) from "https://static.test.tibia.com/launcher/tibiaclient-linux-current/package.json"
[ 2023-11-22 14:27:33,547 ] Finished downloading package configuration for "Tibia" (Linux/x86_64) from "https://static.tibia.com/launcher/assets-current/assets.json"
[ 2023-11-22 14:27:33,547 ] Package configuration for "Tibia" (Linux/x86_64) loaded completely
[ 2023-11-22 14:27:33,665 ] Finished downloading package configuration for "Tibia External Test" (Linux/x86_64) from "https://static.test.tibia.com/launcher/assets-current/assets.json"
[ 2023-11-22 14:27:33,665 ] Package configuration for "Tibia External Test" (Linux/x86_64) loaded completely
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
[ 2023-11-22 14:27:33,955 ] Using spritesheet cache size of 910
[ 2023-11-22 14:27:33,999 ] Sound engine could not not be initialized

```
If that works, it just might need a sym-link to function properly.
And for this:
```
apt list qt* --installed
Listing... Done
qt4-qtconfig/now 4:4.8.7+dfsg-20ubuntu2 amd64 [installed,local]
qt5ct/noble,now 1.5-1build7 amd64 [installed]
qt6-gtk-platformtheme/noble,now 6.4.2+dfsg-19 amd64 [installed,automatic]
qt6-qpa-plugins/noble,now 6.4.2+dfsg-19 amd64 [installed,automatic]
qt6-translations-l10n/noble,noble,now 6.4.2-1 all [installed,automatic]
qt6-wayland/noble,now 6.4.2-5 amd64 [installed,automatic]
qt6ct/noble,now 0.9-1 amd64 [installed]
qtchooser/noble,now 66-2build1 amd64 [installed]
qtcore4-l10n/now 4:4.8.7+dfsg-20ubuntu2 all [installed,local]
qtspeech5-speechd-plugin/noble,now 5.15.10-2 amd64 [installed,automatic]
qtwayland5/noble,now 5.15.10-2 amd64 [installed,automatic]

```
Will not be the issue, but I could be wrong.
```
 apt list xcb* --installed
Listing... Done

```
However check if you have this installed:
```
apt search libxcb-xinerama0 
Sorting... Done
Full Text Search... Done
libxcb-xinerama0/noble,now 1.15-1 amd64 [installed]
  X C Binding, xinerama extension

```
For more here: [https://tibia.fandom.com/wiki/Linux_Client#Installation_and_launch](https://tibia.fandom.com/wiki/Linux_Client#Installation_and_launch)

---

