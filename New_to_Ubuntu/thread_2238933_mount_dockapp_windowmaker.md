---
title: "mount dockapp windowmaker"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by Andy_Crowd on 2014-08-11
Hi!
Does Ubuntu/Debian has an mount dockapp for WindowMaker?

---

### Post by whitesmith on 2014-08-11
I presume you're trying to run a Windows app in Linux. That won't work unless you install Wine as an intermediary -- Wine is really an application compatibility layer -- or run the program in a virtual machine (VM).

---

### Post by Andy_Crowd on 2014-08-11
READ about what WindowMaker is: [http://windowmaker.org/home.php](http://windowmaker.org/home.php)

It is a window manager for the Linux and I need a dockapp/slits for managing [SIZE=1](mount/unmount)[/SIZE] of a connected storage devices. Dockapp is a kind of widget that can be used only on window managers that supports them such as blackbox, opebox, afterstep, windowmaker,.... 
In blackbox they called "slits" but the most common name is "dockapps". I prefer windowmaker for a widescreen laptops, realy easy to config (hotkeys, autostart), very low memory and dockapps for monitoring of many things. 
The only problem is that it has a few dockapps for *tray, mount *and* volume/sound mixer*(with support for Alsa and not for OSS), otherwise it is perfect for older computers. Has a lot of clock, calender, system monitoring (CPU, RAM, SWAP, network, hard drive, temperature, e-mail, .....) dockapps.

I am looking for a dockapp such as ***wmmount ***_or_* **mountapp*** that will work without any problems on my 64bit laptop.

As you can see in the ubuntu repository: [dockapps trusty]("http://packages.ubuntu.com/search?keywords=dockapp&searchon=all&suite=trusty&section=all"), there are no sound mixers for alsa and mount :( , I need if someone know some old deb packages or source code (that could be compiled in ubuntu without any complications/problems), somewere on the intertnet that will work on 64 bit.

---

### Post by mooreted on 2014-08-11
Wow, they created their own distro and removed the dockapps from the dockapps site:

[http://distrowatch.com/table.php?distribution=wmlive](http://distrowatch.com/table.php?distribution=wmlive)

I don't know where to look for dockapps now.

[http://dockapps.windowmaker.org/](http://dockapps.windowmaker.org/)

Cute.

---

### Post by Andy_Crowd on 2014-08-11
Yes, they created a distro and I tested it... flashplayer hangs, almost impossible to watch flash video on the internet, that's why I am using Ubuntu now.

I got the ***wmmount*** to work but it cannot detect connected devices automaticaly or I missing something.
Here is a link for a debian package [http://archive.debian.net/lenny/amd64/wmmount/download](http://archive.debian.net/lenny/amd64/wmmount/download)

****I found *wmvolman* and made a deb package for me for future installations without need to compile it each time, [problems and solutions that I got]("http://ubuntuforums.org/showthread.php?t=2239328").

Thanks for your great help! :P

---

