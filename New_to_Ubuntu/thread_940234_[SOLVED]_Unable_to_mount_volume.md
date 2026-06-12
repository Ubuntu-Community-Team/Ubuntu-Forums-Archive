---
title: "[SOLVED] Unable to mount volume"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by jmiller87 on 2008-10-06
I am trying to use a WD my book external hard drive and I can see it in my places but when I click on it to use I get the message:
Unable to mount Volume.......

Was told to post results of 
sudo blkid
sudo fdisk -l
cat /etc/fstab

I did so in terminal and this is what I got back:


joshua@JDM-Server:~$ sudo blkid
sudo: unable to resolve host JDM-Server
[sudo] password for joshua: 
/dev/sda1: UUID="8a776fcc-dbbd-424c-be88-120829251baf" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="53c42a8b-42d9-493c-8752-201b3f21212b" 
/dev/sdb1: LABEL="My Book" UUID="39D8-62EF" TYPE="vfat" 
joshua@JDM-Server:~$ sudo fdisk -l
sudo: unable to resolve host JDM-Server

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000badda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)
joshua@JDM-Server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8a776fcc-dbbd-424c-be88-120829251baf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=53c42a8b-42d9-493c-8752-201b3f21212b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
joshua@JDM-Server:~$ 




I am super new to all of this a Ubuntu as of about two days ago, and my goal for this dirve right now is to use it for all of my music and videos, and also be able to share it over my home network.
If anyone can help me or has ideas let me know
Thank you all!

---

### Post by Victormd on 2008-10-06
The last time you used this HD with windows, did you "safely remove device"? If so, you're going to have to boot windows, plug the HD in and then safely remove it...

---

### Post by kansasnoob on 2008-10-06
Hmmm, I'm not sure what's up, but I have pmount installed and my external drives all auto mount. It's in the repos so you can either install it from synaptic or just go to terminal and:

```
sudo apt-get install pmount
```

---

### Post by kansasnoob on 2008-10-06
> **Victormd said:**
> The last time you used this HD with windows, did you "safely remove device"? If so, you're going to have to boot windows, plug the HD in and then safely remove it...

+1 - I didn't think of that!

---

### Post by drs305 on 2008-10-06
jmiller87,

Thanks for starting a new post. If you want this disk in your fstab you have given us enough info - just let us know. Of course, if you are having problems mounting it with pmount it may not mount via fstab either...

Added: don't forget you can't type something with spaces (My Book). Enter it as "My Book" or 
My\ Book

---

### Post by jmiller87 on 2008-10-07
Well I tried installing pmount and it didn't work and I safley removed it from windows and that didn't seem to help either.
I am not sure if I want it in fstab, cuz I really don't know what that means...
my goal with the drive is to use it as extra storage for music and video files and share them one a home network. So what ever I should do with this drive to make that as easy as possible is what I want to do.
All your help is greatly appreciated.
thank you all!

---

### Post by cek on 2008-10-07
What about the output of the dmesg command after you plug in the disk?

---

### Post by jmiller87 on 2008-10-07
not sure what that means, I am so new I am still tring to learn all of this.
Could you explain what your asking??

---

### Post by jmiller87 on 2008-10-07
Someone asked me before what the file system was and I answered wrong...
the file system is FAT32, does this mean anything in concerning what I am trying to do??

---

### Post by drs305 on 2008-10-07
> **jmiller87 said:**
> 
my goal with the drive is to use it as extra storage for music and video files and share them one a home network. 

I know you have been working on this for a few days. Let's just try this. It is completely reversible. Names with spaces in them aren't always the easiest to work with, but I will use your "My Book" designation in the following. If you don't want to call the mountpoint "My Book", change the items in bold to the new name.

Make the mountpoints:
```

sudo mkdir /media/**"My Book"**

```

Change the ownership of the mountpoints to yourself and set permissions:
```

sudo chown -R *[COLOR="Red"]username:[/COLOR]* /media/**"My Book"**
chmod -R 750 /media/**"My Book"**

```

