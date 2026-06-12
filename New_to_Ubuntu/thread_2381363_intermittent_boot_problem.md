---
title: "intermittent boot problem"
date: 2017-12-30
forum: New to Ubuntu
---

### Post by wrongusername2 on 2017-12-30
I have intermittent boot problem and every time booting has become a guessing game. 

Last week I installed Ubuntu on a clean hard drive(HD1). Then created an image of the whole disk using DD. Then restored the image to HD2. I did this to practice DR scenario. After the restoring **I fixed the /etc/fstab** so it is pointing to new UUID. **Then ran boot-repair**. I still have boot issues. This is not dual boot.

**Problem**.
1) Turn on the machine
2) Keys starts blinking. This means machine will not even go to BOOT-screen
3) Press ALT_CRTL_DEL
4) Repeat above steps four-five times. Then during one of the attempt machine will go to BOOT screen. There I will select UBUNTU.
5) I get GRUB screen
6) Then OS comes up.

Boot-repair did not help, nor changing boot-loader name to "windows boot manager".

Will uninstalling GRUB help? If so how do I do it?
Should I update BIOS? I did update to latest BIOS lastweek. I can do it again if that is going to help.


**BLKID output**
  /dev/sda1: UUID="BD51-0FC4" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="5cfd3987-de84-400c-a4f3-43c50556aeeb"
  /dev/sda2: UUID="3ae6b0af-d24d-4f49-943c-231cab85a5a4" TYPE="ext4" PARTUUID="02720a2d-db7e-494e-a3cf-6edc6f6d4eaf"
  /dev/sda3: UUID="2af41562-baa3-4c67-9117-22507935b9c6" TYPE="swap" PARTUUID="e7583af4-549b-4f39-8191-74fc70e8add9"
  /dev/sdb1: LABEL="Nothing2Nt" UUID="13342352595E0BA2" TYPE="ntfs" PARTLABEL="Nothing2Nt" PARTUUID="7c9a9a30-934b-4c27-b955-4bbbcac3ed26"
  /dev/sdb2: LABEL="Nothing2Ex4" UUID="56d1c7d6-5ca9-49d6-a7c8-35afdfc9c873" TYPE="ext4" PARTLABEL="Nothing2Ex4" PARTUUID="7dc6b728-60df-4565-8f8f-aa26656ee770"


Please let me know what should I do.

Thanks

---

### Post by wrongusername2 on 2017-12-30
Solved it by reinstalling the bios even though it was latest. Plus removing 'ubuntu' from boot-mgr and just having 'windows....'

---

