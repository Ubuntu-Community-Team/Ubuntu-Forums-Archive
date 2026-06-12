---
title: "[SOLVED] Hard Drive issues"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by chunkychap on 2008-09-25
I've been trying for sometime to move away from windows for various reasons.... I'm now trying ubuntu as a media machine.

I am really new to this but trying to pick things up and could do with some advice. I've been searching but dont seem to have come accross the same problems. 

I have ubuntu Hardy Heron. I have installed a main drive with the OS on it and have 4 extra drives.... all previously used for windows NTFS....

I have been trying to format the drives to EXT3 using gparted. But now when I start the system and access the drives I get 'Unable to mount partition'.... on all drives. It looks like either the permissions or something else are wrong. 

Like I say I have been playing with it now for 3 days on and off and I'm stuck, so any help would be appreciated! Thanks

---

### Post by Elfy on 2008-09-25
Can you post the outputs of these commands please
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by chunkychap on 2008-09-25
Ok 


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1e94908

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 185.2 GB, 185283624960 bytes
255 heads, 63 sectors/track, 22526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3676aa49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22526   180940063+  83  Linux

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e581e57

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       48642   390715841    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa38cd752

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       35227   282960846    7  HPFS/NTFS
/dev/sdd2           35228       60801   205423155    f  W95 Ext'd (LBA)
/dev/sdd5           35228       60801   205423123+  83  Linux


and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=350a7a00-370d-454a-bb24-298be7fda399 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=74cfba0b-ae34-4225-903b-e0989c0ba0d4 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


#Added by diskmounter utility
/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdc1 /media/sdc1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdd1 /media/sdd1 ntfs ro,user,fmask=0111,dmask=0000 0 0


....as you can see I've tried to use diskmounter to mount the drives on boot up also..... but I really have no clue!

Thanks

---

### Post by Elfy on 2008-09-25
Did you make the folders?

Run ```
ls /media
ls /mnt
```

---

### Post by chunkychap on 2008-09-25
Not intentionally....which ones?

cdrom  cdrom0  cdrom1  disk  floppy  floppy0  sdb1  sdc1  sdd1

windrive


Thanks

---

### Post by Elfy on 2008-09-25
Lets try to change on eof the lines and comment out the others for a moment. Open the file to edit ```
gksudo gedit /etc/fstab
```

Change the first 2 sets so they don't ry and mount
> #Added by diskmounter utility
[COLOR="Red"]#[/COLOR]/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
[COLOR="Red"]#[/COLOR]/dev/sdc1 /media/sdc1 ntfs ro,user,fmask=0111,dmask=0000 0 0

Change the final line to read, best to cut and paste

```
/dev/sdd1 /media/sdd1 ntfs-3g auto,rw,utf8   0       0
```
Now try and mount it ```
sudo mount -a
```

---

### Post by chunkychap on 2008-09-25
Ok... Looks like we're getting somewhere. 

This now mounts a drive at startup which is one of the old windows drives and gives me RW access.... although still read only on the EXT3 partition.

What about the Drives I've formatted to EXT3.... do I need to mount them in the same way?

I presume it would be different because of the NTFS bit?

Thanks

---

### Post by Elfy on 2008-09-25
give me the output of ```
df -h
``` so I can see what's going on - should be close then I think :)

---

### Post by chunkychap on 2008-09-25
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  3.2G   31G  10% /
varrun                760M  232K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M  124K  760M   1% /dev
devshm                760M   12K  760M   1% /dev/shm
lrm                   760M   39M  721M   6% /lib/modules/2.6.24-19-generic/volatile
/dev/sdd1             270G  161G  110G  60% /media/sdd1
gvfs-fuse-daemon       36G  3.2G   31G  10% /home/ianandjane/.gvfs
/dev/sdb1             172G  188M  163G   1% /media/disk
/dev/sdd5             195G  188M  185G   1% /media/disk-1

---

### Post by chunkychap on 2008-09-25
There is also a folder called "lost+found" on both of the drives is that helps.

Thanks

---

### Post by Elfy on 2008-09-25
Ok so that has mounted ok - if you want to rewrite fstab 

use the ```
/dev/sdd1 /media/sdd1 ntfs-3g auto,rw,utf8   0       0
``` as a template for your ntfs drives

use ```
/dev/sxy /media/mountfolder ext3 user 0 2
``` as a template for the ext3 drives.

Your fstab is a bit mixed up and the sdb1 you tried to get diskmounter to deal with is mounting as /media/disk

If you want we can rewrite the whole thing - if you want that which drives on sdb, sdc, sdd do you want to mount at startup?

---

### Post by chunkychap on 2008-09-25
Thanks... makes more sense now.

I want all of the drives to mount on startup.... Eventually I'll format them all from NTFS but I need to move some data from them first.

If you could help me tidy the file so that it does this I would appreciate it!

Thanks

---

### Post by Elfy on 2008-09-25
I think that there is only one drive not mounting with fstab now anyway if you've got the others on ok

```
sudo mkdir /media/sdd5
```

Add this to fstab

```
/dev/sdd5 /media/sdd5 ext3 user 0 2
```

Make sure it is unmounted and then remount - stop if there's an error

