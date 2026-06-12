---
title: "Package for application with a plugin"
date: 2009-08-25
forum: Packaging and Compiling Programs
---

### Post by becrux on 2009-08-25
Hi,

I'm trying to create an Ubuntu package for my application, Wally. It's a Qt4 application.
Following instructions contained in PackagingGuide, I was able to create a working deb for Wally, both for i386 and amd64 platform.

The only problem I'm facing now is related to the fact that, when you're using KDE4 (so I'm talking about KUbuntu), Wally needs to compile and install a plugin that, from the point of view of packaging, is totally unrelated to the previous code.

Moreover, while Wally uses the usual steps for a Qt4 application (qmake -> make -> make install), this plugin requires CMake for configuration and has a different set of dependencies.

At the end, it's like I need to have "two debian" dirs in my sources, and debuild should act "twice".

Is it possible such configuration?

The only idea I had is to create a different .deb for this plugin, but, in this case, I'll have a kind of "mutual dependency", cause in KUbuntu you need both packages to run Wally, otherwise it won't work correctly.

Any ideas? I've googled a lot, but nothing :(

Thanks so much,
Tony.

---

