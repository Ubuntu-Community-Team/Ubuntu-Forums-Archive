---
title: "Dual monitors won't enable / Extends desktop but not onto second monitor"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by robathy on 2013-07-17
Hello Ubuntu community.

I have had a look around the forums and although there are numerous dual monitor threads I can't find anything exactly like my issue.

I am running 2 GTX580's in SLi. I also have 2 monitors. My main monitor is a Viewsonic 21.5" 16:9 widescreen 1080 monitor connected via DVI. My second monitor is an HP 19" 16:10 widescreen that supports 1440 x 900, which is a VGA monitor connected via DVI through an adaptor. On my Windows setup I had the HP monitor connected to my slave GFX card and displayed an extended desktop where I kept all my Gadgets so as not to clutter up my main desktop where all my icons are. The reason for this is because when running dual monitors nVidia forces the card with the second monitor to run at maximum clock at all times. By having my second monitor on the slave GFX card it didn't get as hot.

It would seem that Ubuntu doesn't support dual monitors across dual GFX cards so I gave up fiddling with that and plugged the HP monitor into my primary GFX card. The monitor was instantly detected but I cannot enable it properly. The default configuration looks like [this]("https://www.dropbox.com/s/bd07ym3obc348rg/Default.png"). When I enable the monitor and apply [this]("https://www.dropbox.com/s/cdjtdbddw3ewvao/Enabled.png") happens. That is it extends the desktop but only on one monitor, by moving the mouse left to right I can scroll across my elongated desktop, however anything in the black part disappears. At this point the display settings looks like [this]("https://www.dropbox.com/s/gwlcuir6x00vjpo/Enabled2.png"). As you can see the monitor is not enabled. Even if this worked it wouldn't be good enough as my monitors are actually the other way around and they won't enable at all if If drag the HP monitor to its actual position.

Also my system [properties]("https://www.dropbox.com/s/9nbpydlpww8givb/System%20Details.png") say my GFX card is [unknown]("https://www.dropbox.com/s/og1ezox11vc777z/GFX%20Driver.png"). I've tried switching the drivers from Beta to the most recent stable ones and had no joy. I can play Brutal Legend through Steam as well as HL2 and everything appears to be working.

Any help would be much appreciated.

---

### Post by dino99 on 2013-07-17
i cant test myself, but that should work now.
which driver is installed ? and how have it been installed ? which kernel is used ?

[http://www.nvnews.net/vbulletin/showthread.php?t=195057](http://www.nvnews.net/vbulletin/showthread.php?t=195057)
[http://ubuntuforums.org/showthread.php?t=1115999](http://ubuntuforums.org/showthread.php?t=1115999)
[http://ubuntuforums.org/showthread.php?t=2143104](http://ubuntuforums.org/showthread.php?t=2143104)

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by robathy on 2013-08-13
Sorry for late reply, what with the forums going down and all.

The Kernel is: Ubuntu 3.5.0-37.58~precise1-generic 3.5.7.16
Driver version: 310.14 which I can only view from the nVidia X server settings as the system details says "Unknown". I installed it via the normal system updates.

I've since attempted to configure the monitors via the nVidia X server settings and although it all looks fine according to the [settings]("https://www.dropbox.com/s/8rsdb3cxpxvzb9e/nVidia%20Settings.png") it makes no difference whatsoever to the displays.

None of the thread suggestions you posted appear to resolve my issue. i.e. if I run the second monitor off the second card Ubuntu won't even detect the monitor. SLi appears to work fine. I don't really know how to check.

---

