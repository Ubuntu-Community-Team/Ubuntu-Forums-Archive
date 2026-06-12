---
title: "2nd HDD not recognised"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by timbim on 2008-10-23
I have a system with Xbuntu newly installed on one HDD on IDE channel 1, set as the master and a CD Rom as slave.  On channel 0, I have another HDD, this one with Win2000 installed.  I plan to migrate the files onto the new Xbuntu HDD, and leave the Win 2000 HDD unplugged and inactive, but still there if I ever need to use it for anything.  The problem is that I cannot find the HDD in Xbuntu, even in system monitor.  It is recognized by BIOS, as it will try to boot off it unless I tell it to boot into Xbuntu from the boot menu.
How con I make it show up in the Xbuntu file system?

Thanks,
Tim

---

### Post by Peter09 on 2008-10-23
to see if its there try 

```
lshw 
```

see if it shows your unmounted drive.

---

### Post by timbim on 2008-10-23
What am I looking for?  The output from that is confusing at best.

---

### Post by prshah on 2008-10-23
> **timbim said:**
> 
How con I make it show up in the Xbuntu file system?


> **Peter09 said:**
> to see if its there try 
```
lshw 
```


Open a Terminal (Applications-Accessories-Terminal) and post back the output of the command: ```
sudo fdisk -l
```

[s]lshw will not list any information about hard disk drives.[/s] Correction: lshw _does_ show hard disk drive information, as illustrated below in post #6.

---

### Post by Peter09 on 2008-10-23
Ok - put this in a terminal and copy the output to the forum so that we can see what is there.

```
sudo lshw -C disk
```

---

### Post by timbim on 2008-10-23
```
sudo fdisk -l
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a9c0a9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59607fbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3579    28748286   83  Linux
/dev/sdb2            3580        3738     1277167+   5  Extended
/dev/sdb5            3580        3738     1277136   82  Linux swap / Solaris
```


```
sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: Maxtor 6E040L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: NAR6
       serial: E11GQGXN
       size: 38GiB (41GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0a9c0a9c
  *-cdrom
       description: CD-R/CD-RW writer
       product: IDE5232
       vendor: CDWRITER
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 000J
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
  *-disk:1
       description: ATA Disk
       product: Maxtor 2F030J0
       vendor: Maxtor
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/sdb
       version: VAM5
       serial: F146KMTE
       size: 28GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=59607fbd

```

---

### Post by Peter09 on 2008-10-23
Hi,
so your second drive is there, /dev/sda1 but is not mounted. You will need to mount it.

does this link help you?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by timbim on 2008-10-23
Don't think so, I doesn't show up in the places menu!

---

### Post by Peter09 on 2008-10-23
Here is a link which describes how to use the mount command in a terminal.

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

your device is /dev/sda1 and your filesystem type is ntfs. You need to decide where to mount the device. Have a read of the above and see how you feel about mounting it.

---

### Post by Peter09 on 2008-10-23
you will need to use a command like

```
sudo mount /dev/sda1 /mnt
```

/mnt is the directory upon which the disk is mounted. The normal directory used is /media which should exist. Go in and create an empty directory called .....  something like.... disk1.... and use that as the directory to mount it on.

```
sudo mount /dev/sda1 /media/disk1 -t ntfs
```

might work.

---

### Post by 3rdalbum on 2008-10-23
If it wasn't automatically mounted, it might have been improperly mounted from within Windows or might be due for a chkdsk. If you can boot up Windows from it just once, try doing that and then shutting down.

---

### Post by Peter09 on 2008-10-23
Yes, thats a good thought 3rdalbum. Suggest thats the first way to go rather than starting with the mount.

---

### Post by timbim on 2008-10-23
Right, I rebooted into windows, shut down properly, booted back into Xubuntu, but it still isn't showing up.  What command do I need to issue to mount it permanently?

---

### Post by Peter09 on 2008-10-23
firstly can you mount it as suggested?

---

### Post by timbim on 2008-10-23
I tried
```
sudo mount /dev/sda1 /media/disk1 -t ntfs
```
and got
```
fuse: failed to access mountpoint /media/disk1: No such file or directory
```

:confused: Any ideas?

---

