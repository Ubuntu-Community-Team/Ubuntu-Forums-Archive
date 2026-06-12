---
title: "Stuck at Grub prompt"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by bricabrack on 2011-12-16
Hello all, I recently attempted to upgrade from Natty to Oneric but with disasterous results.
I am now stuck at the Grub rescue prompt and can`t boot into Ubuntu or Vista (my other op sys) nothing seems to work. It won`t boot from the CD either. Help required urgently by a silver surfer. Thanks in anticipation.

---

### Post by oldfred on 2011-12-16
You should be able to boot from CD and may need that to repair system. Sometimes a total power shut down (cold boot) helps reset things. You have to make sure BIOS is set to boot CD first or if your system has a one time boot key (f12 on my system) use that to choose to boot CD. You do need a liveCD of the current version to make repairs.

You may be able to boot with these instructions if install is ok.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Otherwise you need liveCD to chroot into your system and update/repair.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot with screen shots
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by bricabrack on 2011-12-17
[SIZE=3]Hello all, Firstly many thanks to oldfred for the reply to my query[/SIZE][SIZE=3]. Unfortunately after trying the links supplied I am still experiencing problems with booting  into Ubuntu. I can`t progress beyond boot prompt! Anybody got any ideas because my hair is rapidly turning white.[/SIZE]

---

### Post by oldfred on 2011-12-17
When you say boot prompt. Is that grub rescue or grub> ?

If system is otherwise bootable sometimes Supergrub helps. But you may have video issues, or other system issues. Can you boot LiveCD?

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

If only minor repairs are required, this may help & from it you can run the boot_info_script that documents your system so we may be able to see exactly what is wrong.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

