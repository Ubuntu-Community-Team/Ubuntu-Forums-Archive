---
title: "Install development version"
date: 2011-05-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wildmanne39 on 2011-05-30
Hi, I want to install 11.10 and help with testing,I read it is safer to install on a separate system then the one I use everyday,the only other system I have is a laptop with wireless would that be an issue with the development version? I have a broadcom 4306 card and it works with current install. I was thinking of setting it up on my second drive of my production machine, any thoughts? Thanks in advance for your help I really appreciate it. I wanted to add another question I have not seen it anywhere else yet, can 11.10 be installed on a usb drive?

---

### Post by screaminj3sus on 2011-05-30
If it works with natty it will probably work with 11.10, but you can never be sure with a development version. Expect things to not work properly regardless of what machine you put it on.

---

### Post by ranch hand on 2011-05-31
You can use it on a box you are using.  There is some but little danger in that.

You do not want to use OO as your production OS.  It WILL break.

It is good if it is dual booted with a stable OS so that you can chroot in to do update/upgrades and other things to get it back on its feet.  Being able to get to the files from another install gives you easy access to log files and so forth.

---

### Post by jerrylamos on 2011-06-01
> **ranch hand said:**
> You can use it on a box you are using.  There is some but little danger in that.

You do not want to use OO as your production OS.  It WILL break.

It is good if it is dual booted with a stable OS so that you can chroot in to do update/upgrades and other things to get it back on its feet.  Being able to get to the files from another install gives you easy access to log files and so forth.

Ranch hand, maybe you've had better luck than I - development versions have pretty well trashed a hard drive, or even a pair of hard drives, for me when install gets the partitioning hopelessly screwed up.  Grub in particular has done me in when it gets badly confused.  

I think I'm always backed up so I may have some frantic hustling to do to get back going but I haven't lost anything important.

Yes, I have at least two other partitions with Natty and Meerkat and/or Lucid LTS on each hard drive.  I spent $10 for a USB hard drive enclosure for a left over laptop hard drive and I'm happily using it for testing new installs.  Even there, Oneiric Ocelot install on /dev/sdc6 grub decided to change the boot menu on /dev/sda.  I was able to get a Meerkat up and re-did the grub install properly.  In a few days I'll go back and do another install and pay more attention to the partitioning menu. 

Jerry

---

### Post by wildmanne39 on 2011-06-02
Hi, think you all for your answers that helps me sort out a few things. I really appreciate it.:)

---

