---
title: "Howto Modify Grub and Menu List"
date: 2006-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by richbarna on 2006-07-30
If you are adding partitions and installing other Linux distros, you will have had problems with either GRUB or the menu.lst.

This guide shows you how to add distros to the menu.lst so that they are bootable from GRUB at startup.

> =======================================================================
This is an example of how to use the GRUB edit function.

Highlight the menu entry you want to edit, then press 'e', then
highlight the line you want to edit and press 'e'. Add what
you want to the line 'hdd=scsi' etc. and press enter, then
'b' to boot.

Examples of the difference between Linux and GRUB device names.

**1st Physical Hard Disc**
Linux IDE:     [COLOR=Blue]GRUB IDE:[/COLOR]       Linux SCSI:    [COLOR=DeepSkyBlue]GRUB SCSI:[/COLOR]
/dev/hda1             ----[COLOR=Blue](hd0,0)[/COLOR]-----                     /dev/sda1-------[COLOR=DeepSkyBlue](hd0,0)[/COLOR]
/dev/hda2       ----[COLOR=Blue](hd0,1)[/COLOR]-----                     /dev/sda2-------[COLOR=DeepSkyBlue](hd0,1)[/COLOR]
/dev/hda3             ----[COLOR=Blue](hd0,2)[/COLOR]-----                     /dev/sda1-------[COLOR=DeepSkyBlue](hd0,2)[/COLOR]
/dev/hda4             ----[COLOR=Blue](hd0,3)[/COLOR]------/dev/sda2-------[COLOR=DeepSkyBlue](hd0,3)

**[COLOR=Black]2nd Physical Hard Disc[/COLOR]**
[COLOR=Black]Linux IDE: [COLOR=Blue]GRUB IDE:[/COLOR] Linux SCSI: [COLOR=DeepSkyBlue]GRUB SCSI:[/COLOR][/COLOR]
[/COLOR] /dev/hdb1----             [COLOR=Blue](hd1,0)[/COLOR]-----                     /dev/sdb1------          [COLOR=DeepSkyBlue](hd1,0)[/COLOR]
/dev/hdb2----             [COLOR=Blue](hd1,1)[/COLOR]-----                     /dev/sdb2------                [COLOR=DeepSkyBlue](hd1,1)[/COLOR]
/dev/hdb3----             [COLOR=Blue](hd1,2)[/COLOR]-----                     /dev/sdb1------                [COLOR=DeepSkyBlue](hd1,2)[/COLOR]
/dev/hdb4----             [COLOR=Blue](hd1,3)[/COLOR]-----                     /dev/sdb2-------[COLOR=DeepSkyBlue](hd1,3)[/COLOR]

These are some examples of how to use GRUB from the command prompt.

Press the 'c' key for the command prompt.

If you want to boot a Linux system on a partition, using it's kernel
/boot/vmlinuz etc., do this.

grub> root (hd0,1)
grub> kernel /boot/vmlinuz root=/dev/hda2 ro
grub> boot

(you can also copy and paste the above (minus the "grub>" to the menu.lst)

You could do this to find what partition the kernel is on.
For example, show me what partitions have a /boot/vmlinuz.

grub> find /boot/vmlinuz
(hd0,1)
(hd0,2)

If you want to boot a Dos/Win partition, do this.

For example, boot partition on /dev/hda1.

grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot

If you want to boot a FreeBSD partition using /boot/loader.

For example, boot freebsd partition on /dev/hda4.

grub> root (hd0,3,a)
grub> kernel /boot/loader
grub> boot

If that doesn't work, try this instead.

grub> rootnoverify (hd0,3,a)
grub> chainloader +1
grub> boot
==============================================================

Press the [Esc] key to return to the GRUB menu.
I regularly test and install new distros and knowing how GRUB works makes life a whole lot easier.

Whe you install Linux, the Grub install at the end should detect all other operating systems on your PC, but sometimes it doesn't, no problem just add it manually.
If you only want to add an already installed distro so that it boots at startup, (maybe you already have Linux installed and now you are installing a second Linux).

Do this in the terminal :-
> sudo nano /boot/grub/menu.lst

This will show you a list of all the OS's that can be booted from GRUB.

You now only have to copy the same format, below, after the last OS.

For example, on your harddrive, you have just installed another linux distro on partition 3. You would add this to the menu.lst

> 
title           Debian Sid
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-4-486 root=/dev/hdc3 ro
initrd          /boot/initrd.img-2.6.20-4-486
savedefault


Remember that you NEED to know the kernel and initrd.image numbers, above is 2.6.20-4-486, otherwise it won't boot. Some linux distros only put "vmlinuz" and "initrd.img".

To find this out, you need to take a peek in the boot folder of the new partition. Like this:-
> cd /dev/hdc3/boot

Then to see it's contents, type:-
> ls

You can now copy those numbers onto the menu.lst.

To save the file press Ctrl + X then typ "Y" for yes and hit "Enter". 

You should now see the other operating system on the list when you reboot the computer.

---

### Post by jemvyc on 2008-07-10
I wish I had found your post months ago.  I had to learn most of that stuff the hard way.  

Maybe you have a solution to my current problem.  I have Hardy, SUSE 10.3 and Windows 2000 on an old Dell system.  SUSE boots from the menu.lst in Hardy.  Every time I update SUSE, it changes the Kernel location and edits the menu.lst in the SUSE installation.  Therefore the grub from Hardy can't find the distro and crashes.  Then I have to use the tools you taught here to find the SUSE boot and edit the menu.lst in Hardy.

Question:  Can I put a link in the menu.lst on Hardy to have it just go execute whatever SUSE has put there?

Thanks

Jim:)

---

### Post by WAZZAT on 2009-03-19
Howdy; [COLOR="DarkRed"]Newbie[/COLOR] here and have to add my 2 cents. With Ubuntu 8.1 using Add/Remove Applications, SEARCH All Open Source applications (in SHOW: box at top of window) for [COLOR="Blue"]_KGRUBEditor_[/COLOR]. While connected to the internet, click apply changes. This will install an easy edit Grub boot order program with a pleasant GUI interface available from the applications menu tab on your desktop. Just did that now and will have to reboot to see if it works. If it does it'll save me lots of trouble as I don't know how to access and run most of the programs that I've:popcorn: installed. Did manage to install the ATI restricted driver on my bigger computer and a few other things that were needed.

---

