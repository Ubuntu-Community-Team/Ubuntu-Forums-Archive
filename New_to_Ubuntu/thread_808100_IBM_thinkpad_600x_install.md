---
title: "IBM thinkpad 600x install"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by jjfourtwenty on 2008-05-26
Hi, I'm having some problems installing dapper on an Ibm thinkpad 600x. The installation runs fine until it comes to load the partitioner at which point the system hangs indefinitely. I am a relative newbie to Ubuntu and it has been around a year since I last used it on a system so any help would be extremely welcome.

---

### Post by quelx on 2008-05-26
Have you considered using the latest Ubuntu?  The alternate iso?

A great site for Thinkpads

[http://www.thinkwiki.org/](http://www.thinkwiki.org/)

---

### Post by jjfourtwenty on 2008-05-26
Sorry, I seemed to have a metal lapse! I am trying to install Hardy, not Dapper. Also I am using the alternate ISO

---

### Post by quelx on 2008-05-26
Here is a guide for 7.10 (probably close enough to 8.04) on the 600E (again probably close enough to the 600X)

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_600E](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_600E)

Unrelated to the partitioning issue notice the author's recommendation for using Xubuntu instead.

---

### Post by jjfourtwenty on 2008-05-26
hmm.. still isn't working. It doesn't seem to be able to detect the HDD, even though there is noticeable hard drive activity elsewhere in the installation

---

### Post by quelx on 2008-05-26
from the alternate CD can you **ALT-F2** and open a new terminal?

Does
```
sudo fdisk -l
```
show the drive?

---

### Post by jjfourtwenty on 2008-05-26
can't open terminal in alternate cd, which sucks.

---

### Post by jjfourtwenty on 2008-05-26
Fluxbuntu seems to work. no idea why but hey, it's something

---

### Post by spiderbatdad on 2008-05-26
Probably need some boot parameters to compensate for the apic bios settings.
From the install options screen press F6. Delete the end of the kernel line where it says --quiet splash. Replace --quiet splash with lapic pci=routeirq

Other  possible good options include:

noapic nolapic

or

acpi=off

Make any changes permanent by editing the file /boot/grub/menu.lst
below ###END DEFAULT OPTIONS####
at the end of the line that begins with the word 'kernel.'

[http://spiderbatdad.wordpress.com/ubuntu-boot-problems/](http://spiderbatdad.wordpress.com/ubuntu-boot-problems/)

---

### Post by lincoln32 on 2008-05-26
I JUST AM FINISHING IBM R40 WITH DUEL BOOT XP AND HARDY AND HAD TO USE A GPARTED BOOT DISK BUT ALSO FOUND A BAD SECTOR ON HARD DRIVE THEN REPAIRED BUT WORKING WELL NOW:popcorn:

---

### Post by kerry_s on 2008-05-26
> **jjfourtwenty said:**
> Fluxbuntu seems to work. no idea why but hey, it's something

```
  ThinkPad 600X

This pages gives an overview of all ThinkPad 600X related topics.
Standard Features

    * Intel Mobile Pentium III 450, 500 or 650MHz
    * Neomagic MagicGraph256ZX with 4MB
          o 13.3" TFT display with 1024x768 resolution 
    * 64MB PC-100 Memory standard
    * 6 or 12GB HDD
    * CS4624/CS4297A Audio controller
    * MiniPCI slot with a Mini-PCI Modem card
    * IrDA 1.1
    * UltraslimBay with one of the following:
          o CD-ROM drive
          o DVD-ROM drive 
    * (2) Type II CardBus slots or (1) type III 
```

have you upgraded the ram to it's max?

---

### Post by jjfourtwenty on 2008-05-28
Well the install is no running, disks have been partitioned. currently at 56% install after, wait for it, 2 days!

anyone care to guess at time left to completion?

---

### Post by kerry_s on 2008-05-28
> **jjfourtwenty said:**
> Well the install is no running, disks have been partitioned. currently at 56% install after, wait for it, 2 days!

anyone care to guess at time left to completion?

what's not installing?
how much ram?

2days you might as well turn it off it's locked up or you ran out of resources.

---

### Post by jjfourtwenty on 2008-06-04
just purchased a dell inspiron 1525. works much better!

---

