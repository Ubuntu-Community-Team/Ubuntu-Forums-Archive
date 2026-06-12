---
title: "Ubuntu HD Mounting Question"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by cyko on 2008-09-17
I'm sure this question has been asked thousands of times, but I'll ask once more.

I downloaded Ubuntu to recover/transfer data on Windows due to a "corrupt SP3 download" which pretty much rendered my C drive useless.  I was notified by a family member's co-worker that I can gain access to my C drive and transfer files into my F drive using Ubuntu.  Once I transfer the files I need, I'll wipe the C and install a fresh copy of Windows once again :roll:

now...

The only problem is, I am unable to mount either my C or F drive.  I've searched Google and none of the information provided really fit the description of my dilemma.

So far this is what I've done -

ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo sudo mount /dev/hdal /media/windows -t ntfs -o nls=utf8,usmask=0222
ntfs-3g: Failed to access volume 'dev/hdal':  No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
ubuntu@ubuntu:~$ /sbin/fdisk -l
ubuntu@ubuntu:~$ sudo mkdir /media/windows
mkdir: cannot create directory '/media/windows': File exists
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hdal /media/windows -o umask0000
ntfs-3g: Failed to access volume '/dev/hdal': No such file or directory

I have not a clue what I'm doing but its probably pretty simple :p

Now for the cheese:
How do I mount both my C and F drives so I can access them both to complete a data transfer?

---

### Post by Shazaam on 2008-09-17
Replace the h in hda with s and try again. (sda1)

---

### Post by Zzl1xndd on 2008-09-17
Not sure if you tried the easy way but normally you can go to places > computer and it will list your drives and all you should have to do is double click on them.

---

### Post by cyko on 2008-09-17
> **tweakedenigma said:**
> Not sure if you tried the easy way but normally you can go to places > computer and it will list your drives and all you should have to do is double click on them.

Tried that already, same mounting error...

Upon changing hdal to sda1 I received an array of text from Terminal...the most pertinent being the latter.

Mount is denied because NTFS is marked to be in use.  Choose one action:

Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line:

mount -t ntfs-3g /dev/sda1 /media/windows/ -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdal /media/windows/ ntfs-3g force 0 0


I don't know what either commands will due.  So far, my C drive is useless in Windows but contains much valuable needed information.  F drive is just massive storage, but at the same time very valuable.

---

### Post by Shazaam on 2008-09-17
Ok lets start over. Shutdown the pc. Unplug ALL external devices except your keyboard, mouse and monitor. If your keyboard or pc has a built in card reader eject ALL cards that are in the slot(s) Boot the Ubuntu livecd, open terminal and try to mount the Windows drive again (sda1?) using your original commands (mkdir, mount, etc).

---

### Post by cyko on 2008-09-17
I receive the same codes...

---

### Post by Shazaam on 2008-09-17
Ok. Try this...
```
sudo umount /dev/sda1
```
tries to unmount the partition, will probably result in more error messages.
As an aside, can you get to Windows Safe Mode by clicking the F8 key while trying to boot Windows?

---

### Post by hellion0 on 2008-09-17
One thing I notice is that when Windows fails to shut down clean, you can't mount its NTFS drives in Linux.

It could be that SP3 screwing up caused an "unclean" shutdown.

---

### Post by cyko on 2008-09-17
> **Shazaam said:**
> Ok. Try this...
```
sudo umount /dev/sda1
```
tries to unmount the partition, will probably result in more error messages.
As an aside, can you get to Windows Safe Mode by clicking the F8 key while trying to boot Windows?

I receive this message now,
ubuntu@ubuntu:~$ sudo unmount /dev/sda1
sudo: unmount: command not found

If I could, I would...this is my last option before totally wiping my C drive.  I've tried every possible option from starting Windows Normally, Last Known Good Configuration, Safe Mode and everything in between.  Once I select one of those options, it cycles through and reboots over and over again. I've tried to repair Windows and get the same issue.

My problem is this, [http://www.tomshardware.com/news/Windows-XP-SP3,5334.html](http://www.tomshardware.com/news/Windows-XP-SP3,5334.html)

---

### Post by Shazaam on 2008-09-17
It is
```
umount
```
not unmount. Try again.

---

### Post by cyko on 2008-09-17
It came up blank, nothing seemed to change. :confused:

---

### Post by Shazaam on 2008-09-17
Cool. If, after you passed the sudo umount /dev/sda1 code and it went back to the $ prompt that means it unmounted sda1. Now try this as an experiment...
```
sudo mount /dev/sda1 /mnt
```
This SHOULD (*crosses fingers*) mount sda1 into the /mnt directory.

---

### Post by cyko on 2008-09-17
Ok, my F drive (storage) seems to have showed up and I can access those files.  Now, my major issue is, the C drive is still inaccessible.

---

### Post by Shazaam on 2008-09-17
Lets see what fdisk lists. Run this...
```
sudo fdisk -lu
```
(that's a lowercase -LU)

---

### Post by cyko on 2008-09-17
Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa472a472

Device Boot/   Start/       End/     Blocks/   Id/   System
/dev/sdal */     63/ 234372284/  117186111/    7/ HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8bcc8bc

Device Boot/   Start/         End/     Blocks/   Id/   System
                 63/   156280319/   78140128+/   7/   HPFS/NTFS

---

### Post by Shazaam on 2008-09-18
No device name on the 80gig drive. I take it this is your C drive. As for fixing the /dev name on the 80gig without destroying the data on it I haven't a clue.
Here is something that some people rave about. It has the program ntfsprogs that we need to proceed....
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Shazaam on 2008-09-18
Try this...
```
sudo mkdir /media/disk
```
```
sudo mount /dev/sdb1 /media/disk
```

---

