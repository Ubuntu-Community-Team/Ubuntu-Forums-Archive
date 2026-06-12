---
title: "Ubuntu won't recognize HDD! :("
date: 2008-10-24
forum: New to Ubuntu
---

### Post by SilverShadow118 on 2008-10-24
Ubuntu won't recognize my HDD! :( I'm currently using Ubuntu live. I've tested both the CD and my memory for defects - both came out clean. I'm using Ubuntu v. 8.04 LTS. I'm really pretty lost and don't know what to do. Please help. :(

---

### Post by niyonk on 2008-10-24
Is it an internal or external HDD?
Is it recognised by any other OS, M$ or Apple??
How long have you had it?
What shows on Gparted?

We need to know most of the above to help, 
Cheers!

---

### Post by SilverShadow118 on 2008-10-24
It's an internal drive. It is recognized by M$ (M$ is installed on one of two partitions). It's a few years old. Nothing is shown on Gparted. :/

---

### Post by niyonk on 2008-10-24
WoW! OK, I am not exactly sure what is happening...

Maybe we might wanna give Nautilus or sudo fdisk -l a try.
It might be a hardware issue, and I am not very familiar with hardware issues.
Also, is it a desktop or laptop?

---

### Post by SilverShadow118 on 2008-10-24
'sudo fdisk -l' gives nothing back in the terminal. What's Nautilus?
It's a desktop.


EDIT: Also

ubuntu@ubuntu:~$ sudo fdisk /dev/hda

Unable to open /dev/hda

---

### Post by niyonk on 2008-10-24
Ok, i ran around the forums and found [this]("http://ubuntuforums.org/showthread.php?t=919905")...
More specifically the 10th post, hopefully it will solve it this time

---

### Post by SilverShadow118 on 2008-10-24
It gets stuck at 15% when I choose 'Install Ubuntu' and 'Try Ubuntu'. >.<

---

### Post by northern lights on 2008-10-24
SilverShadow, can you please post the outputs of```
sudo fdisk -l
``````
cat /etc/fstab
``````
sudo mount -a
```and```
cd /media && ls
```in that order? Thank you.

---

### Post by niyonk on 2008-10-24
Hm...One problem solved, one coming up :(

Anyway...so, it seems the hang-up you are getting is mostly due to either the CD being defective, Giving the root partition a small size (should not be less than 4GB), not enough RAM on your PC....

Well, post your full specs (CPU, RAM, Hardrive)
In the meantime...i will try and find more reasons as to why you might be having the problem :)

---

### Post by SilverShadow118 on 2008-10-24
1. No output for 'sudo fdisk -l' :(

2. "unionfs / unionfs rw 0 0
    tmpfs /tmp tmpfs nosuid,nodev 0 0"

3. No output for 'sudo mount -a' :(

4. "/media$"

You're welcome. ^^

---

### Post by niyonk on 2008-10-24
When you say that it is stuck at 15% (the install), I am assuming it recognised your hardrive after the fix and let you partition no?

---

### Post by SilverShadow118 on 2008-10-24
I have 2 gigs of SDRAM. I have tested both the ram and my CD for defects - they have none. Each partition is 39-40 gigs. Quad core Q6600. It's a seagate. Model number: ST380020A. I don't think that the GFX card is needed but I'll post stuff about it anyway. Nvidia GT 7700

---

### Post by SilverShadow118 on 2008-10-24
> **niyonk said:**
> When you say that it is stuck at 15% (the install), I am assuming it recognised your hardrive after the fix and let you partition no?

No.My Harddrive isn't recognized at all. :/

---

### Post by niyonk on 2008-10-24
> **SilverShadow118 said:**
> No.My Harddrive isn't recognized at all. :/

AFAIK, the percentages show when it is formatting your partitions and then installing the stuff :confused:

EDIT: [this]("http://tillamookrage.blogspot.com/2007/09/debian-derivatives-stuck-on-install.html") might be interesting

---

### Post by SilverShadow118 on 2008-10-24
Sorry for the confusion. The 15% was just an estimate as to how much installing was done (before anything about detecting hard drive etc). >.<

---

### Post by Coreigh on 2008-10-24
> EDIT: Also

ubuntu@ubuntu:~$ sudo fdisk /dev/hda

Unable to open /dev/hda

Have you tried hdb or hdc or sda? I have seen the dev be sda quite often.
Also what *does* show up in gparted (Gnome partition editor)?

---

### Post by northern lights on 2008-10-24
This is really wicked.

The LiveCD not finding an internal hdd is rather odd.

Off hand, I have no idea why this should happen. On top of that, i's late in Europe and I've gotta catch some sleep - I certainly won't come up with a reason tonight.

However here's one quick suggestion of an alternative way of installing that might just work, despite not knowing why the LiveCD fails:

1. Boot your Windows
2. Download the current unetbootin for the Win32 platform from [http://lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html")
3. Execute the downloaded file
4. Choose "Ubuntu 8.04 NetInstall" for the distribution
5. Choose the respective drive as location
6. Apply
7. Reboot
8. A new entry should have been added to your bootmenu. Choose that.
9. If your drive is recognized and you get to partitioning, make sure you do not choose "guided partitioning", and select "manual partitioning" instead (otherwise your Windows partition(s) will be formatted!)
10. Create a "/" root partition (minimum 5-10gig) and a "swap" partition (1-2 gig or once to twice your physical memory / RAM). While not required I'd recommend creating a separate "/home" partition also, if you have the space -  greatly eases reinstalls. If necessary, resize Windows partition(s).
11. At the end make sure you choose to install "ubuntu-desktop" (press SPACE bar to select), otherwise you'll end up with commandline only.
12. This should be it.

---

### Post by SilverShadow118 on 2008-10-24
When I enter 'sudo fdisk /dev/hda' in the terminal, I get "Unable to open /dev/hda" as an output.

What is hdb, hdc and sda? >.< 

This is what is shown up in Gparted after opening and refreshing: 

[[IMG]http://img353.imageshack.us/img353/4590/screenshotgpartedpj8.th.png[/IMG]](http://img353.imageshack.us/my.php?image=screenshotgpartedpj8.png)[[IMG]http://img353.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)


EDIT: I'll try that now, northern lights. Thank you.
NOTE: I have two computers so I'll still be on the forums.

---

### Post by Coreigh on 2008-10-24
It is possible that the disk is not associted as 'hda', it may be 'sda' or 'hdb' or 'sdb' for that matter.

you would type in the terminal "sudo fdisk /dev/sda" (no quotes)

the letters mean hd = hard disk a = first one, b = second one etc.
sd also means hard disk but it was origionally used to identify SCSI disks but is not often used for SATA disks and sometimes sd gets used because of the hardware on the motherboard.

When you open gparted (partition editor) does that show any disks?

---

### Post by Coreigh on 2008-10-24
**Sorry double post.**


It is possible that the disk is not associted as 'hda', it may be 'sda' or 'hdb' or 'sdb' for that matter.

you would type in the terminal "sudo fdisk /dev/sda" (no quotes)

the letters mean hd = hard disk a = first one, b = second one etc.
sd also means hard disk but it was origionally used to identify SCSI disks but is not often used for SATA disks and sometimes sd gets used because of the hardware on the motherboard.

When you open gparted (partition editor) does that show any disks?

---

### Post by SilverShadow118 on 2008-10-24
No disks are shown in Gparted

---

