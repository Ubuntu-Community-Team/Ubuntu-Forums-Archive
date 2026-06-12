---
title: "GRUB2 Won't Launch at Boot? (13.04)"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by WTWkPTm on 2013-07-31
So, I installed Ubuntu 13.04 with Windows 7 already installed (not alongside) but when I power up my laptop (Samsung series 3) no GRUB2 menu appears and I'm presented with my Windows 7 boot up screen.
I installed GRUB onto /dev/sda which I heard somewhere is the MBR and where I was supposed to put GRUB.

Please help! I chose Ubuntu for the huge and friendly community so I hope someone can help me :)
Thanks in advance
- Anthony :)

---

### Post by 7R6Kh6w on 2013-07-31
....i think you' need grub repair,try to boot from your live cd if you can do it from there.

---

### Post by WTWkPTm on 2013-07-31
Thanks, I'll try it.

---

### Post by oldfred on 2013-07-31
Some links.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

