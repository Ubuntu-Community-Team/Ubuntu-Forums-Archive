---
title: "[SOLVED] Trying to use a USB Drive on Ubuntu and Windows"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by amishphysicist on 2008-09-30
Heya,

I've got a flash drive that I'd like to be able to add files to in ubuntu, and read from in windows.  When I plug it into my computer, it shows up, but can't mount.  I get "**Unable to mount location** Can't mount file" when I try to open it.

Do I have to do something fancy here?

thanks,

-nate

---

### Post by Louis de Broglie on 2008-09-30
Try this in a terminal:

> 
cd /mnt
sudo mkdir pendrive
sudo mount /dev/sdb /mnt/pendrive


Mounting should work out of box unless it is a permission issue. Also make sure you have hal daemon running.

---

### Post by amishphysicist on 2008-09-30
getting this for the mount command:
mount: you must specify the filesystem type

how do I check if the hal daemon is up?

---

### Post by Louis de Broglie on 2008-09-30
Open this file ( DONT EDIT IT ):

/etc/rc.conf

Then look at the section daemons=(....)

If you see hal is there then hal is up if not then you will need to install hal to get out of the box usb support :)

---

### Post by amishphysicist on 2008-09-30
> **amishphysicist said:**
> getting this for the mount command:
mount: you must specify the filesystem type

how do I check if the hal daemon is up?

Tried again and got this:

```
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

It's a micro SD card going through a USB adapter thingie, so maybe it's only supported in Winderz.  Is there any way of auto detecting the FS, in case it's doing something wonky?

---

### Post by amishphysicist on 2008-09-30
> **Louis de Broglie said:**
> Open this file ( DONT EDIT IT ):

/etc/rc.conf

Then look at the section daemons=(....)

If you see hal is there then hal is up if not then you will need to install hal to get out of the box usb support :)
Hrmmm. No rc.conf in etc. locate rc.conf gives me nothing as well.  I figure I've got USB support, since I can plug in other goodies already.

---

### Post by Louis de Broglie on 2008-09-30
You can view all devices by the following command :

> 
sudo fdisk -l


---

### Post by Louis de Broglie on 2008-09-30
From there you should be able to determine which one is your usb drive. Then mount the drive with mount command.

---

### Post by amishphysicist on 2008-09-30
> **Louis de Broglie said:**
> You can view all devices by the following command :

Hmm. looks like it's "W95 FAT32"? 13 years later and the ghost lives on...

```
sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72ff72ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9726     3004155    5  Extended
/dev/sda5            9353        9726     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 8168 MB, 8168931328 bytes
39 heads, 5 sectors/track, 81820 cylinders
Units = cylinders of 195 * 512 = 99840 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              43       81821     7973376    b  W95 FAT32

```

---

### Post by WWSmith36 on 2008-09-30
> Is there any way of auto detecting the FS, in case it's doing something wonky?

This will display all drives and their filesystem
```
sudo fdisk -l
```

This will show you the mount points and permissions
```
sudo mount
```

---

### Post by Louis de Broglie on 2008-09-30
Try this :

> 
sudo mount /dev/sdb1 /mnt/pendrive


---

### Post by amishphysicist on 2008-09-30
> **Louis de Broglie said:**
> Try this :

That did it.  You win the pony!

---

### Post by Louis de Broglie on 2008-09-30
Unmount the usb drive before plugging it out :

> 
sudo umount /mnt/pendrive


Also please mark this thread as "SOLVED"

---

### Post by amishphysicist on 2008-09-30
> **Louis de Broglie said:**
> Unmount the usb drive before plugging it out :

Looks like I was too quick in thinking it worked.  I can view the files now but am getting permission errors when trying to add new ones.  Even after chmodding the dir, I can't even touch a new file.  Any ideas there?

---

### Post by Louis de Broglie on 2008-09-30
Unmount the drive with the command first.

Then try mounting it in your home drive :

> 
cd ~
sudo mkdir usbdrive
sudo mount /dev/sdb1 ~/usbdrive


---

### Post by amishphysicist on 2008-09-30
hmm... same as before:
```
:~/usbdrive/DS Roms$ touch sadf
touch: cannot touch `sadf': Permission denied
```

---

### Post by Louis de Broglie on 2008-09-30
What exactly you can't do ? :confused:

Permission denied copying or , executing something else ? :)

---

### Post by amishphysicist on 2008-09-30
I'm trying to copy stuff over to the dir.  If I navigate to the dir, I can't even touch a new file there.  So the drive is effectively locked down.

---

### Post by Louis de Broglie on 2008-09-30
Can you touch the files somewhere else ? I mean not in the usb drive.

---

### Post by amishphysicist on 2008-09-30
heh. yeah. I can touch anywhere else... I'd be pretty hosed if I couldn't touch a new file in my home dir :D

```

:~$ touch asdf
:~$ ls -ltr asdf 
-rw-r--r-- 1 nlieby nlieby 0 2008-09-30 16:03 asdf

```

---

### Post by Louis de Broglie on 2008-09-30
Try posting this permission issue in security support. I am no security expert.:D

---

### Post by amishphysicist on 2008-09-30
OK. Will do. Thanks for getting it mounted, at least!

---

