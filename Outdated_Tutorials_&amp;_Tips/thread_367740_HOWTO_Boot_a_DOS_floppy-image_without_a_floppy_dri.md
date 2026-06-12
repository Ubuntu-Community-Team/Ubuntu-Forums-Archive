---
title: "HOWTO: Boot a DOS floppy-image without a floppy drive"
date: 2007-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Jussi Kukkonen on 2007-02-22
The floppy drive is an almost dead technology by now. Unfortunately one may need to boot  from a floppy image neverteless -- in my case I had to run a BIOS update utlity for my Matrox G450 graphics card. Here's how I did it without a floppy drive.
From step 2 onwards you'll have to be root (or use sudo) pretty much all the time. The example commands are for Ubuntu 6.06 and should work on Debian derivatives.
[LIST=1]
[*]Download the files you want to put on the floppy. (I needed setup_g258_2.exe from Matrox), open the archive if needed:
```
wget ftp://ftp.matrox.com/pub/mga/archive/bios/2006/setup_g258_2.exe
unzip setup_g258_2.exe

```
[*]Install syslinux (dos floppy bootloader):
```
aptitude install syslinux

```
[*]Create a directory for DOS stuff and copy the bootloader and the disk image there. memdisk may be elsewhere on your system, and the image will be wherever you copied/unzipped it to.
```
mkdir /boot/dos
cp /usr/lib/syslinux/memdisk /boot/dos
cp ~/setup_g258_2/mini.ima /boot/dos

```
[*]Create a mount point and mount the floppy image.
```
mkdir /media/floppy
mount -t msdos -o loop /boot/dos/mini.ima /media/floppy

```
[*]Delete unnecessary files (if your actual files need all the space a floppy has). Copy your files to "floppy":
```
rm ~/floppy/autoexec.bat /media/floppy/dl8.exe
cp ~/setup_g258_2/*.bin ~/setup_g258_2/progbios.exe /media/floppy/
umount /media/floppy

```
[*]Add a boot option for the floppy image. With grub on Ubuntu this means adding something like this into /boot/grub/menu.lst (after AUTOMAGIC KERNELS LIST, of course):
```
title	Matrox BIOS update (DOS)
root	(hd0,1)
kernel	/boot/dos/memdisk
initrd	/boot/dos/mini.ima
boot

```
[*]Reboot, choose the "Matrox BIOS update" -boot option. Run whatever programs you need to run, this is for the Matrox BIOS updater:
```
progbios -i auto -q

```
[/LIST]
This howto originally lived in the Matrox forums. Unfortunately the tactless bastards closed the forum down without any warning (this content is rescued from Google cache). I hope this is useful for someone. Corrections are welcome.

[B]sources:
[/B][http://gentoo-wiki.com/TIP_Boot_Floppydisk_Image_without_Floppy_using_GRUB](http://gentoo-wiki.com/TIP_Boot_Floppydisk_Image_without_Floppy_using_GRUB)
[http://forum.matrox.com/mga/viewtopic.php?t=4379](http://forum.matrox.com/mga/viewtopic.php?t=4379) (not available, see above)

---

### Post by chris_x1 on 2008-05-02
very clever, thanks

---

### Post by guschdaevle on 2009-03-04
that's what i am looking for
thanx for rescuing this howto

guschdaevle

---

### Post by patrickjlbyrne on 2009-04-10
I found that '-o mount' does not work in Ubuntu 9.04.

Instead I found via:

  [http://en.wikipedia.org/wiki/Loop_device](http://en.wikipedia.org/wiki/Loop_device)

that doing (eg):

  losetup /dev/loop0 example.img
  mount /dev/loop0 /home/you/dir

works instead.

---

