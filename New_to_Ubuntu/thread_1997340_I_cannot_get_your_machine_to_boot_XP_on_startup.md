---
title: "I cannot get your machine to boot XP on startup"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by sandip144 on 2012-06-05
Hi,

I have installed Ubuntu 12.04 in my Laptop HP Compaq NX 7300. Now i want to load Windows XP but i cannot Get a Boot at Start Up. I am unable to load XP now.

Please help. I only have Ubuntu in my Laptop now. I use Virtual Box but there also Windows does not load.

---

### Post by carl4926 on 2012-06-05
I take it you are referring to a real installation, not a virtual one. Your message is slightly confusing.

What errors if any do you get?

---

### Post by NikTh on 2012-06-05
Hi , 
from Ubuntu open a terminal and write this inside
```
sudo fdisk -l
```it will prompt you for your password , write it and post the results here , inside code brackets # 
Thanks

---

### Post by sandip144 on 2012-06-06
> **carl4926 said:**
> I take it you are referring to a real installation, not a virtual one. Your message is slightly confusing.

What errors if any do you get?
Sir,

I have Ubuntu 12.04 installed in my Laptop. Now i want to load XP for my Family. When i load XP cd and start laptop nothing happens and Ubuntu Starts. My Laptop do not ask on Startup for "Boot from Cd".
 Now what is the best alternative to install WIndows on my Laptop.

I even use Virtual Box for Windows but it shows message " No Bootable Disk Found".

---

### Post by wilee-nilee on 2012-06-06
Is this a a certified Microsoft disc?

---

### Post by z3nhakr on 2012-06-06
have you tried changing your boot configuration? look for the shortcut key on the bios startup screen that takes you to the bios setup. there should be a tab called boot and from there you can change the order of devices to boot from. Move CD/DVD to the top and press F10 to save and reboot. the screen is different on different PCs so i need the make and model to give you exact instructions.

---

### Post by blackbird34 on 2012-06-06
Are you sure you haven't installed Ubuntu on top of XP and taken up the computer's whole  hard drive? 
Run this in your Terminal:
```
sudo update-grub
```
It should repair the GRUB bootloader and list the operating systems you have (apart from the one you are currently using). If nothing is wrong with the bootloader nothing will happen. 

E.g. mine
```
nad@Nad:~$ sudo update-grub
[sudo] password for nad: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda4
done
nad@Nad:~$
```

This means that besides my current Ubuntu 12.04, i also have Ubuntu 11.04 on my computer (and no Windows - I accidentally wiped it a long while back :D )

---

