---
title: "i cant mount my external harddrive wtf?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-06-30
im getting this error message...

i just repartitioned to ext3  since i no longer needed a windows partition. im running 8.04 on a compaq dv6000

---

### Post by iaculallad on 2008-06-30
Try to post your /etc/fstab file.

```
cat /etc/fstab
```

---

### Post by PatrickMoore on 2008-06-30
> **iaculallad said:**
> Try to post your /etc/fstab file.

```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0073e8ca-e864-4c8b-bc81-3a701ebc97d7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=ddbc44b8-a749-419c-9b6a-60501e1488a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by iaculallad on 2008-06-30
Ok. What about mounting partitions manually? What error does it display?

```
sudo mount -a
```

---

### Post by sayakb on 2008-06-30
Assuming the external HDD is /dev/sdb1 (check that by typing **sudo fdisk -l** in a terminal)
 Try:
```
sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk -o force
```

---

### Post by PatrickMoore on 2008-06-30
```
patrick@patrick-laptop:~$ sudo mount -a
patrick@patrick-laptop:~$ sudo mount /dev/sda3
mount: /dev/sda3 already mounted or / busy
mount: according to mtab, /dev/sda3 is already mounted on /

```

if i do sudo mount -a mothing happened then the other gave me that message

---

### Post by PatrickMoore on 2008-06-30
```
wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by iaculallad on 2008-06-30
:confused::confused: Could you post whatever displays when you issue the command on your terminal:

```
sudo blkid
```

---

### Post by PatrickMoore on 2008-06-30
[/CODE]/dev/sda3: UUID="0073e8ca-e864-4c8b-bc81-3a701ebc97d7" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="ddbc44b8-a749-419c-9b6a-60501e1488a9" 
/dev/sdb1: UUID="85fa3d3f-7fea-44fc-8aaf-9f74aa8ce0f4" TYPE="ext2" [/CODE]

---

### Post by Tomatz on 2008-06-30
Can you run an fsck on the drive to see if that fixes the issue???

---

### Post by smo0th on 2008-06-30
> **PatrickMoore said:**
> ```
wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

hi, have you tried to
```
sudo e2fsck -C0 -p -v -f /dev/sdb1
```

this will check your filesystem integrity in partition /dev/sdb1(assumming this is the partition you are interested in)

```
sudo blkid
```

will check your partition types

---

### Post by PatrickMoore on 2008-06-30
> **tomatz said:**
> can You Run An Fsck On The Drive To See If That Fixes The Issue???
 
How Do I Do That?

---

### Post by smo0th on 2008-06-30
> **PatrickMoore said:**
> How Do I Do That?

with ```
sudo e2fsck -C0 -p -v -f /dev/sdb1
``` :lolflag:

---

### Post by PatrickMoore on 2008-06-30
> **smo0th said:**
> with ```
sudo e2fsck -C0 -p -v -f /dev/sdb1
``` :lolflag:

```
 sudo e2fsck -C0 -p -v -f /dev/sdb1
