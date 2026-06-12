---
title: "Unable to mount extenal drive"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by sven_wien on 2008-11-10
how can i mount my external hdd?
pls explain in easy steps as i am new!
Also pls read other tread reg. no sound on acer aspire 6920
thanks

---

### Post by keplerspeed on 2008-11-10
Have a look here:

[http://ubuntuforums.org/showthread.php?t=80737](http://ubuntuforums.org/showthread.php?t=80737)

assuming it is a usb external hd. Otherwise just do a google search for 'mount external hard drive'.

If you having trouble with the other thead, i can run through the process with you. cheers

---

### Post by sven_wien on 2008-11-10
many thanks but it doesnt work 
error could not mount volume

---

### Post by keplerspeed on 2008-11-10
Seems a little weird, it should mount automatically. So is it a usb external hdd?

---

### Post by keplerspeed on 2008-11-10
what does this output?
> sudo fdisk -l

Also what is the output of these?

cat /etc/fstab
df -h

or even a simple lsusb to see if the usb port is working :-)

---

### Post by Ryadt on 2008-11-10
Can you post the error message you are getting.

---

### Post by keplerspeed on 2008-11-10
Previous post with similar issue:

[http://ubuntuforums.org/showthread.php?t=691732](http://ubuntuforums.org/showthread.php?t=691732)

---

### Post by sven_wien on 2008-11-10
xxl@xxl-laptop:~$ sudo fdisk -l

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xc3ba16e0

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       29267   235087146   83  Linux
/dev/sda2           29268       30401     9108855    5  Erweiterte
/dev/sda5           29268       30401     9108823+  82  Linux Swap / Solaris

Platte /dev/sdb: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x817ded30

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS
xxl@xxl-laptop:~$


xxl@xxl-laptop:~$ cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
xxl@xxl-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a2a77d3-95e2-49f3-a142-145b6e1564ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ae815813-71d8-47a9-b304-bd7a325e1748 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
xxl@xxl-laptop:~$

xxl@xxl-laptop:~$ df -h
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/sda1             221G  4,3G  206G   3% /
tmpfs                 1,5G     0  1,5G   0% /lib/init/rw
varrun                1,5G  308K  1,5G   1% /var/run
varlock               1,5G  4,0K  1,5G   1% /var/lock
udev                  1,5G  2,9M  1,5G   1% /dev
tmpfs                 1,5G  236K  1,5G   1% /dev/shm
lrm                   1,5G  2,0M  1,5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/mmcblk0p1        975M  974M  1,3M 100% /media/disk
xxl@xxl-laptop:~$

---

### Post by keplerspeed on 2008-11-10
Ok so the /dev/sdb is the usb hdd. excellent. just to make sure, you dont get a media icon? under place>computer is there a removable disk icon for the hdd?

---

### Post by sven_wien on 2008-11-10
yes there is

---

### Post by keplerspeed on 2008-11-10
And when you click to open it, is that when you recieve the error? It seems like the hdd is detected but not mounting.

---

### Post by sven_wien on 2008-11-10
correct and what now?

---

### Post by keplerspeed on 2008-11-10
Ok. The problem may be that you didnt safely remove the hdd when using a windows machine. If you can access a windows box, plug it in, and safely remove it. do you have access to a windows machine?

---

### Post by sven_wien on 2008-11-10
no i just deleted this shity vista any other possiblity?

---

### Post by sven_wien on 2008-11-10
no i just deleted this shity vista any other possiblity? and while u there any chance of getting my sound working on my acer aspire 6920g ?

---

### Post by keplerspeed on 2008-11-10
you can force mount the hdd by doing this:

sudo mkdir /media/<name>
sudo mount /dev/<device> /media/<name> -o force

to unmount:

umount /media/<name>

---

### Post by sven_wien on 2008-11-10
well its in german but:
xxl@xxl-laptop:~$ sudo mkdir /media/exhdd
[sudo] password for xxl: 
xxl@xxl-laptop:~$ sudo mkdir /media/exhdd
mkdir: kann Verzeichnis „/media/exhdd“ nicht anlegen: File exists
xxl@xxl-laptop:~$ umount /media/exhdd
umount: /media/exhdd ist laut „mtab“ nicht eingehängt (not mounted??)

---

### Post by keplerspeed on 2008-11-10
the first command created a directory: mkdir /media/exhdd

the second command mounts your device: mount /dev/sdb or whatever the name of your device is.

the third command can be used whenever you want to remove the device, or unmount the volume.

SO you have created the directory.

so issue this command:

sudo mount /dev/sdb /media/exhdd -o force

---

### Post by sven_wien on 2008-11-10
well it doesnt work so i have to try later at a friend he has windows!
ow i just need to get my sound working thats more important so if u know anything bout it pls let me know! ps. my msn is [email]svenlucka@live.de[/email]

---

### Post by zamot.de on 2008-11-10
Hi,

I have exactly the same problem.
I have to external HDD. One is 60GB with one linux partition and one FAT32 and is working correctly.
The other is a multimedia (TVIX-DVICO) HDD and I simply can't mount it.
It's already 6 months I deleted windows and changed to Linux. First, tried Ubuntu without luck, because my sound didn't work, neither ACPI, so I changed to PCLINUXOS where everything went well less the sound and an overeating of the laptop (LG LW20). I just installed now UBUNTU 8.10, but it's not only the sound that doesn't work, also shutdown and most important my TVIX HDD (where I have a crucial file I need to recover still this week :((

I have tried all the commands I saw by googling my problem. Nothing works.

I receive this message now (there was different messages before while trying several commands):

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

There's not an icon in Desktop (only the other HDD appears there), but I can see it in locals (but it's not mounted)

I went to a friend's house and could open it from windows, but as a read-only HDD, which shows only the oldest files (not those that I saved there with PCLINUXOS), so I couldn't recover my needed file. I tried to do chkdsk and windows didn't respond. Neither the defragmentation reacted.

The actual information on my FSTAB file is this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=33fba768-00ae-4f7c-b695-33c0fee2c510	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb5 :
/media/TVIX ntfs-3g defaults,locale=pt_PT.utf8,force 0 0

Please help.

---

### Post by zamot.de on 2008-11-13
Hello,

I tried to use disk manager and changed the drive to ntfs-fuse. The result was this answer:
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' option.
NOTE: If you had not scheduled check and last time accessed this volume
using ntfsmount and shutdown system properly, then init scripts in your
distribution are broken. Please report to your distribution developers
(NOT to us!) that init scripts kill ntfsmount or mount.ntfs-fuse during
shutdown instead of proper umount.
Mount failed.

I think that 6 months of data lost, no sound, no shutdown it is too much. Or I be back to windows (which I hate) or I will hate Linux soon too.

---

### Post by zamot.de on 2008-11-13
And with the force option:

WARNING: Dirty volume mount was forced by the 'force' mount option.
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

fuse_mount failed.
Unmounting /dev/sdd1 (TVIX)

---

### Post by Geekboy on 2008-11-13
I had a similar problem with my ext usb.   I followed the advice to connect it to a Windows PC and safely remove.  I was then able to mount it to my Ubuntu PC. Thanks.

---

