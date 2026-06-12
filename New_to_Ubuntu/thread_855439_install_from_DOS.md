---
title: "install from DOS"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by halitech on 2008-07-10
I'm not new to Ubuntu but I'm not a guru either so thought I'd post and se what people think. I have a Compaq Armada M700 (P3 750 with 192 meg of RAM, 12gig hard drive) with no cd rom and will not boot from the USB. It currently has Windows 2000 on it and I have 2 partitions. I know I can use the floppy net install of Debian to install it or Ubuntu if need be but I was wondering if the instructions from here [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(using the win98 section) would work if I just install DOS and then follow the rest? Reason I'm wondering is because if I screw up I have no way of installing windows again (non standard hard drive so no adapter to plug into a desktop). I only keep windows for 2 reasons, motorola phone that only seems to work using windows and the Trednet USB adapter I'm not sure of working.

If anyone knows of a way to use either in Ubuntu (Or Debian if need be) I would be happy to wipe it completely. 

PS. I am in the process of using Unetboot to get me going and praying I don't completely mess up.

---

### Post by snowpine on 2008-07-10
> **halitech said:**
> I'm not new to Ubuntu but I'm not a guru either so thought I'd post and se what people think. I have a Compaq Armada M700 (P3 750 with 192 meg of RAM, 12gig hard drive) with no cd rom and will not boot from the USB. It currently has Windows 2000 on it and I have 2 partitions. I know I can use the floppy net install of Debian to install it or Ubuntu if need be but I was wondering if the instructions from here [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(using the win98 section) would work if I just install DOS and then follow the rest? Reason I'm wondering is because if I screw up I have no way of installing windows again (non standard hard drive so no adapter to plug into a desktop). I only keep windows for 2 reasons, motorola phone that only seems to work using windows and the Trednet USB adapter I'm not sure of working.

If anyone knows of a way to use either in Ubuntu (Or Debian if need be) I would be happy to wipe it completely. 

PS. I am in the process of using Unetboot to get me going and praying I don't completely mess up.

Hi Halitech, unfortunately the minimum RAM for Ubuntu Hardy Heron is 256mb ([http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)). Xubuntu is supposed to run on 192mb however.

Sorry but I don't have any advice on installing without a CD. :)

---

### Post by halitech on 2008-07-10
I'm actually going with the 7.10 Xubuntu install so it should be okay, I just want it usable for the odd time I need it to take on the bus or go to my folks as it won't be my main system.

no worries about the no cd install, hopefully someone else will have some ideas or will say if it will work or not cause believe it or not, I still have copies of Dos 6.2 and 6.22 on floppy ~L~

---

### Post by snowpine on 2008-07-10
Cool, Xubuntu should work for you then. I had it running well on my P3 with 256mb ram. (Switched to Fluxbuntu, but that is a different story.)

I remember DOS vividly. I think in a way it paved the way for me to use command-line Linux today. :)

---

### Post by halitech on 2008-07-10
I had it running before through Wubi but want a native install for the added speed and it was okay.

I cut my teeth on Dos 5 and windows 3.1 so it made it easier to drop to the CLI, just different commands to learn :)

---

### Post by bab1 on 2008-07-10
I also have used DOS 6.22.  I would see if the install files can be run on a 16 bit O/S.  DOS is 16 bit and I'll bet the Linux install requires a 32 bit system.  That being said, I keep a bootable floppy of DOS with support for a CD-ROM drive.

---

### Post by halitech on 2008-07-10
good point, never thought of that, will have to check before I rely on that

---

### Post by Ptero-4 on 2008-09-28
Is your HDD, by chance, a 2.5" one (measure from top to bottom while it is laying on it's bottom in a table). If it is then you can stick it in a 2.5" USB enclosure and hook it to a desktop, or you can try and hook it in a laptop.

---

### Post by shaggy999 on 2008-09-28
I would not recommend using the DOS method not for any technical reasons but merely because I find it likely that you'll run into trouble and need help and since most of the world has moved on (from DOS) it may be hard finding troubleshooting help.

I've seen a method for installing ubuntu where you create a partition on a drive and copy the ubuntu CD to the drive, install grub, and then restart to boot off the live CD from the hard drive, which you then use to install a full installation. You might try that.

The other option is an adapter cable that you could use to plug the HD into a usb port on another computer. An enclosure was mentioned, but you really don't need a full enclosure. You just need to temporarily connect a drive to another system. I picked up a 2.5" IDE to USB 2.0 cable off of compgeeks ([www.compgeeks.com](www.compgeeks.com)) for like $10 about a year ago. Worked perfect for my needs.

Although your drive could be a SCSI drive, too... but the point is hard drives use standard connectors so you should easily find an adapter for whatever model of drive you have. I think investing a few $$ into an adapter would be the wisest and easiest solution IMHO.

---

### Post by shaggy999 on 2008-09-28
I should also mention that basic CD-ROM drives are cheap and you could probably find a used one for free or nearly free on craigslist, a local salvation army/good will, ebay, or even compgeeks as I mentioned above has used computer equipment.

---

### Post by halitech on 2008-09-28
the system in question has recently taken a dump on me so I wasn't able to do any kind of install on it but I have done some fresh installs using boot floppies and installing Debian 4.0 with XFCE with actually ran better on an old toshiba Tecra 550CDT then Ubuntu does on my main desktop (P4 1.8) so if I can bring it back to life, thats the way I'll go with it. I know you can also get to an Ubuntu install using the Debian boot floppies but Xubuntu seemed to be slower then Debian with XFCE so I'll probably stick with Debian on older stuff.

---

### Post by mike1234 on 2008-09-28
> **shaggy999 said:**
> I should also mention that basic CD-ROM drives are cheap and you could probably find a used one for free or nearly free on craigslist, a local salvation army/good will, ebay, or even compgeeks as I mentioned above has used computer equipment.

 newegg.com has some good prices.

M.

---

### Post by halitech on 2008-09-28
thanks but the tecra is working like a top, its the original machine, the Compaq armada that died and I think its either the onboard ram (which would require a motherboard replacement) or the motherboard itself (not worth the cost of a replacement unless I get it free from a place in Canada)

---

