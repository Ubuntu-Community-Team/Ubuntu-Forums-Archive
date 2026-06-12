---
title: "An idiots guide to installing please?"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by peter_mathews2 on 2013-09-07
Good evening from a not very sunny South of France..
I want to experiment and play around with Ubunto on an old Windows XP PC (Acer). However, I am being foiled at every turn.. A friend of mine in the UK send me a CD with an Ubuntu burn, however, how many times I have tried, it will not boot, it just eventually goes to XP after attempting to boot from the CD. So plan B was to create a boot from WUBI - from the install program. This goes great until the very end of the write section when it errors out. The log file gives an "Error 22" and it has not created the boot menu as it should do. I'm getting to the stage where I'm ready to drop the experiment in the bin, but would like to pursue it a little bit more. Can someone point me to a more simple solution where I can perhaps "follow the bouncing ball" rather than learn a whole new language?
Regards - Peter

---

### Post by oldfred on 2013-09-07
Welcome to the forums.

How old is PC, or more correctly what cpu, what video and how much RAM? 
Both my XP systems are from the end of XP and run full Ubuntu but with gnome-panel not Unity ok. Laptop has 1.5GB and Desktop 4GB of RAM.
But older systems with less RAM or older video may need Lubuntu or Xubuntu as they are more lightweight.

Real old systems with Pentium M may have PAE issues and have to have Lubuntu 12.04.
Also BIOS settings can make a difference. If vendor has update make sure it is current. You should have it in AHCI if available otherwise LBA or large not RAID nor IDE.

---

### Post by whitesmith on 2013-09-07
Try going to [http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop") and downloading an .iso of something stable -- maybe 12.04 LTS. You can burn it with ImgBurn, a free tool for personal use. Select Try instead of Install and you should be in good shape.

---

### Post by grahammechanical on 2013-09-07
Are you sure that your friend burned the Ubuntu ISO image to the DVD and did not just copy it onto the disk? It would help us help you if you gave us your own version of the bouncing ball by describing what you see as the machine tried to load an OS from the DVD.

Regards.

---

### Post by TrademarkofAZ on 2013-09-07
> **whitesmith said:**
> Try going to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and downloading an .iso of something stable -- maybe 12.04 LTS. You can burn it with ImgBurn, a free tool for personal use. Select Try instead of Install and you should be in good shape.


I second that. It seems like it would be much easier on you to go through the website itself & download your own personal copy.

---

### Post by craig10x on 2013-09-07
Also...did you change your computer's BIOS settings to boot off the cd/dvd drive?  You need to to that if you have not....then you put in the iso disc while you are running windows, hit restart and then the computer should boot off the iso disc...once the iso loads in you can select to try a live session first to see how it runs...and if you like it you can install by hitting the install button you will find on the Unity Launcher (dock)...

As was previously mentioned, also make sure the disc was burned as an IMAGE...best yet would be to go to the ubuntu website and download it and burn it to image yourself...

---

