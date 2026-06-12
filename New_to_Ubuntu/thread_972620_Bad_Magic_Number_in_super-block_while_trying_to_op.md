---
title: "Bad Magic Number in super-block while trying to open /dev/sda2"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by tchoklat on 2008-11-05
I have stuffed up I think.

I used GPartEd to create an extended partition to allow me to use more primary partitions to try other distros. All went well until I tried to reboot,this is where I get the error; "Bad Magic Number in super-block while trying to open /dev/sda2"

My / partition is sda1 and home partition is now renamed by GPartEd to sda5. sda2 as referred to in the error message is actaully the swap partition.

Simple request ..... what do I do?


tony

---

### Post by bumanie on 2008-11-06
Please post the output of > sudo fdisk -lu

---

### Post by tchoklat on 2008-11-06
> **bumanie said:**
> Please post the output of

from the Ubuntu liveCD!

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    85112369    42556153+  83  Linux
/dev/sda4        85112370   620815859   267851745    5  Extended
/dev/sda5       243738180   361205459    58733640   83  Linux
/dev/sda6       361205523   463764419    51279448+   7  HPFS/NTFS
/dev/sda7        85112496   161887004    38387254+  83  Linux
/dev/sda8       161887068   243738179    40925556   83  Linux
/dev/sda9       463764483   620815859    78525688+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$


sd 1 is /
sd 5 is /home
sd 6 is the virus
I have deleted sd2 which was swap!
the others are the extended partition and the empty ext3 partitions I wanted to try other distros on.


Tony

---

