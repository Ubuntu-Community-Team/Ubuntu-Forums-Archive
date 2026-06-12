---
title: "cannont mount volume"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by marine63 on 2008-05-06
I'm trying to open my ntfs drive thru ubuntu and I get this message
[http://www.flickr.com/photos/10075528@N00/2472047202/sizes/o/](http://www.flickr.com/photos/10075528@N00/2472047202/sizes/o/)
any assistance would be appreciated

---

### Post by cwgatling on 2008-05-06
What steps are you taking to mount it? Looks like you need to 'sudo' :)

---

### Post by ACJarrett on 2008-05-06
Do you know what your device is called under dev?

i believe the command is

```
sudo mount /dev/hd1 /mnt/hd1
```

Where hd1 is the name of your NTFS Volume

---

### Post by marine63 on 2008-05-06
> d@desktop:~$ sudo mount /dev/hd1 /mnt/hd1
[sudo] password for d: 
mount: mount point /mnt/hd1 does not exist
d@desktop:~$ 

:l
do you mean this??
> d@desktop:~$ sudo fdisk -l
[sudo] password for d: 

Disk /dev/sda: 320.0 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46e978f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38725   311058531   83  Linux
/dev/sda2           38726       38913     1510110    5  Extended
/dev/sda5           38726       38913     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc01ac01a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12187    97892046    7  HPFS/NTFS
d@desktop:~$ 


---

### Post by ACJarrett on 2008-05-06
Sorry, I didn't know what your NTFS was labeled as so i put hd1 to make an example.  Try this

```
sudo mount /dev/sdb1 /mnt/sdb1
```

---

### Post by cwgatling on 2008-05-06
First, as AC said, identify where your drive is by

```
sudo fdisk -l
```

Then, (let's assume it's /dev/sda2) create a mount point.

```
mkdir /media/ntfs
```

Then it'll be 

```
sudo mount -t ntfs /dev/sda2 /media/ntfs
```

If you need read/write access every time you boot, use this tutorial:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by marine63 on 2008-05-06
:l
> d@desktop:~$ sudo mount /dev/sdb1 /mnt/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /mnt/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /mnt/sdb1 ntfs-3g force 0 0
d@desktop:~$ mkdir /media/ntfs
mkdir: cannot create directory `/media/ntfs': Permission denied
d@desktop:~$ sudo su
root@desktop:/home/d# mkdir /media/ntfs
root@desktop:/home/d# mkdir /media/ntfs
mkdir: cannot create directory `/media/ntfs': File exists
root@desktop:/home/d# sudo mount -t ntfs /dev/sda2 /media/ntfs
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@desktop:/home/d# sudo mount -t ntfs /dev/sdb1 /media/ntfs
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/ntfs -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/ntfs ntfs-3g force 0 0
root@desktop:/home/d# /dev/sdb1 /media/ntfs ntfs-3g force 0 0
bash: /dev/sdb1: Permission denied
root@desktop:/home/d#             mount -t ntfs-3g /dev/sdb1 /media/ntfs -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
root@desktop:/home/d# 

it worked some how... thx

---

