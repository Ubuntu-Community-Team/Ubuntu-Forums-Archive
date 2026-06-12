---
title: "how do i resize a partition with gparted?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Gopler on 2008-08-01
Hi.
I have been playing a bit with other distros in a virtual machine, and so far everything is great. Now i just want to play around with 3d acceleration on the other distros, so i have to dual-boot with ubuntu. but how do i resize my ubuntu /home partition? all of the options in gparted is grayed out.

How do i resize a ubuntu partition, to make room for other distros?

---

### Post by mevets on 2008-08-01
Im guessing your home partition is mounted. You cant make changes to it while its mounted, so you just need to unmount it. Almost all distros have partitioning tools included during the installations process, where none of the drives are mounted so it might be easiest to just do it during install.

---

### Post by bks on 2008-08-01
> **mevets said:**
> [...]it might be easiest to just do it during install.

You could load up an Ubuntu LiveCD and use gparted. All you need to do once your there is click and drag to resize your desired partition.

---

### Post by bobpur on 2008-08-02
I think you could go to [www.distrowatch.com](www.distrowatch.com) and download the Gparted live ISO burn it to a bootable cd. Start your machine with the Gparted cd you just burnt and resize away.You'll be running off the cd and won't be using Ubuntu so you shouldn't have any problem

Good luck.

---

### Post by Gopler on 2008-08-02
nice. that sounds easier than i thought :) thank you.
When i dual boot two distros, do i have to make another swap partition or can they use the same? and is there other things i don't need two of ?

---

### Post by collinp on 2008-08-02
> **Gopler said:**
> nice. that sounds easier than i thought :) thank you.
When i dual boot two distros, do i have to make another swap partition or can they use the same? and is there other things i don't need two of ?

They can use the same swap, as long as they are on the same hard drive as the swap. I may be wrong about the last part tho.

---

### Post by Rocket2DMn on 2008-08-02
The swap can be on different drives, it should just be posted in each system's fstab file.  This works as long as you don't hibernate one install then try and use another, since the swap space is used during hibernate.

---

### Post by strongboww on 2008-08-02
got the same problem here;

my complete systemdisk is fully formated in ext3 für ubuntu(and of course a swap), so its 2 partitions now

but for a new game unfortunately i need winxp and so i wanted to resize with gparted

can i just resize the system partition on hd1 and then use the new free space to install win again?

i also attached the window of gparted

tia

---

### Post by Rocket2DMn on 2008-08-02
Yes, you will shrink your sda1 partition to make empty space.  That is where you will install windows.
After re-installing windows you will have to reinstall grub  - have a look at [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp]
I suggest using the Super GRUB Disk since it makes life easy - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

