---
title: "[SOLVED] What key represents the space in filenames"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-06
I have a USB memory stick. Ubuntu loses it's file permission ownership and defaults to root.


the folder I need to chown to is named:

Unlawful Detainer

what key or keyboard symbol is used to designate a space?

---

### Post by philinux on 2008-05-06
If memory serves you can put quotes round it or use \ or in the terminal press tab after the first bit and it will sort it for you.

---

### Post by tacutu on 2008-05-06
Alternatively, you can use globbing. Try it, it's fun! Type only
```
Unl<TAB>

```
and the shell will complete the name for you!

---

### Post by Cypher on 2008-05-06
Also, you could put the name in quotes like "Unlawful Detainer"..

---

### Post by Mark_in_Hollywood on 2008-05-06
Yes, using the tab put the right letters & symbols in the command line, still no go

this is what I "commanded"

root@Lexington-19:/media/ubuntu710# chown -R mark Unlawful\ Detainer/

the terminal screen whizzes by dozens of lines of filenames, folder names and stops, but:

see screen print for the result.

---

### Post by tacutu on 2008-05-06
so what is this ubuntu710? a file? a directory? a what?

---

### Post by Mark_in_Hollywood on 2008-05-06
That is the name of the memory stick as seen by the OS

---

### Post by NilsE on 2008-05-06
Try replacing the space with %20

Not sure it will work since that is an HTML convention but worth a try.

---

### Post by Mark_in_Hollywood on 2008-05-06
root@Lexington-19:/media/ubuntu710# sudo chown -R mark Unlawful%20Detainer
chown: cannot access `Unlawful%20Detainer': No such file or directory

---

### Post by tacutu on 2008-05-06
what filesystem do you have on that? ntfs? vfat?

---

### Post by Mark_in_Hollywood on 2008-05-06
msdos

---

### Post by philinux on 2008-05-06
sudo chown -R mark /media/Unlawful%20Detainer

---

### Post by Mark_in_Hollywood on 2008-05-06
hummm?

mark@Lexington-19:/media$ cd /media/ubuntu710
mark@Lexington-19:/media/ubuntu710$ sudo chown -R mark /media/Unlawful%20Detainer
chown: cannot access `/media/Unlawful%20Detainer': No such file or directory

---

### Post by philinux on 2008-05-06
> **Mark_in_Hollywood said:**
> hummm?

mark@Lexington-19:/media$ cd /media/ubuntu710
mark@Lexington-19:/media/ubuntu710$ sudo chown -R mark /media/Unlawful%20Detainer
chown: cannot access `/media/Unlawful%20Detainer': No such file or directory

maybe you need the \ then ot press the tab key after /media/unlawful

---

### Post by phr0ze on 2008-05-06
Dont use the %20. Try either single 'quotes' or double "quotes" around your word with a space. I know DOS prefers it.

---

### Post by Oldsoldier2003 on 2008-05-06
> **tacutu said:**
> Alternatively, you can use globbing. Try it, it's fun! Type only
```
Unl<TAB>

```
and the shell will complete the name for you!

bash completion FTW!

---

### Post by Mark_in_Hollywood on 2008-05-06
Let me come at this problem another way:

mark@Lexington-19:/media$ sudo chown mark ubuntu710/
chown: changing ownership of `ubuntu710/': Read-only file system


ubuntu710 is seen as part of the directory structure. It is the usb memory stick. It has the directory name: ubuntu710

Why is chown report read-only?

---

### Post by bodhi.zazen on 2008-05-06
> **Mark_in_Hollywood said:**
> msdos

You have to set permissions at the time of mounting.

sudo mount /dev/sdxy /mount/point -o uid=100,gid=100,umask=007

or add those options to fstab.

---

### Post by futileissue on 2008-05-06
msdos is a label, not a filesystem.  Recheck the drive in gparted or some other editor, and check to see if it is vfat, fat32, ntfs, ext3, or something else.

FAT filesystems do not allow for permissions.  Most USB sticks come with fat formatting since it is the oldest format that's the most universal between OS's.  If they had permissions when you put them on there, the copies on the USB stick will no longer have an owner or access controls.  It will show up as something like "root" but this is not really accurate.

---

### Post by tacutu on 2008-05-06
because it is mounted as read-only? 
try this to remount read-write:
```
 sudo mount /dev/<your-usbstick-device> /media/ubuntu710 -o remount,rw
```

---

### Post by philinux on 2008-05-06
> **futileissue said:**
> msdos is a label, not a filesystem.  Recheck the drive in gparted or some other editor, and check to see if it is vfat, fat32, ntfs, ext3, or something else.

FAT filesystems do not allow for permissions.  Most USB sticks come with fat formatting since it is the oldest format that's the most universal between OS's.  If they had permissions when you put them on there, the copies on the USB stick will no longer have an owner or access controls.  It will show up as something like "root" but this is not really accurate.

Yes but you can chown the mount point.

---

### Post by Mark_in_Hollywood on 2008-05-06
> **bodhi.zazen said:**
> You have to set permissions at the time of mounting.

sudo mount /dev/sdxy /mount/point -o uid=100,gid=100,umask=007

or add those options to fstab.

My /dev shows usb and usblp0 

I can't tell them apart. Thank to the poster who said msdos is a label. That reminded me that the usb stick named: ubuntu710 had the 7.10 OS on it as a traveling ubuntu. So it is formatted in Linux, maybe as /

---