### Post by Peter09 on 2008-10-23
Yes,
you need to create a folder in /media called disk1

In Linux when you mount something it is mounted over an empty folder. When you then go into that folder you see the filesystem that you have mounted. It is complaining because you have tried to mount on a folder that does not exist.

---

### Post by Peter09 on 2008-10-23
Hi,
the command you want to make the directory is

```
sudo mkdir /media/disk1
```

this should make the directory disk1 in the folder /media

---

### Post by Duck2006 on 2008-10-23
Make your mount point.
Edit your fstab.
Then mount the partition.

For windoze

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For linux

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by timbim on 2008-10-23
So I need to boot up under windows to create the folder?

---

### Post by Peter09 on 2008-10-23
no, go to Applications->Accessories->terminal

that will open a terminal window. 

Type the command in there.

---

### Post by timbim on 2008-10-23
So how which bit of that command identifies which disk that is written to?

---

### Post by Peter09 on 2008-10-23
You are creating the folder on your Ubuntu disk. This is the one that is mounted already. Having done that we will mount the windows drive onto that folder.

---

### Post by timbim on 2008-10-23
Now it's coming back with device or resource busy.

---

### Post by Peter09 on 2008-10-23
What command is giving you that error - the mount command?

---

### Post by timbim on 2008-10-23
Got it now, the contents of the disk shos up in /media/disk1, but it would be preferable to have it listed as a separate volume in places?  Is that possible, or will I have to put up with what I already have?

---

### Post by Duck2006 on 2008-10-23
Change your mount point to where you want it to show up, then edit your fstab.

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by prshah on 2008-10-23
> **timbim said:**
> Got it now, the contents of the disk shos up in /media/disk1, but it would be preferable to have it listed as a separate volume in places?  Is that possible, or will I have to put up with what I already have?

If you want it automounted, you have to list it in your /etc/fstab; an entry similar to ```

/dev/sda1 /media/disk1     ntfs    defaults,umask=007,gid=46 0       1

``` will do the trick.

However, if you want to mount on an as-you-need basis, it's simpler to use [pmount]("apt://pmount") dynamic mounting; this is similar to what is used when (auto)mounting usb storage devices. Just give the command```
pmount /dev/sda1
``` and it will create the mount point, mount the device, list it in places and adjust the necessary permissions. Similarly use pumount to unmount; note that sudo is neither involved nor required (nor even recommended). Using sudo to mount the device as shown earlier will not allow you to use the ntfs partition as an ordinary user (except to read data), and trying to access it with sudo-ed nautilus (the file manager) will open up a whole new bunch of problems.

Also, for the fstab entry it's better you switch to using UUIDs. To find out the UUID of your ntfs partition, use ```
sudo blkid /dev/sda1
``` and then modify the fstab entry as follows```
#/dev/sda1
[color=red]UUID=EC707BBE707B8DD8[/color] /media/disk1     ntfs    defaults,umask=007,gid=46 0       1

``` (Of course, replace the part in RED with the actual UUID of your /dev/sda1)

Also note that both pmount and the above entries require you (your username) to be a member of the group "plugdev" (which is the default behavior in any case).

---

### Post by Peter09 on 2008-10-23
Hi timbim,
hope you finally got things sorted.

---

### Post by timbim on 2008-10-24
I've found the fstab file, but if I try to edit it, it won't let me save.  I'm logged in as an administrator, if that helps.

---

### Post by Peter09 on 2008-10-24
you are using a command like

```
sudo gedit /etc/fstab
```

OK?

---

### Post by timbim on 2008-10-24
Returns ```
sudo: gedit: command not found
```

---

### Post by prshah on 2008-10-24
> **Peter09 said:**
> 
```
sudo gedit /etc/fstab
```


> **timbim said:**
> Returns ```
sudo: gedit: command not found
```

In Xubuntu, use mousepad instead of gedit; but first, make a backup of the original file. From the terminal, give the commands```
sudo cp -p /etc/fstab ~
gksu mousepad /etc/fstab
```

---

### Post by Duck2006 on 2008-10-24
[QUOTE]sudo gedit /etc/fstab/[QUOTE]

Should be.

gksudo gedit /etc/fstab[

---

