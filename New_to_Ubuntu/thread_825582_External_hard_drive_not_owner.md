---
title: "External hard drive not owner ?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-06-11
I have just connected an external hard drive and although the drive is showing up on the desktop , when I try to write to it I get the message "you are not the owner " when I try to change the permissions tag .How do I get access please ? ( I have tried using gparted and formatting as ext2 and ext3 and fat32,still nothing ).

---

### Post by Najand on 2008-06-11
Post your /etc/fstab file and the output of "sudo fdisk -l" here.

---

### Post by ex-wirecutter on 2008-06-11
fdisk -l shows up external drive as /dev/sdb1 ext2

---

### Post by ex-wirecutter on 2008-06-11
Forgot to add , tried /etc/fstab in root but got "permission denied " Normally sudo su lets me into everything . Could it be the external drive is not mounted properly as it shows up on the desktop as "media ".

---

### Post by ukripper on 2008-06-11
> **ex-wirecutter said:**
> Forgot to add , tried /etc/fstab in root but got "permission denied " Normally sudo su lets me into everything . Could it be the external drive is not mounted properly as it shows up on the desktop as "media ".
Can you do following:

```
sudo mount
```

---

### Post by vanadium on 2008-06-11
"Post your /etc/fstab file" means to post the content of that file, which is a text file. You can display the content of that file with the command "cat /etc/fstab".

Anyway, your external drive normally will not be included in your /etc/fstab. If it is, then there is cause of the issue. If it is not, then perhaps you are trying to write to a directory on the drive where you do not have permission, or the drive was not mounted while you were logged in. Normally, you should have user permission to write to the root of an external drive that you mounted while logged in.

Something to try: disconnect the drive (safely), and plug it back in. Then you should be able to create files at least in the root of the drive.

To check the permissions of the drive, issue following commands and post them here if you want us to help interpreting the output:

ls -l /media
ls -l /media/media

(I assume that your drive is being mounted in a directory "media" because it displays on your desktop as "media".)

If the permissions seem OK, but you still cannot write, then the filesystem might need to be checked, although I believe (but I do not know for sure) that in such a case, the drive would not be mounted at all.

---

### Post by ex-wirecutter on 2008-06-11
Thanks for your suggestions , I will try them all .Have to go now unfortunately ( work ) Much obliged for your time.

---

### Post by PokieCarlwin_is_borked on 2008-06-21
> **vanadium said:**
> "Post your /etc/fstab file" means to post the content of that file, which is a text file. You can display the content of that file with the command "cat /etc/fstab".


I tried this and I could not 'tab' out the command when I went looking /fstab did not exist

When I ran the following

> **vanadium said:**
> 
ls -l /media
ls -l /media/media

but as '~/media/SimpleDrivePS'  

I got 
dr-xr-xr-x 1 root root   16384 2007-04-15 08:30 1930-1959
dr-xr-xr-x 1 root root  135168 2007-01-06 07:07 1960-1969
dr-xr-xr-x 1 root root  245760 2007-01-17 11:40 1970-1979
dr-xr-xr-x 1 root root  417792 2007-01-29 08:53 1980-1989
dr-xr-xr-x 1 root root  167936 2007-01-15 19:17 1990-1999
dr-xr-xr-x 1 root root  110592 2007-11-22 09:21 2000-2009
dr-xr-xr-x 1 root root   45056 2006-12-27 17:32 europe 1988
dr-xr-xr-x 1 root root  315392 2007-05-08 18:17 German Music
dr-xr-xr-x 1 root root 1298432 2007-05-08 18:43 My Music
dr-xr-xr-x 1 root root       0 2006-12-20 11:48 RECYCLER
dr-xr-xr-x 1 root root  258048 2007-05-08 18:22 Spanish Music
dr-xr-xr-x 1 root root    4096 2006-12-27 04:40 System Volume Information
-r-xr-xr-x 1 root root  280576 2006-12-27 17:25 Thumbs.db
dr-xr-xr-x 1 root root   61440 2006-12-27 17:32 Vac Germany
dr-xr-xr-x 1 root root   24576 2007-01-29 08:57 Yellowstone1999'

and now I need translation cause I still have denied permission and I'm in way over my head :(

---

### Post by Rocket2DMn on 2008-06-21
Please post all of the following with the drive plugged in:
```
cat /etc/fstab
sudo fdisk -l
sudo blkid
mount
```
Please include the complete output of those commands.

---

### Post by PokieCarlwin_is_borked on 2008-06-21
eek@ladybug:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=45224ac3-9cb8-4c4d-b787-96b6d4b341ff /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3010ad11-59b6-40fe-8be4-1d2090348f4f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
192.168.0.12:/home/eek   /home/eek/from_b-4 nfs rw,bg,hard,intr   0


