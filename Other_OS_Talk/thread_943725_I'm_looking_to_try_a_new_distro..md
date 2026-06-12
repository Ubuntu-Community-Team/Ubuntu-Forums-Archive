---
title: "I'm looking to try a new distro."
date: 2008-10-10
forum: Other OS Talk
---

### Post by Jordan777 on 2008-10-10
I don't have a whole lot of experience with Linux, although I do love it and I really want to use it as my main desktop.  Unfortunately for me Ubuntu is really cool but I just can't get my wireless to work correctly.  I'm hoping if I go to another Distro I can change that.  I'm using an Asus M2N32-Sli Deluxe Mobo with the realtek 8187 card that's installed on it and I just can't get it working stable on Ubuntu. 

So anyways I've been kinda looming around looking into other Distros and I think the top ones that I'm most curious about are:

1. ArchLinux
2. Mandriva
3. Gentoo
4. openSuSE

Now the only things that I really want out of any of these are stability, speed, lots of customization, good support, games (I know it's hard on linux but as long as I can use wine and install OSS games, I'll be set) and I think that's about it.  Now I've never built up my own system (OS-wise) but I'd be willing to try if I could at least get a basic set-up with internet in 1-3 hours of work.  

Sorry if I'm being picky, I just really want to try Linux but have the things listed above as well!  So just remember I'm still pretty new to Linux but if you guys could help me out I'd appreciate it a whole lot!;)

---

### Post by fikelfikel on 2008-10-10
Which edition of Ubuntu do you use? In the new beta, Interpid, it can automaticly connect with the new NetworkManager. I reccommend trying dat before switching.

---

### Post by SunnyRabbiera on 2008-10-10
Out of those choices I say mandriva is the best if you need something that is easy to use and comes with codecs pre installed.
But another one to try is linux mint, Mint is based on Ubuntu but provides tools that might help your internet issues.
Mintwifi is a great tool, and its use of ndis-gtk is very good.

---

### Post by chucky chuckaluck on 2008-10-10
here's the arch wiki page for your wireless card - [http://wiki.archlinux.org/index.php/Rtl8187_wireless](http://wiki.archlinux.org/index.php/Rtl8187_wireless)

you'll get speed out of arch and there's plenty to customize, but of the latter, i'd say that's true with any distro (just differing in experiences, i suppose). during installation, one gets to select which filesystem to use. i tried xfs first and didn't really think it was that much faster than ubuntu. reiser was insanely fast for somethings and disappointingly slow for others. i just switched to jfs and it seems to have a ubiquitous zippiness to it.

---

### Post by Jordan777 on 2008-10-10
Well right now I'm using Ubuntu 8.04.1 I believe it is.

---

### Post by gjoellee on 2008-10-10
Of those I would recommend Mandriva Linux (2009) if you are an inexperienced computer user. If you are experienced and know many commands etc I would recommend Arch Linux.

openSUSE is a distro that is famous for something that works bad. openSUSE have bany bugs, especially in KDE. (my opinion, no offense).

I do think you also should give PCLinuxOS a try. NOTE: For more "out-of-the-box" experience wait for PCLinuxOS 2008. It will come most likely before the year 2009. If you want something lightweight try PCLinuxOS MiniME 2008 (installing the OS took as much as 5min on my laptop whihc is from year 2000.

---

### Post by neoflight on 2008-10-12
i would add centOS to the list. 
Its rock solid, generally built for servers. has the option of selecting gnome/kde or both during installation. 

core packages are not so cutting edge. but firefox is 3.02. 
check out there wiki at [http://wiki.centos.org/](http://wiki.centos.org/). graphic dirver isntall is a two step process...like many other cream distros.


debian testing is also good.

---

### Post by crimesaucer on 2008-10-12
I'm pretty sure that the rtl 8187 module is included in all Linux kernels, and is one of the easier and most supported wirless drivers in Linux.....


I've been helping you in the Arch section with your install, but if you had difficulty in Ubuntu with wireless, distro's like Gentoo and Arch aren't going to be easier.


But just like the link that chucky chuckaluck pointed you to, Arch does support the rtl 8187 and has a nice page for it in the Arch wiki's: 

[http://wiki.archlinux.org/index.php/Rtl8187_wireless](http://wiki.archlinux.org/index.php/Rtl8187_wireless)
[http://wiki.archlinux.org/index.php/Wireless#rtl8187](http://wiki.archlinux.org/index.php/Wireless#rtl8187)


If you finish that Arch install that I've been helping you with, what you're going to need to do next is configure your rc.conf correctly, and also choose an easy way to use your wireless like wicd or networkmanager.... but as for the rtl 8187, it should be easily detected since it's in the default Linux kernel..... you will also need wireless tools, and the wpa supplicant.

---

### Post by chris200x9 on 2008-10-12
I would recommend arch for a binary distro but if your like me and like building from source gentoo all the way

---

### Post by crimesaucer on 2008-10-12
> **chris200x9 said:**
> I would recommend arch for a binary distro but if your like me and like building from source gentoo all the way

I'm using Arch and all my apps (80% or more) are built from source using custom flags. I also use a custom zen2 kernel that I made myself.... if you don't want to make one yourself, there are many kernels to choose from in the AUR (even a nice zenmm one)..... you could even run a slackware kerenl or a "tux on ice" patched kernel.


For open source apps, just use the app called pacbuilder: [http://bbs.archlinux.org/viewtopic.php?id=48957](http://bbs.archlinux.org/viewtopic.php?id=48957)


it's in the AUR. That way you build all packages from source using the ABS and AUR:

[http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS)
[http://wiki.archlinux.org/index.php/AUR](http://wiki.archlinux.org/index.php/AUR)
[http://wiki.archlinux.org/index.php/Safe_Cflags](http://wiki.archlinux.org/index.php/Safe_Cflags)


the cool thing about pacbuilder on Arch, is if it won't compile an app for some reason, you can use regualr pacman to install the binary app. And if you need something really fast and don't want to wait a few minutes to compile, you can use pacman to install the binary, and then replace it later with your app built from source with your custom flags using pacbuilder. It's the best of both worlds.

---

