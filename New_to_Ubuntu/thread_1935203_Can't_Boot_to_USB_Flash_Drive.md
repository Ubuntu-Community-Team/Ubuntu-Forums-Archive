---
title: "Can't Boot to USB Flash Drive?"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by SolarLune on 2012-03-03
Hey. So, I'm trying to get a nice 'dual-boot' kind of setup on my computer here. Ubuntu didn't see my hard drive, so I'm trying an alternative route - a Live USB on a flash drive with Persistence on. The problem that I'm having is that I can't boot from the USB drive, even though it seems like I'm creating a fine startup disk. I used Universal USB Installer, and I'm about to try Unetbootin. I've looked through my BIOS options, and while there's not a large number of options, there are a few.

1. I can change the emulation of the USB device - Floppy, CD-Rom, Hard Drive, and FDD. I tried them all except Floppy - Hard drive didn't do anything, and the others went to a black screen with a flashing white cursor ( _ ).

2. I can change the order of the boot devices. I've always placed the USB device to be first in the process, but it hasn't worked so far... Any ideas?

EDIT: P.S. I've tried using Plop Boot Manager to boot to my USB device, but it hasn't worked, either - either it doesn't see the drive with USB 1.1 forced (mode 1), or it freezes on selecting any device (if I recall correctly).

EDIT 2: The flash drive I'm using is brand new - a Transcend 32GB flash drive. My motherboard is an AMIBIOS (American Megatrends). Don't know the model number.

EDIT 3: My computer is a Sony VAIO Media Center PC, with just one hard drive running Windows XP Media Center edition, 32-bit.

EDIT 4: If it matters, I might be able to use an HP SimpleSave 300GB external hard drive for this purpose as well. It was down until I deleted its partitions and fixed its master boot record with MiniTool Partition Wizard. Now, it seems to be working okay. I'll test it by installing Ubuntu on it. Would this be more likely to work? I'm guessing so because it might have a bootloader, right?

---

### Post by audiomick on 2012-03-03
> **SolarLune said:**
> ... Ubuntu didn't see my hard drive...


You might like to try the alternate CD. 
[http://www.ubuntu.com/download/ubuntu/alternative-download#alternate](http://www.ubuntu.com/download/ubuntu/alternative-download#alternate)

I don't know if it is still the case, but a while back the installer was having problems finding some people's drives. The alternate installer did a better job of it.

Note: there is no live environment on there. It is just the installer. It is only text based, no GUI, but it is not that hard to deal with if you carefully read what is on the screen.

---

### Post by Ryulion on 2012-03-03
Try turning persistence off. I have Ubuntu setup to dual boot with windows 7 ultimate and I used a usb to install Ubuntu with persistence off because if you have it on I read some where it will try save settings etc...which may cause problems.

---

### Post by SolarLune on 2012-03-03
@audiomick - Thanks. While I am still trying to get it to work with the thumb drive, it would be nice to get it installed to my hard drive. I suppose I'd have to repartition the drive, though. Is it really recommended to defragment first (I mean, if I don't, will it kill the install, or worse, my C drive?

@Ryulion - Could that account for why it doesn't boot from the USB drive? I'll check to make sure...

EDIT: Mentioned that this isn't a 'blank' PC that I'm using - it already has Windows installed on it.

EDIT 2: Might have fixed a 300GB External hard drive, which might be better for this purpose...

---

### Post by audiomick on 2012-03-03
> **SolarLune said:**
> . Is it really recommended to defragment first (I mean, if I don't, will it kill the install, or worse, my C drive?

If you don't de-frag your windows partitions before  partitioning work, it wont kill anything.

What might happen, as far as I understand it, is that the partitioning tool wont find as much avaiable space as might be available after the drive has been "tidied up" with a de-frag.

Also, when you make changes to your partitions, it often involves the content of the drive being moved from one area of the drive to another. It seems logical to me to have things tidied up and as orderly as possible before starting any thing like that.

---

### Post by Mark Phelps on 2012-03-04
IF the Ubuntu installer still does not "see" your drive or existing XP install, do NOT force it.  That will effectively erase everything you have now.  NOT a state you want to have when you're finished installing Ubuntu.

If you want to play it safe and install to an external drive, then disconnect your internal drive BEFORE you do that.  Why? Because with the internal drive still connected, GRUB is likely to get installed there -- and if it does, from then on, you won't be able to boot your PC UNLESS you have your external drive connected.

With GRUB installed to the external drive, you should be able to press a Function key when booting your PC and select the external drive as the temporary boot device.

---

