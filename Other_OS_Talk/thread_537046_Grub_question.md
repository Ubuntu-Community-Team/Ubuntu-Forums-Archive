---
title: "Grub question"
date: 2007-08-28
forum: Other OS Talk
---

### Post by happysmileman on 2007-08-28
I have a question... I have GRUB installed on my main hard drive, which is dual-booting Ubuntu and Windows, and I have an external drive which has Gentoo on it, but won't boot.

Grub on my main drive will not recognise my external drive and therefore won't boot, and I can't select external drive in BIOS either.

Will installing GRUB on a floppy disk help this in anyway?

If so, how do I do it, I have literally never used a floppy disk in years, and I was only about 8 or 9 when I did, so I know absolutely nothing, I know that it needs to be formatted etc. first but have no idea how to do it or install grub onto it

---

### Post by ajgreeny on 2007-08-28
If you plug the usb drive in and it is automounted, as many are, you can simply go to the grub menu.lst in the gentoo installation on the usb drive and copy the entry in that which relates to gentoo to the ubuntu grub menu.lst file.  You will probably need to change the partition information in this entry, I imagine, as otherwise it may not be where the ubuntu grub thinks it is, so make sure you know what ubuntu thinks the gentoo partition to be by either right clicking on the desktop icon, if there is one, and selecting properties, or using the terminal command sudo fdisk -l to see which the partition is.

I hope that all makes sense to you.  If not ask again about the bits you don't understand.

---

### Post by happysmileman on 2007-08-28
> **ajgreeny said:**
> If you plug the usb drive in and it is automounted, as many are, you can simply go to the grub menu.lst in the gentoo installation on the usb drive and copy the entry in that which relates to gentoo to the ubuntu grub menu.lst file.  You will probably need to change the partition information in this entry, I imagine, as otherwise it may not be where the ubuntu grub thinks it is, so make sure you know what ubuntu thinks the gentoo partition to be by either right clicking on the desktop icon, if there is one, and selecting properties, or using the terminal command sudo fdisk -l to see which the partition is.

I hope that all makes sense to you.  If not ask again about the bits you don't understand.

The problem is that GRUB on main drive (Ubuntu) doesn't seem to recognise the hard drive at all, as in it only sees hd0, not hd1. Any workaround for this or is it a BIOS/drive problem?

---

### Post by ajgreeny on 2007-08-28
What do you mean "grub doesn't recognise the hard drive"?  You have to point grub to that drive with the partition info as I said.

---

### Post by happysmileman on 2007-08-28
I mena going into the grub command line it only recognises one hard drive (hd0) and two others (fd0 and fd1), therefore it can't get to the external drive  (which should be hd1) using menu.lst and can't boot

---

### Post by Midwest-Linux on 2007-08-28
> **happysmileman said:**
> I have a question... I have GRUB installed on my main hard drive, which is dual-booting Ubuntu and Windows, and I have an external drive which has Gentoo on it, but won't boot.

Grub on my main drive will not recognise my external drive and therefore won't boot, and I can't select external drive in BIOS either.

Will installing GRUB on a floppy disk help this in anyway?

If so, how do I do it, I have literally never used a floppy disk in years, and I was only about 8 or 9 when I did, so I know absolutely nothing, I know that it needs to be formatted etc. first but have no idea how to do it or install grub onto it

 Can't you run Gentoo out of Windows using a Live CD? Then since   a external hard drive will be recognized in Windows, you should be able to run Gentoo that way. Just like a live desktop of say Feisty 7.04 can be run in windows when you put the Live Desktop  disc in windows. Unless I am missing this that Gentoo does not have a live desktop like Feisty does.... I haven't used Gentoo...I'm guessing at this....

---

### Post by fistfullofroses on 2007-08-28
You could try this:

title External
kernel (hd0,1)/boot/kernel root=/dev/sda1

title M$ Winsh!t
root  (hd0,0)
makeactive
chainloader +1

---

### Post by happysmileman on 2007-08-29
Ok that worked, now to get it to boot properly... Linux (gentoo that is) is hard

---

### Post by fistfullofroses on 2007-08-31
Glad it worked. As for Gentoo... I really have no used it much, so no clue. I personally prefer Puppy Linux for back up and what not, and GoboLinux for daily use (though I ported Gentoo Portage to it so as to increase available packages). I use Ubuntu for my gaming needs.

---

