---
title: "[SOLVED] auto mount second drive in ubuntu 7.10"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by linuxnoob123456789 on 2008-07-04
Hello,
everyone

I got samba working and it is using a second hard drive to share, which is used for 10 clients. Is there a way to auto mount this hard drive when Ubuntu turns one.

thank you in advance

---

### Post by sayakb on 2008-07-04
Post the output of:
```
sudo fdisk -l
```And do specify which HDD you want to mount among the command's output..

---

### Post by linuxnoob123456789 on 2008-07-04
here it is

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44364435

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9824    78911248+   7  HPFS/NTFS
/dev/hdb2            9825       10011     1502077+   5  Extended
/dev/hdb5            9825       10011     1502046   82  Linux swap / Solaris

---

### Post by linuxnoob123456789 on 2008-07-04
Does anyone know how to mount a second hard drive when system startup?

---

### Post by sayakb on 2008-07-04
Is this the entire output? What do you have in /dev/sda1 ? Do you have Linux installed on it?
[http://ubuntuforums.org/showthread.php?t=555479](http://ubuntuforums.org/showthread.php?t=555479)

---

### Post by linuxnoob123456789 on 2008-07-05
Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0dcc0dc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         978     7855753+  83  Linux
/dev/hda2             979        1027      393592+   5  Extended
/dev/hda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44364435

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9824    78911248+   7  HPFS/NTFS
/dev/hdb2            9825       10011     1502077+   5  Extended
/dev/hdb5            9825       10011     1502046   82  Linux swap / Solaris

---

### Post by linuxnoob123456789 on 2008-07-06
I really need to know how to do this, its being used in a real office tomorrow and its needs to be able to out mount the second hard drive.:confused:

---

### Post by caljohnsmith on 2008-07-06
> **linuxnoob123456789 said:**
> I really need to know how to do this, its being used in a real office tomorrow and its needs to be able to out mount the second hard drive.:confused:
Are you just trying to mount the NTFS partition on the second HDD I assume since you are using it with Samba? If that is the case, try adding this to your /etc/fstab:

```
/dev/hdb1 /media/hdb1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
```

The /media/hdb1 directory is where the hdb1 partition will be mounted to, so if that directory does not exist, then you'll first have to create that hdb1 folder in the /media directory (sudo mkdir /media/hdb1). Of course you can call it something different if you like, but just keep it consistent with the fstab entry above.

---

### Post by linuxnoob123456789 on 2008-07-06
I do not fallow. This is just confusing me. sorry

---

### Post by caljohnsmith on 2008-07-06
OK, no problem, just open up a terminal (Applications > Accessories > Terminal), and type the following commands:
```
sudo mkdir /media/hdb1
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
That will pull up the gedit text editor with your /etc/fstab file. In that file, just add the following as a newline in the file:
```
/dev/hdb1 /media/hdb1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1

```
Then save and quit gedit. Ubuntu should now automatically mount your NTFS partition on your second HDD on startup, and it will be mounted to the /media/hdb1 directory.

---

### Post by linuxnoob123456789 on 2008-07-06
I got It to work.

Had to mod the code you gave to me to work with samba.

/dev/hdb1 /media/disk ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1]

---

