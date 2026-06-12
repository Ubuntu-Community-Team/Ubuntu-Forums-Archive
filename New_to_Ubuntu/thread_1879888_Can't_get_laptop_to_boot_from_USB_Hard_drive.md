---
title: "Can't get laptop to boot from USB Hard drive"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by gkrules on 2011-11-12
Using YUMI, I created a multiboot USB hard drive. The hard drive is a Western Digital Passport. 
I used it to install Ubuntu 11.10 on my friend's laptop. However, when I try to boot from the hard drive on my computer, nothing happens. It skips straight to the internal hard drive. I know for a fact that USB is ahead of the internal drive in boot order because I can boot from a thumb drive. 

I've tried using an alternative boot manager, plop, but it always freezes when I select USB.

What else can I do?

---

### Post by Ricx94 on 2011-11-12
go into the computer's BIOS (SETUP), find boot order, and see if there is more than one hard drive listed. your external drive may be seen by the computer as a hard drive instead of a removable disc/ device. if there is more than one hard drive, set your external drive ahead of your internal.

other than that, i don't know what could be going wrong. maybe try to use the boot menu (probably F12) to select your external drive.

---

### Post by gkrules on 2011-11-12
The only hard drive listed is the internal one.

Could it possibly be a driver issue? My laptop isn't recognizing it because it doesn't have the drivers for it?

---

### Post by Mark Phelps on 2011-11-12
It's probably not a driver issue, otherwise, you wouldn't be able to boot from the USN thumb drive.

Next time, check to see if there is a "B" drive listed.  I know, that sounds strange because "B" is what used to be the second floppy drive, but recently, I needed to upgrade my BIOS using USB, and it was listed under "B".

---

### Post by gkrules on 2011-11-14
My BIOS is up to date, and I do not see anything listed as B.
I tried setting my internal drive as the last boot device, but it still just skips to grub.

---

### Post by Mark Phelps on 2011-11-15
Then, if it will boot from a USB stick but not from a USB hard drive, your only choice is to use unetbootin to create a bootable USB stick containing Ubuntu and boot from that.

---

### Post by gkrules on 2011-11-16
Is it possible to boot from usb through grub?

---

### Post by dniMretsaM on 2011-11-16
Check for a menu named something like hard drive priority. It might be listed there. And a picture of your BIOS screen would be helpful.

---

### Post by Mark Phelps on 2011-11-16
> **gkrules said:**
> Is it possible to boot from usb through grub?

The unetbootin tool will create a bootable USB stick containing Ubuntu.  Whether or not that works in a specific PC depends on whether or not the PC supports booting from USB stick.

It is not possible to get your PC to do something that the BIOS does not support.

---

### Post by jockyburns on 2011-11-16
When you start the laptop, keep pressing F2 (or whatever your lappy takes)  during the startup and see if it gives you the bios menu. If it does, go along the top until you find BOOT menu then you should be able to manually set the boot priority from HDD to USB. Some laptops can't boot from USB though  so the boot priority may not show USB.

---

