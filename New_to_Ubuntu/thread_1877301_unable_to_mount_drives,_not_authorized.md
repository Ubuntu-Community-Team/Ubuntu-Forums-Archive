---
title: "unable to mount drives, not authorized"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by seagreen on 2011-11-07
first post here, lurked a bunch, enjoying ubuntu, but needed to register and ask this question. 
i imagine the answer is fairly simple, but not sure. 

built my computer a few months ago, installed newest ubuntu, upgraded to ocelot, all went fine. 

two nights ago, didn't shut computer down before falling asleep, power blipped, so i imagine the computer had a hard shutdown. 

after this, my internal hd, cd-drive, and any other data stuff won't automount. the computer recognizes that they exist (visible in disk utility) but says "unable to mount [name]: not authorized". 

in looking at fstab, theres a error remount: ro thing i don't recognize, something i read said that that's part of a file protection system in case of corruption or similar?

any ideas how to return my drives to normal?

thanks!

---

### Post by dileepm on 2011-11-08
Did you try /etc/hal to automount?

---

### Post by pavi_elex on 2011-11-08
Did you check using g-parted? Are the drives shown there? if yes try to mount there.
or check 
$ sudo fdisk -l
is it showing list of partitions?
if yes try manually
sudo mount -t vfat /dev/sda5 /media
(type your sda which is shown in list fdisk -l)

---

### Post by seagreen on 2011-11-08
thanks for your help so far. 

> **dileepm said:**
> Did you try /etc/hal to automount?

not sure what you mean. please elaborate? all devices were automounting fine until a few nights ago. 

> **pavi_elex said:**
> Did you check using g-parted? Are the drives shown there? if yes try to mount there.
or check 
$ sudo fdisk -l
is it showing list of partitions?
if yes try manually
sudo mount -t vfat /dev/sda5 /media
(type your sda which is shown in list fdisk -l)

results of fdisk -l
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8023

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   100501503    50249728   83  Linux
/dev/sda2       100503550   117229567     8363009    5  Extended
/dev/sda5       100503552   117229567     8363008   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      409639      204819+  ee  GPT
/dev/sdc2          409640  1172284639   585937500   af  HFS / HFS+
/dev/sdc3      1172547584  1952149503   389800960    b  W95 FAT32

Disk /dev/mapper/cryptswap1: 8563 MB, 8563720192 bytes
255 heads, 63 sectors/track, 1041 cylinders, total 16726016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x646b5edb

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


```i'm not sure how to fully interpret the above. i see three drives (60G, and 2 at 1T). how do i modify ```
sudo mount -t vfat /dev/sda5 /media
``` to fit my drives? i imagine something like
```
sudo mount -t vfat /dev//sdb/name
sudo mount -t vfat /dev/sdc/name2

```my 60G ssd boot drive is perfect, the computer runs well, i'm on it right now. 

i can't access or mount: 
1) my external drive (1Tb partitioned into 600/400 for Mac TimeMachine backups, and fat32 to move files between systems
2) my internal data drive (1Tb)
3) my cd-drive
4) any usb data stick, etc

my computer also hangs when i try to shut down. thoughts?

---

### Post by seagreen on 2011-11-08
```
cory@seagreen:~$ sudo mount -t vfat /dev/sda5 /media
[sudo] password for cory: 
mount: /dev/sda5 already mounted or /media busy

```says already mounted, it shows up in devices, click on it, "not authorized to mount"

[IMG]http://i256.photobucket.com/albums/hh167/SeaGreen_bucket/Screenshotat2011-11-08092918.png[/IMG]
[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s256.photobucket.com/albums/hh167/SeaGreen_bucket/?action=view&amp;current=Screenshotat2011-11-08092918.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i256.photobucket.com/albums/hh167/SeaGreen_bucket/Screenshotat2011-11-08092918.png%22%20border=%220%22%20alt=%22Photobucket%22%3E%3C/a%3E[/IMG]

---

### Post by coffeecat on 2011-11-08
A few points/questions:

You can't mount sda5 as a vfat partition - it's your swap partition.

Which version of Ubuntu are you running?

Your sdb drive appears to have a completely blank partition table ("Disk identifier: 0x00000000"). Is it new and unformatted?

Post the terminal output of:

```
mount
cat /etc/fstab
```

Please enclose the output between [noparse]```
 and 
