---
title: "Dual boot:: 2 HDD's linux /XP"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Blackmag+c on 2008-05-31
Ok, so Im planning to install linux on a second hard drive to the one I already have with xp installed.

Basically my question is : Is this simple, and ok to do?

and secondly

Can you get to your media files on windows in Linux? I.e Music etc? Or is there some format difference which denies access to the windows drive from the linux drive?

thanks.

---

### Post by powerpleb on 2008-05-31
> **Blackmag+c said:**
> Ok, so Im planning to install linux on a second hard drive to the one I already have with xp installed.

Basically my question is : Is this simple, and ok to do?

and secondly

Can you get to your media files on windows in Linux? I.e Music etc? Or is there some format difference which denies access to the windows drive from the linux drive?

thanks.

Linux should be able to access your Windows drive, but not vice versa. If you change your BIOS so that your soon to be Linux HDD is the first to boot, load up the live CD, install Ubuntu it should recognize Windows and automatically place an option in the boot loader. As they are on different hard disks, if you have any problems you can change the BIOS to load the Windows disk first and it should work as per usual.

---

### Post by Blackmag+c on 2008-05-31
Ok, so theres very little chance that i could fudge my xp install?

---

### Post by hyper_ch on 2008-05-31
the biggest chance of f***** up the xp install is when you select the wrong harddisk to install ubuntu to.

---

### Post by Blackmag+c on 2008-05-31
And the bootloader, If the linux HDD was your second it would be installed on hd1 (hd0 being the first disk: windows)?

---

### Post by powerpleb on 2008-05-31
> **Blackmag+c said:**
> And the bootloader, If the linux HDD was your second it would be installed on hd1 (hd0 being the first disk: windows)?
No, so far as I can tell (but I may be wrong) hd0 is the disk set by the BIOS to boot first. It's not necessarily the same as sda and sdb.

If you set the BIOS to boot from the Linux hard disk first it will install the bootloader there and everytime you boot up you will be given a choice between Ubuntu and XP.

---

### Post by kansasnoob on 2008-05-31
I used the following guide (and some other forum guides it links to) to plan my first dual hard drive-dual boot.

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

Since it's written for use with the alternate install CD it'd probably be wise to look at some other graphical tutorials using the Live CD:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

(NOTE, this second link has nothing to do with dual booting or dual hard drives, it simply has some good graphics of what the Ubuntu installer looks like using the Live CD.)

Personally, I've come to prefer having both (or more) of my operating systems on the same hard drive and adding/partitioning additional drives just for shared storage. That doesn't mean my way is better, it's simply a preference.

My personal preference for installing different OS's on two hard drives is to actually unplug the Windows drive while installing Ubuntu on the other drive and then making the necessary changes to GRUB after the Ubuntu install is complete and I've reconnected the Windows drive.

---

### Post by Blackmag+c on 2008-05-31
As I understand it, if I unplug the current 'master XP' IDE drive (as to ensure no fudging) and set it to cable select and then install ubuntu on the sata drive which will also be  set to 'cable select' then it should all work fine when the xp drive is replaced inside. Is this right?

---

### Post by powerpleb on 2008-06-01
> **Blackmag+c said:**
> As I understand it, if I unplug the current 'master XP' IDE drive (as to ensure no fudging) and set it to cable select and then install ubuntu on the sata drive which will also be  set to 'cable select' then it should all work fine when the xp drive is replaced inside. Is this right?

Yes, it won't touch your XP drive at all. So if you then set your BIOS to boot from the Ubuntu drive first you will need to reconfigure GRUB or edit menu.lst to get dual-booting happening as the XP drive will obviously not have been there to detect during the Ubuntu install.

---

### Post by Ducatiboy Stu on 2008-06-01
If you want to read your linux partition in Xp, install 

ext2ifs_1_11.exe into windows...

You can even move files in and out of your linux/drive partition in windoz

---

### Post by Blackmag+c on 2008-06-01
thanks all, very informative.

---

### Post by AldenIsZen on 2008-06-01
> **Ducatiboy Stu said:**
> If you want to read your linux partition in Xp, install 

ext2ifs_1_11.exe into windows...

You can even move files in and out of your linux/drive partition in windoz


 Be wary and backup your windows installation before trying anything drastic.. I used that program and I think it may have corrupted my partition tables.

---

### Post by Blackmag+c on 2008-06-02
yeh I was just wary about the actual install configuration rather than anything after that. I dont have worrys on the backup score
 
thanks.

---

