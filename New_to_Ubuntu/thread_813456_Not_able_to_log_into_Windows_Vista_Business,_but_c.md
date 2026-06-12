---
title: "Not able to log into Windows Vista Business, but can log into Kubuntu 8.04."
date: 2008-05-30
forum: New to Ubuntu
---

### Post by keith11 on 2008-05-30
Hi,

I have a dual booting system (Lenovo X61 tablet), with Windows Vista Business 32-bit and Kubuntu 8.04. This afternoon, I merged a small partition (30 MB) with my d: drive using Paragon Partition Manager in Vista. The partition manager asked me to restart the system to finish the merging on the small partition with d: drive. So, I restarted the system, and when it reached the grub boot list, and I selected Vista, it did not boot saying "System Error 12: The device could not be found (or started?)". I can boot fine into Kubuntu though. 

As I can't go any further beyond the Windows Vista selection, I can't even go to the Safe Mode. Earlier, when I had a similar (not the same) problem, I went to Safe Mode and ran "chkdsk c: /f" and it fixed the errors it found on c: drive. This had solved the problem and I was able to boot into Vista again. I tried using ntfsfix to fix the c: drive from Kubuntu, but it does not work and a message instructs me to run chkdsk. I formatted the small partition (30 MB), which I was trying to merge with d: drive, using Gparted in Kubuntu, and restarted the system, without any success. I could not boot into Vista. I used Hiren's Boot Disk as it had the Paragon Partition Manager tool in it, but, unfortunately, the CD does not load CDROM drivers once I select the Paragon Partition Manager in the menu after booting in the CD. 

I have recovery DVDs from Lenovo but I don't know if I can go into command prompt using them, like I could do for Windows XP. I need access to command prompt to run chkdsk. I am confused; I would really appreciate if I can get help in fixing this issue. I need to work in Windows Vista as soon as possible. Thanks a lot.

Keith.

---

### Post by iaculallad on 2008-05-30
Post your **fdisk -l** and **/boot/grub/menu.lst** using your kUbuntu. This might be a problem of moved partition.

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by Unix_Slayer on 2008-05-30
[**http://www.supergrubdisk.org/**]("http://www.supergrubdisk.org/")

---

