---
title: "HOWTO compile Kaffeine 1.2.2 on Lucid"
date: 2011-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2011-04-26
Hi,
even if I'm using the Ubuntu Gnome based, for some specific tasks I prefer KDE applications. One of those is Kaffeine, in my opinion the best *nix DVB-T application for digital TV.

On 4/4/2011 has been released the version 1.2.2
[http://kaffeine.kde.org/?q=node/30](http://kaffeine.kde.org/?q=node/30)

Here the steps to compile on Lucid

1 First download dependencies
```
sudo apt-get --assume-yes install cmake subversion kdelibs5-dev libxss-dev libx11-dev wget build-essential libxine-dev
```
2 Download the source
```
cd $HOME
wget http://sourceforge.net/projects/kaffeine/files/current/kaffeine-1.2.2.tar.gz
tar xvzf kaffeine-1.2.2.tar.gz
cd kaffeine-1.2.2
```
3 Compile
```
cmake .
make
sudo make install
cd ..
```
4 Remove the source
```
cd $HOME
rm kaffeine-1.2.2.tar.gz
rm -R kaffeine-1.2.2

```

Reboot the PC
Done!

---

### Post by Jerzy Pitera on 2011-05-01
I did as described, but during .cmake I got the following error:
-- Found X11: /usr/lib/libX11.so
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
  Could NOT find XINE 1.1.1 or greater (missing: XINE_INCLUDE_DIR
  XINE_LIBRARY XINECONFIG_EXECUTABLE XINE_VERSION_OK)
Call Stack (most recent call first):
  /usr/share/kde4/apps/cmake/modules/FindXine.cmake:62 (find_package_handle_standard_args)
  CMakeLists.txt:5 (find_package)

I found in one forum that the message states that is missing libxss-dev. But I recon that I got it installed. Could someone help with it. I have x64 system. Maby it's the cause.

<solved> libxine-dev was missing, so it's one of dependecies.

---

### Post by dentaku65 on 2011-05-02
> **Jerzy Pitera said:**
> 

<solved> libxine-dev was missing, so it's one of dependecies.

Thx, update dependencies :-)

---

### Post by jchiso on 2011-05-16
Great job. Thanks for the write-up.

---

### Post by geazzy on 2011-05-16
great tutorial.. :D

---

