---
title: "commands to mount for windows access ??"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by jfchabot on 2008-09-07
I need to access from ubuntu (yet installed) to my windows files and programs.
Somebody could explain to me what is the process to mount the system for windows access
Thank you for your time

---

### Post by schauerlich on 2008-09-07
Could you post the output of:

```

fdisk -l

```

The basic syntax is 

```

sudo mkdir /media/somenamehere
sudo mount -t ntfs-3g /dev/sdxy /media/somenamehere

```

Where x is the drive letter and y is the partition number.

---

### Post by diwas on 2008-09-07
goto places>click the partition where windows is.

Or do u need the command line??

---

### Post by jfchabot on 2008-09-07
> **diwas said:**
> goto places>click the partition where windows is.

Or do u need the command line??
Thank you diwas
Into places, no windows partition appears...:confused:
Into places/computer the same.......

---

### Post by Xiong Chiamiov on 2008-09-07
Could you please post the output of
```

sudo fdisk -l

```

---

### Post by jfchabot on 2008-09-07
> **EDavidBurg said:**
> Could you post the output of:

```

fdisk -l

```

The basic syntax is 

```

sudo mkdir /media/somenamehere
sudo mount -t ntfs-3g /dev/sdxy /media/somenamehere

```

Where x is the drive letter and y is the partition number.
Thank you EDavidBurg !
This too complicated for a Linux beginner like me. I do not know how to do that :confused:

---

### Post by schauerlich on 2008-09-07
> **jfchabot said:**
> Thank you EDavidBurg !
This too complicated for a Linux beginner like me. I do not know how to do that :confused:

Go to Applications>Accessories>Terminal. You will get a command line. Paste the first command I gave you, hit enter, and then copy and paste everything it sends back to you and put it on here between a [noparse]```
[/noparse] tag and [noparse]
```[/noparse].

---

### Post by Xiong Chiamiov on 2008-09-07
> **jfchabot said:**
> Thank you EDavidBurg !
This too complicated for a Linux beginner like me. I do not know how to do that :confused:
First, you need to [open the terminal]("http://www.psychocats.net/ubuntu/terminal").

Then, if you give us the output of
```

sudo fdisk -l

```
we can help you with the rest.

---

### Post by jfchabot on 2008-09-07
> **Xiong Chiamiov said:**
> First, you need to [open the terminal]("http://www.psychocats.net/ubuntu/terminal").

Then, if you give us the output of
```

sudo fdisk -l

```
we can help you with the rest.
Thanks Xiong Chiamiov

With fdisk -l i get:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfef5de3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/sda2            7140       14283    57384180   83  Linux
/dev/sda3           14284       14593     2490075    5  Extended
/dev/sda5           14284       14593     2490043+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21f16422

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS

---

### Post by schauerlich on 2008-09-07
Is your windows partition the one that's on the same HD as your Ubuntu partition? If so, run this:

```

sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows

```

If your windows partition is on the other hard disk, run those same commands except replace /dev/sda1 with /dev/sdb5

---

### Post by Tatty on 2008-09-07
There is already a thread for this problem here:
[http://ubuntuforums.org/showthread.php?t=913061](http://ubuntuforums.org/showthread.php?t=913061)

OP, Please do not double-post threads, it can lead to some confusion.  Thanks.

---

### Post by alienexplorers on 2008-09-07
This article explains how to mount a windows drive:
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by Xiong Chiamiov on 2008-09-07
Ok, so we can see that you have 2 windows partitions: /dev/sda1 and /dev/sdb5.  I will show the process with one, but it's the same thing for the other.

First, we need to make a place for you to access the files.  It's a good idea to put them in /media, so I'll make a directory there called windows (you can call it whatever you like).
```

cd /media
sudo mkdir windows

```

Normally, for mounting drives, you could just say
```

sudo mount /dev/sda1 /media/windows

```
However, since it's NTFS, you might need to try this:
```

sudo mount /dev/sda1 -t ntfs -o nls=utf8,umask=0222 /media/windows

```

If that's successful, then we can add it to your fstab so that it gets mounted automatically at boot.
First, open the file:
```

gksudo gedit /etc/fstab

```
Then add a line that says:
```

/dev/sda1   /media/windows   ntfs   defaults   0   0

```

EDIT: Whew, I was slow!

---

