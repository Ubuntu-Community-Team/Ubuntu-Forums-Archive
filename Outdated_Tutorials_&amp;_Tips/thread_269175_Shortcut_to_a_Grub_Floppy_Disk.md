---
title: "Shortcut to a Grub Floppy Disk"
date: 2006-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by ajgreeny on 2006-10-01
For anyone who has ever lost grub from their system and has a floppy drive I have set up the following shortcut to making grub on a floppy.  If ever you have to reinstall windows and lose your grub this is an even quicker way to get back into Ubuntu than using the live CD.

1  Make a new launcher (*link to application* if using Kubuntu)on your desktop named anything you like (Grubfloppy)
2  In the Command box of the launcher, copy the following:-
fdformat /dev/fd0 && sudo mkfs /dev/fd0 && sudo mount /media/floppy0 && sudo mkdir -p /media/floppy0/boot && sudo cp -r /boot/grub /media/floppy0/boot && sudo umount /media/floppy0
(this must be exactly as shown with all the spaces etc.)
3  Put a tick in the box which says *Run in terminal *(you need to click the advanced button in Kubuntu to do this)

This will format the floppy, ask for your password then make a filesystem on the floppy, mount it, make a directory called /boot, then copy all contents of /boot from your hard disk to the floppy, then unmount it.  It makes a floppy with an exact copy of your ubuntu grub, including the menu.lst file, so will need to be repeated every time you update your machine or install a new kernel, but as it only needs a click on an icon it will not be too hard to do.  Once you are back in Ubuntu you can restore grub to the MBR using sudo grub-install /dev/hda (or wherever your MBR is)

I hope this is useful to people.  It has cetainly been so to me in the past when I've messed up my system ina variety of ways.  I know there are several ways to restore grub but this seems to be a quick and simple way for the uninitiated to do it, and hopefully gain some more information into the workings of linux.

---

