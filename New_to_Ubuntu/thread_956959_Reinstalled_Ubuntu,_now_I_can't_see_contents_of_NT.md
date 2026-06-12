---
title: "Reinstalled Ubuntu, now I can't see contents of NTFS formatted USB hard drive"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by danimaltron on 2008-10-23
I installed Ubuntu last night. ntfs-3g must have been installed automatically with desktop amd64 version.

But I had to reinstall to fix some partitioning errors I made. I used the 32bit Alternate CD this time in order to use LVM.

But now, I can't see any of the files on the USB hard drive. I see that it's mounted (icon on my desktop) but when I open it up no files or folders are shown. It also tells me how much space is used/free.

I checked synaptic package manager, and ntfs-3g is installed. I also opened ntfs-3g config and checked off option to enable writing on external hard drives.

Still no love.

What can I do to make this work? It worked great yesterday out of the box. Not sure what's going on now.

---

### Post by danimaltron on 2008-10-23
Is there some packages that don't come installed if you use the Alternate CD?

---

### Post by Ducatiboy Stu on 2008-10-23
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by danimaltron on 2008-10-24
I can see the files fine on my Mac. The frive is NTFS. I have ntfs-3g installed on my Mac as well. The drive doesn't need to be recovered.

---

### Post by bumanie on 2008-10-24
Hmm... 8.04 installs ntfs-3g by default. As  ntfs-config didn't help, are you getting an error message? If so please attach a screenshot. I suspect that the ntfs drive may have not been shut down correctly  - if a filesystem has not been unmounted properly, linux will not read it as the filesystem is seen as still being in use. If this is the case restart in windows and shutdown properly via 'safely remove hardware'. Other options are to install ntfsprogs. > sudo apt-get install ntfsprogsand then type > sudo ntfsfix /dev/sdx,x - on the next attempted boot of the ntfs drive/partition, an attempt will be made to repair the filesystem so that it can boot. You could also try > sudo ntfsck /dev/sdx,xwhich will check the ntfs filesystem for errors. If none of these work, a manual mounting of the ntfs filesystem - if you don't know how to do this post again. Good luck.

---

### Post by danimaltron on 2008-10-24
On odd thing is that on NTFS config, "enable write support for internal device" is grayed out and not available. But "enable write support for external device" is available and checked.

This is not an internal device, but I wonder if that's an issue?]

I will try the other things you suggested. I no longer have a windows box. Just mac and Ubuntu right now.

---

### Post by danimaltron on 2008-10-24
> **bumanie said:**
> If this is the case restart in windows and shutdown properly via 'safely remove hardware'. Other options are to install ntfsprogs. and then type  - on the next attempted boot of the ntfs drive/partition, an attempt will be made to repair the filesystem so that it can boot.

I ran that first command after the install, and this is what I got:

```
Failed to determine whether /dev/sdx,x is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

```

---

### Post by Ducatiboy Stu on 2008-10-25
[COLOR="DarkOrange"]Failed to determine whether /dev/sdx,x is mounted: No such file or directory.[/COLOR]
[COLOR="Black"]You first need to determine the location of the drive...x,x refers to the positions..
ie it could be /dev/sda,2 or /dev/sdb,0[/COLOR]

Do a [COLOR="Blue"]*sudo -l* [/COLOR] to list all your storage devices, then work out which is you NTFS

---

### Post by bumanie on 2008-10-25
Sorry, I should have been more specific /dev/sdx,x refers to your hard drive/partition names for your computer, you need to substitute the x,x for the corresponding number(s) for your partitions. If are not sure post the output of > sudo fdisk -lu and someone will help you out.

---

### Post by Ducatiboy Stu on 2008-10-25
should look something like this...depending on your setup

> stuart@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd0cfd0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155    78156224    13478535    5  Extended
/dev/sda5        51199218    76919219    12860001   83  Linux
/dev/sda6        76919283    78156224      618471   82  Linux swap / Solaris


On my system, windows is on /dev/sda1 and ubuntu is on /dev/sda5..

My other external USB drive is locted at /dev/sdb[COLOR="Blue"]x[/COLOR], but as it is not connected it is not shown

---

