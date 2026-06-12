---
title: "mounting msdos vfat etc"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by signseeker on 2008-06-08
hi,

is support for msdos/vfat etc compiled into the kernel by default? 

thanks

---

### Post by powerpleb on 2008-06-08
> **signseeker said:**
> hi,

is support for msdos/vfat etc compiled into the kernel by default? 

thanks

Yes
Ubuntu usually automatically recognises these drives and they should be accessible by opening Filesystem and looking for them in the directory /media

Otherwise you can mount these partitions manually by typing:
```
$ sudo fdisk -l
```
Looking for the relevant partition, eg. /dev/sda2
then typing
```
$ sudo mkdir /media/windows
```
This will make a dir called "windows" in your media directory
then type
```
$ sudo mount /dev/sda2 /media/windows
```
To mount the drive at the directory you just made

---

### Post by signseeker on 2008-06-08
Thanks for the response. It's just that I'm trying to mount a FreeDOS boot disk (so I can install it via VirtualBox) - and I keep getting wrong fs type errors.

---

### Post by niteshifter on 2008-06-08
Hi,

> It's just that I'm trying to mount a FreeDOS boot disk (so I can install it via VirtualBox) - and I keep getting wrong fs type errors.

Here's what I did to get FreeDOS in a VBox VM:

Downloaded "fdfullcd.iso" from freedos.org. fdbasecd.iso will work but doesn't have all the goodies.

Setup a VM with the memory and video you desire. The full install takes about 150MB of disk space, size accordingly (I used 256MB, leaving 108MB free). Network as NAT on the AM79C293 adapter. Audio and USB as you need them. Under the General settings of the VM, in tab Other uncheck "Remember Media at runtime".

Use VBox' Virtual Disk Manager to add the fdfullcd.iso under the CD/DVD Images tab. Then set the CD for your VM to fdfullcd.iso.

Start the FreeDOS VM, it should boot from the iso image, just like from a CD. It's a rather long installation dialog of selecting various packages. When it's completed, shutdown the VM and change the VM's CD setting to point to an actual drive in your system.

Enjoy FreeDOS, it's a lot of fun (tripping down memory lane for me, it was)

---

