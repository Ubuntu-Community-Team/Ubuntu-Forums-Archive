---
title: "Help! Laptop is paperweight now because of UEFI, ASUS X201E DH01 with Ubuntu"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by newbietwo on 2013-12-25
I am not a Linux guru.

I am a guy who does not like Microsoft and prefers Linux over Mac and M$ (have all 3).  It's becoming difficult to use Linux because of this UEFI issue.

So, I've read about 1,000 different tutorials in the past two days on how to re-install Ubuntu on my Asus and I have tried them all...

All to no avail.

I have used Gparted and changed to GPT from MSDOS as I read and still I am told that no OS can be found. I partitioned the hard drive and left the boot_grub as requested on sda1, created a swap area and left the rest formatted to ext4.

The computer is simply not reading my Unetbootin 13.10 USB.

Is there a newbie friendly UEFI work around that's easy to understand and implement out there???  Candidly, I just don't have the time to mess with this but hate that I now have a $400 paperweight vs a working Linux system.

Thanks in advance for any newbie friendly help that may be out there.

---

### Post by grahammechanical on 2013-12-25
So, what is the problem? You cannot get the Ubuntu Live Session to run and so cannot install Ubuntu or the live session runs but when selecting install Ubuntu something goes wrong. It is not clear from your post.

> [COLOR=#000000]The computer is simply not reading my Unetbootin 13.10 USB.[/COLOR]

Describe for us what happens. It will give us clue. This is the best advice that I know of

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Actually UEFI is not the issue here. That and Secure Boot have been fixed. That version of Ubuntu 13.10, is it AMD64 or i386? You will need 64bit Ubuntu = AMD64. Why did you remove the OS that was originally on it? Installing Linux on a machine with Windows on got much more difficult when Windows 8 was released. 

Regards.

---

### Post by newbietwo on 2013-12-25
Sorry..  Can't get to Ubuntu live session...at start it just reads that no OS found, reboot and try another boot option....

---

### Post by cincibluer6 on 2013-12-25
IIRC, the main problem is unetbootin does not work well with 13.10 for whatever reason. I had the same problem before. Use something like PowerISO (on Windows) or the dd command in Linux/Mac (careful!) to write the image to the USB.

That should fix your issue.

---

### Post by newbietwo on 2013-12-25
Found a repartitioning tutorial immediately after posting this.  All worked well.  Merry Christmas.

---

