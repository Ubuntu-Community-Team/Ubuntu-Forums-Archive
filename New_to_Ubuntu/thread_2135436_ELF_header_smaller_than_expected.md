---
title: "ELF header smaller than expected"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by ohlimi on 2013-04-14
Hi,
I use ubuntu 12.04 LTS 64bits that I installed on a SSD drive. It's was fine until ubuntu freeezes so I reset the computer. Since I have an error in grub rescue "ELF header smaller than expected".
 I tried to fix with boot-repair but an error occured.
[http://paste.ubuntu.com/5707349/](http://paste.ubuntu.com/5707349/)
I searched for a while so now I'm asking for a clue if anyone have one before formating the drive.

Thanks

---

### Post by Impavidus on 2013-04-14
Can you still boot an older kernel? I see you have two older kernels installed. If you can boot them, you can try to repair your current one.

Edit: but read next post. Oldfred is a guru on these matters.

---

### Post by oldfred on 2013-04-14
Your 60GB drive is MBR and your 2TB drive is gpt. 
Ubuntu will boot from gpt drives, but needs a tiny 1MB unformatted space with the bios_grub flag for core.img. Normally core.img is installed in the sectors after the MBR but before the first partition but with gpt that space does not exist.
But since only having an install on the MBR drive you should not have to install grub to gpt drive. But your install in sda may still need to be updated. 
Boot repair defaults to installing in all MBR, so that may be part of the issue?

I now only use gpt for all new drives. But it really is only required for drives over 2TB, but if drive will ever be transferred to a new computer with UEFI then it also need to be gpt. Since I am planning on building a new system soon, I put both efi and bios_grub partitions on my SSD using gpt partitioning. So I currently boot using the bios_grub, but new UEFI system will use efi partition. Neither are large so I do not lose much space.

       Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

---

