---
title: "Unetbootin &amp; my USB stick"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by paulmagarey on 2012-05-06
I have downloaded an ISO image of Lubuntu 12.04 and MD5SUM check - it is OK. I seem to never be able to create a USB boot stick with the image though. Unetbootin always seems to freeze at file 10 of (however many) and then, even though I've deleted all files and it's a 4GB stick, says its full. Any advice on how to format the USB stick or get Unetbootin working properly?  Be grateful for any advice.

Cheers,

Paul

---

### Post by wilee-nilee on 2012-05-06
Format the stick in the disc utility to a fat32. You probably have a hidden trash in there open the stick and hit crtl-h a see if anything shows. You can also right click the icon and click format, then try loading it again.

---

### Post by oklokl on 2012-05-06
sudo apt-get install gparted

gparted
run...

umount usb Stick
 Easily format


sudo parted -l

umount -l /dev/sdc1
umount -l /media/abcUSB

sudo parted /dev/sdc
mktable
msdos
mkpart
pr
ig
0
-1
q
sudo mkfs.vfat /dev/sdc1

cd ~/Downloads
dir
lubuntu.iso

sudo dd if=lubuntu.iso of=/dev/sdc bs=1M
(Do not remove until depths of termination.
 Is failing.)

usb badblock testing..

umount -l /dev/sdc1
  umount -l /media/abcUSB

sudo badblocks -vw /dev/sdc
(It takes a long time)

## remove usb
sudo dd if=/dev/zero of=/dev/sdc bs=512 conunt=12345

---

### Post by paulmagarey on 2012-05-12
Thanks for feedback. Got disk utility to format to Fat32 and then it worked.  Problem solved.

Cheers,

Paul

---

