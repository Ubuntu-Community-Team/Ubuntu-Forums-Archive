---
title: "Permission HTFS/NTFS external hard drive"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by Pepito26 on 2011-11-10
Greetings, and thank you all for so many solutions I have never had to post for, until today.
 
 I can't change, copy, view or execute permissions for files in part of an HPFS/NTFS external drive.
 On the other hand it's possible to move or delete the same files, as  long as they stay on the HD (one partition, or id have tried moving to  see).
This only happens to files in one folder (7Gb "My Documents" from tower  iwanted to format - 'sheepish' smiley) ever since I recently backed it  up from an XP pack2/Ubu 9.10 AMD tower.

When browsing the files on XP, the names of blocked files are green, but  this has not affected ANY o.s. until i copied to this HPFS/NTFS disk.
Internet has shown me this has something to do with encryption, but  neither the HD, the tower, the Ubuntu laptop, nor the XP laptop have  ever had encrypted data.

I have tried the solution in a thread posted as "solved":
open GKSU Nautilus as root and change the permissions from there, but  the USER and GROUP options always change immediately back from the one  chosen to "root". (even tried disblocking options in the usersettings  whith Nautilus open in case it was relevant).
as well, the options regarding actual permissions revert to their original 

"create and delete files
-----
create and delete files
-----"

, as soon as i try to apply changes to all files or exit the properties.
(the "-----" are fields that revert to blank)

Impossible to change whether the file can be executed as a program or  any options next to "OTHERS"(just becomes 'grey', reverts to blanks  respectively  with the aforementioned conditions).

Ive tried moving the files instead of copying them, as the Web sez files inherit EFS settings upon *moving*. To no avail.

:confused::confused::confused:

have been investigating the whole day, but have come to the conclusion  this is not a highly documented phenomenon especially if you add that  antiviruses don't find anything and the green (easily visible only in  Win) titles of files and folders seem to spread like a virus but havent  infected any friend's computer.

Is there any way to *force*change any of these options?
Is it a problem that i don't access internet from any of the _mentioned_ computers, and haven't done so for perhaps more than six months?
Could this be work of a virus, or could i change this easily with some downloadable utility?
I'd really need to rescue the data for its sentimental value to me.

Thanks in advance for your time, let me know if this is the right way to  post (been reading you for years but never been desperate so am  technically brand new hopeful : )
... or if this excessively complete description is spamming you up, or if missing information.

---

### Post by mikewhatever on 2011-11-10
I'd recommend checking the filesystem. Since this is NTFS, use Windows XP, in 'My Computer', right click the drive, select 'Properties', 'Service' tab. You don't have to check for bad blocks, because it will take very long.

PS: Linux permissions don't work on NTFS or other none *nix filesystems.

---

### Post by Pepito26 on 2011-11-11
Thanks for prompt reply, will check said properties - although on Win side all 'visible' options have been checked and no access is permitted from XP or DOS.

Was hoping the effects seen were some bug Linux could workaround, but will keep eyes peeled and hopes up.

Back in a minute.

---

### Post by Mark Phelps on 2011-11-11
No access is permitted in Windows because those files are protected against access other than by the Windows account that created them.  That's how My Documents works in XP.

Windows doesn't have the Linux filesystem concept of execute permissions.  So, that's not going to work.

---

### Post by Pepito26 on 2011-11-11
Have checked for 'services' tab, no success. 
Never mind, ill keep trying with utilities until i find one that knows how to manipulate these permission, either in Dos or Linux.

Will post solution when i find one.

---

### Post by coffeecat on 2011-11-11
> **Pepito26 said:**
>  
Never mind, ill keep trying with utilities until i find one that knows how to manipulate these permission, either in Dos or Linux.

Mark Phelps has already mentioned why you can't change the permissions, but let me expand. NTFS is a Microsoft filesystem that does not support Linux permissions. When a NTFS filesystem is mounted in Linux, permissions are set globally for the whole fileystem by the mount options. You cannot change permissions for individual files. You can only change them for all files with the mount options. If you want to change permissions of individual files, you have to copy them to a Linux filesystem.

Are you mounting the external drive by letting it be automounted when it is plugged in? Plug the drive in and post the output of this terminal command:

```
mount
```

---

### Post by Pepito26 on 2011-11-11
> **Mark Phelps said:**
> No access is permitted in Windows because  those files are protected against access other than by the Windows  account that created them.  That's how My Documents works in XP.


This has never happened to me, and although I must admit itsa dubious  manipulation this copy-paste of 'My Docs', it has never produced  anything similar... remember, the access restrictions had spread around  files until i put them onto the USB HDD, but so few days have passed  since this problem arose, that i havent observed any more spreading.

Im rooting for a security in NTFS blocking the access to these files, or  that the HDD had some large part erased in one go, which causes  problems in HPFS apparently.

I dont really find much info online about this combined HPFS/NTFS fs.
Checking threads...

---

### Post by Pepito26 on 2011-11-11
Boy, am i daft.
Sorry guys for wasting time and posts without first mounting from the terminal.

Am on it.

---

### Post by Pepito26 on 2011-11-11
HDD is stuck in file verification process since i was suggested the 'right-click HDD, configurations options -- Services etc' potential solution.
And now im stuck on interrupting said process without killing it or creating error.
We may have to take a break until it finishes or reaches another prompt.
Have the feeling this cannot be solved through guindows; important to know that in my crosoft forum no solutions were found(apparently).

