---
title: "Window 7 does not show up anymore in grub"
date: 2015-02-27
forum: New to Ubuntu
---

### Post by Jean-Baptiste_P on 2015-02-27
Hello ! 

I am a new ubuntu user and I run a dual-boot installation on an sd drive. To begin with, I had an issue to open my session because of a full disk. I solved it by deleting some files through ctrl+alt+f2 and reboot. Good here. 
But since then, grub does not show my window 7 os does not show in grub. 

I tested the boot-repair process, which did not change a bit of the situation, so I got a status for you : [http://paste.ubuntu.com/10442436/](http://paste.ubuntu.com/10442436/)
I also tried sudo-update-grub and got this result :
```
jean-baptiste@jeanbaptiste-System-Product-Name:~$ sudo update-grub[sudo] password for jean-baptiste: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

Could someone please give me a hint ? 

Jean-Baptiste

---

### Post by yancek on 2015-02-27
If you look at all of the ntfs (windows) partitions on your drives with the boot repair output, there is nothing in the section for Boot files and that usually shows in the boot repair script.  Is your windows system on the sda drive and the others are just data partitions?  Either the boot repair did not detect the windows boot files (which is unlikely) or they are no longer there.  Do you have a windows installation medium to repair the windows boot?

---

### Post by Jean-Baptiste_P on 2015-02-27
Hello,
My window system is on the sda drive and all the other are data partitions. I will download a W7 and try to repair the boot.
Thank you. 

Jean-Baptiste

---

### Post by Jean-Baptiste_P on 2015-03-02
So, I tried to launch a w7 installation usb key and repair the boot, but I got a message saying it was not able to repair the boot. Should I reinstall window ?

---

### Post by yancek on 2015-03-02
>  Should I reinstall window ? 		

If your windows installation medium didn't fix the boot files and you want windows, I guess that's your only option.  If you still want Ubuntu, make sure you have the Ubuntu medium to repair the bootloader so you can boot Ubuntu.

---

### Post by Jean-Baptiste_P on 2015-03-14
So I went all the way so reinstall window and got back the bootloader with an ubuntu livekey. Thx

---