### Post by bumanie on 2008-11-06
A bad magic number is not a good sign, as you probably realize. Here are a couple of pages with suggestions how you may be able to recover things, but it looks difficult and any attempted fix may make things worse. [Read]("http://www.bellevuelinux.org/superblock") [the following]("http://linuxgazette.net/issue32/tag_superblock.html") and post back with questions - someone may be able to help, but it looks it could be a hardware issue, but there is one mention about changing partitions causing the problem. I would be tempted to use something like [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to try and rewrite the disk back to how it was before you used gparted - but if you make a mistake with testdisk, you will probably make things worse. Do you have large enough external hard drive (or separate internal) to copy your hard drive to? Trying to fix these things can be difficult. Alternatively, you could copy important data via the live cd and reinstall. If you did that, place windows on the first partition - it doesn't behave well in logical partitions, but linux will operate fine from a logical partition. If you try testdisk, read the documentation well before using it - also look [here]("http://www.users.bigpond.net.au/hermanzone/p21.html").

---

### Post by tchoklat on 2008-11-06
> **bumanie said:**
> A bad magic number is not a good sign, as you probably realize. Here are a couple of pages with suggestions how you may be able to recover things, but it looks difficult and any attempted fix may make things worse. [Read]("http://www.bellevuelinux.org/superblock") [the following]("http://linuxgazette.net/issue32/tag_superblock.html") and post back with questions - someone may be able to help, but it looks it could be a hardware issue, but there is one mention about changing partitions causing the problem. I would be tempted to use something like [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to try and rewrite the disk back to how it was before you used gparted - but if you make a mistake with testdisk, you will probably make things worse. Do you have large enough external hard drive (or separate internal) to copy your hard drive to? Trying to fix these things can be difficult. Alternatively, you could copy important data via the live cd and reinstall. If you did that, place windows on the first partition - it doesn't behave well in logical partitions, but linux will operate fine from a logical partition. If you try testdisk, read the documentation well before using it - also look [here]("http://www.users.bigpond.net.au/hermanzone/p21.html").


Hmmmm! If I copy the data from / and from /home to an external HDD, will I be able to copy it back after reformatting and partitioning the HDD? If so what commands do I use. I really need my /home partition, would like my / partition and can live without the ntfs partition?

I am unable to mount the partitions using the liveCD, I get 
error: device /dev/sda7 is not removable 
error: could not execute pmount


Your assistance is magic!

regards


Tony

---

### Post by meierfra. on 2008-11-06
Did you update your "fstab" after the partitioning?  Post the output of


```

sudo mount /dev/sda1 /mnt
sudo blkid
cat /mnt/etc/fstab
```

---

### Post by tchoklat on 2008-11-08
> **meierfra. said:**
> Did you update your "fstab" after the partitioning? Post the output of
 
 
```

sudo mount /dev/sda1 /mnt
sudo blkid
cat /mnt/etc/fstab
```
 
 
Think you got it right. FStab was not correctly idintifying the partitions, it did not appear to have changed when I amended the partitions. I always thought that GPartEd did this, I was wrong, at least in this instance.
 
I have reconstructed a new install and all is well now, thanks!
 
 
Tchoklat

---

### Post by meierfra. on 2008-11-08
> I always thought that GPartEd did this

Nope, GpartedEd does not edit fstab.

Glad you got it to work.

---

### Post by kevinluu on 2009-01-01
> **meierfra. said:**
> Nope, GpartedEd does not edit fstab.

Glad you got it to work.


Dear Bumanie, meierfra and tchoklat:

My name is Kevin. 

I am very new to Linux. 

I need help from you all to show me how can i fix the same problem "Bad magic number in super-block while trying to open /dev/sda2" i just encounter after i resize my /dev/sda2 partition.

On my system the command: fdisk -lu 

Disk /dev/sda:500.1GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1* 512 =512 bytes

Device     Boot  Start        End     Blocks  Id  System

/dev/sda1   *       63     208844     104391  83  Linux
/dev/sda2       208845  976768064  488279610  83  Linux


Would you please show me:

Where can i find the "fstab" that meierfra mentioned and how must i update this fstab using infomation disaplyed from the fdisk -lu command?

Thank you very much.

Kevin

---

### Post by unutbu on 2009-01-01
Please post the output to the commands 
```
sudo mount /dev/sda2 /mnt
sudo blkid
cat /mnt/etc/fstab

```
Given that info, we should be able to set you right.

---

### Post by kevinluu on 2009-01-04
> **unutbu said:**
> Please post the output to the commands 
```
sudo mount /dev/sda2 /mnt
sudo blkid
cat /mnt/etc/fstab

```
Given that info, we should be able to set you right.

Dear Iced Blended Vanilla Crème,

your request for the information output by the below commands, 

"
sudo mount /dev/sda2 /mnt
sudo blkid
cat /mnt/etc/fstab
"

Below are the methods that i tried to get the your requested infomation: 

A) "Use the Knoppix CD to boot up" method:

From the terminal, i enter the:

sudo mount /dev/sda2 /mnt

i got response message below:

mount: you must specify the filesystem type.

then i tried the below command

sudo mount -t ext2 /dev/sda2 /mnt
or
sudo mount -t ext3 /dev/sda2 /mnt

i got response message below:

mount: wrong fs type, bad option, bad superblock on/dev/sda2, missing codepage or other error
       In some cases useful info is found in syslog - try dmesg | tail or so

I don't know what to do next so i stopped using this A) method to get your asking infomation.


B) "Use the hard drive to boot up" method:

After bootup, i switch to "su" super-user.


1) i enter command : blkid  

i got the below response message:

/dev/sda1: LABEL="/boot" UUID="6ebd2490-a30b-4444-b67b-e1e2f19cf4c6" SEC_TYPE="ext2" TYPE="ext3"

/dev/dm-0: UUID="cc9b38d2-bd6d-456b-9aa4-5febe5361826" SEC_TYPE="ext2" TYPE="ext3"

/dev/dm-1: TYPE="swap" UUID="2732d729-c410-48bd-b6bc-c0cc6ac74797"

/dev/mapper/VolGroup-LogVol01: TYPE="swap" UUID="2732d729-c410-48bd-b6bc-c0cc6ac74797"


I did not see the /dev/mapper/VolGroup-LogVol00 here which i think the /dev/sda2 is mapped to.


2) i enter command: cat /etc/fstab

i got the below response message

#This file is edited by fstab-sunc - see 'man fstab-sync' foe details
/dev/VolGroup00/LogVol00  /        ext3   defaults       1 1
LABEL=/boot               /boot    ext3   defaults       1 2
/dev/devpts               /dev/pts devpts gid=5,mode=620 0 0
/dev/shm                  /dev/shm tmpfs  defaults       0 0
/dev/proc                 /proc    proc   defaults       0 0
/dev/sys                  /sys     sysfs  defaults       0 0
/dev/VolGroup00/LogVol01  swap     swap   defaults       0 0
#/dev/sdb1            /mnt/windows ntfs   ro,unmask=0222 0 0
/dev/hda         /media/cdrecorder auto   pamconsole,exec,noauto,managed 0 0


