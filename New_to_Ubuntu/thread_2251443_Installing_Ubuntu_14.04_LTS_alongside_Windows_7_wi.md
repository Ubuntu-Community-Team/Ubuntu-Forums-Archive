---
title: "Installing Ubuntu 14.04 LTS alongside Windows 7 with RAID"
date: 2014-11-04
forum: New to Ubuntu
---

### Post by joaoavp on 2014-11-04
Hello! I am trying to install Ubuntu 14.04 LTS alongside Windows 7 and I show you in the attachments how my partitions look like. I am a complete beginner and all I know is that I should create at least two partitions, one for swap and another with ext4. My question is, if I pick INSTALL ALONGSIDE WINDOWS 7, what will happen? Will Ubuntu be installed using the free space and so I shouldnt worry about partitioning manually? Also, I can only do another partition, because itll say unusable space instead of free space.

Thank you so much in advance.

---

### Post by Jimit_Shah on 2014-11-04
Hi there,
It's good question.
Ubuntu defenetely gona install along with windos 7 if you choose that option.
But after that you may not get the all the partition in ubuntu. i am not sure but 99% you not gona access whole hdd.
It's better to create a new partition from windows 7 and select something else option from installtion and install ubuntu over that.
I have experience it wont effect anything and smoothly u can access whole hdd partition on windows as well as ubuntu.
Thanks,
Jimit

---

### Post by sudodus on 2014-11-04
> **Jimit_Shah said:**
> Hi there,
It's good question.
Ubuntu defenetely gona install along with windos 7 if you choose that option.
But after that you may not get the all the partition in ubuntu. i am not sure but 99% you not gona access whole hdd.
It's better to create a new partition from windows 7 and select something else option from installtion and install ubuntu over that.
I have experience it wont effect anything and smoothly u can access whole hdd partition on windows as well as ubuntu.
Thanks,
Jimit

+1

Use Windows tools to shrink the Windows partition but avoid 'dynamic partitions', because they don't work with linux. You can create partitions when booted from the Ubuntu install DVD/USB boot drive with the tool ***gparted*** before starting the installation, or within the installer. I find gparted intuitive and easy to use.

The option 'Something else' at the partitioning window gives you better control of what happens, and I also recommend using it.

---

### Post by oldfred on 2014-11-04
You are showing jmicron RAID.

I really do not know RAID, but desktop installer is not fully configured yet for RAID installs. With 12.04 we had the alternative installer for RAID and LVM. They discontinued the alternative installer with 12.10 and said either use server install and add desktop of choice or use 12.04 and upgrade.
I see now with 14.04 they have LVM as an install option. And reports show installer does see RAID where it did not before, but grub doe not yet correctly install in RAID, so not fully implemented yet for RAID.

RAID is a bit more complicated, so may be better to use server installer. You may be able to install with Desktop isntaller and use Boot-Repair to correctly install grub. If it does show an option to install, you must install grub to the root of the RAID not the MBR of the hard drive.

---

