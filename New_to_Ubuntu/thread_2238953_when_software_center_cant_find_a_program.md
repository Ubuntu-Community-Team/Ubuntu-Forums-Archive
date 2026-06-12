---
title: "when software center cant find a program?"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by Saffo on 2014-08-11
[ATTACH=CONFIG]255390[/ATTACH]

What does it mean when something says "Available on the Software Center" and I click and the Software Center can't find it? I have all four repositories enabled.

---

### Post by coffeecat on 2014-08-11
That must be a bug. If you search for zsnes - it shows you ZSNES in a list of two and then when you click on more info, you get the not found message.

Try this: search for zsnes:i386. The more info button for the single search result takes you to the information and install screen.

---

### Post by grahammechanical on 2014-08-11
The Ubuntu apps directory page does not show an available version for 14.04.

[https://apps.ubuntu.com/cat/applications/zsnes/](https://apps.ubuntu.com/cat/applications/zsnes/)

Regards.

---

### Post by Saffo on 2014-08-12
thanks!

---

### Post by CantankRus on 2014-08-12
If you install using terminal it will install zsnes:i386 along with other i386 packages.
```
@Trusty:~$ **sudo apt-get install zsnes**&#8203;[sudo] password for glen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libasound2:i386 libasyncns0:i386 libcaca0:i386 libflac8:i386 libgpm2:i386
  libjson-c2:i386 libncurses5:i386 libncursesw5:i386 libogg0:i386
  libpulse0:i386 libsdl1.2debian:i386 libslang2:i386 libsndfile1:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386
Suggested packages:
  libasound2-plugins:i386 gpm:i386 pulseaudio:i386
The following NEW packages will be installed:
  libasound2:i386 libasyncns0:i386 libcaca0:i386 libflac8:i386 libgpm2:i386
  libjson-c2:i386 libncurses5:i386 libncursesw5:i386 libogg0:i386
  libpulse0:i386 libsdl1.2debian:i386 libslang2:i386 libsndfile1:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 **zsnes:i386**
0 to upgrade, 17 to newly install, 0 to remove and 8 not to upgrade.
Need to get 2,972 kB of archives.
After this operation, 12.8 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

---