```
sudo umount /media/disk
sudo umount /media/disk-1
sudo mount -a
df -h
```

Post the result of df -h if all ok please

---

### Post by chunkychap on 2008-09-25
Ok

Here are the results

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  3.2G   31G  10% /
varrun                760M  236K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M  124K  760M   1% /dev
devshm                760M   12K  760M   1% /dev/shm
lrm                   760M   39M  721M   6% /lib/modules/2.6.24-19-generic/volatile
/dev/sdd1             270G  161G  110G  60% /media/sdd1
gvfs-fuse-daemon       36G  3.2G   31G  10% /home/ianandjane/.gvfs
/dev/sdd5             195G  188M  185G   1% /media/sdd5

---

### Post by chunkychap on 2008-09-25
It seems to mount the hard drives ok.... but only the NTFS drives have read write access.... the ext3 drives mount ok but I can't write to them. Thanks

---

### Post by Elfy on 2008-09-25
Sorry I thought you had done the other 2 :(

Still have to add sdb1 and sdc1 to fstab

```
/dev/sdb1 /media/sdb1 ext3 user 0 2
/dev/sdc1 /media/sdc1 ntfs-3g auto,rw,utf8   0       0
```

Then ```
sudo mount -a
``` once more and you should then see thes in df -h

/dev/sda1
/dev/sdb1
/dev/sdc1
/dev/sdd1
/dev/sdd5

---

### Post by Elfy on 2008-09-25
Get them all mounting and when that is done come back and we can sort the permissions for the ext3s

Edit - I'll add it here - assuming that all of your drives are now mounted run these commands - chnage user for your username.

```
sudo chown user.user /media/sdb1
sudo chown user.user /media/sdd5
sudo chmod 770 /media/sdb1
sudo chmod 770 /media/sdd5
```

SHould now all be mounted and writable

This link goes through the whole thing from beginning to end for an ext3 [http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

---

### Post by egalvan on 2008-09-25
> **forestpixie said:**
> 
use the ```
/dev/sdd1 /media/sdd1 ntfs-3g auto,rw,utf8   0       0
``` as a template for your ntfs drives

use ```
/dev/sxy /media/mountfolder ext3 user 0 2
``` as a template for the ext3 drives.

Your fstab is a bit mixed up and the sdb1 you tried to get diskmounter to deal with is mounting as /media/disk
...

Is there an advantage one way or the other to using

/media/mountpoint

versus

/mnt/mountpoint


I understand that  media will place icons on the desktop, and mnt will not.
Is this correct?

Any other views?
 Is one or the other preferable for internal versus external drives.?


Thanks

---

### Post by Elfy on 2008-09-25
> Is this correct?Yes - I only found that out recently myself. I believe that /media was for cdroms etc and I guess usb drives/sticks. But when I started here they were mounting internals on /media and I followed.

I think that if you didn't want to see your drives on the desktop but did wnat to see cds etc then you would have to mount the drives in /mnt

---

### Post by chunkychap on 2008-09-25
Ok thanks for all your help.

Seems to be working ok...ish. Have had some problems restarting the machine (crashed on startup) and only one of the EXT 3 drives will let me mount.

I'll have a play with it and let you know how I get on.

Thanks

---

### Post by egalvan on 2008-09-25
> **chunkychap said:**
> Ok thanks for all your help.

Seems to be working ok...ish. Have had some problems restarting the machine (crashed on startup) and only one of the EXT 3 drives will let me mount.

**I'll have a play with it and let you know how I get on.**

Thanks

Please,  don't forget to keep us informed.

Thanks!

ErnestG

---

### Post by chunkychap on 2008-09-26
Ok,

New day new restart.... all seems to be working ok.

All drives now mount on startup fine and I can access them from my user. 

Trying now to share the drives with my windows machine so that I can start to move over Photos, music etc. I have managed to get it so that the windows machine can view and create files/folders but I can't access them using Ubuntu after that and visa-versa.....

Is there a command that will fully share the drives with network machines.... even those with different OS's.... I'm trying to make this work on the EXT3 formatted partitions.

A link to the right thread would be really helpful!

Thanks again

---

### Post by Elfy on 2008-09-26
Ok - that is all good then.

I have no experience with networking linux and windows, but I believe it to be samba that you need to look at. Ubuntu will be the client if you are sharing from windows.

There are more than a few threads kicking about, I've found 2 community pages which should be fo some help

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

There is also this page, but someone has said that it's out of date - so be careful with it

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

I wouldn't normally do so, but you might find that you can search for suitable threads better yourself, rather though than use the forum search I use [http://www.uboontu.com/](http://www.uboontu.com/) or [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

If you don't find what it is you are looking for then there is a specific network forum [here]("http://ubuntuforums.org/forumdisplay.php?f=336") to look in.

If you do need help then I think that your best bet would be to start a new thread in here, a thread in the network forum _might_ take a while to be answered, although I've never used it myself - anyone looking here would assume it to be a hard drive issue :)

One final piece of advice - if you find that a thread isn't being answered, resist the urge to bump it - I for one look for threads with 0 replies and there is a team specifically looking at 0 reply threads - one bump and it could be lost :)

Good luck

---