### Post by Mark_in_Hollywood on 2008-05-06
Filesystem is FAT16

---

### Post by Mark_in_Hollywood on 2008-05-06
hmmmm, again:

mark@Lexington-19:~$ sudo mount /dev/**sdb1** /mount/point -o uid=100,gid=100,umask=007

mount: mount point /mount/point does not exist

see screenshot, please

---

### Post by bodhi.zazen on 2008-05-06
LOL

First, identify the device with :```
sudo fdisk -l
```

Second unmount the device.

Third re-mount it. You have to change "/mount/point" to the location you want it mounted, ie /media/usb

If the mount pint does not exist, make it :

```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb -o uid=100,gid=100,umask=007
```

---

### Post by Mark_in_Hollywood on 2008-05-06
> **bodhi.zazen said:**
> LOL

First, identify the device with :```
sudo fdisk -l
```

Second unmount the device.

Third re-mount it. You have to change "/mount/point" to the location you want it mounted, ie /media/usb

If the mount point does not exist, make it :

```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb -o uid=100,gid=100,umask=007
```

=============

mark@Lexington-19:~$ sudo fdisk -l

Disk /dev/sdd: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

Next I unmount, then remount:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         122      979933+  83  Linux

sudo mkdir /media/usb

mark@Lexington-19:~$ sudo mount /dev/sdd1 /media/usb -o uid=100,gid=100,umask=007

mark@Lexington-19:~$ 

yet, when I look at the properties of the device, they all show as owned by root.

Can I just reformat the memory stick into ext3 or something simple? This is kinda driving me nuts.

---

### Post by bodhi.zazen on 2008-05-06
LOL, not the device, the device is always owned by root

Access the files at /media/usb

ls -l /media

---

### Post by Mark_in_Hollywood on 2008-05-06
> **bodhi.zazen said:**
> LOL, not the device, the device is always owned by root

Access the files at /media/usb

ls -l /media

No, thanks, the stick now cannot be mounted. When I remove it and re-insert the stick no file browser window opens any longer, nor can I save a file into it.

The permissions say that they cannot be determined.

Can I reformat the stick? Is it better to use ext2 or ext3? Should the partition be primary or extended?

ls -l /media
drwxr-xr-x 2 root root  4096 2008-05-06 16:37 usb

I just ran the System/Admin/Partition Editor against the device again, and now it's /dev/sdb1. I did not change or repartition it, just looked to see what /dev it is now.

---

### Post by bodhi.zazen on 2008-05-06
The device will not auto mount unless you remove the entry from fstab as auto mounting and manual mounting are not the same.

Removable devices may change designation, thus you may want to use labels or uuid in /etc/fstab. List the device uuid with ```
blkid
```The basics of mounting are not dependent on the file system, setting the permissions are.

You say the devices is now /dev/sdb1 ? that is the same as you last posted.

What happens when you :

```

sudo umount /dev/sdb1
sudo mount /dev/sdb1 /media/usb -o uid=100,gid=100,umask=007
ls -la /media
ls -la /media/usb
```Is there an error message of any kind ? if so please post the exact error message.

If you re-format the device with ext2 or ext3 you will mount it with :

```
sudo mount /dev/sdb1 /media/usb
```

and set ownership with chown and chmod.

Once you decide on a filesystem and mount point we can write an entry for fstab.

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Mark_in_Hollywood on 2008-05-09
mark@Lexington-19:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted

mark@Lexington-19:~$ sudo mount /dev/sdb1 /media/usb -o uid=100,gid=100,umask=007
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mark@Lexington-19:~$ ls -la /media
total 44
drwxr-xr-x  7 root root  4096 2008-05-09 06:49 .
drwxr-xr-x 21 root root  4096 2008-04-23 21:56 ..
lrwxrwxrwx  1 root root     6 2008-04-22 07:58 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-04-22 07:58 cdrom0
drwxr-xr-x  2 root root  4096 2008-04-22 07:58 cdrom1
lrwxrwxrwx  1 root root     7 2008-04-22 07:58 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-04-22 07:58 floppy0
-rw-r--r--  1 root root   115 2008-05-09 06:49 .hal-mtab
-rw-------  1 root root     0 2008-05-09 06:49 .hal-mtab-lock
drwx------  5 mark root 16384 1969-12-31 16:00 UDISK 28X
drwxr-xr-x  2 mark root  4096 2008-05-06 16:37 usb

mark@Lexington-19:~$ ls -la /media/usb
total 8
drwxr-xr-x 2 mark root 4096 2008-05-06 16:37 .
drwxr-xr-x 7 root root 4096 2008-05-09 06:49 ..

relevant line in /etc/fstab:

none /proc/bus/usb usbfs auto,devmode=0666 0 0

mark@Lexington-19:~$ dmesg | tail
[ 1569.493923] usb 3-1: usbfs: interface 0 claimed by usblp while 'brscan-skey-0.2' sets config #1

above repeats ten times with differing numbers at the start of the lines.

---

### Post by Mark_in_Hollywood on 2008-05-11
I'm hopelessly lost now. I've been at this for 3 days and turned myself inside out.

See the attached screenshot.

---

### Post by Mark_in_Hollywood on 2008-05-27
Eventually, I took the USB memory stick or jumpdrive to a friend's house. Even though he uses Windows XP, the device was found, reported as unformatted. When I was asked if I wanted to format the device, I responded "YES". Once formated, the device is now read/write back at home, under Hardy Heron v 8.04

Thanks everyone.

---