eek@ladybug:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 252 MB, 252968960 bytes
16 heads, 32 sectors/track, 965 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         965      246989+   6  FAT16

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7295    58597056    7  HPFS/NTFS





eek@ladybug:~$ sudo blkid
/dev/sda1: UUID="45224ac3-9cb8-4c4d-b787-96b6d4b341ff" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="3010ad11-59b6-40fe-8be4-1d2090348f4f" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="7C2A-DCD4" TYPE="vfat" 
/dev/sdb1: TYPE="ntfs" 
eek@ladybug:~$ 
eek@ladybug:~$ sudo blkid
/dev/sda1: UUID="45224ac3-9cb8-4c4d-b787-96b6d4b341ff" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="3010ad11-59b6-40fe-8be4-1d2090348f4f" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="7C2A-DCD4" TYPE="vfat" 
/dev/sdb1: TYPE="ntfs" 






eek@ladybug:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdb1 on /media/SimpleDrivePS type ntfs (rw,nosuid,nodev,umask=222,utf8)

---

### Post by Rocket2DMn on 2008-06-21
The problem is that it is using a umask of 222 which is blocking the ability to write.  Unmount the drive with
```
sudo umount /dev/sdb1
```
Unplug the drive and wait 10 seconds, then plug it back in.  Does it automount?  Are you able to read/write?
If still not, unmount it again, then run
```
sudo mkdir /media/external
sudo mount -t ntfs-3g /dev/sdb1 /media/external
```
Then go to /media/external and see if you can read/write from/to the drive.

---

### Post by PokieCarlwin_is_borked on 2008-06-21
> **Rocket2DMn said:**
> 
sudo mount -t ntfs-3g /dev/sdb1 /media/external[/code]
Then go to /media/external and see if you can read/write from/to the drive.

it all was going ok except for the 'permission denied' and the 

eek@ladybug:/$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
mount: unknown filesystem type 'ntfs-3g'

---

### Post by Rocket2DMn on 2008-06-21
Oh my, what version of Ubuntu are you running?
If you are using Feisty, run
```
sudo apt-get install ntfs-3g ntfs-config
```
Then go to Applications->System Tools->NTFS Configuration Tool and enable writing on internet and external drives.
ntfs-3g comes preinstalled on all later versions of ubuntu.  Older versions don't have the stable ntfs-3g driver available direct from Ubuntu repos.

---

### Post by PokieCarlwin_is_borked on 2008-06-21
Ok you busted me and that's my next dilemma.  I dont know if it is appropiate here and I haven't yet found the correct forum to read, but I would like to upgrade to the newest version w/o lossing data & settings and I'm unsure how.  Suggestions??



Back to the hard drive
sudo mount -t ntfs-3g /dev/sdb1 /media/external

gives me

eek@ladybug:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.


BTW I'm doing this to back up my data so I can get off Feisty

---

### Post by Rocket2DMn on 2008-06-21
Do you have access to a windows machine?  I would do what it says if at all possible.  You may also be able to get it to mount by appending the force option to the mount command:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/external -o force
```
If you didn't use the drive with Vista, you can also try ntfsfix which is available in the ntfsprogs package
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```
Then try mounting again.

---

### Post by PokieCarlwin_is_borked on 2008-06-21
eek@ladybug:~$ sudo ntfsfix /dev/sdb1
Refusing to operate on read-write mounted device /dev/sdb1.


it is now a belief that instead of ntfsfix it maybe fat filesystem?  are you familar w/ this?  also when I plug it into a windows machine the drive doesn't even allow access to any of the files.   we attempted an atrib but I don't have that either??  little over my head scratch that way over my head

---

### Post by Rocket2DMn on 2008-06-21
It IS a NTFS drive, we could see that when we ran the fdisk command (post 10).  It sounds like the drive is a little messed up and probably needs to be replaced.  You said in your initial post that you tried different filesystems on the drive, but it never worked.  You can try formatting the drive again as something else (FAT32 works, but I've noticed some people have propblems automounting it).  If you don't use the drive with windows computers, ext3 would work.
If that doesn't work, I would replace the drive since it is not functioning correctly, so even if you managed to get it to work, it is unreliable as a backup source.

---

### Post by vanadium on 2008-06-22
You always need to unmount a drive before you can check it.

---

### Post by PokieCarlwin_is_borked on 2008-06-22
at this point I'd like to just reformat it and start from scratch.  The hardrive isn't a year old and hardly used by my dad on a windows machine.  i ran my fdisk program -d delete partitions1-4 and made a new one -n  and lastly -w  but when it came to 

mkfs.ext3

it wouldn't allow it:(

thank you all

---

### Post by Rocket2DMn on 2008-06-22
I suggest using GParted to format the drive, it is really easy.  It is available on the LiveCD, but you can also download it on your regular install
```
sudo apt-get instal gparted
```
Then go to System->Administration->Partition Editor.

---

