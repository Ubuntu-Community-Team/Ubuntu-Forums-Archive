---
title: "Howto: Asus Z63A and Ubuntu Breezy"
date: 2006-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by pizzach on 2006-04-09
This is the beginings of a howto for getting rid of the qwirks with Breezy Badger on Asus Z63A.  This setup probably has a lot in common with other asus laptops, but is brought together for easy reference.  I'm hoping to add this to the wiki once it matures a bit because there is currently nothing there specific to the Z63A.

[size=4]Index[/size]

[b]1. Fixing the inital install hang on Hotplug after install
2. Wireless freezing
3.  What's with the two white blocks that appear just before arriving at the  gdm login screen? 
4. Compiling a new kernel
a. Links and other resources
[/b]

[size=4]Content[/size]

**1. Fixing the initial Install hang up on Hotplug after install:**

To get past the inital hotplug freeze, press Alt-Sys Req-E.  This will disable some features tha hotplug after Alsa.  The temporary workaround is to add snd-intel-hda to the bottom of /etc/hotplug/blacklist and then restart.

Now you should have an internet connection.  Go to [http://www.alsa-project.org/](http://www.alsa-project.org/) and download the latest Alsa driver, compile and install it.
```
./configure --with-oss --with-cards=intel-hda
make
make install
```
Remember to read the INSTALL file for other notes.  I'll be adding those a bit latter to this howto.  Now you can remove snd-intel-hda from /etc/hotplug/blacklist.  With a restart you should have sound.  (Remember to turn your volume up.) Done.


**2.  Wireless freezing**
I noticed my wireless seems to freeze on me.  It's rare enough to not fix, but often enough to be annoying.  

I think I have fixed the problem, but I'll wait and see.  Wireless uses the drivers from [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/). Get instructions at [http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL)  I installed some newer drivers (and a newly compiled kernel) and it seemed to help.  I'll expand upon that when I'm sure it fixed it.


**3.  What's with the two white blocks that appear just before arriving at the  gdm login screen?**
Dunno.  But it seems compiling the kernel with less random video drivers did the trick.  Keep in mind that linux uses the i810 and you should be able to find the right driver to keep.


**4. Kernel compilation**
When you compile a new kernel, you need to go through compiling and installing Alsa again and reinstall your wireless as it will be gone.  A good rule of thumb is to not include Alsa and Oss in the kernel so you don't have to deal with the freezing problem on bootup as they don't work anyway.  Also, the wireless networking install instructs you to build the kernel **without** the drivers for a number of things.

Drivers to look out for pretaining to the Asus Z63A:
```
Select:
Processor type and features ---> Processor family (Pentium M)

Moduleized / Enabled:
Graphics support ---> Intel 810/815 support
Processor type and features ---> Intel Enhanced SpeedStep
Sound --> Sound card support
Device Drivers ---> SCSI device support

Disabled (because you have in install manually later...):
Networking support -->Wireless LAN (non-hamradio) --> Generic IEE 802.11 Networking Stack
Sound --> Advanced Linux Sound Architecture
```

I have included my own present kernel config.  [color=red]***USE AT YOUR OWN RISK***[/color] If you do use it, make sure to read things over first and modify it for your needs.


**a. Links and other resources**
Fedora Core 4 on Asus Z63A
[http://z63a.koneko.org/fc4-z63a.html#xorg](http://z63a.koneko.org/fc4-z63a.html#xorg)

A Z63A specific forum
[http://z63a.koneko.org/viewforum.php?f=4&sid=3a6bebd933bd7c60835a06116efce828](http://z63a.koneko.org/viewforum.php?f=4&sid=3a6bebd933bd7c60835a06116efce828)

Intel Wireless Pro 2200BG
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

Alsa Project
[http://www.alsa-project.org/](http://www.alsa-project.org/)

Ubuntu Howto: Kernel Compilation
[http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)

---

