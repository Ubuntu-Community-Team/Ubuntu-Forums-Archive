---
title: "Add Additional HDD on Ubuntu 16.04"
date: 2017-09-16
forum: New to Ubuntu
---

### Post by ramster2 on 2017-09-16
Hello,

I recently built an Ubuntu machine and installed version 16.04.
I used 1 HDD when I built it. Now, I have installed an additional HDD connected directly to the motherboard using SATA cable.
My computer sees that 2nd HDD as a removable storage (I can't even rename the darn HDD).

My question is:
How do I make that HDD permanently installed? just like in Windows PC with 2 drives, C: and D:

I'd be forever grateful if you could provide a step-by-step guide because I know absolutely nothing about linux.
Thanks a million !

---

### Post by oldfred on 2017-09-16
Basically you have to partition (gpt over MBR recommended) and have at least one partition.
If Linux formatted you also have to give yourself ownership & permissions. If you label it then it will auto mount a partition that is labeled with the label. I use labels on some partitions I do not want or use every time.
But for partitions you want always mounted you need to add an entry to fstab. Best to use an example to paste into fstab, but using your unique UUID & mount point.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. +

I do like to have an Ubuntu install on every hard drive, even is just for emergency boot on a drive normally used for data. So I partition all new drives using gpt, and first two partitions are the ESP - efi system partition for UEFI boot and a bios_grub for BIOS boot. And the a Linux partition, large data partition, backup partition for data from other drives (which is not really backup, just another copy as not versioned), and other test installs. Or I do not make just one large data partition.

Info on mounting & permissions, note corrections in post #8.
[https://ubuntuforums.org/showthread.php?t=1795369](https://ubuntuforums.org/showthread.php?t=1795369)

---

