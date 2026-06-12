---
title: "Kernel 	v3.1-rc1-oneiric: full set of debs now available (in ppa mainline daily)"
date: 2011-08-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2011-08-13
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc1-oneiric/) only has one deb in it, but [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/) has all the debs need to install 3.1-rc1.

Working ok here:

```
uname -a
Linux oneiric 3.1.0-999-generic #201108131102 SMP Sat Aug 13 12:16:32 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by xeizo on 2011-08-14
Not so ok here, after halfway boot it takes forever to load. So long, that I don't fancy it eventually arriving at the login screen.

There seems to be numerous issues during boot, so I don't expect it to hit the Oneiric repositories shortly.

I did the rebuild of nvidia-current before trying to boot it of course, but now I'm back at 3.0.0-8.10 which seems to work flawless.

---

### Post by Harry33 on 2011-08-14
> **xeizo said:**
> Not so ok here, after halfway boot it takes forever to load. So long, that I don't fancy it eventually arriving at the login screen.

There seems to be numerous issues during boot, so I don't expect it to hit the Oneiric repositories shortly.

I did the rebuild of nvidia-current before trying to boot it of course, but now I'm back at 3.0.0-8.10 which seems to work flawless.

Actually, the latest in Oneiric repos is 3.0.0-8.11
Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-8.11](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-8.11)

---

### Post by varx on 2011-08-14
> **paul_in_london said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-rc1-oneiric/") only has one deb in it, but [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/") has all the debs need to install 3.1-rc1.

Working ok here:

```
uname -a
Linux oneiric 3.1.0-999-generic #201108131102 SMP Sat Aug 13 12:16:32 UTC 2011 i686 i686 i386 GNU/Linux
```
For a couple of months, I've been updating to the newest rc releases in this repo as they come out, which was roughly once a week. I've never had serious problems with these test kernels.

I'm more reluctant to go with what appears to be a daily release or snapshot. Is there a way to discern which of this string of releases can be considered to have the status of a release candidate?

---

### Post by VinDSL on 2011-08-14
> **varx said:**
> Is there a way to discern which of this string of releases can be considered to have the status of a release candidate?
OMG!!!  Sorry for the diatribe!  LoL!  :D

I change kernels all the time, and don't remember one serious problem, ever - nVidia drivers, yes - Linux kernels, no.

Personally, I prefer Liquorix kernels ( [http://liquorix.net/](http://liquorix.net/) ) to Ubu kernels, but I'm trying to work inside "the system" at the moment.  It's only fair to run official Ubu & mainline kernels, if I'm posting in the Dev Branch Forums.

Linux kernels, in general, are hard as nails.  As long as they can access your memory, they will work. Period.  Exclamation point!  ;)

If a Linux kernel locks up on you (blue screen in Win parlance), you've got a hardware problem.  And, 99.9% of the time, if a Linux kernel hard-locks, it's because of a bad mobo or RAM stick.  Linux kernels will compensate for everything else, but when it cannot access your memory, it'll give you the middle finger.

When you think about it, Linux is simply the kernel - that's all.  Most of the things we own, are powered by Linux. It works fine in all sorts of devices - cell phones, automobiles, refrigerators, computers, blah, blah, blah.  Operating Systems, so called, are just app loaders.

As time goes on, various Linux OS will change dramatically.  The desktop OS is a thing of the past.  As time goes on, desktop distros (e.g. app loaders) will become more simple and featureless - functionally, a marriage between Android and Mac OS X.  You can see it happening every day with Unity and Gnome3.  Apps will rule the day, not the OS.

That said, fear not!  The Linux kernel is in good hands.  

The only difference between this-or-that kernel is which device(s) it supports.

If you're running a 10 year-old eMachine, you won't want the latest kernel, because they clean out the closet, from time-to-time.

Conversely, if you're running the latest and greatest hardware, you will want the latest kernel.

Soooo... I guess this is a long-winded way of saying, judge which kernel to use, based on the devices it supports, not its release status.

---

### Post by VinDSL on 2011-08-14
Heh!  Guess I'm bored...  :D

Here's Ubu00 A3, fully patched and mod'ed, running on top of:

```

Linux Zuul **[COLOR="Red"]2.6.39-4.dmz.1-liquorix-686[/COLOR]** #1 ZEN SMP PREEMPT Thu Aug 4 04:56:08 UTC 2011 i686 i686 i386 GNU/Linux

```


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-08-14 17:35:29(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-14 17:35:29.png")[/INDENT]


Liquorix kernel is working great, as usual.  ;)

---

### Post by varx on 2011-08-15
> **VinDSL said:**
> Heh!  Guess I'm bored...  :D

Here's Ubu00 A3, fully patched and mod'ed, running on top of:



It all looks great ... except that outside temperature. Whew!

---

### Post by VinDSL on 2011-08-15
> **varx said:**
> It all looks great ... except that outside temperature. Whew!
That's Arizona for you - the heat either makes you healthy, or it kills you!


BTW, I discovered something interesting...

Before switching to the Liquorix kernel, I was experiencing runaway mem usage in Compiz.  The longer I left this machine on, the higher the usage climbed.  It never went down - it always went up (and up and up).  This has been taking place for a week or two.

Also, Flash apps have been creeping, such as full screen YouTube videos, and online Flash games.

After switching to Liquorix, Compiz was still running amuck, and the above mentioned Flash apps were even slower.

So... I checked my swappiness, and the dern thing was set at "0".  Hello?!?!?

Ubu swappiness usually defaults to "60".

I reset it to "30".  Compiz immediately calmed down, and I can now watch YouTube vids in fullscreen 720p HD.  I can play online Flash games in Opera-Next.  And, Compiz mem usage rises and falls like normal, depending on what I'm doing.

Can you guys check your OEM install, and see where the swapiness is set, please?

```

