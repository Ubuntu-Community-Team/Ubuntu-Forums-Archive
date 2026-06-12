---
title: "Could any help me recover Windows?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pgtl10 on 2008-04-26
Earlier today I had a problem loading my Windows after installing Ubuntu. I used a bootdisk to access the Windows recovery console.

I typed "fixmbr" in the C drive which caused me to lose access to both my Ubuntu and Windows. I manage to get Ubuntu back but when I try to load Windows I the following message:

Error Loading Operating System

Any idea how to fix my partition?

The following link suggests to someone that he should use a bootdisk from bootdisk.com:

[http://www.softwaretipsandtricks.com...r-problem.html](http://www.softwaretipsandtricks.com...r-problem.html)

Should I try a bootdisk as well?

---

### Post by Joeb454 on 2008-04-26
Is it a Windows XP partition or Windows Vista?

---

### Post by pgtl10 on 2008-04-26
Xp

---

### Post by Joeb454 on 2008-04-26
So you booted from the XP install disc, got to a command prompt, and then typed ```
fixmbr
``` and it still wouldn't let you boot Windows?

---

### Post by pgtl10 on 2008-04-26
yes

---

### Post by Joeb454 on 2008-04-26
It could be that your system files under Windows are corrupted :( Have you installed anything or done any Windows updates recently that could have caused this?

---

### Post by pgtl10 on 2008-04-26
Ubuntu is the last install. No Windows updates recently.

---

### Post by Joeb454 on 2008-04-26
Have you tried adding Windows to the GRUB bootloader?

---

### Post by pgtl10 on 2008-04-26
No could you show me?

---

### Post by Joeb454 on 2008-04-26
Ok so open up a terminal, and type (or copy) ```
sudo fdisk -l
``` and paste the output here :)

A couple of things:
1) That is a lowercase 'L'
2) You will be asked for a password, but it will not show any input while you type it :)

---

### Post by pgtl10 on 2008-04-26
Here you go:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c4b2ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4321    34708401    7  HPFS/NTFS
/dev/sda2   *        4322       19553   122351040   83  Linux
/dev/sda3           19554       19929     3020220    5  Extended
/dev/sda5           19742       19929     1510078+  82  Linux swap / Solaris
/dev/sda6           19554       19741     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Joeb454 on 2008-04-26
Hmm...that's odd. Your NTFS partition doesn't seem bootable. I'm pretty sure it should be

---

### Post by st33med on 2008-04-26
Ok, you might need to sit down on this because you got pwned pretty badly :)

Somehow, you removed the boot flag while installing. You need to burn a [gparted LiveCD]("http://gparted.sourceforge.net/livecd.php"). Then, go in and, where it says flags, enable a boot flag for the NTFS partition and continue.

---

### Post by pgtl10 on 2008-04-26
> **st33med said:**
> Ok, you might need to sit down on this because you got pwned pretty badly :)

Somehow, you removed the boot flag while installing. You need to burn a [gparted LiveCD]("http://gparted.sourceforge.net/livecd.php"). Then, go in and, where it says flags, enable a boot flag for the NTFS partition and continue.

Would a Ubuntu live CD work?

Edit: I've been sitting down for roughly 15 1/2 hrs. So if you can get me standing that be great.

---

### Post by adult swim on 2008-04-26
you could from a terminal type in ```
sudo apt-get install gparted
```
and then go to system/administation/partition editor and make your /dev/sda1 bootable from there

---

### Post by st33med on 2008-04-26
Probably, yes. You have to do in the terminal:
```
sudo gparted
```

Else if you don't do sudo, it will tell you it is a 'Weapon of Mass Destruction' :)

No, seriously, it will.

Or, you could do what adult swim said, but my method is more safe because you aren't operating while on the hard drive.

---

### Post by Joeb454 on 2008-04-26
It might do, gparted is on the Ubuntu Live CD.

---

### Post by pgtl10 on 2008-04-26
Got the boot check for the Windows partition. I'm going to reboot.

Edit: didn't work

---