Make a backup copy of fstab and open with text editor (example uses gedit):
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Replace the fstab contents with the following. 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=8a776fcc-dbbd-424c-be88-120829251baf / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=53c42a8b-42d9-493c-8752-201b3f21212b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
LABEL="My Book" /media/**"My Book"** vfat users,uid=1000,umask=027,utf8 0 0

```
Save and exit.

Mount the new drive:
```

sudo mount /dev/sdb1

```

---

### Post by jmiller87 on 2008-10-07
well i put everything in terminal and changed the name to MYBOOK no spaces or anything.
and after I put in:

sudo mount /dev/sdb1

I got back:

mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

and I dont' think it worked....

---

### Post by drs305 on 2008-10-07
> **jmiller87 said:**
> well i put everything in terminal and changed the name to MYBOOK no spaces or anything.
and after I put in:

sudo mount /dev/sdb1

I got back:

mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

and I dont' think it worked....

What I would guess happened is that you changed the LABEL name in fstab to "MyBook". Unless you actually changed the label of the partition you would need to keep the LABEL="My Book" in the last line as it is (not LABEL="MyBook").

If that wasn't it, would you post your fstab again and we'll see what happened.

---

### Post by jmiller87 on 2008-10-07
this is what i did in terminal:

joshua@JDM-Server:~$ sudo chown -R joshua: /media/"MYBOOK"
sudo: unable to resolve host JDM-Server
joshua@JDM-Server:~$ chmod -R 750 /media/"MYBOOK"
joshua@JDM-Server:~$ sudo cp /etc/fstab /ect/fstab.backup
sudo: unable to resolve host JDM-Server
cp: cannot create regular file `/ect/fstab.backup': No such file or directory
joshua@JDM-Server:~$ sudo cp /etc/fstab /etc/fstab.backup
sudo: unable to resolve host JDM-Server
joshua@JDM-Server:~$ gksudo gedit /etc/fstab
joshua@JDM-Server:~$ sudo mount /dev/sdb1
sudo: unable to resolve host JDM-Server
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
joshua@JDM-Server:~$

---

### Post by jmiller87 on 2008-10-07
joshua@JDM-Server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=8a776fcc-dbbd-424c-be88-120829251baf / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=53c42a8b-42d9-493c-8752-201b3f21212b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
LABEL="MYBOOK" /media/"MYBOOK" vfat users,uid=1000,umask=027,utf8 0 0



So when I had the drive on windows I actually renamed it MYBOOK,
so when it's in windows and I can use it, it shows up as MYBOOK.

---

### Post by semitone36 on 2008-10-07
> **jmiller87 said:**
> I am not sure if I want it in fstab, cuz I really don't know what that means...

fstab is short for File System TABle.  It is just the type of filing system that governs each partition of your HDD.  I think what they were asking was do you want the file system to be the same as Linux's.  

Unfortunately I am a little green when it comes to hard core mounting projects like this but here is what comes to my mind while reading this thread:

FAT32 (the file system of your external HDD) is generally the file system type of windows.  Perhaps there are compatibility issues between Linux and the HDD?

---

### Post by Deathturtle on 2008-10-07
I have this problem, but I'm not using an external storage device, I'm just trying to open documents from my computer, I click "Places>Docs" and it says:
Cannot mount volume.
Unable to mount the volume 'Docs'.
"CLICK DETAILS"
$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb3': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g/dev/sdb3/media/Docs_-o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb3/media/Docs_ntfs-3g force 0 0

Problem is I have tried the first action and it comes up with this (limited in code usageageage):

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

And I have no idea how to do the second option.

HEEEELP! Thanks =]

---

### Post by semitone36 on 2008-10-07
It would probably be better for you to start a another thread.  Threads can get hard to follow when there are two separate problems being addressed.

---

### Post by vanadium on 2008-10-07
Back on the issue of jmiller87: it concerns an external fat formatted drive. Such a drive should not be mounted from /etc/fstab. It should mount automatically when plugged in.

I suggest you remove the line you added again from your /etc/fstab (or place a comment sign # before it. It is perhaps safest to restart the system before proceeding.

Then try mounting the drive manually, and post any messages here: these might give a clue as to why the disk does not mount:

```

cd
sudo mkdir test
sudo mount /dev/sdb1 test

```

---

### Post by drs305 on 2008-10-07
Follow up:

jmiller87 and I spent some time working on his problem via PM. 

The sudo commands were not working due to an entry in the HOSTS file. The computer name in the HOSTS file had an additional description beyond the computer name which was preventing sudo commands to work reliably. We edited the HOSTS file and changed the second line from:
```
127.0.1.1 computername.1234.abcd
to
127.0.1.1 computername
```
At this point sudo began working again.

Next we ensured the mountpoint was created and then corrected his fstab entries. The final fstab entry input was:
```

/dev/sdb1 /media/"MYBOOK" vfat users,uid=1000,umask=027,utf8 0 0

```
I will recommend he change "/dev/sdb1" to either a label or UUID entry since this is a removable drive and the device designation may change.

---

### Post by stephanvaningen on 2008-10-07
remember you can also mount forced (see man mount) which will mount even when Windows did not shut down properly (can it? maybe that's the only thing it can properly, besides suck ;-) [joke])
> **kansasnoob said:**
> +1 - I didn't think of that!

---

