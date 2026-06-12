---
title: "How to make an ubuntu 8.04.1 boot floppy"
date: 2008-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by gregphil on 2008-08-31
There are various posts about this topic already, but none of them actually worked for me using a new Ubuntu 8.04.1 installation.  Since I finally figured out how to do this, I thought I would share the results.

For reference, my computer is setup like this:
Windows Xp installed on an IDE drive /dev/hda using whole disk
Ubuntu  8.04.1 installed on SATA drive /dev/sda using whole disk
Kubuntu 8.04.1 installed on SATA drive /dev/sdb using whole disk

If the BIOS are set to an IDE boot I get windows.  If the BIOS are set to SCSI boot I boot into GRUB on the MBR of the primary SATA disk. This is how I have the BIOS set for the remainder of this post (to boot to GRUB on the MBR of a SATA disk).  If I change the BIOS boot order it breaks GRUB, I think because the disks get assigned in a different order (hd2,0) becomes (hd0,0) etc.  (this is annoying....)

Once booted into Ubuntu I wanted to make a backup floppy boot disk just in case something ever happened to the Linux install. I followed various posts I could find on the internet but none actually worked.  Below is what finally did work for me:

1.  Open a terminal window
2.  $ su       and enter password to become the root 'super user'
3.  # gformat --device=/dev/fd0   

Set format type to DOS in the GUI application, for some reason whenever I tried to format these to Linux ext2 the floppy could not be used in later steps. I can't explain this.  The command line "fdformat" also would not make usable floppies. However, once you have a usable blank formatted floppy:

4.  # mke2fs /dev/fd0
5.  # mount /dev/fd0 /media/floppy
6.  # mkdir -p /media/floppy/boot/grub
7.  # cd /boot/grub
8.  # cp * /media/floppy/boot/grub

Note I copied ALL files, not just stage1, stage2, menu.lst and device.map files like some other posts suggested.  The resulting floppy would not fully work for me unless I copied ALL files.

9.  # umount /dev/fd0
10. # grub
11. grub> device (fd0) /dev/fd0

Note the need for the 2nd parameter, device (fd0) would not work

12. grub> root (fd0)   

Ignore the message about not recognizing the partiton header.

13. grub> setup (fd0)
14. grub> quit
15. # exit
16. $ exit

The floppy you just wrote should now be bootable and have the entire GRUB menu on it (and actually working).  Make sure your BIOS are set to try a floppy boot before the hard disk boot to test the boot loader floppy.

Good Luck!  :)

---

### Post by bapoumba on 2008-09-01
Thread moved to Tutorials & Tips.

---

