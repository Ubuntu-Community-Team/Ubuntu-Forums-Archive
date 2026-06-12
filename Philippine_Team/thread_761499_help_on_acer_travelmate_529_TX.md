---
title: "help on acer travelmate 529 TX"
date: 2008-04-21
forum: Philippine Team
---

### Post by stephencezar on 2008-04-21
Hello every one!

this is my first time to try Linux, in particularLinux Ubuntu. And I'm trying it to Acer TravelMate 529TX. When I boot the CD 7.10 desktop version it does not proceed to installation guide. I even tried adding the instruction "break=top pci=noacpi" as I have seen on some threads. Sa Server CD gumana yun, pero sa desktop, hindi eh.

Could anyone help me?

Thanx and more power!

---

### Post by loell on 2008-04-21
what do you see last when you try to install the desktop version? 
could be a bad media/cd or the ISO file is corrupted before it was burned?

---

### Post by stephencezar on 2008-04-22
> **loell said:**
> what do you see last when you try to install the desktop version? 
could be a bad media/cd or the ISO file is corrupted before it was burned?


Ei loell thanx! Someone suggested that I use xubuntu. Now it is installed on my laptop. But after installing it. I cannot access my CD-ROM drive. I have seen red hat once, when a CD has been inserted to the drive, an ICON for the CD will be created to the desktop. Is it not the same with xubuntu? 

I very much appreciate it if you could help me. Thanx!

---

### Post by loell on 2008-04-22
yes xubuntu will put an icon in the desktop if a media is detected

---

### Post by stephencezar on 2008-04-22
> **loell said:**
> yes xubuntu will put an icon in the desktop if a media is detected

Correct me if I'm wrong, but I think the device is not detected. there is no /dev/cdrom/ in my file system.

The unit is ACER travelmate 529TX, the CD ROM drive is toshiba 20x.

I was able to install the live CD using that drive just by adding "break=top pci=noacpi" during installation, but upon installing it, no drive has been detected.

I tried adding the drive to synaptic package manager>edit>add cd-rom the system is asking me to insert a disk into the drive. after inserting a disk into the drive the system reported error: failed to mount the cd-rom.

I'm having trouble migrating from windows to xubuntu. If you could help me I very much appreciate it. Thanx again!

---

### Post by loell on 2008-04-22
can you copy/paste the ouptut? 

```
ls /dev/sc*
```

and also your fstab

```
cat /etc/fstab
```

---

### Post by stephencezar on 2008-04-23
> **loell said:**
> can you copy/paste the ouptut? 

```
ls /dev/sc*
```

and also your fstab

```
cat /etc/fstab
```


Ei loell thanx a lot. I hope Im not troubling you too much.

Any way heres the result.....

ctad@ubuntu:~$ ls /dev/sc*
ls: /dev/sc*: No such file or directory
ctad@ubuntu:~$ 


ctad@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cc321984-3c95-45a9-bc0a-a4607988f7d7 /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda5
UUID=c1a30568-65fb-4a0d-ab19-5600a574dcd5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
ctad@ubuntu:~$ 

I have no idea what this means....:confused:

---

### Post by loell on 2008-04-23
hmm, ```
dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

so x/ubuntu detected it.

can you edit it ie( **sudo gedit /etc/fstab** then find the above second to the last line and make it

```
dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec**,utf8** 0 0
```

reload your fstab by

**sudo mount -a**

see if there's any detected media.

---

