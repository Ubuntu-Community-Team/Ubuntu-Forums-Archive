---
title: "Can't write to new hd [cant change permissions]"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by jimsonweed on 2008-10-13
Ive checked through the already posted threads on this topic and Ive followed 
instructions posted on the threads. 

> 
sudo chown -R <name> /media/mynewdrive
sudo chmod -R 755 /media/mynewdrive 

and It says. 
> 
chown: changing ownership of `/media/mynewdrive': Read-only file system

I don't want to leave it read-only. 
Here is whats in my fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0a0faa6e-64e6-4fa1-9ef9-661f6045dd65 /               ext3    defaults,errors=remo$
# /dev/sda6
UUID=e2e8f9cf-6df8-4fa5-9028-f61c08397a3b none            swap    sw              0   $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb    /media/mynewdrive   ext3    defaults     0        2
.

I started messing around with it in Gparted and I think I messed it up. :(

Just a little confused. 


--jimsonweed--

---

### Post by alwayshere on 2008-10-13
try using windows 98se boot disk or g part or just install and ubuntu on to it i should go to a formating before in installs even if you had to install the ubuntu os theres a fresh start

---

### Post by gizmoZA on 2008-10-13
Was your drive formatted as NTFS Partition? Use fdisk to format the HDD using ext3 file system. Should then be able mount the drive as writable.

---

### Post by jimsonweed on 2008-10-13
:( Im sorry but I can't make out what you said.@alwayshere

---

### Post by alwayshere on 2008-10-13
try using ubuntu live install disk then you will be able to unmount hd may be you are trying to unmount a hd you are mounted on ? just some ideas here im not to sure what it is you are working with and towards ?

---

### Post by jimsonweed on 2008-10-13
@gizmo in the fstab file its listed as ext3 :confused:

---

### Post by alwayshere on 2008-10-13
is the hd the only hd and holding the os you wish to use or is it a slave drive ??

---

### Post by jimsonweed on 2008-10-13
> **alwayshere said:**
> try using ubuntu live install disk then you will be able to unmount hd may be you are trying to unmount a hd you are mounted on ? just some ideas here im not to sure what it is you are working with and towards ?

Im running out of space on hd1. I'm running ubuntu on an old pc, I have two hds. One is  16 partitioned to 8.0 gigs and hd2 is 10gigs. I installed it and everything, had it mounted and all but at the time could only see a lost+found folder and couldnt do anything with it. After I started fooling around with it I don't even see that folder.. .I just want to be able to save on hd2.

---

### Post by forger on 2008-10-13
I suppose this is the **/dev/sdb** device we're talking about?

Can you post the output of:
```
sudo fdisk -l
sudo mount
```

also, try this:
1) remove the line of that device in fstab
2) do this
```

sudo umount /dev/sdb
sudo mkdir /media/sdb
sudo mount -t ext3 /dev/sdb /media/sdb
sudo chown -R $USER:$USER /media/sdb
sudo chmod -R 755 /media/sdb

```
Does it show any errors?

---

### Post by alwayshere on 2008-10-13
i would try installing ubuntu   onto the 2 hd then try deleting it using a gparted live disk or win 98se boot disk   be sure to unplug your main one as not to mess that up while you do this 

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

above link to 98se boot disk install to make a flopy boot disk  best you make this disk and launch the dloaded floppy maker on a win pc to play it safe   once you made a floppy and booted it wait for it to do ts thing then type fdisk and you will figure it from there

---

### Post by alwayshere on 2008-10-13
i have formatted hd heaps of times only once i have had a sneeky one that would'nt format easy it ended up taking me 10 hrs of trying allsorts and in the end i did it but still not sure what i did that did it lol 

good luck

---

### Post by alwayshere on 2008-10-13
here is link to gparted live cd  
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by jimsonweed on 2008-10-13
> 
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9800481f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1112     8932108+   7  HPFS/NTFS
/dev/sda2            2121        2433     2514172+   f  W95 Ext'd (LBA)
/dev/sda3            1113        2120     8096760   83  Linux
/dev/sda5            2173        2433     2096451    7  HPFS/NTFS
/dev/sda6            2121        2172      417627   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00025010

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         784     6297448+   5  Extended


When I get to *sudo mount -t ext3 /dev/sdb /media/sdb*, it gives me this:
> 
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

sorry for the slow response.

---

### Post by Orange_and_Green on 2008-10-13
I think you might be getting confused between "ext3 file system" and "Extended partition". Sdb1 is an extended partition with no logical drives on it (from what I can see from your output, unless you trimmed something).

Try using gparted to remove /dev/sdb1, then create a "Primary partition" and format it with "ext3 file system".

Good luck :KS

NOTE: You said the drive is new, so there is no data on it right? 'Cause if there is some data you want to recover on it, before proceeding we would need to back it up first so if there is any data on it, don't do anything and post again.

---

### Post by jimsonweed on 2008-10-13
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0a0faa6e-64e6-4fa1-9ef9-661f6045dd65 /               ext3    defaults,erro$
# /dev/sda6
UUID=e2e8f9cf-6df8-4fa5-9028-f61c08397a3b none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb    /dev/sdb   ext3    defaults     0        2

.
its all repartiotioned and all, but im still confused

---

### Post by forger on 2008-10-13
yep, Orange_and_Green's suggestion :)
extended is *not* ext3!

You can go to the extended partition in gparted (System > Administration > Partition editor), right click on it and select Format to > Ext3
**[COLOR="Red"]WARNING![/COLOR]** This will actually format that partition/drive, backup any important data you might want to save!

---

### Post by Orange_and_Green on 2008-10-13
> **jimsonweed said:**
> /dev/sdb /dev/sdb ext3 defaults 0 2 

Does changing this line in fstab to 

```
/dev/sdb1 /media/sdb ext3 defaults 0 2
```
change something?

(to see the effects, you will have to either reboot, or
```
sudo umount /media/sdb
mount -a
```)

Good luck :KS

---

### Post by Elfy on 2008-10-13
Is sdb1 showing as linux in sudo fdisk -l now? Not like

/dev/sdb1 1 784 6297448+ 5 Extended 

if it still says that it's not formatted and you will not be able to mount it.

---

### Post by forger on 2008-10-13
As I said, **remove that line** from /etc/fstab - do:
```
gksu gedit /etc/fstab
```

remove the line "/dev/sdb /dev/sdb ext3 defaults 0 2"
Press save and exit

Also, paste again the output of ```
sudo fdisk -l
```

---

### Post by forger on 2008-10-13
One last thing:
When you do the above, make sure you mount your **partition** and not your device.
I mean the partition should be with a number, e.g. /dev/sdb1

You should be able to see which partition it is in the output of sudo fdisk -l

So you do the following:
```
sudo mount -t ext3 /dev/sdb1 /media/sdb
```

---