$ cat /proc/sys/vm/swappiness

```

---

### Post by dino99 on 2011-08-15
60 on my side

---

### Post by VinDSL on 2011-08-15
> **dino99 said:**
> 60 on my side
Thanks!

Hrm...

Wonder how mine got set to "0"?!?!?

Oh, well, another mystery...

---

### Post by dino99 on 2011-08-15
So many tweaks ;) you need to build a changelog :)

---

### Post by VinDSL on 2011-08-15
> **dino99 said:**
> So many tweaks ;) you need to build a changelog :)
Bwahahaha!  Really!

Don't we all?  :D

---

### Post by dino99 on 2011-08-15
> **VinDSL said:**
> Bwahahaha!  Really!

Don't we all?  :D

no of course :)  only fresh install because too many tweaks makes a custom distro, then you cant name it Ubuntu and report serious bug (domino/butterfly effect)

---

### Post by varx on 2011-08-15
I'm trying to install the amd64 kernel packages from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc2-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-rc2-oneiric/")

When I run this:

```
$ sudo dpkg -i linux-headers-3.1.0-0301rc2-generic_3.1.0-0301rc2.201108150905_amd64.deb
```I keep getting hung up when dkms tries to handle the ndiswrapper modules. I have the current version of ndiswrapper (1.56+r2729-1) installed.

I've had good success keeping up with the latest release candidates in the 3.x series as well as the last couple of months of the 2.6.x series. But suddenly it's not working.

Any ideas, anyone?

---

### Post by Harry33 on 2011-08-15
> **varx said:**
> I'm trying to install the amd64 kernel packages from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc2-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-rc2-oneiric/")

When I run this:

```
$ sudo dpkg -i linux-headers-3.1.0-0301rc2-generic_3.1.0-0301rc2.201108150905_amd64.deb
```I keep getting hung up when dkms tries to handle the ndiswrapper modules. I have the current version of ndiswrapper (1.56+r2729-1) installed.

I've had good success keeping up with the latest release candidates in the 3.x series as well as the last couple of months of the 2.6.x series. But suddenly it's not working.

Any ideas, anyone?

Canonical is moving more and more to the direction where one can install only Ubuntu patched kernel and ubuntu patched proprietary drivers to have them work properly.

The truth is that a distro does not run only with a certain kernel. A number of other packages must be "vanilla" if the kernel is of "vanilla" flavour.

---

### Post by varx on 2011-08-15
> **Harry33 said:**
> Canonical is moving more and more to the direction where one can install only Ubuntu patched kernel and ubuntu patched proprietary drivers to have them work properly.

The truth is that a distro does not run only with a certain kernel. A number of other packages must be "vanilla" if the kernel is of "vanilla" flavour.
My ndiswrapper package came from a standard repo, I believe. The package maintainer is listed as "Ubuntu Developers".

---

### Post by varx on 2011-08-15
> **Harry33 said:**
> Canonical is moving more and more to the direction where one can install only Ubuntu patched kernel and ubuntu patched proprietary drivers to have them work properly.

The truth is that a distro does not run only with a certain kernel. A number of other packages must be "vanilla" if the kernel is of "vanilla" flavour.
> **varx said:**
> My ndiswrapper package came from a standard repo, I  believe. The package maintainer is listed as "Ubuntu  Developers".

Actually, I don't even need the ndiswrapper package, as my wifi adapter is natively supported. Is there a way I can have the kernel installation routine skip ndiswrapper altogether? Is it sufficient to blacklist ndiswrapper in /etc/modprobe.d? I don't mind editing scripts or manually altering config files.

Thanks.

---

### Post by cariboo on 2011-08-16
As far as I know ndiswrapper isn't installed by default, so you shouldn't have to do anything.

---

### Post by Harry33 on 2011-08-16
> **varx said:**
> Actually, I don't even need the ndiswrapper package, as my wifi adapter is natively supported. Is there a way I can have the kernel installation routine skip ndiswrapper altogether? Is it sufficient to blacklist ndiswrapper in /etc/modprobe.d? I don't mind editing scripts or manually altering config files.

Thanks.

Just purge ndiswrapper if you do not need it.
Anyway, probably that has nothing to do with the actual kernel installation problems you have.
I named "vanilla" proprietary drivers (like fglrx and nvidia-current) as a possible source of problems, because they may not work properly with the Oneiric patched kernel.

---

### Post by xebian on 2011-08-16
3.1.0-RC2 is now out and significantly snappy.

---

### Post by VinDSL on 2011-08-17
Just installed 3.0.2-030002 mainline.

Running fine!  ;)

```

vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p && echo && dpkg -s mesa-utils && echo

Wed Aug 17 05:35:46 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.2-030002-generic
unity 4.8.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

vindsl@Zuul:~$ 

```

I'll try the RCs next...

---

