---
title: "Returning to Ubuntu! ....now what."
date: 2008-12-01
forum: New to Ubuntu
---

### Post by VampiricFang on 2008-12-01
It's been MONTHS since I was using Ubuntu, and the reason I had initially stopped using it was because it did not support my wireless card. This is not an issue anymore, so I reinstalled Ubuntu, and installed the latest version; 8.10. I'm in the process of reinstalling wow and everything....just...can't figure out how to install Flash again so I can go to youtube and such. I also would like to know if there was any essential tools I should be aware of, or what would make games run smooth with Wine. I've installed WineHQ and Wine itself already, I remembered a little bit about using the Terminal.

 (While installing WoW everything "seemed" fine, but when I went into the game to update it a couple patches it didn't load the updater, and when I was in-game it was so ungodly slow I could speed-type my name, go upstairs and get a drink if I really wanted.)

Another issue. When using Ventrilo through wine, it does not recognize my USB headset as a microphone, but rather a sound mixer, and when I click input device there's only "Default Direct Sound Device" and "default"....double ewe tea eff?

ANY help is greatly appreciated.

EDIT: I got to the WoTLK disc, and seeing as it is a DvD, I was not able to boot install.exe with Wine, thus I'm updating it through the patcher, which should take only about 5 times as long. Time really doesn't concern me, it's the fact that the sound is HORRID when I started up the game. The cinematic sounded horrible and the sound itself skipped and is VERY choppy. Any fixes?

---

### Post by ohzopants on 2008-12-01
The wine AppDB ([http://appdb.winehq.org/](http://appdb.winehq.org/)) usually has per application tips, tricks and tweaks to improve performance.

You should check there first.

Your best bet for flash is to go directly to their website and download the installer for version 10.  I think it's still in beta, but I find it is MUCH better than version 9.

---

### Post by VampiricFang on 2008-12-01
A new issue arises. When downloading the .deb from Adobe so I can install Flash, I come up with this error when it loads up and everything:

[COLOR="Red"]Error: Wrong architecture 'i386'[/COLOR]

I don't know, maybe I'm just trying to set it up too fast...:confused:

---

### Post by ohzopants on 2008-12-01
Are you using the 64-bit version of ubuntu?  And if you are, are you running a 32- or 64-bit firefox?

---

### Post by VampiricFang on 2008-12-01
I'm using the 32 bit version of both.

---

### Post by VampiricFang on 2008-12-01
Well, this is nice. Spending the whole day reinstalling World of Warcraft onto Ubuntu and it says I only have 5.7Gb left....how is this possible when I partitioned 30G, and is there a way to increase it, because I *really* don't want to reinstall Ubuntu, then reinstall Wine and such....this is kind of nerve racking.:mad:

EDIT: After uninstalling some things that should have given me JUST enough room, it states that I still only have 5.7Gb left.

---

### Post by ohzopants on 2008-12-01
If you want to resize a partition you should try the gparted live cd ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)).  Use it at your own risk; resizing filesystems can result in disaster, but it's always worked for me.

For the architecture problem: which kernel are you using?  To find out, either use some command line magic (which I don't know off the top of my head) or use synaptic and search for packages linux-kernel****.  A while ago Ubuntu started using the "generic" one instead of the "i386" one.  They work pretty much the same, so if you have the "i386" one installed try the "generic" one.*

* I haven't seen this in quite a while (pre-Hardy, I think) so I'm not sure both kernels are even still available.

If installing the .deb still doesn't work, you could install it from the source.  I'm sure you could find a guide for that somewhere.

Good luck.

---

### Post by SunnyRabbiera on 2008-12-01
eh if you cant get the installer to work on adobe's website use this:
[http://packages.ubuntu.com/hardy-backports/flashplugin-nonfree](http://packages.ubuntu.com/hardy-backports/flashplugin-nonfree)

try both installers out, see what works

---

### Post by VampiricFang on 2008-12-01
Thanks, I figured out my flash problem....now to just resize the partitioned space....rawr. :confused:

---

### Post by linux_tech on 2008-12-01
GParted is also included with Ubuntu LiveCD, (but I'm not sure if this version works with NTFS or not).
It works well and isn't tough to use
Here is a reference on how to resize a partition-
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by kk0sse54 on 2008-12-01
> **linux_tech said:**
> GParted is also included with Ubuntu LiveCD, (but I'm not sure if this version works with NTFS or not).
It works well and isn't tough to use
Here is a reference on how to resize a partition-
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

It works with ntfs and pretty much most well known file systems (except for things like *BSD type filesystems etc..)

---

