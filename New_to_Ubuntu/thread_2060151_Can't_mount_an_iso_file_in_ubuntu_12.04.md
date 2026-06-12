---
title: "Can't mount an iso file in ubuntu 12.04"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by kmegamind on 2012-09-19
I am trying to mount a 5.8GB .iso file, first I used "gmount" but it gave this error "An error occured In some cases useful info is found in syslog - try dmesg | tail  or so" 
Then i tried "Furious iso mount", after mounting the mount point was empty !!
help please :)

---

### Post by cmont899 on 2012-09-19
What is the command you are using? The following works for me:

```
sudo mount -o loop /path/to/file.iso  /path/to/mount/point
```

---

### Post by kmegamind on 2012-09-19
It says : 

can't find "directory" in /etc/fstab or /etc/mtab

---

### Post by cmont899 on 2012-09-19
What is the exact command you are running?

---

### Post by kmegamind on 2012-09-19
the command :

sudo mount -o loop /home/khalid/ml2011au.iso /home/khalid/mountPoint

that what it says now :

mount: you must specify the filesystem type

never mind what it said before (i guess i didn't write the command correctly)

---

### Post by cmont899 on 2012-09-19
Add -t for type:

```
 sudo mount -t iso9660 -o loop /home/khalid/ml2011au.iso /home/khalid/mountPoint
```

---

### Post by kmegamind on 2012-09-19
It gave this :

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by cmont899 on 2012-09-19
May be a corrupt iso, did you create it yourself or is it downloaded? Have you tried checking the md5? If you right click the iso in nautilus are you able to open the file with Archive Manager?

---

### Post by kmegamind on 2012-09-19
I downloaded it, when i open it with archive manager it says "CD-ROM is NOT in ISO 9660 format"
i guess it's corrupt :S
thanx for your help :) 
and whats "md5" ?, I am new to ubuntu and trying to learn as much as possible.

---

### Post by The Cog on 2012-09-19
md5 is a method of creating a checksum for a piece of data. The checksum is always 128 bits long (I think), and the chances of two different bits of data (or a corrupt iso image) giving the same checksum are billions to one against. So calculating and comparing the md5 checksum is a good way of verifying that the image is good (or not). 

The command md5sum is installed by default in Ubuntu:
```
md5sum ml2011au.iso
``` will print the checksum for your image. Compare that with the checksum that the site you donwloaded it from says it should be.

---

### Post by kmegamind on 2012-09-19
Thnx for the info 
the command :
 md5sum /home/khalid/ml2011au.iso
made the terminal stop working (blinking cursor only)
maybe because the file is corrupted ?

---

### Post by kmegamind on 2012-09-19
i tried it on a non corrupt iso it gave this : 
8b1085bed498b82ef1485ef19074c281 
that's not 128 bit long, is it valid ?

---

### Post by The Cog on 2012-09-19
> md5sum /home/khalid/ml2011au.iso
made the terminal stop working (blinking cursor only)
maybe because the file is corrupted ?No - it's probably just taking several seconds to work it out. Give it a minute or so.

> i tried it on a non corrupt iso it gave this : 
8b1085bed498b82ef1485ef19074c281 
that's not 128 bit long, is it valid ?That looks right - 32 hex digits represents 16 bytes - 128 bits, I think.

---

### Post by kmegamind on 2012-09-19
thanx for the help :D

---