3) i enter command: cat /mnt/etc/fstab

i got the below response message:

/dev/ram0             /      ext2 rw 0 0
proc                  /proc  proc rw 0 0

Please help me to solve the "Bad Magic Number in super-block while trying to open /dev/sda2"

Thank you very much.

Kevin

---

### Post by kevinluu on 2009-01-05
Please help.

I have posted the output of the:

sudo mount /dev/sda2 /mnt
sudo blkid
cat /mnt/etc/fstab

Thank you very much.

Kevin

---

### Post by caljohnsmith on 2009-01-05
Since meierfra and unutbu haven't had a chance to get back to you yet, I just wanted to ask: is your sda2 partition LVM by chance? I'm wondering because it looks like from the output of blkid that sda2 might have been mapped to /dev/dm-0, which I think would be either RAID or LVM (but I'm not sure). How about trying:
```
sudo mount /dev/dm-0 /mnt && ls -l /mnt
```
And please post the output.

---

### Post by kevinluu on 2009-01-05
> **unutbu said:**
> Please post the output to the commands 
```
sudo mount /dev/sda2 /mnt
sudo blkid
cat /mnt/etc/fstab

```
Given that info, we should be able to set you right.


Hi All,

booted from my hard disk then switch to "su" user. I then 

1) Enter command: mount  /dev/dm-0 /mnt

i got no output message for this command.

2) Enter command: ls -l /mnt

The output message for this command is shown below:

total 196
drwxr-xr-x  2 root root  4096 Aug 16  2006 bin
drwxr-xr-x  2 root root  4096 May 18  2006 boot
drwxr-xr-x  4 root root  4096 May 18  2006 dev
drwxr-xr-x 91 root root 12288 Jan  5 17:40 etc
drwxr-xr-x  9 root root  4096 Apr 18  2008 home
drwxr-xr-x 11 root root  4096 Aug 16  2006 lib
drwx------  2 root root 16384 May 18  2006 lost+found
drwxr-xr-x  4 root root  4096 Jan  5 17:38 media
drwxr-xr-x  2 root root  4096 Apr 25  2005 misc
drwxr-xr-x 15 root root  4096 Apr 16  2008 mnt
dr-xr-xr-x  2 root root  4096 May 24  2006 net
drwxr-xr-x  4 root root  4096 Oct 16 05:25 opt
drwxr-xr-x  2 root root  4096 May 18  2006 proc
drwxr-x--- 27 root root  4096 Nov  5 21:34 root
drwxr-xr-x  2 root root 12288 Aug 16  2006 sbin
drwxr-xr-x  2 root root  4096 May 18  2006 selinux
drwxr-xr-x  2 root root  4096 May 23  2005 srv
drwxr-xr-x  2 root root  4096 May 18  2006 sys
drwxrwxrwt  6 root root  4096 Jan  5 17:42 tmp
drwxr-xr-x 14 root root  4096 Feb 27  2006 usr
drwxr-xr-x 25 root root  4096 Apr 16  2008 var


I rebooted the system again to erase the previous mount command.

After the system rebooted i then enter:

A) The "fdisk -l" command gives the below message;

Disk /dev/sda: 500.1GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13 104391 83 Linux
/dev/sda2 14 60801 488279610 8e Linux LVM

Yes the /dev/sda2 in my system is Linux LVM. 

B) The " df -h" command shows:

Filesystem                    size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-LogVol00 224G  194G   19G  92% /
/dev/sda1                      99M   14M   80M  15% /boot
/dev/shm                      628M     0  628M   0% /dev/shm

It looks like the /dev/sda2 is mapped to /dev/mapper/VolGroup-LogVol00

The "fsck -n /dev/sda1" shows:

fsck 1.37 (21-Mar-2005)
e2fsck 1.37 (21-Mar-2005)
ext2fs_check_if_mount: Permission denied while determing whether /dev/sda1 is mounted.
/boot: clean, 36/26104 files, 17488/104388 blocks

The "fsck -n /dev/sda2" shows:
 
