---
title: "Is it easy to pach a .deb package?"
date: 2008-08-21
forum: Packaging and Compiling Programs
---

### Post by Helge on 2008-08-21
How much effort would it be to make a simple patch to a Ubuntu package?

I haven't compiled a program in ages, and I don't understand makefiles. But I know which source file I want to change, and could do it in five minutes, if it was read at runtime, rather than being compiled. 

What I'd like to do, is to download the source using apt-get, change a *.h file, make a new *.deb file, and install that. But I have never made a package, and am worried that it would take days to learn.

Where should I start? I there a simple step-by-step guide for this?

The particular task is to try to make my Sansa c240 mp3 player to work, by patching the package libmtp with a change in the file src/music-players.h. I would add the lines


  { "SanDisk", 0x0781, "Sansa c240", 0x7451, 
    DEVICE_FLAG_UNLOAD_DRIVER |  DEVICE_FLAG_BROKEN_MTPGETOBJPROPLIST_ALL |   DEVICE_FLAG_NO_RELEASE_INTERFACE },


All suggestions are appreciated
Helge

---

### Post by mrsteveman1 on 2008-08-21
this may help

[http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)

---

### Post by ssam on 2008-08-22
have you filed a bug on launchpad.net asking for this to be added?

to get the source of an ubuntu package use

```
apt-get source packagename
```

you also need all the tools needed to build it

```
sudo apt-get build-dep packagename
```

and some packaging tools
```

sudo apt-get install devscripts build-essential wget fakeroot cdbs patchutils debhelper
```

now you should have a directory of source in you current directory. cd into it, make and changes you need and then run

```
dpkg-buildpackage -rfakeroot
```

let us know if there are any error messages (i may have missed a step or a package)

---

