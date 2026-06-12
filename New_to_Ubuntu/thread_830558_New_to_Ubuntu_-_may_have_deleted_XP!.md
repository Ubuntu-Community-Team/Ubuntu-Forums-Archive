---
title: "New to Ubuntu - may have deleted XP!"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by DjChac on 2008-06-15
Hi everyone. I am really new to Ubuntu and is really digging the OS. I use windows most of the time but I was beginning to feel as if I am suffocating therefore I bought a Mac. A mew world opened for me and as I started reading about Unix, I stumbled across Linux Ubuntu. I really like the feel but as I installed Ubuntu I didnt dual boot so now I think XP is totally erased from my HD. I downloaded the boot CD from bootdisk.com but cant for the life of me to get xp booted. I have searched the forum but I can't find anything that gives a step by step instruction to reboot and reinstall both systems. As I mentioned before I am fairly new to Ubuntu. I really like an alternative os but I do need xp for my work. Someone please help. Thanks

---

### Post by powerpleb on 2008-06-15
Did you choose 'Use entire disk' when you installed?

Also open Accessories > Terminal and post the output of this command:```
sudo fdisk -l
```
This will show if there is a Windows partition on your PC.

---

### Post by Lupgaru on 2008-06-16
Did that once myself and I did delete XP by mistake. Not saying you did the same but in my case I reloaded XP (which deleted Ubuntu) then did a dual boot properly. My problem was not using the disc partitioner properly. Once I did that correctly I reinstalled my backups and had a nice dual boot. I wish you all the best. I bet you will enjoy Linux and do away with Windows.

---

### Post by akiratheoni on 2008-06-16
Go to Applications -> Accessories -> Terminal and type in:
```
sudo fdisk -l
```

Post the output here.

If you see a line that has NTFS in it (one of the first lines) then you probably have Windows on there.

---

### Post by nowshining on 2008-06-16
Hardy Heron should automatically use half. The last Time i looked @ the installer it auto-halved the hard drive.

---

### Post by djdarrin91 on 2008-06-16
To dual boot you should install xp first then install ubuntu,be sure NOT to select 'entire hard drive' when setting up your partition.good luck to ya:)

---

### Post by akiratheoni on 2008-06-16
> **nowshining said:**
> Hardy Heron should automatically use half. The last Time i looked @ the installer it auto-halved the hard drive.

This is true, it should set up an automatic dual-boot if you just clicked through the defaults.

---

### Post by hyper_ch on 2008-06-16
> **akiratheoni said:**
> This is true, it should set up an automatic dual-boot if you just clicked through the defaults.

Why? I don't think it should automatic dual-boot  -  and I don't think you should just click through the defaults but **read** what is written there.

---

