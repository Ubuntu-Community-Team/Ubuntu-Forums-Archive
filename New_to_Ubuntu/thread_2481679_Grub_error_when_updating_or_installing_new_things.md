---
title: "Grub error when updating or installing new things"
date: 2022-12-06
forum: New to Ubuntu
---

### Post by neul2 on 2022-12-06
```

Setting up grub-pc (2.06-2ubuntu7) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is not configured yet.

dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                      Errors were encountered while processing:
 grub-pc
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I  thought this error might be related to dual boot and plus I decided  to  use Linux full-time, I deleted Win 10 partition and from grub menu. 
But I still have this issue. And I had this error when I was using dual boot too.
I have no problem with booting into Ubuntu and Win 10 (before I deleted it).
Tried  things such as boot repair, purging grub and reinstalling (this might've had it worse) but nothing worked for me.
What can cause this issue? How can I solve it?

---

### Post by oldfred on 2022-12-06
Post link to summary report from Boot-Repair.
The grub-pc package is for BIOS based installs. If system is UEFI, you use grub-efi-amd64.
And if UEFI best to have gpt partitioning. Microsoft required vendors to use UEFI/gpt with all installs starting 10 years ago.

Be sure to boot Ubuutnu live installer in same mode as install, either UEFI or BIOS. And use ppa to add Boot-Repair.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by neul2 on 2022-12-07
[https://paste.ubuntu.com/p/Xd4g5YQzKZ/](https://paste.ubuntu.com/p/Xd4g5YQzKZ/)
Boot Repair Summary

---

### Post by oldfred on 2022-12-07
You have UEFI system with Ubuntu installed in UEFI boot mode to gpt partitioned drive.
But you are getting some sort of update error on this file. 
libdevmapper.so

My system does show that libdevmapper file but it is for LVM which I am not using.
Synaptic shows I have it, but terminal does not let me reinstall it. So part of installing LVM or RAID or something related.
Can you reinstall lvm? Which has libdevmapper as a requirement.
sudo apt install lvm2

---

### Post by neul2 on 2022-12-08
Boot info, [https://paste.ubuntu.com/p/nsmH3Hf6hM/](https://paste.ubuntu.com/p/nsmH3Hf6hM/), might be helpful.
Boot repair info, [https://paste.ubuntu.com/p/g8PNgxhybC/](https://paste.ubuntu.com/p/g8PNgxhybC/), still same error.
 

Lvm2 already installed in my system and live Ubuntu USB and I reinstalled it as well.
And I can open it in terminal by "lvm".

---

### Post by oldfred on 2022-12-08
Lets try a reinstall

sudo apt-get install --reinstall lvm2

That file is a dependency of lvm2 and should be there if lvm is installed.

---

### Post by neul2 on 2022-12-19
The issue resolved by running 
"sudo apt remove shim-signed grub-efi-amd64-bin --allow-remove-essential"

---

