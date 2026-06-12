---
title: "ISO to USB UNetbootin &quot;invalid or corrupt kernel image&quot;"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by diskmaster23 on 2012-02-03
This problem isn't specially with Ubuntu Live CDs, but I am going crazy trying to figure out how to put an ISO onto a USB stick to boot off.

First, I'll go into GParted and reformat my usb stick to a FAT32. 

Then I'll download an ISO or two from FreeNAS (the actual website, not the one that comes with UNetbootin), just as an example, I'll download FreeNAS-8.0.3-RELEASE-p1-x64.iso or FreeNAS-amd64-LiveCD-0.7.2.8191.iso or FreeNAS-amd64-LiveCD-0.7.2.7903.iso. I'll let UNetBootin do it magic work. 

Next, I take out the USB stick and put it into another machine and try and boot into the USB stick. But it doesn't work because it gives me the "invalid or corrupt kernel image" error. However, if I let UNetbootin download its own image, it works. But mine doesn't.

I have downloaded these isos over and over, but they haven't worked. However, I burned all of these ISOs to a CD and they work fine.

So...what am I doing wrong and how can I fix it?

---

### Post by oklokl on 2012-02-03
sudo -i
fdisk -l

/dev/sdb1

#remove

dd if=/dev/zero of=/dev/sdb bs=446 count=12351

cd /home
cd username.. 

or

&#65279;cd ~/downloads
&#65279;cd ~/download

/home/test 

dir 

ubuntu-11.10-desktop-amd64.iso

dd if=ubuntu-11.10-desktop-amd64.iso of=/dev/sdb bs=1M

##rebooting
install ubuntu


usb Partition bug clean



Low-Level-Format ->windows..
[http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/](http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/)

or 
dd if=/dev/zero of=/dev/sdb
very longtime

badblocks -v /media/testdisk

badblcok view..

---

### Post by diskmaster23 on 2012-02-03
I've followed your advice. Everything seemed to work except the computer doesn't load the USB key. I've gone into the bios to make sure the computer loads the usb key, but it doesn't load it. 

But the iso is on the usb key, because when I unplug it from the computer as soon as it is done 'dd'ing. It comes up with the contents of the usb key.

---

