---
title: "Vista erased my fedora partition?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by thesonisshining on 2008-06-26
I know that this is about Fedora, but since I'm already a member here and most distro's are pretty similar, here's my dilemna.

1. I installed Fedora on to an external hard drive.
2. I shutdown Fedora but it locked up before shutting off the PC.
3. I restarted the computer trying to get Vista and all that would pop up was the word GRUB.
4. I did a system restore point a few days back.
5. I tried to restart the PC and load Fedora again but i get an error that says that my OS failed to load.

I really hope someone can help me. I would like to have a traveling OS.

Thanks in advance.

---

### Post by bodhi.zazen on 2008-06-26
What kind of data is on the external hard drive ?

Most likely you need to re-isntall grub

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

Although if you installed Fedora with default settings you likely have a LVM partition, in which case do you have a boot partition ?

---

### Post by thesonisshining on 2008-06-26
I deleted the prior partition (XP).
Installed an LVM partition. 
Boot pratition...I have no idea.
How do i re-install GRUB without messing up Vista?

Sorry, I'm not much of a linux person. Last time I installed ubuntu and I followed a screencast...so I don't have much knowledge ion this area. I am however, good at following instructions.

---

### Post by bodhi.zazen on 2008-06-26
NP

Start with an inventory of your partitions.

Boot a live CD (Fedora is fine)

Show us the output of :

```
sudo fdisk -l
```

The link I gave you will walk you through installing Grub. It should not damage windows, although we may need to make a few edits.

You need a separate boot partition with LVM. If you overwrote the boot partition we will need to manually make one, then mount your LVM and look at the LVM format and kernel ...

I guess what I am saying is if you do not have a /boot partition it will be a fairly technical recovery ...

---

### Post by thesonisshining on 2008-06-27
So apparently the Fedora disc I have doesn't run live...I'm in the process of trying to figure out how to burn an ISO to disc using Vista since my Nero doesn't work with Vista...A may take a moment.

---

### Post by thesonisshining on 2008-06-27
I found some free software to do the trick but it's late. I'll be back tomorrow.

---

### Post by thesonisshining on 2008-06-27
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ddd1ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17931   144030726    7  HPFS/NTFS
/dev/sda2           17932       19457    12257595    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x916b916b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14        4863    38957625   8e  Linux LVM

---

### Post by bodhi.zazen on 2008-06-27
/dev/sdb1 * 1 13 104391 83 Linux

This is almost certainly a boot partition.

With the usb drive plugged in, reinstall GRUB

Use "root (hd1,0)" at the grub prompt

From a live CD (ubuntu will be fine)

```
sudo grub

grub> root (hd1,0)
grub> setup (hd0)
```

The "grub>" indicates the grub prompt (and not part of the commands you need to enter).

Quit grub
reboot

We *may* need to edit your grub menu, but we can do that from Fedora.

---