---

### Post by Pepito26 on 2011-11-11
Okay, got it out, plugged into Ubu laptop, mounted in terminal to find that the HPFS/NTFS fs is not supported by ntfs-3g. 
I there any other mounting utility for this, would fmount support a FS that ntfs-3g doesn't?

---

### Post by coffeecat on 2011-11-11
> **Pepito26 said:**
> Okay, got it out, plugged into Ubu laptop, mounted in terminal to find that the HPFS/NTFS fs is not supported by ntfs-3g. 

What do you mean? ntfs-3g is the standard userspace read-write driver for NTFS in Ubuntu. It works for me, and for everyone else.

If you mean there was an error message, it would be better if you posted it.

---

### Post by Pepito26 on 2011-11-11
Oops sorry here's that content:

   mount 
  /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) 
  tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) 
  proc on /proc type proc (rw,noexec,nosuid,nodev) 
  sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
  varrun on /var/run type tmpfs (rw,nosuid,mode=0755) 
  varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
  udev on /dev type tmpfs (rw,mode=0755) 
  tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) 
  devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) 
  fusectl on /sys/fs/fuse/connections type fusectl (rw) 
  lrm on /lib/modules/2.6.28-19-generic/volatile type tmpfs (rw,mode=755) 
  securityfs on /sys/kernel/security type securityfs (rw) 
  capifs on /dev/capi type capifs (rw,mode=0666) 
  binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
  gvfs-fuse-daemon on /home/dani/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dani) 
  /dev/sdb1 on /dev/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

---

### Post by Pepito26 on 2011-11-11
Feel like a bit of a dope...
PS ntfg-3g gave no error, but the partition did not mount but disappeared when i put in the terminal (before entering 'mount'):
sudo mount -t hpfs/ntfs *ID */dev/sda1

---

### Post by coffeecat on 2011-11-11
> **Pepito26 said:**
>   /dev/sdb1 on /dev/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

fuseblk is the ntfs-3g driver, but "/dev/sdb1 on /dev/sda1"? What on earth did you do to get that? I didn't think it was even possible.

Just to compare, this is the equivalent line when I plug in a NTFS USB drive and let it be automouted:

```
/dev/sdc1 on /media/Samsung80ntfs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

Mounted on a mountpoint in /media.

---

### Post by Pepito26 on 2011-11-11
I should restart the OS, no? Believe i messed up going 'faster than the music'.

---

### Post by Pepito26 on 2011-11-11
Yup i messed up putting that command line together.
Hope i dont get what a smartypants deserves.
Have restarted am trying more carfully now.

---

### Post by coffeecat on 2011-11-11
Just for the record. When mounting a NTFS drive from the terminal. Make a mountpoint:

```
sudo mkdir /media/mountpoint
```

Change "mountpoint" to whatever is suitable. Despite what you might read, it's perfectly OK to manually mount partitions to /media so long as you don't mount to /media itself and you create a sub-folder in /media for your mountpoint. Assuming the partitition you want to mount is /dev/sdb1:

```
sudo mount /dev/sdb1 /media/mountpoint
```

Don't bother with "-t ntfs". It works without. You can add "-o *options*" if you need to vary the defaults for special permissions.

Good luck with that.

---

### Post by Pepito26 on 2011-11-11
Thanks a million for your patience, will get on it in a few minutes.
Cheers!

---

### Post by Pepito26 on 2011-11-14
Greetings Ubuntuforums team,

Am back from weekend. Have had no success with the last potential solution posted.

Someone unsubsscribed me from the thread... Unexpected but good timing since on the weekend I dont generally have internet (at least as accessible), and i should have done so myself, before interrupting communications, no?

Back to work...

p.s.: if no Admin unsubsribed me from this thread, are there conditions that provoke unsubscription? Is it appropriate to subscribe to threads in general or is it a case of 'newbie spamming'?

---

### Post by Pepito26 on 2011-11-14
No success on manual mounting. 
Have created mountpoint with:
mkdir \media\htfsmount

and mounted manually with 
sudo mount \dev\sdb1 \media\htfsmount

(having checked for wether device is sdb1 2 etc)

Will keep trying.

Anybody know of linux utilities for manipulating DOS/Win-exclusive  characteristics?
Have got Xubuntu, Kubuntu, Guadalinex ready to install if it helps.
Will install any OS i need to in order to get this under control, if it  is useful.

---

### Post by Pepito26 on 2011-11-14
Have been trying all options in manual mounting. No success.

A colleague has told me fstab is important in mounting, but i dont  understand how you include in mount arguments, or what to write into the fstab file.

Another thread i about permissions, mounting, ntfs, FSTAB.
Reading around i see the key is in fstab when problems with permissions arise.

Will keep trying around, WILL POST when i get the issue underhand,
WILL POST the solution as SOLVED as soon as i get the data accessible.

---

### Post by Pepito26 on 2011-11-14
Never mind this useless thread, more problems appearing with FSTAB.
May be that although fstab HAS been used for various non-internal HW, it is not supposed to.
Am reinstalling Ubu.
Kill this thread if it its proper... will post when I run out of options with the fresh OS.

Bother you in a few days, thanks again for the pointers.

---

