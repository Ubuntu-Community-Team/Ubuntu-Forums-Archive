---
title: "Ubuntu Windows dual boot goes straight to Ubuntu"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by p0ps1c1e on 2013-05-17
I've been checking the forum but all I can find is problems where it goes straight to Windows. Mine on the other hand just boots into Ubuntu. I'm fairly new with Linux so if anyone could help me out that would be great.

---

### Post by oldfred on 2013-05-17
Often need details. Since Ubuntu is working you can install this into your working install, your installer, or download it just as a repairCD. I like to have several repairCD as alternative ways to boot.

First have you run this just to see if it finds Windows from a terminal:
sudo update-grub

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by p0ps1c1e on 2013-05-17
I ran boot repair and it fixed the problem. Thanks

---

