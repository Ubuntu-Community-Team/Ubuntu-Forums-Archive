---
title: "Intel GMA 500"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by loudsound on 2012-06-15
I'm very new to Ubuntu. I downloaded the OS because I'm trying to revive a Dell Inspiron Mini 1210 by booting Ubuntu on a USB. I thought it's straightforward but realized there's a compatibility issue with the Intel GMA 500 and the OS. 

I came across this blog post -- [http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/) -- thru some research but got stuck in editing the syslinux.cfg file. Is there a way that I can edit this file in Windows or OS X like in Notepad or TextEdit? I'm still starting to learn Ubuntu and I can't find my way to its console.

Another question that I want to ask is if there's an available Ubuntu version that I can download that is already compatible with my netbook and Intel GMA 500?

Thanks in advance

---

### Post by nothingspecial on 2012-06-15
Question moved to it's own thread.

---

### Post by chowno on 2012-06-15
Hmm, according to this [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") there is some support in the 3.3.4 kernel without needing GRUB modifications so installing that kernel may solve a few problems.  It looks like your particular situation is very sticky and you may want to hold off your first run in linux to a system with more compatible hardware.  Graphics can be very tricky to sort out.  Otherwise it looks like a complicated mess to fix but as always the Ubuntu team has given an awesome step-by-step method to coerce support for your card into the system.  Sorry the news isn't better but linux is definitely worth some of the hassle with drivers.  You should be able to access your console when booting into Ubuntu by pressing ctrl+alt+F1 or any of F1-F6.  F7 is reserved for X.  You may also look into an Ext filesystem driver for Windows.  I don't believe Mac OS has one that is capable of handling Ext4 but can do prior versions.  I think I've used Ext2fsd from [http://www.ext2fsd.com/]("http://www.ext2fsd.com/") to access Ext partitions from Windows in the past. Hope this helps. Good luck!

---

### Post by mikewhatever on 2012-06-18
> **loudsound said:**
> 
...
I came across this blog post -- [http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/) -- thru some research but got stuck in editing the syslinux.cfg file. Is there a way that I can edit this file in Windows or OS X like in Notepad or TextEdit? I'm still starting to learn Ubuntu and I can't find my way to its console.

You can try, after all, it's only a text file. Windows doesn't format text files the same way, so it might show everything in one line in Notepad.

> Another question that I want to ask is if there's an available Ubuntu version that I can download that is already compatible with my netbook and Intel GMA 500?

Thanks in advance

No. The next release of Ubuntu should boot without modifications, but the driver will still lack important features. I don't think Ubuntu and gma500 will ever be fully compatible.

---

