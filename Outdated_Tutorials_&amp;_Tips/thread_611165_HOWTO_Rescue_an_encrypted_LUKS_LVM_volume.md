---
title: "HOWTO: Rescue an encrypted LUKS LVM volume"
date: 2007-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by peanut butter on 2007-11-12
This HOWTO is for people who have encrypted their main volumes of their hard drives using the method offered by the Alternate CD installer. IT will probably work on other ways of installation.

1. Boot into a Live CD environment (the other OS is imposable to boot to right?) and open up a terminal window. (applications<accessories<terminal)

2. Install needed packages:
```
sudo apt-get install lvm2 cryptsetup
```
3. probe needed module:
```
sudo modprobe dm-crypt
```
4. setup the crypto module to recognise the partition
```
sudo cryptsetup luksOpen /dev/hda5 crypt1
```
Enter your passphrase. You should get the following message:
key slot 0 unlocked.
Command successful.
If not, something has gone wrong.
5. scan for volume groups
```
sudo vgscan --mknodes
sudo vgchange -ay
```
REMEMBER the name of the volume group, as you will need it for step 7.
6. Create a mount point:
```
sudo mkdir /volume
```
7. mount the encrypted volume to the mountpoint you just created. (replace paulb-desktop with the name of the volume group found in step 5.)
```
sudo mount /dev/paulb-desktop/root /volume
```
8. The volume is mounted, now you can chroot or whatever else you need to do. If you would like to open the gnome file manager for writing to it issue the following command:
```
sudo nautilus /volume
```

9. Happy Crypting.:)

---

### Post by secure bit on 2007-12-13
thanks for very good howto

when I try to execute step No# 7 I face the following problem :

> mount: you must specify the filesystem type

I use ubuntu studio , what should I do ?

thanks in advance

---

### Post by secure bit on 2007-12-14
> **secure bit said:**
> thanks for very good howto

when I try to execute step No# 7 I face the following problem :



I use ubuntu studio , what should I do ?

thanks in advance
I have tried the same steps with gutsy, same result :

> 
mount /dev/bit-desktop/root /volume/
mount: you must specify the filesystem type


---

### Post by secure bit on 2007-12-15
up up up !

---

### Post by secure bit on 2007-12-17
now what todo ??

---

### Post by johannes on 2007-12-17
EDIT: Erased

---

### Post by secure bit on 2007-12-18
thanks !

so you don't have a solution mister ?

---

### Post by secure bit on 2007-12-19
> **johannes said:**
> EDIT: Erased
step 7 not working

> mount: you must specify the filesystem type

---

### Post by elsi on 2007-12-31
to get rid of the "mount: you must specify the filesystem type" message

try:
```
mount -t ext3 /dev/{yourdevice} /mnt/{your mount point} 
```

if this does not work too try

```
mount -t ext2 /dev/{yourdevice} /mnt/{your mount point} 
```

peanut butter: thanks for your nice little howto

---

### Post by peanut butter on 2008-02-09
Sorry for the very late response, ive had a lot on my plate lately... School really gets in the way. Yeah. That must have been a typo on step 7 or something.

---

### Post by chrisdavid_175 on 2008-02-20
Great how-to!!! I've always been booting between my desktop and server partitiions but now I can just access the encrypted partition. Thanks!

---

### Post by blastus on 2008-03-01
Nice guide :) Is step 5 really necessary? My encrypted partition /dev/sda3 contains a volume group called lvm1 which contains two logical volumes called root and swap. When I... 

```
sudo cryptsetup luksOpen /dev/sda3 crypto
```

...I noticed that it automatically created the device mapper files lvm1-root and lvm1-swap in /dev/mapper. I just needed to mount /dev/mapper/lvm1-root and that was it to use it.

---

