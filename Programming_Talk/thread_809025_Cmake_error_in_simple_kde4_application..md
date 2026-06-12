---
title: "Cmake error in simple kde4 application."
date: 2008-05-27
forum: Programming Talk
---

### Post by h_b_k117 on 2008-05-27
Hi,

I'm trying to compile a simple kde4 application. When I try to create a makefile for it using CMake, it gives me following output.


-- Found Qt-Version 4.4.0 (using /usr/bin/qmake)
-- Found X11: /usr/lib/libX11.so
-- Found KDE 4.0 include dir: /usr/lib/kde4/include
-- Found KDE 4 library dir: /usr/lib/kde4/lib
-- Found KDE4 kconfig_compiler preprocessor: /usr/lib/kde4/bin/kconfig_compiler
-- Found KDE4 automoc: /usr/lib/kde4/bin/kde4automoc
CMake Error: ERROR: the installed kdelibs version 3.5.9 is too old, at least version 3.9.0 is required
-- Configuring done

I'm using Kubuntu 8.04, and I've already installed kdelibs5-dev on my system. How should I make the program compile ?

---

