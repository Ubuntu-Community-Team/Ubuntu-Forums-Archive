---
title: "HOWTO: Video on iPod w/packages"
date: 2006-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by quietglow on 2006-02-21
I, probably like you, am tired of trying to track down the exact CVS snapshots, compile them in the proper order with the proper interlinking flags all to get what I consider to be essential functionality out of my computer: the ability to upload and watch video on my 5G ipod. If I had a nickle for each person I've heard say "I'd switch to ubuntu if they'd just support my video ipod"...

The last time I sucessfully managed to video transfer working properly, I saved all my debs. So here are the essential three packages you need to get video onto your 5G ipod. They were compiled on Breezy and have been tested on DDF4.

You'll use gtkpod to make the transfer, so you'll need to familiarize yourself with its use if you haven't already.

**Uninstall any and all of these packages which you may already have installed:**

```
sudo apt-get remove gtkpod libgpod libgpod0 mpeg4ip-libs
```

**download these packages into your home directory (or desktop)**

[gtkpod]("http://www.freeyourpod.com/software/gtkpod_0.99.2-1_i386.deb")
[libgpod]("http://www.freeyourpod.com/software/libgpod_0.3.0-1_i386.deb")
[mpeg4ip-lib]("http://www.freeyourpod.com/software/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb")

**Open a terminal and go to whatever directory you downloaded those files to** (if to your home, you don't need to go anywhere)

**Then** 
```
sudo dpkg -i libgpod_0.3.0-1_i386.deb

```

and

```
sudo dpkg -i mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb
```

and

```
sudo dpkg -i gtkpod_0.99.2-1_i386.deb
```

Gtkpod doesn't seem to come up in my menu very well so you'll need to fire it up thusly:

```
gtkpod
```


**NB:  If you use ANY OTHER packages in concert with these (i.e. some other version you've already compiled), you're on your own--especially if you've done a "make install" with locally compiled versions of these. That seems to have a way of dinking up any debs of the same software installed later.**

---

### Post by patsissons on 2006-03-03
I have made a deb for gtkpod that includes video support.  available at this thread here:

[http://www.ubuntuforums.org/showthread.php?t=104937&page=4](http://www.ubuntuforums.org/showthread.php?t=104937&page=4)

---

