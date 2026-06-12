---
title: "Installer for java apps"
date: 2009-03-07
forum: Programming Talk
---

### Post by rock_fredde on 2009-03-07
Im writing an app in java, but im a newbie and i dont know how to create an installer for it.

First of all, obviously, the program in which to make the installer must be open source. Ive downloaded Izpack but although Ive read through the manual several times, i dont understand what to do.

The whole program is in the same folder on my drive. It really shouldnt be that hard.

Is there anyone out there that knows how to use izpack? Or any other program i could use?

First, id like to simply create an installer for PCs, but since this is intended to become an app for mobile use later on, it would also be interesting to know how to create installers for mobile phones running java apps.

---

### Post by cthug on 2009-03-07
Cross-platform install? if so make your own in java .jar, maybe there some software to do this. If just for linux (debian based), you can make a .deb easily, there would be some examples on his forum. For windows, use NSIS (Nullsoft Scriptable Install System), which is a scriptable install system (hence the name) or you can use something with a GUI like quickInstall (bloodshed).

---

