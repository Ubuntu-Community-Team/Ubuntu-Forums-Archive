---
title: "Usb sticks wont show, also AWN items wont drag"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Rioku on 2008-07-20
I'm having problems with AWN dock. I cant seem to drag any items onto the dock they just refuse to go on. ( I used to be able to on a previous installation )

Can anyone help with that?

Also My USB sticks wont mount/show at all in ubuntu when I plug in After the OS starts. (If I put a usb stick in then turn on my laptop they will show)

Can anyone help with this also :S ? 

I seem to remember having that USB problem the last time I installed Ubuntu but after I downloaded updates it fixed itself... this is no longer the case.

Thanks for your time

---

### Post by LinuxRocks713 on 2008-07-23
First enable /proc/bus/usb:

sudo nano /etc/init.d/mountdevsubfs.sh 

and uncomment

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

then find usb with:

lsusb

in the results look for your usb:

Bus XXXX Device YYYY: ID ****:**** linux name for usb
Where XXXX is something like ABCD, X = BCD
Where YYYY is something like QEWR, Y = EWR

then mount using

sudo mount -t vfat /proc/bus/usb/BCD/EWR -o uid=1000,gid=1000,umask=777

---

