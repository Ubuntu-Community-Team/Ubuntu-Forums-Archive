---
title: "Can't install Ubuntu 18.04 LTS in Dual Boot with Windows 10 Pro"
date: 2020-02-21
forum: New to Ubuntu
---

### Post by tony-99 on 2020-02-21
Hello. I have an ASUS ZenBook Flip 14 UX463FL with Windows 10 Pro pre-installed. 
I want to install Ubuntu for academic stuff. So I made a bootable Ubuntu USB stick with Rufus. Then I disabled FastBoot and SecureBoot on my laptop before lauching the installation. Everything is ok till the memory allocation step. The installation does not detect my hard drive so I cannot create a partition for Ubuntu. When I try to add the hard drive manually, the pc just crashes. There's a black screen showing many errors. I see "Error communicating to TPM chip" written like 5 or 6 times. I tried to create two disk partitions to see whether it will detect the non-allocated partition but this also does not work. 
Thanks in advance if you could help me.

---

### Post by CelticWarrior on 2020-02-21
> The installation does not detect my hard drive so I cannot create a  partition for Ubuntu. When I try to add the hard drive manually, the pc  just crashes.

Please stop!!!

If the drive isn't detected, whatever you're trying to do WILL have serious consequences.

The usual reason for a drive not being detected is an incompatible SATA mode. RAID or Intel RST aren't supported and you need to change it to AHCI. But keep in mind that you need to install AHCI support in Windows 10 first or it won't boot after that change.

---

