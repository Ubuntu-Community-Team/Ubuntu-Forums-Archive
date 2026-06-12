---
title: "Initrd"
date: 2005-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by oldmarti on 2005-04-04
Hi, I wan't to take a look at the files in original initrd. How I can mount or uncompress this file? Thanks

---

### Post by jameswilhelm on 2005-04-04
Had a quick go on Redhat 9:

I had /boot/initrd-2.4.20-28.9.img

Copied it to a work directory!

In the work directory:
mv initrd-2.4.20-28.9.img initrd-2.4.20-28.9.img.gz 
(to keep gunzip happy - I'm sure there is a better way!)

gunzip initrd-2.4.20-28.9.img.gz

mkdir mounthere

mount -o loop initrd-2.4.20-28.9.img mounthere

And I can view the files in mounthere/.

I'm no expert on this, but am curious about the details on different systems. Please let me know how this works for you. I'll try it on Ubuntu later.

---

### Post by jameswilhelm on 2005-04-04
Works differently on Warty:

As root, create loopback devices: 

modprobe loop

([http://ubuntuforums.org/showthread.php?t=1709)](http://ubuntuforums.org/showthread.php?t=1709)). Don't know why they are not there. You have to recreate them if you reboot.

The initrd file on Debian is in cramfs format and can be mounted using the loopback device:

([http://www.edseek.com/archives/2004/03/22/creating-an-initrd-image-on-debian-gnulinux/](http://www.edseek.com/archives/2004/03/22/creating-an-initrd-image-on-debian-gnulinux/))

mkdir mounthere

mount -o loop <initrdfile> mounthere

I definitely need to do some more reading! This works, though.

---

### Post by az on 2005-04-04
cp /boot/initrdXXXXX.img /home/me/initrd
sudo losetup /dev/loop0 /home/me/initrd
sudo mkdir /initrd
sudo mount /dev/loop0 /initrd

I am not at home in front of my Ubuntu box, but that should work.

---

