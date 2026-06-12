---
title: "HOWTO: Make a Ubuntu Boot-CD (Like a boot floppy)"
date: 2005-03-11
forum: Outdated Tutorials &amp; Tips
---

### Post by GrapeApe on 2005-03-11
This will make a boot cd which is similar to a boot floppy.  It bypasses grub, but still uses your partitions.  Really only useful if you mess up grub, or copy your installation to a new hard drive and need to reinstall grub.  It's not a full O/S on CD.   Just the kernel.   It's always nice to have in case something gets messed up.

( 1 ) Install syslinux (package).

( 2 ) make a directory called bootcd

( 3 ) copy /usr/lib/syslinux/isolinux.bin to bootcd

( 4 ) copy desired kernel image from /boot to bootcd/linux.  Example:
*cp /boot/vmlinuz-2.6.10-4-386 bootcd/linux*

( 5 ) copy desired initrd.img from /boot to bootcd/initrd.img.  Example:
*cp /boot/initrd.img-2.6.10-4-386 bootcd/initrd.img*

( 6 ) edit bootcd/isolinux.cfg and place the following line
**DEFAULT linux initrd=initrd.img ro root=<your-root-dev>**
     Where, <your-root-dev> will be  something like /dev/hda1.   If you don't know your root device, look at your current grub config in /boot/grub/menu.lst.

( 7 ) make your iso image via (you should be one directory below bootcd).
**mkisofs -o bootcd.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -hide-rr-moved -R bootcd/ **

( 8 ) burn the image to CD.

( 9 ) Test it.

Hopefully this will work for you and be helpful to someone.  It worked for me in hoary.

You can burn the iso to CD by finding the iso in the directory viewer (nautilus).  When you find your ISO, right click and hi-lite "Write To Disk".  Follow instructions.

Obviously you need a cd-burner.

This is fairly easy, but figured it may help someone out at some point.

---

### Post by Nano on 2005-03-12
[QUOTE=GrapeApe]This will make a boot cd which is similar to a boot floppy.  It bypasses grub, but still uses your partitions.  Really only useful if you mess up grub, or copy your installation to a new hard drive and need to reinstall grub.  It's not a full O/S on CD.   Just the kernel.   It's always nice to have in case something gets messed up.

( 1 ) Install syslinux (package).

( 2 ) make a directory called bootcd

( 3 ) copy /usr/lib/syslinux/isolinux.bin to bootcd

( 4 ) copy desired kernel image from /boot to bootcd/linux.  Example:
*cp /boot/vmlinuz-2.6.10-4-386 bootcd/linux*

( 5 ) copy desired initrd.img from /boot to bootcd/initrd.img.  Example:
*cp /boot/initrd.img-2.6.10-4-386 bootcd/initrd.img*

( 6 ) edit bootcd/isolinux.cfg and place the following line
**DEFAULT linux initrd=initrd.img ro root=<your-root-dev>**
     Where, <your-root-dev> will be  something like /dev/hda1.   If you don't know your root device, look at your current grub config in /boot/grub/menu.lst.

( 7 ) make your iso image via (you should be one directory below bootcd).
**mkisofs -o bootcd.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -hide-rr-moved -R bootcd/ **

( 8 ) burn the image to CD.

( 9 ) Test it.

Hopefully this will work for you and be helpful to someone.  It worked for me in hoary.

You can burn the iso to CD by finding the iso in the directory viewer (nautilus).  When you find your ISO, right click and hi-lite "Write To Disk".  Follow instructions.

Obviously you need a cd-burner.

This is fairly easy, but figured it may help someone out at some point.[/QUOTE]
 Thanks a lot, this is great.
I'll have to use when I'll format my windows partition and reinstall it.

Cheers

---

### Post by datu on 2005-07-04
Will this boot an Ubuntu install from a USB HD?

I installed ubuntu to a USB 2.0 6GB HD. . . when i installed it ubuntu saw it as a scsi device, sda.

What i want to do is pop a CD into the CD Rom and have it boot straight into ubuntu without installing grub or any kind of boot loader. Im still using windows XP.

Im i making sense? 

lol

thnx

---

### Post by MySchizoBuddy on 2005-07-17
How do  u change it so to allow booting of Windows from Cd as well

---

### Post by djvishnu on 2007-02-18
doh - posted by mistake

---

### Post by Princegiri on 2007-12-17
can an OS selection screen also be packed with this method??? can windows or other distros be selected at boot time?

further, i have this problem. I have my ubuntu FF installed on an external hard disk drive.

At home, on my desktop machine, i have the option of booting from "USB EXTERNAL HARDDISK" in my BIOS......
BUT my laptop doesnt. this means that i can use this BOOTCD to boot into the ubuntu on my external drive, with my laptop.

**PROBLEM**: on my desktop machine there are already two internal hard disks, so the external one is **(hd2)** (*/dev/sdc3* on linux) while in my laptop there is only one hard disk. 
so this means that the external device will now be **(hd1)** and linux will be on (*/dev/sdb3*), right?
[B]
SOLUTION[/B]: will changing the **isolinux.cfg** file to point to /dev/sdb3 instead of /dev/sdc3 solve the issue????

---

### Post by yufeng66 on 2008-04-02
Does this still work with more recent ubuntu distributions?

one section of my menu.lst looks like this

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=b83661e5-2869-4ac8-ae8d-890fbc5d530b ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic

should I use root=UUID=b83661e5-2869-4ac8-ae8d-890fbc5d530b  in the isolinux.cfg?

---