[sudo] password for patrick: 
                                                                               
      11 inodes used (0.00%)
       1 non-contiguous inode (9.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
  496035 blocks used (0.81%)
       0 bad blocks
       1 large file

       0 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       2 files

```

still wont mount

---

### Post by smo0th on 2008-06-30
hey patrick, 

good news it reported no errors, that's good, just wondering if the partition is not mounted because whenever you do a fsck to a partition it should be unmounted, it says wrong fs type, we should take a look at the partition types you have with ```
sudo blkid
``` and also ```
dmesg | tail
``` to check system error messages to get more from the picture

---

### Post by Tomatz on 2008-06-30
As it's just been partitioned and formatted it wouldn't hurt to format the partition again.


In a terminal type:

```
sudo apt-get install gparted
```

Then open gparted *(System, Administration, Gnome Partition Editor)* and reformat the partition.

;)

---

### Post by PatrickMoore on 2008-07-04
> **smo0th said:**
> hey patrick, 

good news it reported no errors, that's good, just wondering if the partition is not mounted because whenever you do a fsck to a partition it should be unmounted, it says wrong fs type, we should take a look at the partition types you have with ```
sudo blkid
``` and also ```
dmesg | tail
``` to check system error messages to get more from the picture

when i run sudo blkid i get
```
/dev/sda3: UUID="0073e8ca-e864-4c8b-bc81-3a701ebc97d7" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="ddbc44b8-a749-419c-9b6a-60501e1488a9" 
/dev/sdb1: UUID="aa6bc002-6264-4d44-b8b7-f1d9bb0f29db" TYPE="ext2" 

```

and dmesg | tail i get

```
[ 4100.200860] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4100.200872] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 4100.200873]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4100.200875]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 4100.200877] ata1.00: status: { DRDY }
[ 4102.468341] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 4105.406374] ata1: device not ready (errno=-16), forcing hardreset
[ 4105.406381] ata1: soft resetting link
[ 4105.898531] ata1.00: configured for MWDMA1
[ 4105.898544] ata1: EH complete

```

im lost

---

### Post by PatrickMoore on 2008-07-04
i really need to solve this. anyone have any  ideas?

---

### Post by PatrickMoore on 2008-07-05
bump

---

### Post by Tomatz on 2008-07-05
Try reformatting it with gparted like i said above ;)

---

### Post by PatrickMoore on 2008-07-05
> **Tomatz said:**
> Try reformatting it with gparted like i said above ;)

i did thats where im at right now after the formatting

---

### Post by Tomatz on 2008-07-05
So what is happning now?

---

### Post by bumanie on 2008-07-05
What files do you have on the drive? It seems clear from the parts i understand that ubuntu is not recognizing the file system, for whatever reason. I would copy any files off the drive and reformat it, or run fsck on it and see if that will fix the errors within the filesystem. Fsck needs to be done with the drive unmounted.

---

### Post by Tomatz on 2008-07-05
BTW is it a Hitachi drrive as there is a problem with some Hitachi drives under linux?

---

### Post by PatrickMoore on 2008-07-05
> **Tomatz said:**
> BTW is it a Hitachi drrive as there is a problem with some Hitachi drives under linux?

no western digital...

the drive is empty

if i run fsck i get 

```
patrick@patrick-laptop:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=0073e8ca-e864-4c8b-bc81-3a701ebc97d7'

```

---

### Post by bumanie on 2008-07-05
> **Tomatz said:**
> BTW is it a Hitachi drrive as there is a problem with some Hitachi drives under linux?

Good point. Hitachi are not the only drives that have issues with open source. A few of the proprietary produced external drives are not well supported and some of the drive manufacturers, say they have no intention of supporting linux.

---

### Post by Tomatz on 2008-07-05
In a terminal type:

```
sudo vol_id /dev/sda3
```

Post the output ;)

---

### Post by PatrickMoore on 2008-07-05
it was working when i had my windows partition on the drive but then i made the mistake of removing that partition  since it was irrelevant  since ive deleted all windows and ive had permissions and mounting issues since...

what originally happened was that when o adjusted the size of my partition i encountered an error. so i reformated the whole drive since i didnt have much i just moved it to my hard drive on my laptop.

---

### Post by Tomatz on 2008-07-05
> **bumanie said:**
> Good point. Hitachi are not the only drives that have issues with open source. A few of the proprietary produced external drives are not well supported and some of the drive manufacturers, say they have no intention of supporting linux.

I really can't see the point in it? Interoperability can only benefit manufacturers.

:confused:

---

### Post by PatrickMoore on 2008-07-05
```
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=0073e8ca-e864-4c8b-bc81-3a701ebc97d7
ID_FS_UUID_ENC=0073e8ca-e864-4c8b-bc81-3a701ebc97d7
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

---

