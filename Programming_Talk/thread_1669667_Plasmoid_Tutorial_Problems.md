---
title: "Plasmoid Tutorial Problems"
date: 2011-01-18
forum: Programming Talk
---

### Post by crugsmash on 2011-01-18
most of the programming I do is c, c++, openGL, and SDL, but one day I came across these plasmoids and wanted to play around with them. So I started working through a Plasmoid tutorial on [http://techbase.kde.org/Development/Tutorials/Plasma/GettingStarted](http://techbase.kde.org/Development/Tutorials/Plasma/GettingStarted).

When I attempt to make the file I get the following error.

```

CMake Error at /usr/local/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/crugsmash/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:5 (find_package)

```The FindeKDE4Internal.cmake is located below.

```

kdelibs5-dev: /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake

```I think I have all the required packages installed, but i am not 100% sure.

Thanks for any help.

---

