---
title: "[SOLVED] Should I mount extra ide hard drives on boot?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by jomo_london on 2008-06-26
Hi there all
I'm a new ubuntu user. Hurrah! I have a dual partition main hard drive. One partition with Windows XP and the other ubuntu 8.04. I have two other IDE drives, both NTFS formatted, one called data, the other music. I want to automatically be able to access these drives after boot up. And to use the data drive and folder X on it as my main area for documents (the equivalent of My Documents in Windows XP). I want to continue to use folder X as My Documents folder in windows.  So, how do I use folder X as my main document store, and the music drive as as my main dual boot for both ubuntu and windows. Do I need to mount these drives (steady!) during boot? As a new user, please can anyone give step by step instruction? Thanks in anticipation.

---

### Post by Canis familiaris on 2008-06-26
Could you plz post the output of:
```
sudo fdisk -l

```

---

### Post by jomo_london on 2008-06-26
> **Anurag_panda said:**
> Could you plz post the output of:
```
sudo fdisk -l

```
Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18d4f0d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7509    60316011    7  HPFS/NTFS
/dev/sda2            7510       15017    60308010    5  Extended
/dev/sda5            7510        7882     2996091   82  Linux swap / Solaris
/dev/sda6            7883       10260    19101253+  83  Linux
/dev/sda7           10261       15017    38210571   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f5d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c90de2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       20023   160834716    7  HPFS/NTFS

---

### Post by Canis familiaris on 2008-06-26
First go to the terminal.

```
sudo mkdir /mnt/windows
```

```
mount -t ntfs-3g /dev/sda1 /mnt/windows/
```

EDIT: It should be
```
sudo mount -t ntfs-3g /dev/sda1 /mnt/windows/
```

Now navigate to /mnt/windows and check whether you can read and write.

EDIT:
This is only to check whether ntfs-3g works in your system

---

### Post by jomo_london on 2008-06-26
> **Anurag_panda said:**
> First go to the terminal.

```
sudo mkdir /mnt/windows
```

```
mount -t ntfs-3g /dev/sda1 /mnt/windows/
```

Now navigate to /mnt/windows and check whether you can read and write.

EDIT:
This is only to check whether ntfs-3g works in your system
Thanks. Haven't tried yet.  Just first want to clarify: Folder X, where windows points to as 'My Documents' is on data drive /dev/sdb and music drive is  /dev/sdc drive.  Why do I need to mount sda1? Remember I am new to this! This might be very silly of me to query.

---

### Post by Canis familiaris on 2008-06-26
> **jomo_london said:**
> Thanks. Haven't tried yet.  Just first want to clarify: Folder X, where windows points to as 'My Documents' is on data drive /dev/sdb and music drive is  /dev/sdc drive.  Why do I need to mount sda1? Remember I am new to this! This might be very silly of me to query.

I asked you to mount /dev/sda1 just to check whether read/write in the ntfs worked. Before you edit your GRUB.
Now you can unmount it;
```
sudo umount /dev/sda1
```

So
/dev/sdc1 is your music drive
/dev/sdb1 is your documents drive

Now you want to automount these partitions at startup. Right?

So
Proceed only if you can read/write to the ntfs partition as per previous post.

First make a backup copy of fstab.
```
sudo cp /etc/fstab /etc/fstab.bak
```

Now 
```
sudo mkdir /mnt/music
```
```
sudo mkdir /mnt/docs
```

Then
```
gedit /etc/fstab
```

Scroll to the end of the file and add the following lines:

```
# Manually added partitions:
/dev/sdb1     /media/docs     ntfs-3g     defaults,locale=en_US.utf8   0    0
/dev/sdc1     /media/music     ntfs-3g     defaults,locale=en_US.utf8   0    0
```

Save it.

To apply enter this command
```
sudo mount -a
```

Now you can access those partitions at bootup in the /mnt folder.
If you can list where in the /dev/sdb1 is your document files and where in the /dev/sdc1 is your music files. Then I can tell you how to create a symbolic link to access those folders from the home folder.```

```

---

### Post by Victormd on 2008-06-26
You don't need to install ntfs-3g assuming you're using Hardy.
Check out the link on my signature.

---

### Post by drs305 on 2008-06-26
If you install and run ntfs-config from synaptic or command line it can run a wizard that will set up the ntfs partitions to automatically mount and make the appropriate fstab entries.

---

### Post by jomo_london on 2008-06-26
Thanks for that.

Just tried:

sudo mkdir /mnt/windows

and then

mount -t ntfs-3g /dev/sda1 /mnt/windows/

and I get the response

mount: only root can do that

Should I sign in as root so tht I have permission to mount /windows?

---

### Post by Canis familiaris on 2008-06-26
> **drs305 said:**
> If you install and run ntfs-config from synaptic or command line it can run a wizard that will set up the ntfs partitions to automatically mount and make the appropriate fstab entries.
I made the work seem much harder.:lolflag:

@OP:
Ignore my previous post and:

```
sudo apt-get install ntfs-config

```
And then run ntfs-config

---

### Post by Canis familiaris on 2008-06-26
> **jomo_london said:**
> Thanks for that.

Just tried:

sudo mkdir /mnt/windows

and then

mount -t ntfs-3g /dev/sda1 /mnt/windows/

and I get the response

mount: only root can do that

Should I sign in as root so tht I have permission to mount /windows?

ER! Sorry !
It should be 
```
sudo mount -t ntfs-3g /dev/sda1 /mnt/windows/
```

---

### Post by jomo_london on 2008-06-26
```
sudo apt-get install ntfs-config

```

Thanks very much for that.  Now a happy bunny.  Or is it a happy heron?
Thanks also to drs305 and Victornd as well.


> **Anurag_panda said:**
> I made the work seem much harder.:lolflag:

@OP:
Ignore my previous post and:

```
sudo apt-get install ntfs-config

```
And then run ntfs-config

---

### Post by Canis familiaris on 2008-06-26
If it has worked for you Kindly mark the thread as solved

---

### Post by HousieMousie2 on 2008-08-19
> **drs305 said:**
> If you install and run ntfs-config from synaptic or command line it can run a wizard that will set up the ntfs partitions to automatically mount and make the appropriate fstab entries.

If I could kiss you I WOULD!

THANK YOU!  THANK YOU!  THANK YOU!!!

Unfortunately... the option to give you a formal thanking was not available, or I would have done that also!  I will however give you a thank you on the thread I posted trying to fix my own mounting issues.

Again..



THANK YOU!  THANK YOU!  THANK YOU!!!  You :guitar: !!!


EDITED:
Ah, good... it gave me back the option to 'thank'!

---