fsck 1.37 (21-Mar-2005)
e2fsck 1.37 (21-Mar-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
   e2fsck -b 8193 <device>

As you can see my /dev/sda2 has bad magic number in super-block.

Please help me to fix this problem in my /dev/sda2? 


Thank you very much.

Kevin

---

### Post by caljohnsmith on 2009-01-05
You can't do an fsck on sda2 directly since it is LVM. How about instead trying:
```
sudo fsck -yCM /dev/dm-0
```
And please post the output.

---

### Post by kevinluu on 2009-01-06
> **caljohnsmith said:**
> You can't do an fsck on sda2 directly since it is LVM. How about instead trying:
```
sudo fsck -yCM /dev/dm-0
```
And please post the output.

Hi All,

After switching to "su" super user account, i then i enter the "fsck -yCM /dev/dm-0". I got the output as shown below:

fsck 1.37 (21-Mar-2005)
e2fsck 1.37 (21-Mar-2005)
/dev/dm-0 is mounted

Warning!!! Running e2fsck on a mounted filesystem may cause SERVERE filesystem damage.

Do you really want to continue (y/n)?

I enter "n" this time to stop.

Should i eneter "y" to continue?

Thank you very much.

Kevin

---

### Post by caljohnsmith on 2009-01-06
I'm glad you said "n" about the fsck since it seems /dev/dm-0 is mounted somewhere. To find out where it is mounted, you can do:
```
mount | grep dm-0
```
And to unmount it you can try:
```
sudo umount /dev/dm-0
```
Once you have dm-0 unmounted, let me know if you can run the fsck on it OK.

---

### Post by kevinluu on 2009-01-23
> **caljohnsmith said:**
> I'm glad you said "n" about the fsck since it seems /dev/dm-0 is mounted somewhere. To find out where it is mounted, you can do:
```
mount | grep dm-0
```
And to unmount it you can try:
```
sudo umount /dev/dm-0
```
Once you have dm-0 unmounted, let me know if you can run the fsck on it OK.

Hi,

I am very sorry.
I were very busy with other works at the office and did not have time to try out your steps yet.

I will do your suggested steps this weekend and let you know the output.

Thank you very much.

Kevin.

---

### Post by dreas on 2009-02-27
*sigh*

This is an embarrassing first post for me. I'm having the exact same issue as OP. I partitioned 739GB as ext3 and incorrectly mounted the file. Upon reboot its saying:

"Bad Magic Number in super-block while trying to open /dev/sbd1/"

The problem is that sbd1 is actually an NTFS partition, and my linux partition is on sbd2. Additionally, the error on boot says:

"The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem, then the superblock is corrupt."

I decided to delete the partition I just made (all 739GB) and keep it unallocated as it was before, but after rebooting, it gave me the same error.

I'm typing this from the LiveCD, and upon looking at Gparted, it's saying my original partition is ext3.

Finally, upon trying to edit (or at least inspect) my fstab file, I'm not seeing what is usually there. I'll post all relevant outputs below:

sudo fdisk -lu

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa47ea47e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   268414019   134206978+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x120ca290

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    25768259    12884098+   7  HPFS/NTFS
/dev/sdb2        25768260  1953520064   963875902+   f  W95 Ext'd (LBA)
/dev/sdb5      1638919233  1743791489    52436128+   7  HPFS/NTFS
/dev/sdb6      1540794276  1634806529    47006127   83  Linux
/dev/sdb7      1634806593  1638919169     2056288+  82  Linux swap / Solaris
/dev/sdb8      1743791553  1953520064   104864256    7  HPFS/NTFS
/dev/sdb9      1528649073  1540794149     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

sudo blkid
```

/dev/sda1: UUID="3A840561840520CD" TYPE="ntfs" 
/dev/sdb1: UUID="28CCC945CCC90DCE" LABEL="Extra Storage and OS" TYPE="ntfs" 
/dev/sdb5: UUID="54BCAFBA64F8FBA4" LABEL="Ubuntu" TYPE="ntfs" 
/dev/sdb6: UUID="61fa493a-4ab4-42e9-ac97-cce110d0bd37" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="d46aa2b1-e0fc-4d6e-b662-ea59dd0ee9d2" 
/dev/sdb8: UUID="152F2BE9FEF7D9F9" LABEL="Vista" TYPE="ntfs" 
/dev/sdb9: TYPE="swap" UUID="31435922-2975-4ac0-8ae9-8c0b31fc3823" 
/dev/loop0: TYPE="squashfs" 
```

my fstab file looks like this:
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb7 swap swap defaults 0 0
/dev/sdb9 swap swap defaults 0 0
```

I'm almost positive all of this is because I incorrectly mounted the new partition before rebooting, but now that my fstab file looks like that, I don't know what to do!

I've searched google and these forums for a few hours before making this post, and have great success on here findind solutions to some of the problems I've been running into, but I can't find this one anywhere, so hopefully you can let me know what I'm doing wrong.

Thanks a bunch.

---

### Post by caljohnsmith on 2009-02-28
Dreas, it would first help to get some more info about your system, so how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (and put code tags around it). The results of that script will help clarify your setup.

---

### Post by dreas on 2009-02-28
> **caljohnsmith said:**
> Dreas, it would first help to get some more info about your system, so how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (and put code tags around it). The results of that script will help clarify your setup.

Thank you for the reply. Below is the output of results.txt

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa47ea47e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x120ca290

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    25,768,259    25,768,197   7 HPFS/NTFS
/dev/sdb2          25,768,260 1,953,520,064 1,927,751,805   f W95 Ext d (LBA)
/dev/sdb5       1,638,919,233 1,743,791,489   104,872,257   7 HPFS/NTFS
/dev/sdb6       1,540,794,276 1,634,806,529    94,012,254  83 Linux
/dev/sdb7       1,634,806,593 1,638,919,169     4,112,577  82 Linux swap / Solaris
/dev/sdb8       1,743,791,553 1,953,520,064   209,728,512   7 HPFS/NTFS
/dev/sdb9       1,528,649,073 1,540,794,149    12,145,077  82 Linux swap / Solaris
/dev/sdb10         25,768,386 1,528,649,009 1,502,880,624  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3A840561840520CD" TYPE="ntfs" 
/dev/sdb1: UUID="28CCC945CCC90DCE" LABEL="Extra Storage and OS" TYPE="ntfs" 
/dev/sdb5: UUID="54BCAFBA64F8FBA4" LABEL="side storage" TYPE="ntfs" 
/dev/sdb6: UUID="61fa493a-4ab4-42e9-ac97-cce110d0bd37" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="d46aa2b1-e0fc-4d6e-b662-ea59dd0ee9d2" TYPE="swap" 
/dev/sdb8: UUID="152F2BE9FEF7D9F9" LABEL="Vista" TYPE="ntfs" 
/dev/sdb9: UUID="31435922-2975-4ac0-8ae9-8c0b31fc3823" TYPE="swap" 
/dev/sdb10: LABEL="Linux 732" UUID="1138f191-e449-4f2a-bfda-a857bebec695" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN


=========================== sdb6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=61fa493a-4ab4-42e9-ac97-cce110d0bd37

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		61fa493a-4ab4-42e9-ac97-cce110d0bd37
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		61fa493a-4ab4-42e9-ac97-cce110d0bd37
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		61fa493a-4ab4-42e9-ac97-cce110d0bd37
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		61fa493a-4ab4-42e9-ac97-cce110d0bd37
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		61fa493a-4ab4-42e9-ac97-cce110d0bd37
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb8
UUID=d46aa2b1-e0fc-4d6e-b662-ea59dd0ee9d2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/mynewdrive   ext3    defaults     0        2

=================== sdb6: Location of files loaded by Grub: ===================


 819.2GB: boot/grub/menu.lst
 819.2GB: boot/grub/stage2
 819.2GB: boot/initrd.img-2.6.27-11-generic
 819.2GB: boot/initrd.img-2.6.27-7-generic
 819.3GB: boot/vmlinuz-2.6.27-11-generic
 819.3GB: boot/vmlinuz-2.6.27-7-generic
 819.2GB: initrd.img
 819.2GB: initrd.img.old
 819.3GB: vmlinuz
 819.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  90 a2 0c 12 00 00 00 01  |................|
000001c0  01 00 07 fe ff ff 3f 00  00 00 05 31 89 01 00 fe  |......?....1....|
000001d0  ff ff 0f fe ff ff 44 31  89 01 7d 28 e7 72 00 00  |......D1..}(.r..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Any info you can give me I would greatly appreciate it. I am totally stuck for now, but I feel like once I get through these kinks, Ubuntu will be worth sticking with for the long haul. Thanks again!

---

### Post by unutbu on 2009-02-28
Notice that your /etc/fstab contains this line:
```

/dev/sdb1       /media/mynewdrive   ext3    defaults     0        2
```



It says that sdb1 should be mounted at /media/nmynewdrive and that there is an ext3 filesystem inside. At boot up, Linux balks at this, since it can not find any ext3 filesystem on sdb1.

To fix: boot from the LiveCD, open a terminal (Applications>Accessories>Terminal) and type
```

sudo mount /dev/sdb6 /mnt
gksu gedit /mnt/etc/fstab

```
And change ```

/dev/sdb1       /media/mynewdrive   ext3    defaults     0        2
```
to```

/dev/sdb1       /media/mynewdrive ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0

```

Next around line 5 (though this is not critical) change

```

# /dev/sdb7
```

to
```

# /dev/sdb6
```

in /etc/fstab too. UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 refers to /dev/sdb6 rather than /dev/sdb7.

Save the file and then reboot.

---

### Post by dreas on 2009-02-28
> **unutbu said:**
> Notice that your /etc/fstab contains this line:
```

/dev/sdb1       /media/mynewdrive   ext3    defaults     0        2
```



It says that sdb1 should be mounted at /media/nmynewdrive and that there is an ext3 filesystem inside. At boot up, Linux balks at this, since it can not find any ext3 filesystem on sdb1.

To fix: boot from the LiveCD, open a terminal (Applications>Accessories>Terminal) and type
```

sudo mount /dev/sdb6 /mnt
gksu gedit /mnt/etc/fstab

```
And change ```

/dev/sdb1       /media/mynewdrive   ext3    defaults     0        2
```
to```

/dev/sdb1       /media/mynewdrive ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0

```

Next around line 5 (though this is not critical) change

```

# /dev/sdb7
```

to
```

# /dev/sdb6
```

in /etc/fstab too. UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 refers to /dev/sdb6 rather than /dev/sdb7.

Save the file and then reboot.


This worked perfectly and I am now back up and running. Thank you so much for your help.

I'm trying to understand the logic behind this though. I followed the tutorial of adding a new drive from the following site:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Granted, I was really just adding a partition to my current OS, but close enough. Notice how it suggests a mount point of /media/mynewdrive/ and to add the following to your fstab:

```

/dev/sdb1       /media/mynewdrive   ext3    defaults     0        2
```

I chose (or at least I thought I did) that partition to be an ext3 so that it would work. How did you know to change it to:

```

/dev/sdb1       /media/mynewdrive ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0

```

?

Where did you get the values for uid, gid, and dmask? Apologies for the probably stupid questions but I'm just trying to figure out the logic so I learn from this (give a man a fish vs teach a man to fish, etc). Thanks again!

---

### Post by unutbu on 2009-02-28
I'm glad what I suggested worked \\:D/

Your questions are very good ones, but the answers take a little while to explain. If what I wrote makes your eyes glaze over, feel free to ask for clarification. I'll try my best.

As you mentioned in post #19, sdb1 is an NTFS partition.
The instructions in [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
say
> 
Add this line to the end (**for ext3 file system**): 
  /dev/sdb1    /media/mynewdrive   ext3    defaults     0        2

As you've seen, it only works for ext3 file systems.
To find the right syntax for an ntfs entry in /etc/fstab, I went to bodhi.zazen's guide, [How to fstab ]("http://ubuntuforums.org/showthread.php?t=283131").

As described in that guide, uid=1000 (gid=1000) sets you as the owner (and group owner) of all files in /media/mynewdrive. By default on Ubuntu, the first normal user account is assigned uid=1000. If you type
```

id

```
in the terminal, you will see your uid and gid numbers.

dmask and fmask are a little tricky to explain. Are you familiar with file permission notation? If not, you will find a very good explanation [here]("https://help.ubuntu.com/community/FilePermissions"). Once you grok file permission nomenclature as explained on that page, there is just one more fact you need to know: by convention, dmask=027 sets the permission on all directories in /media/mynewdrive to equal the seven's complement of 027 -- that is, 750. (Each digit in 750 is obtained by subtracting the corresponding digit of the dmask from 7. 7=7-0, 5=7-2, 0=7-7.) In computer lingo, a mask is almost always a number which is the complement of some other fixed number. In the case of dmask and fmask, that fixed number is 7.

Thus, dmask=027 means directory permissions will be set to 750, which means you will have read,write and execute permissions on all directories in /media/mynewdrive, anyone in your group will have read and execute permissions, and everyone else will have no permissions.

Similarly, fmask=137 means file permissions will be set to 640, which means you will have read,write permissions on all files in /media/mynewdrive, members of your group will have read permission, and all others will have no permissions.

---

### Post by dreas on 2009-03-01
> **unutbu said:**
> I'm glad what I suggested worked \\:D/

Your questions are very good ones, but the answers take a little while to explain. If what I wrote makes your eyes glaze over, feel free to ask for clarification. I'll try my best.

As you mentioned in post #19, sdb1 is an NTFS partition.
The instructions in [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
say


As you've seen, it only works for ext3 file systems.
To find the right syntax for an ntfs entry in /etc/fstab, I went to bodhi.zazen's guide, [How to fstab ]("http://ubuntuforums.org/showthread.php?t=283131").

As described in that guide, uid=1000 (gid=1000) sets you as the owner (and group owner) of all files in /media/mynewdrive. By default on Ubuntu, the first normal user account is assigned uid=1000. If you type
```

id

```
in the terminal, you will see your uid and gid numbers.

dmask and fmask are a little tricky to explain. Are you familiar with file permission notation? If not, you will find a very good explanation [here]("https://help.ubuntu.com/community/FilePermissions"). Once you grok file permission nomenclature as explained on that page, there is just one more fact you need to know: by convention, dmask=027 sets the permission on all directories in /media/mynewdrive to equal the seven's complement of 027 -- that is, 750. (Each digit in 750 is obtained by subtracting the corresponding digit of the dmask from 7. 7=7-0, 5=7-2, 0=7-7.) In computer lingo, a mask is almost always a number which is the complement of some other fixed number. In the case of dmask and fmask, that fixed number is 7.

Thus, dmask=027 means directory permissions will be set to 750, which means you will have read,write and execute permissions on all directories in /media/mynewdrive, anyone in your group will have read and execute permissions, and everyone else will have no permissions.

Similarly, fmask=137 means file permissions will be set to 640, which means you will have read,write permissions on all files in /media/mynewdrive, members of your group will have read permission, and all others will have no permissions.



Ahh ok this makes perfect sense. The tutorial assumed my new partition was sdb1 (which would be right if I was installing a new hard drive), but the partition that I wanted to add was actually on sdb6. I blindly followed the tutorial on that page instead of realizing my partition was in a different spot (in my case, sdb6). If I had replaced the tutorial example (sdb1) with sdb6, the drive would have mounted perfectly and I wouldn't have had that error. Is that correct? I'm trying to be overly wordy here in case anyone finds this page and runs into a similar problem.

I wasn't familiar with the file permission notation, and that link helped a bunch (I'm still not 100% on this, but I have a somewhat decent grasp on this). Thanks again for all of your help. I just have one last thing to configure before I can have Ubuntu 8.10 as my primary OS, but I'll post that in the appropriate thread.

---

### Post by unutbu on 2009-03-01
Yes, I think the tutorial would have worked if sdb6 were substituted for sdb1.
However, note that you also have this entry in your /etc/fstab:

```
UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 /               ext3    relatime,errors=remount-ro 0       1
```

UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 is another way of specifying a partition. 
The output of "blkid" (also in RESULTS.txt) shows 

```
/dev/sdb6: UUID="61fa493a-4ab4-42e9-ac97-cce110d0bd37" SEC_TYPE="ext2" TYPE="ext3" 
```

So UUID=61fa493a-4ab4-42e9-ac97-cce110d0bd37 means /dev/sdb6.

Thus, you already have a valid entry in /etc/fstab for sdb6 -- it is your Ubuntu root partition (/). If you were to put

```
/dev/sdb6       /media/mynewdrive   ext3    defaults     0        2
```

in your /etc/fstab, I think Ubuntu would mount the sdb6 filesystem twice -- once at / and a second time at /media/mynewdrive. On the one hand, you can do this, but on the other hand, you have to ask yourself if you really want to. :)

---

