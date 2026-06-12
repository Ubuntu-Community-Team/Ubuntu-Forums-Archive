---
title: "freshly formatted usb drive mounts but cant write"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by bradleyd on 2008-04-24
hello everyone,
I have a weird problem, it is probably just me. I bought a sony usb 2Gb thumb drive. I promptly formatted it create ext3 file system on it. Th eproblem is when I plug it in, it automounts fine, but I cant write anything to it?
Never had this happen before. This is the second drive today that this has happened, and on two different machines. I am stumped.
My steps:
```
sudo fdisk /dev/sda

```Delete current partition, then create one, primary and the full size of disk. Then write it out.
```
sudo mkfs.ext3 /dev/sda1
```
Finishes up, then I reinsert usb drive. Mounts fine but no write.
I maybe just tired:)
Thanks for your time,
Brad

---

### Post by sam_delta on 2008-04-24
check if you can write to it with super user priviledges

click alt - f2 and type "gksudo nautilus" then browse to /media/<usb flash> and write to it

sam

---

### Post by bradleyd on 2008-04-24
yes I can write to it as root. But it should be writable no matter what user.

---

### Post by sam_delta on 2008-04-24
you can follow the following steps to change USB permissions
QUOTED FROM: [http://ubuntuforums.org/showthread.php?p=616396#post616396](http://ubuntuforums.org/showthread.php?p=616396#post616396)

1. Open your

/etc/fstab

using your favourite editor.
Ex:
Code:

sudo kate /etc/fstab

you can use gedit if using ubuntu (kate for kubuntu)

2. Add these lines into the fstab file :

sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0

3. reboot.
4. That's all folks
Hope that's help.. 



sam

---

### Post by bradleyd on 2008-04-24
Thanks for the reply.
The only problem is that I have never had to change anything in fstab. I have purchased many of thumb drives and just plugged them in and can write to them. This seems to only happen to thumb drives or usb drives that I format with ext3 FS. There is something else going on here. I have another thumb drive that is vfat(from the store) and it mounts rw and I can write to it fine(no matter what machine  am on)

---

### Post by sam_delta on 2008-04-24
have you updated distros? or fresh install?

---

### Post by bradleyd on 2008-04-25
nope, this happens on ubuntu 7.10 and Debian etch. Two different machines. Does anyone have a thumb drive that they can try these steps to reproduce?

---

### Post by sam_delta on 2008-04-25
ok, i added a new partition on my usb flashdrive and formatted it to ext3, so now i have 2 partitions on my usb (fat32 and ext3), indeed happened the same to me, i need sudo privileges to access my ext3 partition but not my fat32 partition, after comparing both partitions, i realized that the fat32 partition has Sam (my user name) as the owner, while the ext3 partition had root as the owner, so, i just changed the  owner to myself instead of root and everything worked fine

to change owner i did 

 sudo chown sam /media/usb_sam 

where "sam" is the user name and usb_sam is the mount point

let us know how it goes

sam

---

### Post by sam_delta on 2008-04-25
sry did a double post, does anyone know how to delete double posts?

thx

---

### Post by bradleyd on 2008-04-25
thanks for going the extra on this. Now when you plug it in to another box does is it still writable?(different username)
If u replug it in does it retain those permissions?
thanks again.

---

### Post by sam_delta on 2008-04-25
when i unplug the usb and insert it again, itll work fine, (appears my username as owner) and i can read/write fine. i havnt rebooted my pc to check if reboot will change anything but i bet it dont.

i havnt checked on a different computer since i dont have another linux box available at the moment, but ill check as soon as i get my hands on one,.

sam

---

### Post by bradleyd on 2008-04-25
It also does the same with vfat(fat16) You could remove ext3 part and create vfat from it. Then try it on a Windows or Ma, if you have it?

---

### Post by sam_delta on 2008-04-25
just tryied on another machine running ubuntu 8.04 HARDY, and mounted fine with rw permissions

---

