---
title: "How do I use the patch command properly?"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by brinstar117 on 2013-03-01
I'm pretty much a Linux newbie, I have played with some Live CDs here and there but never have really gotten into the command line aspect of it.

I have installed [Crystalbuntu]("http://stmlabs.com/tag/crystalbuntu/") (Ubuntu LTS 8.04 I think) to an Apple TV hard drive and am trying to get an original XBOX DVD Remote to work with Xbox Media Center (XBMC). I am using Putty to SSH into the Apple TV.

Crystalbuntu can see the remote hardware 

```
lsusbBus 002 Device 006: ID 045e:0284 Microsoft Corp. Xbox DVD Playback Kit
Bus 002 Device 005: ID 04d9:1400 Holtek Semiconductor, Inc.
Bus 002 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 05ac:8241 Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000



```

I am trying to follow the directions from this blog post: 
[http://flossnotes.blogspot.co.uk/2012/09/getting-original-xbox-dvd-dongle-to.html](http://flossnotes.blogspot.co.uk/2012/09/getting-original-xbox-dvd-dongle-to.html)

Here are the blog post instructions up to the point to where I get stuck.

[QUOTE]

[COLOR=#333333][FONT=Arial]Just follow the instructions and input the lines of code into a terminal...[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]-------------------------------------------------------------------------------------------------------------------- [/FONT][/COLOR]
[HR][/HR][COLOR=#333333][FONT=Arial]...got it going, I just compiled the xbox driver rather than all of lirc[/FONT][/COLOR]

```
[COLOR=#333333]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]
```

[COLOR=#333333][FONT=Arial]add 'blacklist xpad' without the quotes to the bottom of the file

[/FONT][/COLOR]```

sudo update-initramfs -u
sudo apt-get build-dep lircsudo apt-get install git dialog automake autoconf libtoolgit clone git://lirc.git.sourceforge.net/gitroot/lirc/lirc
wget [URL="http://old.nabble.com/attachment/31787507/0/lirc_0.9.1_lirc_xbox_driver.patchcd"]http://old.nabble.com/attachment/31787507/0/lirc_0.9.1_lirc_xbox_driver.patch
[/URL]cd lirc/
patch -p1 <../lirc_0.9.1_lirc_xbox_driver.patch

```

I am able to to edit .conf files just fine (I used nano instead of gedit). I was able to install "git" using apt-get install git-core.

The "cd lirc/" command I assume just means go to the /etc/lirc directory, please correct me if I'm wrong.

However after using git to download the patch I'm not sure what to do. When running the patch command I get this:

```
atv@Crystalbuntu:/etc/lirc$ sudo patch -p1 <../lirc_0.9.1_lirc_xbox_driver.patch-bash: ../lirc_0.9.1_lirc_xbox_driver.patch: No such file or directory
atv@Crystalbuntu:/etc/lirc$

```

I put the patch file in the /etc/lirc/drivers/lirc_xbox directory and tried running the patch command, but then I get this:

```

can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/configure.ac b/configure.ac
|index 6c07e0d..9af2a96 100644
|--- a/configure.ac
|+++ b/configure.ac
--------------------------
File to patch:

```

I told it to patch lirc_xbox.c but it only patched 1 out of 6 files.

I'm reinstalling Crystalbuntu so I have a fresh untampered files to work with as I ran the patch command a few times in different lirc directories and now I'm not sure what to do. Thanks for any help and tips!

---

### Post by sully101 on 2013-03-02
I think where your going wrong is your in the wrong directory when you patch it.
> git clone git://lirc.git.sourceforge.net/gitroot/lirc/lirc .... downloads lirc to the current directory.
> wget [http://old.nabble.com/attachment/31787507/0/lirc_0.9.1_lirc_xbox_driver.patch](http://old.nabble.com/attachment/31787507/0/lirc_0.9.1_lirc_xbox_driver.patch) will download the patch to the current directory.
So you need to just ```
cd ./lirc
```

---

### Post by brinstar117 on 2013-03-02
Thank you so much sully101! I was indeed in the wrong directory. There were two different lirc directories. I kept trying to patch /etc/lirc/lirc but I needed to patch /home/atv/lirc.

However, now I've run into another issue but that's for another thread. Thanks again!

I've looked around the forum posting/editing options and can't seem to find how to mark this solved. :oops:

---

### Post by sully101 on 2013-03-02
from [http://ubuntuforums.org/showthread.php?t=1422475]("http://ubuntuforums.org/showthread.php?t=1422475")

> When your problem is solved, mark your thread as [SOLVED] by using the [COLOR="#FF0000"]Thread Tools menu near the upper-righthand corner[/COLOR] of the page, and remember to thank those who helped fix your problem. This lets us know that we are doing some good with our time, and encourages us to keep at it.

Good to hear you got past that one brinstar117, lirc can be a headache, I've got a few mythtv boxes and every time i reinstall its a pain in the ...

---