### Post by Tomatz on 2008-07-05
> **PatrickMoore said:**
> ```
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=0073e8ca-e864-4c8b-bc81-3a701ebc97d7
ID_FS_UUID_ENC=0073e8ca-e864-4c8b-bc81-3a701ebc97d7
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

Well the volume UUID matches with that in fstab.

Another dead end :(

Try formatting the drive to ext2 to see if that has any effect.

---

### Post by PatrickMoore on 2008-07-05
> **Tomatz said:**
> Well the volume UUID matches with that in fstab.

Another dead end :(

Try formatting the drive to ext2 to see if that has any effect.


ill do that. and post the reponses later its late i need rest thank you guys

---

### Post by Tomatz on 2008-07-05
> **PatrickMoore said:**
> ill do that. and post the reponses later its late i need rest thank you guys

Cool :)

I'll have a google to see if i can find anyone else with the same problem.

---

### Post by bumanie on 2008-07-05
> **Tomatz said:**
> I really can't see the point in it? Interoperability can only benefit manufacturers.

:confused:

I have seen quotes by ubuntu users who have had issues and contacted the drive manufacturer and the answer quote from the manufacturer is "We don't support linux". However, I must say, most drives work, but not all. I have not heard of a WD that doesn't work with linux. Personally I re-use desktop or laptop hard drives in an external case after having them work with ubuntu in a computer -they always work. As your drive has nothing on it, other than a not too healthy filesystem - reformat it to see if that fixes it.

---

### Post by PatrickMoore on 2008-07-05
i reformatted to ext2 with an msdos disklabel same issue...


i enclosed the error message with details if that helps

---

### Post by Tomatz on 2008-07-05
The drive may be corrupted. A low level format may fix the issue.

See if you can find the low level format utility for your drive here:

[http://support.wdc.com/product/download.asp?lang=en](http://support.wdc.com/product/download.asp?lang=en)

It will probably be called diagnostic tools or something along those lines.

Hope that helps :)

---

### Post by PatrickMoore on 2008-07-05
> **Tomatz said:**
> The drive may be corrupted. A low level format may fix the issue.

See if you can find the low level format utility for your drive here:

[http://support.wdc.com/product/download.asp?lang=en](http://support.wdc.com/product/download.asp?lang=en)

It will probably be called diagnostic tools or something along those lines.

Hope that helps :)

i dont see anything that would be of use.
should i check synaptec?

---

### Post by PatrickMoore on 2008-07-05
any other ideas i cant find a low level formator

---

### Post by nkri on 2008-07-05
I think it's a lot simpler than what everyone has posted so far.  The error is saying that there is a "/" in the name of the mount point.  All you have to do is rename the mount point (probably in /mnt or /media) or replace the "/" with "_" or "-"

I think it's that easy, but not quite sure.

Good luck!
-nkri

---

### Post by Tomatz on 2008-07-05
> **nkri said:**
> I think it's a lot simpler than what everyone has posted so far.  The error is saying that there is a "/" in the name of the mount point.  All you have to do is rename the mount point (probably in /mnt or /media) or replace the "/" with "_" or "-"

I think it's that easy, but not quite sure.

Good luck!
-nkri

Thats a generic error. Basically mount cant find anything mountable on the fs/partition :(

A low level format will be the only way to fix the issue IMO. Can you give your drive model/model number?

---

### Post by PatrickMoore on 2008-07-05
> **Tomatz said:**
> Thats a generic error. Basically mount cant find anything mountable on the fs :(

A low level format will be the only way to fix the issue IMO. Can you give your drive model/model number?

of course its. a western digital wd2500I032-001
250 gig hard drive

---

### Post by PatrickMoore on 2008-07-05
ok so i can manually mount my harddrive by doing

```
pmount /dev/sdc1 
```

i just noticed that my harddrive (the one that is actually in my computer)
is coming up twice 
once under dev/sda3
again under gvfs-fuse-daemon

i took a screenshot of the windowand attached it

---

### Post by PatrickMoore on 2008-07-05
i got an interesting new error message...

```
patrick@patrick-laptop:~$ sudo mount -t ext2 /dev/sdb1 /media/sdb1 -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` i think the disk is indeed damaged. formatter anyone?

---

### Post by moore.bryan on 2008-07-05
for what are you using this external drive? if it's simply for data, fat32 might be the best choice. i have a western digital that died under ext3, but works fine under fat32; however, that's a side-note.

how does ```
pmount /dev/sdb1 /media/disk
``` work, assuming /dev/sdb1 is indeed your external hd and /media/disk exists?

---

### Post by PatrickMoore on 2008-07-05
> **moore.bryan said:**
> for what are you using this external drive? if it's simply for data, fat32 might be the best choice. i have a western digital that died under ext3, but works fine under fat32; however, that's a side-note.

how does ```
pmount /dev/sdb1 /media/disk
``` work, assuming /dev/sdb1 is indeed your external hd and /media/disk exists?

yeah it munts but i cant write to it.

right now im using 

 sudo mount -t ext2 /dev/sdb1 /media/sdb1

and im getting into the drive but i dont have permission to save anything

---

### Post by moore.bryan on 2008-07-05
just "pmount"--i.e., without "sudo" in-front of it--should mount it as yours and no one else's. hmm.
first, unmount the drive, then try this:
```
sudo chmod -R 777 /media/disk
pmount /dev/sdb1 /media/disk
```

---

### Post by PatrickMoore on 2008-07-05
> **moore.bryan said:**
> just "pmount"--i.e., without "sudo" in-front of it--should mount it as yours and no one else's. hmm.
first, unmount the drive, then try this:
```
sudo chmod -R 777 /media/disk
pmount /dev/sdb1 /media/disk
```

still dont have permission. i have to use

sudo umount -t ext2 /dev/sdb1 /media/sdb1

to unmount

---

### Post by moore.bryan on 2008-07-05
that's okay; you had to do that because you mounted it via mount and not pmount.

did you chmod /media/disk?

if so, try this ```
sudo mount -t ext2 -o rw /dev/sdb1 /media/disk
```

---

### Post by PatrickMoore on 2008-07-05
> **moore.bryan said:**
> that's okay; you had to do that because you mounted it via mount and not pmount.

did you chmod /media/disk?

if so, try this ```
sudo mount -t ext2 -o rw /dev/sdb1 /media/disk
```

i can mount and unmount via terminal but it will not mount if i plug in the drive and also the conky info is completely wrong it shows 716 mb when its a 250 gig drive

---

### Post by PatrickMoore on 2008-07-05
on the bright side i have the ability to write to it now its just getting it to auto mount

---

### Post by Tomatz on 2008-07-06
You could write a script to mount your drive:


In a terminal type:

```
sudo touch /usr/bin/mount-me
```

```
sudo gedit /usr/bin/mount-me
```

**Add to the file:**

```
gksu mount -t ext2 /dev/sdb1 /media/sdb1
```

**Save** the file


Now in a terminal type:

```
chmod a+x /usr/bin/mount-me
```

**Done**

Now all you have to do is create a gnome panel launcher with the command **mount-me** Then just click on it to mount your drive.

Not ideal but it will work ;)



P.s 

I couldnt find a low level format utility for this drive but i did find a tool that restores the drive back to near factory defaults:

[http://support.wdc.com/product/download.asp?groupid=101&sid=34&lang=en](http://support.wdc.com/product/download.asp?groupid=101&sid=34&lang=en)

---

### Post by moore.bryan on 2008-07-06
^ good advice.

i found with hardy all my "large" external hd's (250gb and 500gb) won't automount; i have to do them by hand. perhaps THAT'S the issue. however, conky reporting the file size screwed-up is an interesting wrinkle. have you tried formatting the drive fat32 to see if SOME of the issues go away? like i wrote, that might not make it automount, but in the long run it could save you some headaches.

---

