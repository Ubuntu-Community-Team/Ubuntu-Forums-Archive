---
title: "Computer reboots after selecting Ubuntu in GRUB"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by stylishjm on 2013-01-26
Hello,

I've got a mini-computer running on an AMD Geode x86 processor. It's locked down with EmbeddedBios and cannot boot from any external devices.

It was running Windows XP Embedded on a 4GB compact flash card. It has no SATA / IDE ports for traditional hard disk drives.

As I cannot boot from an external CD/DVD drive, or a USB, I put the 4GB Compact Flash card into a card reader on my work HP computer, booted from the Ubuntu 12.10 install DVD and installed it onto the CF card.

It boots 100% fine when plugged into my computer (although I have to manually select the drive to boot from in the bios), but when i tried it in the AMD Geode device, it wont go past the purple grub screen. Selecting anything on the list simply reboots the machine back to the purple grub screen. I am only able to access the grub "Minimal BASH-like editor" by pressing C.

I'm assuming the issue is because the Ubuntu installer may have installed some information into my HP's primary HDD MBR.

How would I resolve this? I am limited to the 4GB CF card, and the installer wouldn't proceed if I had the HP's primary HDD disconnected (as it needed a drive with 5GB free).

Here is some information from boot-repair which I ran when the CF card was in the PC - [http://paste.ubuntu.com/1572732/](http://paste.ubuntu.com/1572732/)

I've also attached an image of the AMD Geode device if that helps.

---

### Post by grahammechanical on 2013-01-26
My first though was that the AMD Geode device has a different CPU to the HP computer. My second thought after briefly looking at the boot-repair printou was that my first thought may be correct. Please give us a comparison of the hardware specifications of the two machines, especially CPU.

In the boot-repair printout I see this:

> Grub2 (v2.00) is installed in the MBR of /dev/sdf

I assume that sdf is the CF card? Grub is not in the MBR of sda.

This might be the problem.

>  the installer wouldn't proceed if I had the HP's primary HDD disconnected (as it needed a drive with 5GB free).

The installer wanted a 5GB space but all you have was a 4GB CF card. The installer may have indeed put some things on the the hard disk. Grub is doing its job because you say this

> Selecting anything on the list simply reboots the machine back to the purple grub screen. 

Does it give an error message of any kind? If you look through the boot-repair printout after his point

> sdf1/boot/grub/grub.cfg:

go down to here

> ### BEGIN /etc/grub.d/10_linux ###

and after this this

> menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os ... etc., etc.

You will see this

> gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root=**'hd5,msdos1'**

hd5,msdos1 means the fifth hard disk, the first partition.

Grub is looking for a Linux image to boot on the first partition of the fifth hard disk. This is why Grub is bumping you back to the menu.

I have given you the reason (I think). I cannot give you the solution. I do not know how to fix this.

Regards.

---