```[/noparse] tags for readability.

---

### Post by seagreen on 2011-11-08
> **coffeecat said:**
> A few points/questions:

You can't mount sda5 as a vfat partition - it's your swap partition.

Which version of Ubuntu are you running?

Your sdb drive appears to have a completely blank partition table ("Disk identifier: 0x00000000"). Is it new and unformatted?

Post the terminal output of:
{snip}


noted. 

version 11.10 

it shouldn't have a blank partition table, all drives should have something on them, unless i've lost data somehow. 

```
cory@seagreen:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpgs on /tmp type tmpfs (rw)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/cory/.Private on /home/cory type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=20fd5eeffb639b5a,ecryptfs_fnek_sig=0cdcce3f4d2f9cb8)
gvfs-fuse-daemon on /home/cory/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cory)
cory@seagreen:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4daf46d5-c4fb-4d56-b465-3a445a807c3f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=331d57b7-609e-4a16-bb23-9d0ea707474f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
tmpgs /tmp tmpfs defaults ,noatime, mode=1777 0 0

```
thank you!

---

### Post by coffeecat on 2011-11-08
In fact, your /etc/fstab shows the original swap line has been commented out. Even so, you won't be able to mount sda5 as vfat because it is a swap partition. /etc/fstab is mounting an encrypted swap, but I can't make out where this is physically.

With regard to your 1TB sdb drive - I've only ever seen "Disk identifier: 0x00000000" on unused unformatted drives or on ones where I've blanked the partition table with dd or shred. If you expect there to be partitions on that drive, I can't explain the "Disk identifier: 0x00000000" beyond what I've just said.

You should be able to mount your sdc3 FAT32 partition in the file browser, but I see nothing to correspond to it except "Disk1" and you are getting a "not authorised" for that. Curious. Try giving sdc3 a partition label with Disk Utility and then see if it appears in the file browser list. Or try mounting it from the terminal with:

```
sudo mkdir /media/sdc3
sudo mount -t vfat /dev/sdc3 /media/sdc3
```

Apart from that I'm somewhat mystified, and can't offer much more.

---

### Post by seagreen on 2011-11-08
> **coffeecat said:**
> In fact, your /etc/fstab shows the original swap line has been commented out. Even so, you won't be able to mount sda5 as vfat because it is a swap partition. /etc/fstab is mounting an encrypted swap, but I can't make out where this is physically.

With regard to your 1TB sdb drive - I've only ever seen "Disk identifier: 0x00000000" on unused unformatted drives or on ones where I've blanked the partition table with dd or shred. If you expect there to be partitions on that drive, I can't explain the "Disk identifier: 0x00000000" beyond what I've just said.

You should be able to mount your sdc3 FAT32 partition in the file browser, but I see nothing to correspond to it except "Disk1" and you are getting a "not authorised" for that. Curious. Try giving sdc3 a partition label with Disk Utility and then see if it appears in the file browser list. Or try mounting it from the terminal with:

```
sudo mkdir /media/sdc3
sudo mount -t vfat /dev/sdc3 /media/sdc3
```Apart from that I'm somewhat mystified, and can't offer much more.



the 1TB drive sdb is named "Disk1", it should not have any partitions (ie i never split it) but it should be formated ext4. if that drive is a loss, i guess i'll just start over fresh or something. gross. 

sdc3 fat32 is named "swap", but i typically use it as a plug-and-play drive to move data between my computers. in disk utility, it is already labeled "swap". 

trying to mount it through terminal as you suggested, terminal responds "special device /dev/sdc3 does not exist"

again, thanks for your help. i think this problem is exacerbated by my naming my data disk "disk1" and one of my partitions "swap", as this is making me more confused.

---

### Post by seagreen on 2011-11-08
for my own reference, and to aid anybody who's trying to help (and thank you!), this is what disk utility is telling me about all the drives, summarized in a nice, neat table. 

```
 
Device        Label              Cpcity     Mountpoint     Format    Details
/dev/sda       -                 60               /        ext4        OS drive, has 3partitions(sda1,sda2,sda5)
/dev/sdb       Disk1             1000       currently not    ext4        Internal drive, 1partition
/dev/sdd1     TimeM...        600          currently not     hfs+       timemachine partition on external usb drive
/dev/sdd2     SWAP            400         currently not      fat32       partition on external usb drive

