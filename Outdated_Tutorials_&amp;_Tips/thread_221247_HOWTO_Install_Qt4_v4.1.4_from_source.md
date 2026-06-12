---
title: "HOWTO: Install Qt4 v4.1.4 from source"
date: 2006-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jooize on 2006-07-22
[COLOR="Green"][SIZE="2"]**0. I had some trouble installing Qt4 on Gnome so I made this ;)**[/SIZE][/COLOR]

[COLOR="Green"][SIZE="2"]**1. Install this package: (copy/paste to a terminal)**[/SIZE][/COLOR]
```
sudo apt-get install xlibs-dev
```
**NOTE: It will install some other packages too, accept them. (see which in bottom of HOWTO)**

[COLOR="Green"][SIZE="2"]**2. Download qt-x11-opensource-src-4.1.4 from [http://www.trolltech.com/developer/downloads/qt/x11](http://www.trolltech.com/developer/downloads/qt/x11)**[/SIZE][/COLOR]

**Direct link:**
```
ftp://ftp.trolltech.com/qt/source/qt-x11-opensource-src-4.1.4.tar.gz
```
**Torrent:**
```
http://www.trolltech.com/torrents/qt-x11-opensource-src-4.1.4.tar.gz.torrent
```

[COLOR="Green"][SIZE="2"]**3. Extract it somewhere and browse to the folder in a terminal.**[/SIZE][/COLOR]

[COLOR="Green"][SIZE="2"]**4. Then run this in a terminal:**[/SIZE][/COLOR]
```
./configure
```
**OR - If you want it to install to "/usr/include/qt4" use -prefix**
```
./configure -prefix /usr/include/qt4
```
**NOTE: Default install directory is: "/usr/local/Trolltech/Qt-4.1.4"**

[COLOR="Green"][SIZE="2"]**5. Build it. This will take TIME so run this in a terminal and go to next step :).**[/SIZE][/COLOR]
```
make
```

[COLOR="Green"][SIZE="2"]**6. Go make coffee.**[/SIZE][/COLOR]

[COLOR="Green"][SIZE="2"]**7. Now we will install it (wee).**[/SIZE][/COLOR]
```
sudo make install
```
**OR - if you can't use sudo (requires rootaccess):**
```
su make install
```

[COLOR="Green"][SIZE="2"]**8. DONE!**[/SIZE][/COLOR]

[COLOR="Green"][SIZE="2"]**9. If there is ANY typo or something, PLEASE tell me so I can correct it.**[/SIZE][/COLOR]

------------

[COLOR="Red"][SIZE="2"]**If you get this error:**[/SIZE][/COLOR]
```
$ sudo apt-get install xlibs-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xlibs-dev
```
**follow this guide: [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)**

------------

**Extra notes:**

Packages installed by step 1:
libice-dev libsm-dev libxext-dev libxi-dev libxmu-dev libxmu-headers libxmuu-dev libxpm-dev libxrandr-dev libxt-dev libxtrap-dev libxtst-dev libxv-dev x-dev x11proto-randr-dev x11proto-record-dev x11proto-trap-dev x11proto-video-dev x11proto-xext-dev xlibs-dev zlib1g-dev

**Thanks to: myself.**

---

### Post by widjajayd on 2006-08-16
Thank you this is very usefull for me starting to learn program with qt4

---

### Post by Icarosaurus on 2006-10-23
I think I installed it...
Now how can I compile sources requiring Qt4?
when I ./configure them it seems it doesn't find qt4....
Thank you for your howto

---