```this contradicts results from terminal, disk utility isn't even showing an "sdc"

---

### Post by audiomick on 2011-11-08
I think that will format better if you use the quote tags instead of the code ones.

---

### Post by seagreen on 2011-11-08
> **audiomick said:**
> I think that will format better if you use the quote tags instead of the code ones.

quote doesn't preserve the number of spaces between words, code does.

---

### Post by audiomick on 2011-11-08
oops, sorry. Thought it was the other way round....

---

### Post by seagreen on 2011-11-08
> **audiomick said:**
> oops, sorry. Thought it was the other way round....

cheers, michael.

should i post this on openubuntu?

---

### Post by audiomick on 2011-11-08
No need. They already know I'm erratic... :)

---

### Post by seagreen on 2011-11-08
more meant if anybody there might be able to help, but i appreciate your humour. LOL

---

### Post by audiomick on 2011-11-08
> **seagreen said:**
> more meant if anybody there might be able to help,
Post it there. There are a couple of people there who might have an idea. ;)

---

### Post by seagreen on 2011-11-10
> **seagreen said:**
> thanks for your help so far. 

results of fdisk -l
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
[B]
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.[/B]


```> **coffeecat said:**
> 

With regard to your 1TB sdb drive - I've only ever seen "Disk identifier: 0x00000000" on unused unformatted drives or on ones where I've blanked the partition table with dd or shred. If you expect there to be partitions on that drive, I can't explain the "Disk identifier: 0x00000000" beyond what I've just said.


can anybody shed some light on the error message i bolded? perhaps a partition table exists, but isn't being shown?



computer is still hanging on shutdown.

---

### Post by Miljet on 2011-11-10
There is a new partitioning scheme out now that addresses the inability of the old MS-DOS / MBR format to handle large disks. For more info google "MBR vs GUID Partition Table".  Here is one such site:
[http://www.petri.co.il/gpt-vs-mbr-based-disks.htm](http://www.petri.co.il/gpt-vs-mbr-based-disks.htm)

---

### Post by cyberm@rmotte on 2011-11-10
> **seagreen said:**
> thanks for your help so far. 



not sure what you mean. please elaborate? all devices were automounting fine until a few nights ago. 



results of fdisk -l
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8023

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   100501503    50249728   83  Linux
/dev/sda2       100503550   117229567     8363009    5  Extended
/dev/sda5       100503552   117229567     8363008   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      409639      204819+  ee  GPT
/dev/sdc2          409640  1172284639   585937500   af  HFS / HFS+
/dev/sdc3      1172547584  1952149503   389800960    b  W95 FAT32

Disk /dev/mapper/cryptswap1: 8563 MB, 8563720192 bytes
255 heads, 63 sectors/track, 1041 cylinders, total 16726016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x646b5edb

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


```i'm not sure how to fully interpret the above. i see three drives (60G, and 2 at 1T). how do i modify ```
sudo mount -t vfat /dev/sda5 /media
``` to fit my drives? i imagine something like
```
sudo mount -t vfat /dev//sdb/name
sudo mount -t vfat /dev/sdc/name2

```my 60G ssd boot drive is perfect, the computer runs well, i'm on it right now. 

i can't access or mount: 
1) my external drive (1Tb partitioned into 600/400 for Mac TimeMachine backups, and fat32 to move files between systems
2) my internal data drive (1Tb)
3) my cd-drive
4) any usb data stick, etc

my computer also hangs when i try to shut down. thoughts?

> **seagreen said:**
> ```
cory@seagreen:~$ sudo mount -t vfat /dev/sda5 /media
[sudo] password for cory: 
mount: /dev/sda5 already mounted or /media busy

```says already mounted, it shows up in devices, click on it, "not authorized to mount"

[IMG]http://i256.photobucket.com/albums/hh167/SeaGreen_bucket/Screenshotat2011-11-08092918.png[/IMG]
[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s256.photobucket.com/albums/hh167/SeaGreen_bucket/?action=view&amp;current=Screenshotat2011-11-08092918.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i256.photobucket.com/albums/hh167/SeaGreen_bucket/Screenshotat2011-11-08092918.png%22%20border=%220%22%20alt=%22Photobucket%22%3E%3C/a%3E[/IMG]

Exactly the same problems here, hanging, and mounting....

---

### Post by seagreen on 2011-11-10
the hang on shutdown is not related to the mounting issues, and is common. fixes are published, but i haven't tried any yet. 

i think something in the permissions has been messed up, perhaps the drives are only accessible to root? does this make sense?

---

### Post by seagreen on 2011-11-14
solved this the old fashioned way; reinstalled last night. goodbye pretty 11.10, hello working 11.04. didn't lose any data on disks, so not any worse off than i was a few weeks ago. 

thanks to those who tried to help!

---

