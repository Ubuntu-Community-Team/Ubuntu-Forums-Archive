---
title: "HOWTO: Mount NTFS volumes with write support"
date: 2006-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by LKRaider on 2006-03-10
Please refer to this thread now: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

This guide is outdated since there is a new and better ntfs supporting driver now.

======================

**[COLOR="Red"]ATTENTION, OLD INSTRUCTIONS FOLLOW BELOW FOR REFERENCE ONLY! PREFER THE INSTRUCTIONS FOUND ON THE NEW THREAD:[/COLOR]**
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)


======================


[SIZE="1"]As initially posted on the Wiki: [https://wiki.ubuntu.com/Lkraider/NtfsFuse](https://wiki.ubuntu.com/Lkraider/NtfsFuse)[/SIZE]

*Initial Remark:*
**[COLOR="Red"][SIZE="3"]Warning!** Ntfs writing support is still experimental! You should not enable it on production machines and/or volumes you don't have backups of. Proceed at your own risk![/SIZE][/COLOR]
*End of Initial Remark.*

That being said, it is quite safe and if it fails to write something, will not corrupt your disk (unless there's a bug somewhere).

[COLOR="RoyalBlue"]**This initial part is for Breezy only, Dapper users already have the required packages**[/COLOR]
----
** I - Install the necessary dependencies**
[INDENT]
```
bash:~$ sudo apt-get install libfuse2 fuse-utils
```
[/INDENT]

** II - Get the latest ntfsprogs package**
[INDENT]
*Note: You will be downloading these directly from the Dapper repositories, so they are safe to install.*[LIST]
[*] [libntfs8]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-ntfs/libntfs8_1.12.1-1_i386.deb")
[*] [ntfsprogs]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-ntfs/ntfsprogs_1.12.1-1_i386.deb")
[*] [libfuse2]("http://archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.4.2-0ubuntu3_i386.deb")
[*] [fuse-utils]("http://archive.ubuntu.com/ubuntu/pool/universe/f/fuse/fuse-utils_2.4.2-0ubuntu3_i386.deb")
[/LIST]
[/INDENT]

** III - Install the downloaded packages**
[INDENT]
```
bash:~$ sudo dpkg -i libfuse2_*.deb fuse-utils_*.deb ntfsprogs_*.deb libntfs8_*.deb
```
[/INDENT]
----

[COLOR="RoyalBlue"]**Dapper and Breezy instructions from here on:**[/COLOR]
[SIZE="1"]Note: you can replace the "*gksudo gedit*" commands with your preferred editor (ex: "*sudo nano*", for instance)[/SIZE]

** 1 - Add fuse to the list of modules to load**
[INDENT]
```
bash:~$ echo fuse | sudo tee -a /etc/modules
```
[/INDENT]

** 2 - Create a user group to access the ntfs disks**
[INDENT]
```
bash:~$ sudo addgroup ntfs
```
The output should look something like this:
```

Adding group `ntfs' (1002)...
Done.

```
Take notice of your group GID (the number printed after the group name), as it can differ for you and we will need it.
[/INDENT]

** 3 - Edit the fstab file to mount the disks**
[INDENT]
Make a backup of your current settings:
```
bash:~$ sudo cp /etc/fstab /etc/fstab.bak
```
Edit the fstab file:
```
bash:~$ gksudo gedit /etc/fstab
```
Find the line that currently mounts your ntfs partitons, and change them to look like this:
```

/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1002,umask=0002    0    0

```
Notice the use of the group's GID from before, and the umask to allow write access just to owner (root) and group (ntfs), and read access to everyone.
You could also use an _umask=0007_ to block all access for users not on the ntfs group.
[/INDENT]

** 4 - Add users to the ntfs group**
[INDENT]
```
bash:~$ sudo adduser username ntfs
```
Where *username* stands for the user you whish to add (replace it with a real username). Do this for all the users you want to be able to write to ntfs disks.
[/INDENT]

** 5 - Fix Dapper [bug #29865]("https://launchpad.net/distros/ubuntu/+source/linux-ntfs/+bug/29865") of the linux-ntfs package:**
[INDENT]
```

bash:~$ sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

```
[/INDENT]

----

If you reboot now, the disk will be writable to the selected users when they logon.

If you want the changes to take effect immediately without rebooting, execute these commands:
```
bash:~$ sudo modprobe fuse && sudo umount -a && sudo mount -a
```
(Ignore errors about "/" and others not being unmounted, it doesn't matter)
You'll have to logout from all your user sessions for the new group to be acknowledged (usually a logout from your graphical session and login back again will do it).

**TROUBLESHOOT**
1) If you get this error:
```
Couldn't mount device '/dev/hda1': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.
```
You will have to boot into your Windows OS and do a "chkdsk /f" (aka. scandisk) on the partiton that you are trying to mount. Currently, ntfsprogs can't check/fix the integrity of the partitions and will refuse to mount them if they are marked as dirty (ie. needing to be checked), so you'll have to do it from Windows.

2) You can't access the ntfs partitions from Nautilus anymore from the computer:/// places. This is a bug of Nautilus I think. You'll get an error like this:
```
Unable to mount the selected volume mount: according to mtab, /dev/hda1 is already mounted on /media/hda1
```
A workaround is manually creating a link from the mountpoint to your desktop for easy access.


3) If you want to check whether you are in the ntfs group, type:
```
bash:~$ groups
```
it will output all groups the current user is in. Example:
```
username adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin ntfs
```

4) If you partition/format the NTFS drive in Linux then the System Volume Information folder is not created and you must run chkdsk on it in order for it to work correctly. ([as reported by glycerin](http://ubuntuforums.org/showthread.php?p=1248880))

---

### Post by SSamiK on 2006-03-11
Hit a snag when trying to mount a NTFS disk...

ntfsmount: error while loading shared libraries: libntfs.so.9: cannot open shared object file: No such file or directory

:-k

---

### Post by elsupermang on 2006-03-11
How fast is the read access compared to the read-only NTFS driver? I noticed with captive-ntfs the read access is way slower compared to the native linux NTFS driver

---

### Post by briancrutin on 2006-03-11
big help! thanks!:)

---

### Post by NMUrugbysteve on 2006-03-11
Thanks for the howto, i'm having some troubles though. I've done everything step by step, have write access as root, but my user can't access anything. Any ideas as to why?

---

### Post by elsupermang on 2006-03-11
you have to add users to your /etc/fstab like this:

/dev/hda1   /mnt/hda1 ntfs defaults,users,gid=users  0 0

you can then give the group read write and execute permissions

---

### Post by NMUrugbysteve on 2006-03-11
[QUOTE=elsupermang]you have to add users to your /etc/fstab like this:

/dev/hda1   /mnt/hda1 ntfs defaults,users,gid=users  0 0

you can then give the group read write and execute permissions[/QUOTE]

Wouldn't that completely defeat the purpose of making the ntfs user group?

---

### Post by muzaki on 2006-03-11
for a while ago i use captive from suse 10.0 which works great for writing on ntfs....
now i dont need it as i ve changed all my HD to fat
info on captive:

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

try it

---

### Post by Peacepunk on 2006-03-12
[QUOTE=SSamiK]Hit a snag when trying to mount a NTFS disk...

ntfsmount: error while loading shared libraries: libntfs.so.9: cannot open shared object file: No such file or directory

:-k[/QUOTE]

Same for me. I must add that anyway, I cannot even read hda1.

Nor can I change read permissions or ownership: readonly file.

:confused:

---

### Post by shinygerbil on 2006-03-12
I also cannot find libntfs.so.9 -  I assume this is a Breezy thing. Although a quick hunt shows me that Dapper has libntfs.so.8, so I may be wrong.

Still, I would love to be able to get write access on my NTFS partition. It has a buggered install of XP, but too much data which I cannot backup (30+ GB) for me to format. But if I can use it like a normal hard drive (or at least write to it), then I would feel much happier :P

If anyone feels like enlightening us on this problem, don't hesitate  :D 

Steve


EDIT -- Well as soon as I wrote this one of my housemates wandered in - and aftr a brief conversation he's lending me his 30GB iPod to sort the problem out. Oh well. :P Still, for other user it would be a very useful tool!

Steve

---

### Post by opticyclic on 2006-03-12
[QUOTE=SSamiK]Hit a snag when trying to mount a NTFS disk...

ntfsmount: error while loading shared libraries: libntfs.so.9: cannot open shared object file: No such file or directory

:-k[/QUOTE]
Unfortunately I hit the same snag. :(
I'm running Breezy too.

---

### Post by NMUrugbysteve on 2006-03-12
Ok, the fstab entry is where it's all going awry. When I use the ntfs mount command with my uid or the NTFS gid it'll mount. I just can't get it to mount read/write.

---

### Post by LKRaider on 2006-03-13
> missing libntfs.so.9 errors
Okay, there's a solution for that, and I will update the HowTo so people don't run into it again.

First, the [COLOR="Orange"]Cause[/COLOR]: the ntfsprogs-fuse package people were downloading require a ntfs library higher ( v.9 ) than the one avaiable for breezy ( v.5 ) or dapper ( v.8 ).

Now, the [COLOR="RoyalBlue"]Solution[/COLOR]: Get the Dapper packages:
[libntfs8](http://packages.ubuntulinux.org/dapper/libs/libntfs8)
[ntfsprogs](http://packages.ubuntulinux.org/dapper/otherosfs/ntfsprogs)

Before installing those, you'll want to remove the non-working one:
```
dpkg --remove ntfsprogs-fuse
```

Then, install the two Dapper packages:
```
dpkg -i libntfs8_1.12.1-1_i386.deb ntfsprogs_1.12.1-1_i386.deb
```


> fstab issues
Please, post your fstab contents, an output of "ls -l /media" (or where the mountpoint is, so we can see the current permissions), and the output of running the command "groups" as your regular user so we can try do identify the issues better.

---

### Post by NMUrugbysteve on 2006-03-13
I'm stuck booting into windows for a class, but when I get back on ubuntu I'll try to post all that. Another big thanks for this howto, even if I have to sudo into it, I've been messing with tons of files on my windows partition and it's still running fine.

---

### Post by NMUrugbysteve on 2006-03-14
Here's what ya asked for, hope it can help.

stephen@ubuntu:~$ ls -l /media
total 12
lrwxrwxrwx 1 root    root    6 2006-02-25 19:12 cdrom -> cdrom0
drwxr-xr-x 2 root    root 4096 2006-02-25 19:12 cdrom0
drwxrwx--- 1 stephen root 8192 2006-03-13 22:25 hda1
stephen@ubuntu:~$ groups
stephen adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin nvram ntfs

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    noatime,sync,errors=remount-ro,data=writeback 0       1
/dev/hda4       /home           ext3    noatime,sync,data=writeback    0       2
/dev/hda1    	/media/hda1	ntfs-fuse   	auto,gid=1001,umask=0007    0    0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by LKRaider on 2006-03-14
First of all, you are not using the ntfs group for controlling the access (which is ok, I'm just checking if you understand that).

> When I use the ntfs mount command with my uid or the NTFS gid it'll mount. I just can't get it to mount read/write.
The permissions clearly show it was mounted with r/w access for owner and group.
It shows it was mounted with UID:stephen and GID:root (and that differs from what is set on your fstab).

If you try writing a file when logged as user stephen, does it deny access? What kind of error is produced, if any?
( for example, run: dmesg > /media/hda1/my_dmesg_log.txt )

Just as comparison, here is how my ntfs part. is set:
```
drwxrwx--- 1 root ntfs 12288 2006-03-13 13:07 hda1
```
Now, my user is a member of ntfs group, and this gives him full access to the partition.

---

### Post by Mr. Polite on 2006-03-15
I wasn't quite able to get my Windows (C:) drive to mount. I'll post my fstab and the error later.

---

### Post by sawjew on 2006-03-16
I can mount fine as root using ntfsmount but when I try to mount from fstab I get 'mount: unknown filesystem type 'ntfs-fuse''. 

any ideas?

---

### Post by LKRaider on 2006-03-16
[QUOTE=sawjew]I can mount fine as root using ntfsmount but when I try to mount from fstab I get 'mount: unknown filesystem type 'ntfs-fuse''. 

any ideas?[/QUOTE]
Did you include the fuse module on the modules file?
Try running "modprobe fuse" and then "mount -a".

I can't think of anything else...

---

### Post by rantak on 2006-03-16
sudo mount -a

mount: unknown filesystem type 'ntfs-fuse'

I'm getting this too. I followed the directions correctly, fstab seems to be correct, modprobe didn't help. Ntfsmount as root is succesful
I also tried installing the deb's even though I'm using dapper.

edit: Also my ntfsprogs is version 1.12.1 and according to this page everything should be ok in fstab
[http://wiki.linux-ntfs.org/doku.php?id=ntfsmount]("http://wiki.linux-ntfs.org/doku.php?id=ntfsmount")

---

### Post by LKRaider on 2006-03-16
All I can ask is for you guys post your fstab entries... don't know what else could be missing and/or how to reproduce the issues here.

---

### Post by rantak on 2006-03-16
Here's my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0 1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/matrox   ntfs-fuse auto,gid=1002,umask=0007 0 0
/dev/hdb1       /media/samsung  vfat    iocharset=utf8,umask=000   0 0

I am in the ntfs group, /etc/modules has fuse, sudo modprobe fuse doesn't help.

$ sudo mount -a
mount: unknown filesystem type 'ntfs-fuse'

---

### Post by NMUrugbysteve on 2006-03-16
ok, i can't get the drive to mount under NTFS group without doing it by hand with ntfsmount. The reason that my last post said that i was the owner is that i forgot that i had already just done a ntfsmount command with my uid.

---

### Post by LKRaider on 2006-03-16
[SIZE="4"][COLOR=RED]**ATTENTION ALL PEOPLE WITH NTFS-FUSE UNKNOWN FILESYSTEM ERROR!**[/COLOR][/SIZE]
[SIZE="1"]*Did I grab your attention?*[/SIZE] :p

I forgot to mention that you must correct a file link (which is a [known bug](https://launchpad.net/distros/ubuntu/+source/linux-ntfs/+bug/29865) in Dapper package)... sorry! I corrected it here and forgot to include it in the tutorial!

Here's what you need to do:
```
sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
```

**NMUrugbysteve**: do this and check if you still have problems aswell.

I will be updating the How-To. Again, sorry for the incovenience...

---

### Post by sawjew on 2006-03-17
Thanks for that LKRaider,

I now have read/write access to my Windows partition but there is just one small item you may be able to help me with.

Is there any way to get the drive to show up on the desktop like drives normally do.  Also I cannot access it through Computer.  The drive shows up but when I click on the icon it says its not mounted although I can access it fine at /media/Windows with Nautilus.

I have tried mounting it as user in fstab rather than the ntfs group but it made no difference.

not a big deal because I do have access but if anyone knows how to do this I would appreciate it.

Steve

---

### Post by rantak on 2006-03-17
Thanks, I got the fstab ntfs-fuse working too.

I have also a small issue similar to sawjews that in Konqueror I get this error
message when trying to access the drive through media:/hda1 

Could not mount device
The reported error was:
mount: according to mtab, /dev/hda1 is already mounted on /media/matrox
mount failed

But I also can access the drive fine through /media/matrox so I doesn't really matter.

---

### Post by NMUrugbysteve on 2006-03-17
LKRaider, you rock my socks. That new link totally worked.

---

### Post by Mr. Polite on 2006-03-17
When I do:
michael@ubuntu:~$ sudo ntfsmount /dev/hda1 /media/hda1 -o umask=0007

I get:
```
fusermount: failed to access mountpoint /media/hda1: No such file or directory
fuse_mount failed.
Unmounting:
```

Here is the result of sudo fdisk -l
```
Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3589    28828611    7  HPFS/NTFS
/dev/hda2   *        3590        4943    10876005   83  Linux
/dev/hda3            4944        5005      498015    5  Extended
/dev/hda5            4944        5005      497983+  82  Linux swap / Solaris

Disk /dev/hdb: 4343 MB, 4343463936 bytes
255 heads, 63 sectors/track, 528 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         528     4241128+  83  Linux

Disk /dev/hdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           2       10011    80405325    f  W95 Ext'd (LBA)
/dev/hdd5               2       10011    80405293+   7  HPFS/NTFS
```

Any help is appreciated.

---

### Post by Mr. Polite on 2006-03-17
Nevermind. It took me reading my own post to realize the error.

---

### Post by LKRaider on 2006-03-17
[QUOTE=sawjew]Is there any way to get the drive to show up on the desktop like drives normally do. Also I cannot access it through Computer. The drive shows up but when I click on the icon it says its not mounted although I can access it fine at /media/Windows with Nautilus.[/QUOTE]

I am aware of this, and AFAIK it is a bug in the desktop support for ntfs-fuse (since I think it doesn't detect it correctly, as of yet).

A workaround is to create a link on the desktop to the folder where you are mounting to (and you can even change the icon to look like other HD's).
About linking it in Nautilus tho, I couldn't do it either. I'll post a bug report there. (edit: [bug #35354]("https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/35354"))

For KDE, I believe the situation is similar. You could try posting a bug report to the Konqueror package.

---

### Post by crshman on 2006-03-18
I followed all the instructions, i can mount and i can read however i cannot write.

My Error:
```

sudo dmesg > /media/hda1/my_dmesg_log.txt
bash: /media/hda1/my_dmesg_log.txt: Permission denied

```

Here is my fstab line:
```

/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1001,umask=0007    0    0

```

My group id:
```

sudo addgroup ntfs
Adding group `ntfs' (1001)...
Done.

```

any ideas as to what the problem is here?

---

### Post by LKRaider on 2006-03-18
Turns out the command was not correct. Try this:
```
sudo sh -c "dmesg > /media/hda1/my_dmesg_log.txt"
```

I've updated the How-To.

[COLOR="RoyalBlue"]Reasoning:[/COLOR] the shell assumes the output file (I/O redirection) to be the permissions of the regular user, ignoring the sudo command. Thus, I've corrected the command as a workaround for this issue.

---

### Post by Peacepunk on 2006-03-19
Hi all.

I used this technique successfully on my laptop - allright, my ntfs files are present. On the laptop.


So I felt confident with the Desktop... 

*[SIZE="3"] it does mount, appear on screen, and theeennn[/SIZE] *


                                               ...Well, I'm now stuck with good Ole'

> **The folder contents could not be displayed.**

You do not have the permissions necessary to view the contents of "hda5".

my **fdisk** list:

> /dev/hda5            1229        6092    39070048+   7  HPFS/NTFS  

my **fstab**:

> /dev/hda5       /media/hda5    ntfs-fuse auto,gid=1003,umask=0007   0    0 

my** ls /media -l**:

>  drwxrwx---   1 root root  4096 2006-02-26 17:57 hda5   

 - - Sure 1003 is the new id generated during the present tutorial - -
 - - Yes I did add the users to the ntfs group --
 - - I bet the ***1 root root*** up here should'nt look like this... --


[COLOR="Sienna"]
What did I missed ?[/COLOR]

---

### Post by Peacepunk on 2006-03-19
Can we get back to this part of the process ?

> 
Just as comparison, here is how my ntfs part. is set:
```
drwxrwx--- 1 root ntfs 12288 2006-03-13 13:07 hda1
```
Now, my user is a member of ntfs group, and this gives him full access to the partition.

How do you achieve that ?
[COLOR="DarkRed"][SIZE="2"][B]
Thanks.[/B][/SIZE][/COLOR]

---

### Post by LKRaider on 2006-03-19
Hmm, seems you need to restart the system first. Or just do this sequence of commands:

```
sudo umount /dev/hda5
sudo ntfsmount /dev/hda5 /media/hda5 -o gid=1003,umask=0007
ls -l /media
```

See if it is now with group ntfs set.

---

### Post by rogerly on 2006-03-19
I was able to mount my NTFS partition, but I did not have to remove the incorrect link as per your instructions.  I just had to create the link, and everything went fine.

Being able to edit the NTFS files helps me a lot.

---

### Post by dave84 on 2006-03-21
hi!

thank you for this great howto.
i've to make further tests, but it seems really working.

lg dave

---

### Post by LKRaider on 2006-03-21
I'll rework the How-To to simplify it (there are steps that can be streamlined and shortened).

Glad it's working for everyone.

---

### Post by sYs^ on 2006-03-22
Hi!

I can't delete some files , it writes: "Directory not empty. Delete it recursively?"
I say Yes.  Then "Cannot remove directory "blabla". Directory not empty (39)."

For examaple this dir:
```
dani@ubuntu:~/windows/c/bacsa/suli$ ls -all
total 0
drwxrwx--- 1 dani ntfs 0 2006-03-21 23:05 .
drwxrwx--- 1 dani ntfs 0 2006-03-21 23:05 ..
drwxrwx--- 1 dani ntfs 0 2006-03-21 23:05 Szakmai Gyakorlat
dani@ubuntu:~/windows/c/bacsa/suli$

```

My fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdd     /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/hdc1    /home/dani/windows/c    ntfs-fuse    auto,uid=1000,gid=1001,umask=0007    0    0
/dev/hdc4    /home/dani/windows/g    ntfs-fuse    auto,uid=1000,gid=1001,umask=0007    0    0
/dev/hdb1    /home/dani/windows/f    ntfs-fuse    auto,uid=1000,gid=1001,umask=0007    0    0
/dev/hda1    /home/dani/windows/d    ntfs-fuse    auto,uid=1000,gid=1001,umask=0007    0    0
/dev/fd0     /media/floppy0                       auto    rw,user,noauto  0       0

```

Thanks.

---

### Post by cyanideoverdose on 2006-03-22
Thanks.. Your howto really helped! (oh and my drives showed up on the gnome desktop right away.. maybe they fixed that problem?)

---

### Post by LKRaider on 2006-03-22
**_sYs^_**: You may be hitting a known [ntfsprogs limitation](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount#what_do_you_mean_by_this_will_either_succeed_or_it_will_be_refused), that is, it currently cannot delete/create on 100% of the requests.

Try deleting single files and see if it will succeed. If some work and others don't, then there's nothing to do other than wait for a newer version of ntfsprogs, I'm affraid.

---

### Post by sYs^ on 2006-03-22
ah , I see, thanks, are there any other way to write ntfs file systems?

---

### Post by LKRaider on 2006-03-22
Yes, you can use **Captive** (as suggested by [muzaki](http://ubuntuforums.org/showpost.php?p=814926&postcount=8) earlier).

I have not tested it, and it isn't in the Ubuntu repositories.
Check the website: [http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

It works by emulation of a windows enviroment and loading native MS libraries to access the ntfs disks (you'll have to get these libraries yourself, from your windows installation). It should work 100% of the time, as it is actually just emulating the part of windows itself that deals with ntfs access, and, as such, I would guess it is a bit slower.

---

### Post by sYs^ on 2006-03-22
Okey, thank you again, I'll wait a little, I hope they'll fix this bug or what :p

---

### Post by tuxcantfly on 2006-03-22
If anybody's experiencing trouble setting up fuse, check out:

[http://ubuntuforums.org/showthread.php?t=148359](http://ubuntuforums.org/showthread.php?t=148359)

---

### Post by mcwtlg on 2006-03-22
Wow, worked like a charm.  Followed your great tutorial and rebooted.  Fantastic.  That has fixed one of my problems dual booting!

I originally tried Captive, but it takes a very new kernel and Breezy just does not have it yet (I am too scared to try compiling my own :) ).

Thanx for the great how-to.:KS

---

### Post by akilamen on 2006-03-30
It seemed to work at first but I found out that I can only create new files or directories if I delete an existing one. What coul it be. Ntfs-progs limitation?

---

### Post by LKRaider on 2006-03-30
I would guess so, tho I don't really know for sure.

You could try informing the developers of your problems at the ntfsprogs [forums]("http://forum.linux-ntfs.org/"), [mailing-lists]("http://www.linux-ntfs.org/content/view/17/31/"), or even report a bug at the package [launchpad page]("https://launchpad.net/distros/ubuntu/+source/linux-ntfs/+bugs").

---

### Post by etherealbeats on 2006-03-30
Here's what i get:

```
paul@thumpa:~$ sudo modprobe fuse && sudo mount -a
fusermount: failed to access mountpoint /media/hda1: No such file or directory
fuse_mount failed.
Unmounting:

```


Here is my fstab in case it helps:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/hda1 ntfs-fuse auto,gid=1001,umask-0002 0 0
```

Thanks for your help, I'm supposed to be recovering a load of stuff on an NTFS drive for a customer. Don't know what I'd do without you guys.

---

### Post by LKRaider on 2006-03-30
As it says, you need to create the directory for mounting the drive to:
```
sudo mkdir /media/hda1
```

---

### Post by etherealbeats on 2006-03-30
Ok thanks, I hadn't done that.

Now I am getting this error though:

```
paul@thumpa:~$ sudo modprobe fuse && sudo mount -a
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting:
```


It also comes up as 'failed' when i start Ubuntu up as well.

---

### Post by LKRaider on 2006-03-31
On your fstab you have a typo:
```
umask-0002
```

should be:
```
umask=0002
```

---

### Post by GoBieN on 2006-03-31
thanks, works like a charm ;)

---

### Post by stairwayoflight on 2006-04-10
[QUOTE=LKRaider][SIZE="1"]

If you reboot now, the disk will be writable to the selected users when they logon. If you want the changes take effect imediatelly without rebooting, execute these commands and you're all set:
```
bash:~$ sudo modprobe fuse && sudo mount -a
```[/QUOTE]

hi thanks for the great tutorial!!! i love it!

one tiny quibble perhaps:
i did all instructions as req'd, but the "gksudo" commands didn't work for me.. i just used sudo and nano for an editor...
..also this command above did not allow me to properly write to the ntfs partition before reboot; i was frustrated until i realised that for some reason the ubuntu "users and groups" administration dialog from gnome recognized my user as part of the ntfs group, while if i typed "groups" with my user from the term, ntfs was definitely not listed.

perhaps you could add a comment about that situation in your tutorial?

(maybe it was just because i did what you said for ntfs to be available exclusively to the ntfs group-- "umask=0007" in fstab i think)

great howto!

---

### Post by LKRaider on 2006-04-10
Ooops, you are right about the group issue... you must logout and login back again to the group be acknowledged by the system.

I'll update the tutorial. Thanks for the report :)

About the gksudo... I don't know why it doesn't work... maybe you're using KDE?(don't know how it responds under KDE as I don't use it).
I prefer to use gksudo because it is more user-friendly than regular sudo... at least in Gnome.

---

### Post by djpate on 2006-04-10
hello,

I'm struggling with mounting the stuff.

here is what i got.

djpate@pepette:~/Desktop$ sudo modprobe fuse && sudo mount -a
Couldn't mount device '/dev/hda2': Opération non supportée
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.
Couldn't mount device '/dev/hdb1': Opération non supportée
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

---

### Post by LKRaider on 2006-04-10
Hmm, yes, that is a known issue of ntfsprogs. It cannot fix the filesystem yet (ala chkdsk on windows, or fsck on linux).

If it complains the disk was not shut down properly, you'll have to boot into Windows and run chkdsk (scandisk) on the drive to mark it as clean.

You can also try forcing the mount (read ntfsprogs help), but that is not advisable, since there may be filesystem inconsistencies which need to be fixed.

---

### Post by dom02 on 2006-04-13
another thing that might be important to mention is that when you create the user group the GID may not always be the same.  You say it's imporant but don't mention that it may be different.  This took me a while to realize.

---

### Post by RRS on 2006-04-13
I'm the sole user of my desktop. 

Do I really need to create a group and then add my user name to it for this or can I simply edit my current fstab line to mount hda1 with fuse?

Here's my current fstab entry;
/dev/hda1       /media/windows ntfs  nls=utf8,umask=0222 0    0

Though it lists "Root" as owner I can open it from the desktop and copy files to my fat32 while logged in as user. I'd like to write with similar ease.

Security is not an issue as I'm the only person with physical access to this computer.

Thanks.

---

### Post by domino on 2006-04-14
This how-to works fine in Breezy. In Dapper, ntfs mounts and I have w/r acces. However, drive icon doesn't show up on my desktop and I can not access the drive icon under "Computer". I have to browse to the "media" folder and access it.

---

### Post by sque on 2006-04-14
Yes it worked! :)
Thanx for this fine how-to and a numerous of problems that previous users reported and you replied a solution, they helped a looot.

The only problem is with icons on desktop and link in computer.
I am curious who did cyanideoverdose managed it?

[QUOTE=cyanideoverdose]Thanks.. Your howto really helped! (oh and my drives showed up on the gnome desktop right away.. maybe they fixed that problem?)[/QUOTE]

Dapper full updated user :)

---

### Post by pulsharc on 2006-04-16
> If it complains the disk was not shut down properly, you'll have to boot into Windows and run chkdsk (scandisk) on the drive to mark it as clean.

If you use hibernation in windows it will also give you this error, you just have to boot windows and shutdown normally instead of hibernate and you don't have to run chkdsk. Took me a while to figure out but it works great now! Thanks for the howto.

---

### Post by SSamiK on 2006-04-16
Finally! Read/Write to my NTFS partitions! Thanks for a great howto, it solved one of my biggest problems so far.

---

### Post by LKRaider on 2006-04-16
> **dom02]when you create the user group the GID may not always be the same.[/QUOTE]
I've updated the tutorial to better address this. Thanks for pointing it out.

[QUOTE=RRS]I'm the sole user of my desktop.
Do I really need to create a group and then add my user name to it for this or can I simply edit my current fstab line to mount hda1 with fuse?
[/QUOTE]
I am also the sole user of my desktop, and yes, you could do it without using the group assignment.
I used the group because:
[LIST=1]
[*]It is more secure
[*]Works for all kinds of users (single & multi)
[*]Gives you more options
[*]You learn more about Linux :)
[/LIST]

So, even for single-users, it will work fine, but if you want to configure without a group, you sure can too.

[QUOTE=domino and sque]Problem with icons on desktop and link in computer[/QUOTE]
I've [filled a bug report about this](https://launchpad.net/distros/ubuntu/+source/hal/+bug/35354), but it still remains unsolved. Seems the HAL doesn't recognize fuse mounted devices yet.
A workaround is to manually link the devices from the media folder to the desktop said:**
> shutdown normally instead of hibernate and you don't have to run chkdsk
That's great! Thanks for finding it out.
Maybe it is a bug of the ntfsprogs package? (I don't see a reason why a ntfs partition wouldn't be clean after hibernating?)

---

### Post by RRS on 2006-04-16
Finally went ahead and followed the rest of your(from step #3 on) instructions earlier today.

I had done the installation and configuring for fuse last week.

Since creating a group just for this one thing seemed like extra work I simply edited my fstab to add the fuse entry from your guide and left the other options as I already had them.
```
.......umask=000,uid=1000,gid=1000 0    0
```

Before doing this I unmounted my windows partition.I then rebooted rather then simply remounting.

During the boot process the mount showed a "failed" flag as the system loaded. When I tried to manually mount I was told the device was "damaged" and couldn't be mounted.

I restored the original fstab line:
```
/dev/hda1       /media/windows ntfs nls=utf8,umask=000,uid=1000,gid=1000 0    0

```

This allowed me to mount as before, user as owner with read and execute permissions so it apparently was something with fuse that detected the "damage"

I'm guessing at 2 possibilities;
A> I missed a step or performed one incorrectly, a combination of both seems most likely.
B> The reason I want to write into windows is that I managed to corrupt the boot.ini file and can no longer boot the system.

Could "B" be the damage fuse is seeing? As a recent entry (ultra newbie) to the world of computers, let alone Linux, I still lean towards "A".

Sorry for the long post but I've been studying your directions and the Q & A's from others in the thread and haven't found anything similar to my problem.

Thanks for your patience and hopefully you can get me pointed in the right direction.

---

### Post by gant1979 on 2006-04-16
Hello all. I to have problems mounting my ntfs drive with write support in Dapper Drake. There is no problem when I mount it with read-only. I get a fail message in the boot process when I try to mount it with write support: "Couldn't mount /dev/sda1, operation not supported.

This is my fstab:

/dev/sda1    /media/windows ntfs-fuse    auto,gid=1001,umask=0002    0    0

I have all the required latest packages installed, the ntfs group is 1001, my username belongs in this group and fuse is in /etc/modules.

I can't seem to find the solution. Could it be that the ntfs drive that I want to mount is a sata drive?

---

### Post by gant1979 on 2006-04-17
Hmmm Ive fixed it. I to had the same message to check and shutdown properly the windows disk. I now have write and read access but I can't delete!! If I get this correctly it is a bug of ntfsprogs ?

EDIT: Ive noticed that it lets me copy files a limited amount of files to the ntfs drive, usually 5-6. After that I get the error message: 

cp: cannot create regular file "filename": Operation not supported.

Any suggestions???

---

### Post by cooperaa on 2006-04-18
Wow this is way more difficult than it should be!  I've worked through all sorts of problems thanks to this great thread, but now I'm stuck.

I am able to run "sudo modprobe fuse && sudo mount -a" and everything seems fine, my SATA NTFS partition (double hell) even mounts!  The problem is that there is nothing in the drive!  No contents!  And it seems to think that it is a 8 GB partition with 4 GB used - when in actualit it is a 250 GB partition with probably 180 GB used.

Here's my /etc/fstab:
```
/dev/sda1 /media/music ntfs-fuse auto,gid=1001,umask=0002 0 0
```

Any ideas?

---

### Post by cooperaa on 2006-04-19
I can't believe what I was doing wrong...  I was looking in /home/music (a directory I had created for my music drive) and do you notice where I'm telling the drive to mount in /etc/fstab?  Yeah, in mount/music...

For some reason I can't write to the drive.  Does anyone notice any glaring mistakes with my fstab?

---

### Post by domino on 2006-04-19
[QUOTE=LKRaider]Seems the HAL doesn't recognize fuse mounted devices yet.
A workaround is to manually link the devices from the media folder to the desktop; but I don't know a workaround for the Nautilus 'computer' place, unfortunatelly.
[/QUOTE]
It kind of gets me wondering why HAL doesn't recognize fuse. You already pointed out that the current kernel already implements the feature.

I also added a link pointing to the mounted ntfs directory in Nautilus bookmarks. It should also show up when browsing to open files.

---

### Post by -ColdFire- on 2006-04-20
Can I mount a NTFS HDD with a live cd? If so, HOW??

---

### Post by Master Dwarf on 2006-04-21
How does this work with a removable HD?  I followed all the instructions and then realized my fstab depicted hda vs sda so I changed it to the following:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sda1    /media/sda1    ntfs-fuse    auto,gid=1001,umask=0002    0    0

I remmed it out because it wouldn't mount at all.  To sum it up, I have a removable USB drive. I can mount it no problem but it only has read & execute permissions.  It says that its a 'read only disk' if I try to give it write permissions.

ls -l /media:
> skelley@dwarf:~$ ls -l /media
total 24
lrwxrwxrwx  1 root    root        6 2006-03-13 15:51 cdrom -> cdrom0
drwxr-xr-x  2 root    root     4096 2006-03-13 15:51 cdrom0
lrwxrwxrwx  1 root    root        7 2006-03-13 15:51 floppy -> floppy0
drwxr-xr-x  2 root    root     4096 2006-03-13 15:51 floppy0
dr-x------  1 skelley skelley 16384 2006-04-11 21:31 sda1


Does this go back to [this issue]("http://www.ubuntuforums.org/showpost.php?p=824574&postcount=16") since root is not mounting it?

---

### Post by dragonfyre13 on 2006-04-22
[QUOTE=muzaki]for a while ago i use captive from suse 10.0 which works great for writing on ntfs....
now i dont need it as i ve changed all my HD to fat
info on captive:

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

try it[/QUOTE]
 Was using that on Ubuntu for a while, but it continually gives weird bugs and errors on Debian based systems in my experience. This, however, works like a charm. Thanks!

---

### Post by guitaristz on 2006-04-22
Hi, new user here- like 2 days. I figured out how to enter those command lines in Terminal. Pasting in the right code I can handle.  hda5 is the NTFS partition I'm trying to fully access. I'm sorry but I don't understand the following:

 1 - Add fuse to the list of modules to load

Code:

    bash:~$ gksudo gedit /etc/modules

    Make a new line and write fuse there. Example:
    Code:

# /etc/modules: kernel modules to load at boot time. 
#
 # This file contains the names of kernel modules that should be loaded # at boot time, one per line. Lines beginning with "#" are ignored.
floppy 
nvidia 
fuse

So, ah, can you guys make it any easier? Why the # signs? Unbutu rocks killingly.
Bu you guys really know what you're doing, Thanks, eh.

---

### Post by imtezcan on 2006-04-23
Hello everyone,
I installed ntfsprogs today and it works great (i even fixed a partioning problem which norton disk doctor had caused :P)

Well my question is:
How are we supposed to mount ntfs drives with utf8 support?
I tried iocharset=utf8 which works fine with the kernel driver, and nls=utf8 which I have seen in some forums (I don't know what nls is), but they didn't work (it says invalid argument when I try to mount with mount -a )
Then I added in fstab the "locale=utf8" or "locale=iso8859-9" (locale for turkish alphabet) and when I mount with mount -a it says:

**Failed to set locale to iso8859-9.  Continue anyway.**

and, well, it continues anyway and it works! But how? Why? What is that "failed to set locale" warning? And if it has failed, how does it work at all? I can see the turkish-named folders and write to the drive without any problems after that.
Am I doing something wrong or is it just a weird warning that I should ignore?

---

### Post by LKRaider on 2006-04-27
Sorry, I've been away for a while. I'll try to answer what I can.

**imtezcan:** about locale support, I too use it (pt-BR here). Set the locale in fstab like this:
1- Type in a terminal:
```
set | grep LANG
```
It will output something like:
```

GDM_LANG=pt_BR.UTF-8
LANG=pt_BR.UTF-8
LANGUAGE=pt_BR.UTF-8

```
Just copy the part that reads "pt_BR.UTF-8" into your fstab locale setting. Ex:
```
/dev/hda1     /media/hda1     ntfs-fuse       auto,gid=1002,umask=0007,succeed_chmod,locale=pt_BR.UTF-8 0       0

```

**Master Dwarf:** I can't say how it would differ for a removable HD. I would guess it should work all the same. I don't understand the 'read only disk' error. Could you do a step by step which causes this? And how and where exactly the error message appears?

**-ColdFire-:** Yes, you can. I did it on a Knoppix Live session without problems. I would guess it should work for Ubuntu Live aswell.
For a live session, I would recommend not using the group assignment, but instead allow everyone read+write access, since it will then require no changes to the user permissions, and since you are running live, the security risk is minimal.
Just do a ntfsmount with umask=000 and you should be done to use the ntfs drives.

**cooperaa:** What error does it gives when you try to write?

**gant1979:** You are hitting a ntfsprogs limitation. Check the ntfsprogs page to read more about it.

EDIT:
**guitaristz:** I simplified that step on the HowTo. Thanks for reporting.

---

### Post by Dearhell on 2006-04-28
I have followed step by step this how-to, but when I reboot or make:

```
modprobe fuse && sudo umount -a && sudo mount -a
```

I get this:

```
umount: /dev: bussy device
umount: /: bussy device

```

My fstab line:

```
/dev/sda1	/media/sda1	ntfs-fuse	auto,gid=1002,umask=0002	0	
```

But, if i mount the windows ntfs partition manually with read access like this:

```
mount /dev/sda1 /media/sda1/ -t ntfs
```

It works fine, but obviously I only have read access in this way.

All the steps were made with root privileges.

---

### Post by Master Dwarf on 2006-04-28
I'll mount the disk:
Places->Computer
Right click 149.0 GB Volume->Mount

The volume is mounted and icon is produced upon the desktop.
Right click icon on desktop->Properties->Permissions Tab

It displays the dirve with Read & Execute only.  If I try to check the 'Write' permissions or change the file group it gives me a popup box with the following message:

[COLOR="Red"]Couldn't change the permissions of "sda1" because it is on a read-only disk[/COLOR]

It says the file group is skelley and that I am not the owner so I can't change these permissions.

---

### Post by SiMoNsAyS on 2006-04-28
just thanks. working perfectly here ;)

1 thing, i didn't added my user to ntfs group so only root can read/write while user can just read, should be added as a tip to minimize corruption possibilities :)

---

### Post by morequarky on 2006-04-30
Help.

I installed Breezy recently.  I reinstalled Breezy recently.  Recently, I installed XP then following that I installed Breezy in another partition of the same harddrive. Dual booting is a piece of cake.

When I logged in I had "hda1" drive on my desktop with no access to anything on it.  Gave me errors everytime I tried to access it. No read, no nothin'; blank file window.

I ran all the commands with copy and paste from the beginning of this thread.
(edit: I only ran the directions in the first post, I need to add gid=??? to that file)

The drive file on my disktop disappeared after a reboot/relog.
Now "sudo" command gives me "errors" in reference to "read-only file system"
I can't "mkdir /???/windows" for the same reason.

What did I do wrong?  I am in a hurry so I am sorry if you don't understand my post or how to help me. Did I miss something?  (I always search the forum for relative threads)

My goal in trying to access NTFS was solely to back up windows so I can unzip it into another computers partition.

Thanks.

---

### Post by morequarky on 2006-04-30
I have done everything on this thread, probably in the wrong order, and everything on my computer now seems messed up.

NTFS does not mount at all.

@nikola:~$ sudo ntfsmount /media/hda1 /media/hda1 -o gid=1001,umask=0007
Use the force option to work with files.
Mount failed.

 ls -l /media
total 12
lrwxrwxrwx  1 root root    6 2006-04-27 17:56 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-04-27 17:56 cdrom0
lrwxrwxrwx  1 root root    7 2006-04-27 17:56 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2006-04-27 17:56 floppy0
drwxr-xr-x  2 root root 4096 2006-05-01 00:00 hda1

hda1 is the NTFS partition

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       /home           ext3    defaults        0       2
#/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /tmp            ext3    defaults        0       2
/dev/hda6       /usr            ext3    defaults        0       2
/dev/hda7       /var            ext3    defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/hda1	ntfs-fuse    auto,gid=1001,umask=0002    0    0

I have done everything and I know this information above is wrong.  cause it doesn't work.  I even installed fuse from the dapper packages and now when I boot my computer the "PCI" module fails along with the "filesystem" module.

frustrated.  I love ubuntu and I have had no trouble with previous HowTo's.  This one is giving me a headache.

Help!!

---

### Post by _linux_ on 2006-04-30
Thanks! I think I'll try it. It might come in handy sometime.....

---

### Post by PopcornEaterMan on 2006-04-30
II - Get the latest ntfsprogs package


    Note: You will be downloading these directly from the Dapper repositories, so they are safe to install.

        * libntfs8
        * ntfsprogs
        * libfuse2
        * fuse-utils

=========================
I clicked on the link... what am I supposed to do afterwards to get these files installed?  Firefox suggested that I open the link with the default, and I did that.  I'm not sure what I'm supposed to do next.  Are the files installer files?  Where do they go?  Sorry, new to this.

---

### Post by nszabolcs on 2006-05-01
use add/remove applications or synaptic package manager or aptitude or apt-get install etc.
select and install the listed packages

---

### Post by YaNoS on 2006-05-01
I'm sorry for asking such a stupid question, but how do I know if my device is hda1, hd0..?
Windows is in the same HD as Ubuntu, different patitions.
Also, I only have one SATA HD.

---

### Post by morequarky on 2006-05-01
YaNos,

If you installed windows first and then ubuntu and can dual boot with no problems then reading "sudo gedit /etc/fstab" might tell you which is ntfs.

Also there is a "fdisk" command in this thread somewhere I think that will also tell you all your partitions and what ubuntu has them named as.  I can't remember off hand what the command was.

---

### Post by YaNoS on 2006-05-01
Thanks a lot, morequarky

my fstab(changed it following the tutorial) is like

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda0    /media/hda0    ntfs-fuse    auto,gid=1001,umask=0002    0    0 <-- line added accordinly to the tut

I guess i've done something wrong there?

---

### Post by morequarky on 2006-05-02
I have issues with my ntfs too.  Here is what I did today.

I reinstalled Breezy.  After installing hda1 is automatically on my desktop.  But when I click on it, it says I can't access it.  I go to "System - Administration - Disks"  in disk I look at the hda1 (the ntfs partition).  There is a browse button.  I click it and it allows me to browse windows no problem.  I can't "write" to it, but I will work on that later.

I am going to try to stay away from Dapper until it is finished.  Breezy is fine with me.

---

### Post by jdackle on 2006-05-03
[QUOTE=YaNoS]Thanks a lot, morequarky

my fstab(changed it following the tutorial) is like

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda0    /media/hda0    ntfs-fuse    auto,gid=1001,umask=0002    0    0 <-- line added accordinly to the tut

I guess i've done something wrong there?[/QUOTE]

Well, it does seem you did do something wrong! I take it you have edited you /etc/fstab file yourself in the past...?
The thing that puzzles me in your file is the "/dev/hda0" use in there, particular the zero(0) after hda!

In Linux systems, "hda" stands for the first physical IDE hard-disk in your system, "hdb" for the second and so on...
"hda1" is the first partition in the first physical hard-disk, "hda2" the second partition and so on...

"hda0" is for the disk-descriptor/partitions-table/MBR or the like, which you are NOT supposed to mount!!!
So you obviously have something wrong there! Your ntfs would most certainly be located in "hda1"... BUT... your root Linux partition seems to be in "sda2" (a SCSI disk?), not "hda2"... So unless you have two disks (one IDE and one SCSI), your NTFS partition should probably be "sda1"...

I know this is far from all-the-info-you-need, but I think you might be able to figure it out by yourself with these directions...
It is quite safe to play around with your (un)mounted non-root partitions - just as long as you keep your root partition line intact, providing it is currently working - in your system that's the line starting with "/dev/sda2" and marked by the root-mountpoint ("/")... ;)

---

### Post by jdackle on 2006-05-03
@ morequarky:

You must be trying to access your NTFS partition as a regular user, without administrative priviledges.

What happens when use the "Disks" application is you get asked for your password so that you do get those priviledges...
You can do the same by invoking nautilus from a command-line as such:```
gksudo nautilus
``` and then browse to your Windows folder.

Another way around it is to give access to your NTFS to all users, by adding the option "umask=0002" to your ntfs line in /etc/fstab. My /etc/fstab looks like this:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1       /windows        ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /windows    ntfs-fuse    auto,gid=1001,umask=0002    0    0

```
This way, you can just go to that partition without priviledges, using no-matter what program, without being asked a thing... ;)

---

### Post by pkbarber on 2006-05-03
This doesnt work for me... what with that?
```
sudo dpkg -i libfuse2_*.deb fuse-utils_*.deb ntfsprogs_*.deb libntfs8_*.deb

```

I get this when I try
```
pkb@LinuxBox:~$ sudo dpkg -i libfuse2_*.deb fuse-utils_*.deb ntfsprogs_*.deb libntfs8_*.deb
dpkg: error processing libfuse2_*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fuse-utils_*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing ntfsprogs_*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing libntfs8_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libfuse2_*.deb
 fuse-utils_*.deb
 ntfsprogs_*.deb
 libntfs8_*.deb


```

---

### Post by pkbarber on 2006-05-04
Now I cant access either drive.  
My drives arent even accessable.
```

total 8
lrwxrwxrwx  1 root root    6 2006-04-25 17:15 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-04-25 17:15 cdrom0
lrwxrwxrwx  1 root root    7 2006-04-25 17:15 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2006-04-25 17:15 floppy0

```

```

df
/dev/hda1              9408480   2344040   6586508  27% /
tmpfs                   160900         0    160900   0% /dev/shm
tmpfs                   160900     12588    148312   8% /lib/modules/2.6.12-10-386/volatile


```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

```

sudo fdisk -l
Disk /dev/hda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1190     9558643+  83  Linux
/dev/hda2            1191        1245      441787+   5  Extended
/dev/hda5            1191        1245      441756   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241    7  HPFS/NTFS
```

PS The floppy isnt plugged in so I dont know why its there.

---

### Post by morequarky on 2006-05-04
@jdackle:

Just to clearify something before I work on this again.

The output of my fstab you are refuring to was before I reinstalled.  After reinstalling I was able to read through "disk".

I will try to change fstab again and see if that is all it takes to get read and write working.

Thanks.  I'll post any results.

---

### Post by jdackle on 2006-05-04
@ morequarky:
Erm... I hadn't even looked at that post of yours (the one with the output from your fstab)! :D

I was just replying to this one:
[QUOTE=morequarky]I have issues with my ntfs too.  Here is what I did today.

I reinstalled Breezy.  After installing hda1 is automatically on my desktop.  But when I click on it, it says I can't access it.  I go to "System - Administration - Disks"  in disk I look at the hda1 (the ntfs partition).  There is a browse button.  I click it and it allows me to browse windows no problem.  I can't "write" to it, but I will work on that later.

I am going to try to stay away from Dapper until it is finished.  Breezy is fine with me.[/QUOTE]

Cheers!

---

### Post by LKRaider on 2006-05-04
@**pkbarber**: I don't know what you are expecting, but your configuration files are a mess, so of course you can't access the disk.

First of all, your fstab includes no mention of mounting a ntfs partition. Also, it mounts hdc as a cdrom drive, which it isn't (just look at the fdisk output).

I don't know which tutorial you were following, but sure wasn't this one.

Sorry, but this isn't a general fstab/mountig/fdisk/linux support thread. It's okay to ask for help, but be sure you actually *read* the tutorial and *_understand_* what you are doing.

---

I think that maybe I should include a notice that people that don't understand the limits and extents of the ntfsprogs package, should stay away from this guide. It wasn't intended for every linux newbee to access NTFS partitions with write privileges with full functionality, since ntfsprogs is still in testing and far from being completely compatible with this filesystem. Be sure to read the [ntfsprogs page]("http://www.linux-ntfs.org") for complete details of it's current development stage.

---

### Post by Dearhell on 2006-05-05
[QUOTE=Dearhell]I have followed step by step this how-to, but when I reboot or make:

```
modprobe fuse && sudo umount -a && sudo mount -a
```

I get this:

```
umount: /dev: bussy device
umount: /: bussy device

```

My fstab line:

```
/dev/sda1	/media/sda1	ntfs-fuse	auto,gid=1002,umask=0002	0	
```

But, if i mount the windows ntfs partition manually with read access like this:

```
mount /dev/sda1 /media/sda1/ -t ntfs
```

It works fine, but obviously I only have read access in this way.

All the steps were made with root privileges.[/QUOTE]

Any idea about this?

---

### Post by pkbarber on 2006-05-05
@LKRaider
I will immeditatly conceed im a newb.  However I followed the tutorial to the T, allowing for user specific commands.  I was having system wide issues with 5.10: networking problems as well as other driver issues.  I have since switched to the beta of drake to see if i could solve some of these probs.  Some of the issues have been resolved but not all of them.  Bottom line, I still dont have access to my master hd.  Even prior to attempting to mount the ntfs drive in drake there are errors in my fstab file.  I have to assume that with a clean install of both OSs with persisting problems that there is a problem with the hardware.  ie jumpers, bios settings, etc.

---

### Post by maruchan on 2006-05-05
**Big note:**

If you are a Dapper user and have problems with this command in step 5:

> bash:~$ sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

...please go back to the Breezy section and make sure you have *all* these packages installed:

libntfs8
ntfsprogs
libfuse2
fuse-utils

I upgraded to Dapper from Breezy and I'm not sure how, but I was missing a couple of those packages. I installed them from Synaptic and everything worked.

---

### Post by LKRaider on 2006-05-07
**Dearhell:** Don't worry about the 'busy device' warning, it is just saying it won't unmount the root filesystem. Check the directory where you pointed to mount the ntfs partition, it should be there and working.

---

### Post by moneylosr20 on 2006-05-14
I've tried following this tutorial and others for mounting NTFS, and while I can read the NTFS partition on my hard drive, I can't write to it. The tutorial in ubuntuguide.org lets me read the NTFS partition, but when I try to configure /etc/fstab according to the HOWTO in this thread, I'm not able to read or write to the partition, as the icon to the NTFS partition is gone, preventing me from accessing it. Any ideas as to why this is happening?

Sorry for the seemingly dumb question:-?

---

### Post by rubengs on 2006-05-15
I'm getting this while I try to mount manually or by fstab my windows partition: 

```

Couldn't mount device '/dev/hda1': Invalid argument
Mount failed.
```

I'm in dapper and have already made the bug fix mentioned before, my fstab is: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdg8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdg5       /home           ext3    defaults        0       2
/dev/hda1    /media/hda1    ntfs-fuse   auto,gid=1002,umask=0002    0    0
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hde1       /media/hde1     ext3    defaults        0       2
/dev/hdf1       /media/hdf1     ext3    defaults        0       2
/dev/hdg6       /media/hdg6     ext3    defaults        0       2
/dev/hdg9       /media/hdg9     ext3    defaults        0       2
/dev/sda1       /media/sda1     ext3    defaults        0       2
/dev/sdb1       /media/sdb1     ext3    defaults        0       2
/dev/hdg7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by gasull on 2006-05-16
[QUOTE=LKRaider][SIZE="1"]As initially posted on the Wiki: [https://wiki.ubuntu.com/Lkraider/NtfsFuse](https://wiki.ubuntu.com/Lkraider/NtfsFuse)[/SIZE]
** 3 - Edit the fstab file to mount the disks**
[INDENT]
```
bash:~$ gksudo gedit /etc/fstab
```
Add a line like this:
```

/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1002,umask=0002    0    0

```[/INDENT]
[/QUOTE]
If you want to read/write, use this line instead:
```

/dev/hda1 /mnt/c ntfs-fuse fmask=0111,dmask=0,succeed_chmod 0 0

```
[SIZE="1"]Ref: [http://wiki.linux-ntfs.org/doku.php?id=ntfsmount#mounting_via_fstab_in_1.12.1_and_later](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount#mounting_via_fstab_in_1.12.1_and_later)[/SIZE]

---

### Post by IainT on 2006-05-16
This seems the appropriate thread to ask - how safe is this generally considered to be?

I did an install on an 80gb drive with 50gb NTFS and 30 ext3. Didn't bother with an FAT32 partition, which was probably stupid. I'm not in any way pushed for space, but it would be nice to write video and music files to the XP partition as I'm using Ubuntu 95% of the time now.

I don't want to fall victim to endless tinkering with what is essentially working and ending up with it all broken.

---

### Post by l4v4_f10w on 2006-05-22
nice one LKRAIDER, after doing chkdsk within my windows system it fixed allthe problems, cheers mate.

---

### Post by brallan on 2006-05-24
Does anyone know how the autodetect/automount for USB drives works enough to modify it so that ntfs drives are hot-mounted (dynamically) without needing an fstab entry? The problem with fstab is that is really best suited to permanent drives.

Write support for NTFS is fantastic, a great breakthrough for linux users. thanks to [those heroes ]("http://www.linux-ntfs.org")who reverse engineered and thanks to all who contribute!

brian

---

### Post by hsn on 2006-05-27
I cant seen to download: 
# libfuse2
# fuse-utils

Files cannot be found on the server? Is there any place else I can download them from?

Thx.

---

### Post by hsn on 2006-05-28
Bump? ](*,) 

:-k

---

### Post by LKRaider on 2006-05-30
I fixed the links on the first post, as the packages were updated.

Whenever you need a package from any ubuntu version, you can search for it at [http://packages.ubuntu.com](http://packages.ubuntu.com) .

---

### Post by hsn on 2006-05-31
Thank you.

I have a big problem. I followed the instructions, then I used the command to make it work immediately, and I forgot to log-out first. I tried opening a map but it just disapeared. Then I rebooted the machine, and all files are gone now. It says 8.1gb drive. But it's a partition above 130gb. :confused:

---

### Post by johnbl on 2006-06-02
Thank you for the how to. Worked though at all ' appeared ' to work. ntfs Group exists and user is member. Now I'm a newbie so sorry if this sounds stupid but what now. I STILL can't see the contents of the ntfs partions.. Mind you I do have an error on boot - " mounting kocal file systems FAILED " only reference I have been able to find to this message is in German thread however,,, in dark here.

---

### Post by joshyf on 2006-06-02
works great for me, yay!! read write with ntfs on linux, what could be better?!

---

### Post by Rudy507 on 2006-06-04
When I get to the part about doing > sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

I get the following error:
rm: cannot remove `/sbin/mount.ntfs-fuse': No such file or directory

Everything worked perfectly up until this point. I tried rebooting anyway just to see if it worked, and of course it didn't.

Thanks,
David

---

### Post by rodrigo666 on 2006-06-07
Someone could rewritte this article with a more easy understandable text?

It's not newby friend and I could not do it.

I'm using Dapper Drake and managed to install all of the apps throught the Synaptic Package Manager. But could not writte on my NTFS partition.

I kindly ask, also, to whoever writte this future article make it, if possible, in a way that do not need to create a "NTFS writte permission group", but in a way where every user can writte on it.

---

### Post by wyk on 2006-06-08
on 6.06
2Rudy507, i found that there is no /sbin/mount.ntfs-fuse file, but there is /sbin/mount.ntfs-fu. i renamed it and aded "se". after run the 
sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

now it should work just fine.

---

### Post by realjose on 2006-06-13
Perhaps a stupid question, but I've got one of them external ntfs disks. Is it possible to make drake use fuse to mount such a disk?

Cheers

---

### Post by nbv4 on 2006-06-14
I have all the packages installed and they are all up to date.

I have fuse listed in the modules file.

This is my fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    	/media/hda1   	ntfs-fuse    auto,gid=1001,umask=0002    0    0

```

the ntfs group has my user name as one of it's members and I made sure the guid is the same.

I also ran that bugfix posted at the bottom of the OP. 

When I reboot, nothing appears in /media/hda1.

This very ame drive I had mounted in /stuff using the default ntfs read only support. Even though that entry has been removed from the fstab, /stuff remains part of my filesystem. Whats going on here?

---

### Post by JohanSwe on 2006-06-14
[QUOTE=wyk]on 6.06
2Rudy507, i found that there is no /sbin/mount.ntfs-fuse file, but there is /sbin/mount.ntfs-fu. i renamed it and aded "se". after run the 
sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

now it should work just fine.[/QUOTE]
The command:
sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
didn't work for me. I got the message that /sbin/mount.ntfs-fuse didn't exist.
In nautilus I then looked for the /usr/bin/ntfsmount file but couldn't find that one neither.

I have restarted my computer but the ntfs partition was not mounted. Then I checked if I had the mentioned packeges but couldn't found 
# libntfs8
# ntfsprogs
# libfuse2
so I installed them.

I have a clean dapper install 

All help would be highly aprociated :)

---

### Post by roytobin on 2006-06-14
How to assure the necessary "fuse" module is loaded into the kernel.

 % /sbin/modprobe -l | /bin/grep fuse
/lib/modules/2.6.15-23-386/kernel/fs/fuse/fuse.ko

If you don't see this pipe return a line like the one above that contains fuse, you don't yet have fuse loaded into the kernel.  As the instructions state, this new dynamically loaded piece of the kernel must be present to mount a 'ntfs-fuse' type filesystem.  You need to either a) reboot or b) execute the modeprobe command as root as the original post states.
Both options, of course, are after you have followed the procedures in the original post already.

Depending on your font, please know the lowercase "el"
character (for "list") is passed to the modprobe program in the above example, and the vertical bar symbol (aka pipe symbol) follows.

The instructions were good enough to get me going on
% uname -a
Linux ldt-sdoa-004 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Dapper system without any troubles and with gratitude.

---

### Post by roytobin on 2006-06-14
The instructions to add this line to /etc/fstab:
/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1002,umask=0002    0    0

presume /dev/hda1 has a ntfs filesystem.  Certainly on
my setup, this was the case, but I don't know if it is true for everybody.  Perhaps it is the case for Windows OSes that use the NTFS filesystem *must* be on the first partition?

For me, upon install, Dapper recognized that /dev/hda1 had a valid ntfs filesystem on it, and it automatically put this into the /etc/fstab:

/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Note the filesystem type is "ntfs" and not "ntfs-fuse"
This "ntfs" calls out the standard, read-only driver to access the Windows NTFS filesystem.  This is the driver you want to replace with the "fuse" one this thread is about so you can get write access in addition to read access.

The instructions would perhaps be a bit more general and precise if it said to **change** the existing entry to mount the ntfs filesystem to be as described, not unconditionally **add** it to /etc/fstab.

While obvious to veterans, may not be so for newbies who
are letter-for-letter following the instructions without depth of understanding regarding block devices, mount points, drivers, etc.

---

### Post by nbv4 on 2006-06-14
[QUOTE=roytobin]The instructions to add this line to /etc/fstab:
/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1002,umask=0002    0    0

presume /dev/hda1 has a ntfs filesystem.  Certainly on
my setup, this was the case, but I don't know if it is true for everybody.  Perhaps it is the case for Windows OSes that use the NTFS filesystem *must* be on the first partition?

For me, upon install, Dapper recognized that /dev/hda1 had a valid ntfs filesystem on it, and it automatically put this into the /etc/fstab:

/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Note the filesystem type is "ntfs" and not "ntfs-fuse"
This "ntfs" calls out the standard, read-only driver to access the Windows NTFS filesystem.  This is the driver you want to replace with the "fuse" one this thread is about so you can get write access in addition to read access.

The instructions would perhaps be a bit more general and precise if it said to *change* the existing entry to mount the ntfs filesystem to be as described, not unconditionally *add* it to /etc/fstab.

While obvious to veterans, may not be so for newbies who
are letter-for-letter following the instructions without depth of understanding regarding block devices, mount points, drivers, etc.[/QUOTE]

I totally agree. I think that may have been my problem. I had a line in my fstab for the read-only ntfs, which I had to remove in order to replace it with the one listed in the howto. If I had been thinking, I'd have backed up my fstab, as there were more than a few differences (that I can vaugely recall) between the existing one and the new one. Now everything is all messed up. I wish I had known to just change "ntfs" to "ntfs-fuse", then maybe it would have worked...

---

### Post by JohanSwe on 2006-06-15
[QUOTE=roytobin]How to assure the necessary "fuse" module is loaded into the kernel.

 % /sbin/modprobe -l | /bin/grep fuse
/lib/modules/2.6.15-23-386/kernel/fs/fuse/fuse.ko

If you don't see this pipe return a line like the one above that contains fuse, you don't yet have fuse loaded into the kernel.  As the instructions state, this new dynamically loaded piece of the kernel must be present to mount a 'ntfs-fuse' type filesystem.  You need to either a) reboot or b) execute the modeprobe command as root as the original post states.
Both options, of course, are after you have followed the procedures in the original post already.

Depending on your font, please know the lowercase "el"
character (for "list") is passed to the modprobe program in the above example, and the vertical bar symbol (aka pipe symbol) follows.

The instructions were good enough to get me going on
% uname -a
Linux ldt-sdoa-004 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Dapper system without any troubles and with gratitude.[/QUOTE]

Thanks. I tried typing the command:
```
chefen@chefen-desktop:~$ /sbin/modprobe -l | /bin/grep fuse
/lib/modules/2.6.15-23-386/kernel/fs/fuse/fuse.ko

```

I have restarded my computer and also been trying to run the command:
```
chefen@chefen-desktop:~$ sudo modprobe fuse && sudo umount -a && sudo mount -a
Password:
umount: /home: enheten är upptagen (couldn't unmount)
umount: /dev: enheten är upptagen (couldn't unmount)
umount: /var/run: enheten är upptagen (couldn't unmount)
umount: /: enheten är upptagen (couldn't unmount)
```

But the ntfs partition is not mounted. It was mounted before the changes in fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda8       /home           ext2    defaults        0       2
/dev/hda5       /media/lagring  vfat    user,utf8,auto,fmask=0111,dmask=0000 0       1
#/dev/hda5       /media/lagring  vfat    defaults,utf8,umask=007,gid=46 0       1
[COLOR="Red"]/dev/hda1       /media/win      ntfs-fuse    auto,gid=1002,umask=0002    0    0[/COLOR]
[COLOR="Olive"]#/dev/hda1       /media/win      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1[/COLOR]
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

```
    Enhet Start     Början        Slut     Block    Id  System
[COLOR="Red"]/dev/hda1   *           1         637     5116671    7  HPFS/NTFS[/COLOR]
/dev/hda2             638       24321   190241730    f  W95 Utökad (LBA)
/dev/hda5            5228       24321   153372555    b  W95 FAT32
/dev/hda6             638        1275     5124672   83  Linux
/dev/hda7            1276        1402     1020096   82  Linux växling / Solaris
/dev/hda8            1403        5227    30724281   83  Linux

```

```
chefen@chefen-desktop:~$ uname -a
Linux chefen-desktop 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```

And I have installed the packages libntfs8, ntfsprogs and libfuse2 from synaptic since they were not installed on my clean desktop install of dapper?

I hope I have provided enough information so that we could see what's wrong. Any ideas? :?:

---

### Post by Lunar_Lamp on 2006-06-15
I followed the guide in the 1st post.

My /etc/fstab :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
#/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0
    1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1001,umask=0002    0    0

```


and the output from ls -l /media:
```
lrwxrwxrwx 1 root root    6 2006-06-09 19:42 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-06-09 19:42 cdrom0
dr-x------ 1 root root 8192 2006-06-08 19:53 hda1

```

When I booted up the computer /dev/hda1 was not mounted, and I had to mount it as root, and now I can navigate it as root and open files from it as root, but I cannot even navigate as a normal user. 

When, as root, I try to write a file to the NTFS drive, I get told it is a read-only drive.

I did remember to add my normal user to the group ntfs, so what have I not managed to do correctly?

---

### Post by roytobin on 2006-06-15
[QUOTE=JohanSwe]Thanks. I tried typing the command:
[

I hope I have provided enough information so that we could see what's wrong. Any ideas? :?:[/QUOTE]


Only one theory: did you fix the Dapper bug by making the
hard link?  Here is the way my Dapper system stands
after making this link, which I've read in this thread was not in the
original version of the HOWTO, but this step is certainly there now.

```
 % /bin/ls -i /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
1140828 /sbin/mount.ntfs-fuse  1140828 /usr/bin/ntfsmount
```

Do not be concerned that your inode numbers differ
from mine.  What is important is that 1) both filesystem entries
exist in your Dapper system and 2) they are links
(meaning the inode numbers are identical).

Caveat: the use of a "hard" link to fix this Dapper bug, and not a
symbolic link, presumes the directories /sbin and /usr/bin are on the same
filesystem, probably the root filesystem.  For example, if you have /
mounted on one partition, and /usr mounted on another, you will have to
use a symbolic link.  I don't think this very subtle point is impacting
anyone on this thread that I saw, but thought I'd mention it.  If you have
no understanding what this paragraph is talking about, just ignore it.

---

### Post by JohanSwe on 2006-06-15
Thank you roytobin. But my system is strange. The files just don't exist but the maps are there?

[QUOTE=JohanSwe]The command:
[COLOR="SeaGreen"]sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
didn't work for me. I got the message that /sbin/mount.ntfs-fuse didn't exist.
In nautilus I then looked for the /usr/bin/ntfsmount file but couldn't find that one neither.[/COLOR]

I have restarted my computer but the ntfs partition was not mounted. Then I checked if I had the mentioned packeges but couldn't found
# libntfs8
# ntfsprogs
# libfuse2
so I installed them.
[/QUOTE]

```
chefen@chefen-desktop:~$ sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount
Password:
rm: cannot remove `/sbin/mount.ntfs-fuse': No such file or directory
chefen@chefen-desktop:~$

```

```
chefen@chefen-desktop:~$ /bin/ls -i /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
/bin/ls: /usr/bin/ntfsmount: No such file or directory
/bin/ls: /sbin/mount.ntfs-fuse: No such file or directory

```
```
chefen@chefen-desktop:~$ dir /
ATI_LICENSE.TXT  cdrom  home        lib         mnt   root  sys  var
bin              dev    initrd      lost+found  opt   **[COLOR="red"]sbin[/COLOR]**  tmp  vmlinuz
boot             etc    initrd.img  media       proc  srv   usr

chefen@chefen-desktop:~$ cd /usr
chefen@chefen-desktop:/usr$ dir
**[COLOR="red"]bin[/COLOR]**  games  include  lib  lib64  local  sbin  share  src  X11R6
chefen@chefen-desktop:/usr$

```

How can I fix the dapperbug when the files that I am suppuse to fix isn't there?
My NTFS are not mounted at all. The catalog in /media/ is just empty. As you can see in my previous post (this is my third) I could mount this partition before editing fstab as sad in the how to :confused:  :rolleyes: 

btw What is the column <pass> for in fstab?

---

### Post by nbv4 on 2006-06-15
```

priestc@priestc-desktop:~$ sudo mount -a
Couldn't mount device '/dev/hda1': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

```

Has anyone else gotten this error? I know fuse is loaded into my kernel because when I mount the ntfs drive as read-ponly, it gives no error. It's only when "rw" is added to the fstab that I get this error. This is weird because this drive is a storage drive only. No windows installation has ever existed on this drive.

Edit: upon further investigation, it seems that I need ntfs.sys and ntoskrnl.exe, which I actually have, but where do I put them? I can't find this answer anywhere...

---

### Post by JohanSwe on 2006-06-15
nbv4: If you have win load it so that the ntfs partition is mounted i win. I got this problem when using gparted and a start up and shut down of win solved it.

---

### Post by nbv4 on 2006-06-15
[QUOTE=JohanSwe]nbv4: If you have win load it so that the ntfs partition is mounted i win. I got this problem when using gparted and a start up and shut down of win solved it.[/QUOTE]
Could you rephrase this post? I'm not understanding what you mean here. This drive does not have windows installed on it. Mounting it on a computer running windows will not change anything on the drive.

---

### Post by JohanSwe on 2006-06-16
I don't know. I just know that I had the same problem, except that I had win on the same partition. But have you been trying to mount your partition in win? Are you sure it doesn't matter?

---

### Post by roytobin on 2006-06-16
[QUOTE=JohanSwe]Thank you roytobin. But my system is strange. The files just don't exist but the maps are there?

How can I fix the dapperbug when the files that I am suppuse to fix isn't there?
My NTFS are not mounted at all. The catalog in /media/ is just empty. As you can see in my previous post (this is my third) I could mount this partition before editing fstab as sad in the how to [/QUOTE]

You need to first successfully install the packages outlined in the HOWTO so you *will* have
all necessary files.   If a file doesn't exist, it was deleted accidentally, or never installed.  Either
way, the only solution is to reinstall!

As for your mount point being empty, this is because it is just that: a mount point, since the
NTFS filesystem can not be mounted there because you don't have the needed binaries.

If you were to put your fstab back to call out the standard, read-only filesystem type "ntfs"
(and all other options on the line!), I suspect you could again mount the filesystem read-only.
The filesystem type "ntfs" is standard with Dapper installs, I understand.  One could say it is built-in.

---

### Post by sopo_dan on 2006-06-16
i've gone through all the posts in this thread, but nobody seems to have had my problem. 
i have 2 ntfs patitions, one is primary and has 10GB, the other logical and has ~230GB. i followed the tutorial and i seem to have done it right, because the primary, smaller partition mounts as it should (including r/w acess), but for the other one i get this when doing "mount -a"
```
Couldn't mount device '/dev/sda5': Input/output error
Mount failed.
``` my /etc/fstab looks like this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>       <type>      <options>       <dump>  <pass>
proc            /proc               proc        defaults        0       0
/dev/sda6       /                   reiserfs     defaults        0       1
/dev/sda8       /boot               reiserfs     notail          0       2
/dev/sda7       /home               reiserfs     defaults        0       2
#/dev/sda1      /media/winc         ntfs        defaults,nls=utf8,umask=007,gid=46 0       1
#/dev/sda5      /media/wind         ntfs        defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda10    /home/sopo/stuff    reiserfs     defaults    0    2
/dev/sda9       none                swap        sw              0       0
/dev/hda        /media/cdrom0       udf,iso9660     user,noauto     0       0
/dev/sda1     /media/winc         ntfs-fuse     auto,gid=1001,umask=0002          0        0
/dev/sda5     /media/wind         ntfs-fuse     auto,gid=1001,umask=0002          0        0
``` could it have something to do with the unusually large size of the second partition?
any help would be greatly appreciated, because that's the one i actually need to be able to write on, the small one is just the win install

---

### Post by haani on 2006-06-16
i did exactly wot sed in the how-to but i cant write to my ntfs partition this is wot my fstab looks like;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/sda1     ntfs-fuse    auto,gid=1002,umask=0002    0    0
/dev/sda1       /media/sda1     ntfs-fuse    auto,gid=1002,umask=0002    0    0
```

---

### Post by sopo_dan on 2006-06-16
**haani** you forgot to comment out the original lines for the 2 ntfs partitions. those lines are first, so it uses them and when it gets to the ones you actually want they get ignored, as the partitions are already mounted.
your /etc/fstab should read:
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/sda1     ntfs-fuse    auto,gid=1002,umask=0002    0    0
/dev/sda1       /media/sda1     ntfs-fuse    auto,gid=1002,umask=0002    0    0
```

---

### Post by haani on 2006-06-17
ok i commented them out and i restarted the computer, when i go places > computer > downloads (thats my ntfs parition) it says Unable to mount the selected volume mount: according to mtab, /dev/sda5 is already mounted on /media/sda5

mount failed

but when i go to system > administrator >disks it tells me that the partitions are already mounted but i still cant write to it!!! and i dont have icons of my ntfs paritions on my desktop..!

now my fstab looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/sda1    ntfs-fuse    auto,gid=1002,umask=0002    0    0
/dev/sda5       /media/sda5    ntfs-fuse    auto,gid=1002,umask=0002    0    0
```

**EDIT:** Nevermind i think its working now i just made a shortcut for the partitions on the desktop and it writes to it now!

---

### Post by a-musing amazon on 2006-06-17
[QUOTE=brallan]Does anyone know how the autodetect/automount for USB drives works enough to modify it so that ntfs drives are hot-mounted (dynamically) without needing an fstab entry? The problem with fstab is that is really best suited to permanent drives.

Write support for NTFS is fantastic, a great breakthrough for linux users. thanks to [those heroes ]("http://www.linux-ntfs.org")who reverse engineered and thanks to all who contribute!

brian[/QUOTE]
Certainly regular read only auromounting works OK when I attach my 80Gb LaCie drive using usb. This is in with a vanilla amd64-bit Dapper 6.06 setup.

---

### Post by gorilla on 2006-06-18
I just noticed that my music folder on that NTFS disk got emptied; about 10 gigs gone. Not really a problem since I have a backup on DVD, but it scares me a bit.
I mounted the drive with RW support just a few days ago.. I have booted into win one time since that, and the folder was still there. And I surely havn't deleted it (knowingly) in linux.. however I had a lot write actions in there.
just a little reminder to make backups until the driver is mature..

---

### Post by haani on 2006-06-20
how can i mount my usb ntfs harddrive. do u have to change something in mtab?

---

### Post by haani on 2006-06-22
my write support in parition 1 worked fine but after i reinstalled ubuntu (got corruput) i again installed write support, but on partition 1 it says only root can mount /dev/sda1 to /media/sda1??? but my other partition works fine??

this is wot my fstab looks  like

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#/dev/sda3       /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/sda1     ntfs-fuse    auto,gid=1002,umask=0002    0    0
/dev/sda3       /media/sda3     ntfs-fuse    auto,gid=1002,umask=0002    0    0
[B]
Edit:[/B] i fixed it

---

### Post by n00buntu on 2006-06-24
Hello, I tried to follow the instructions and when I try to mount my ntfs drive, it says only root can mount.  My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1001,umask=0002    0    0

Any help would be appreciated.  I am pretty new to linux, and I may have missed something obvious.  Thank you.

---

### Post by haani on 2006-06-24
[QUOTE=n00buntu]Hello, I tried to follow the instructions and when I try to mount my ntfs drive, it says only root can mount.  My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1001,umask=0002    0    0

Any help would be appreciated.  I am pretty new to linux, and I may have missed something obvious.  Thank you.[/QUOTE]

m8 u need to go into windows and run scandisk on ur hard drive and than reboot, when u boot into ubuntu ur partition will be mounted than go to /media/hda1 to see ur mounted windows files. you also need to create a shortcut on ur desktop if u want.

---

### Post by Brando569 on 2006-06-24
i have a wierd problem, im added to the ntfs group and i modded the fstab correctly and it still says that i have insufficient privledges to write changes.... even as root!

heres my fstab:

/dev/sdb1  /media/stuff  ntfs-fuse   auto,gid=1001,umask=0002    0       0

---

### Post by haani on 2006-06-25
m8 u need to do wot i sed on the above post

---

### Post by Giga on 2006-06-25
i use ntfs writing support before and works fine..
on that time, a friend of mine mount my other hard disks for me.

i installed Dapper 6.06 and i couldnt make it work
Could you help me?

my fstab:

# sda1 = ATA
# hdb1 = BACKUP
# sdb2 = SATA II
# sdb1 = OS

/dev/sda1       /media/ATA    **ntfs**     user,auto,gid=1000,umask=0007    0    0
/dev/hdb1       /media/BACKUP   **ntfs**     user,auto,gid=1000,umask=0007    0    0
/dev/sdb1       /media/OS       **ntfs**     user,auto,gid=1000,umask=0007    0    0
/dev/sdb2       /media/SATAII   **ntfs  **   user,auto,gid=1000,umask=0007    0  


With **ntfs**  as filyesystem, after i reboot the hard disks are all mounted
but if i change to ntfs-fuse, doesnt work

i already checked all steps.. fuse loading, id group (it is 1000)..
everything is fine.... when i try to write something at any drive. i got the message: " error, u do not have permission...." 

Any clue why i can't ntfs read/write?

Thanks

---

### Post by blacknyx on 2006-06-26
Alright guys.. I'm REALLY confused.   
I followed all of the steps completely.  
Here's my **/etc/fstab**

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
**/dev/hdb1       /hd             ntfs-fuse    auto,gid=1002,umask=0002    0    0**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Then> 
rain@rain-desktop:~$ /bin/ls -i /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
9340652 /sbin/mount.ntfs-fuse  9340652 /usr/bin/ntfsmount

> 
rain@rain-desktop:~$ **groups**
rain adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin **ntfs**
I have a folder in root 
**/hd**
and my hard drive is a 120 GB hard drive on the hdb1
It worked as read only.
I followed ALL of the steps in the first post.

> 
rain@rain-desktop:/$ cd hd
rain@rain-desktop:/hd$ ls
rain@rain-desktop:/hd$


> 
rain@rain-desktop:/hd$ sudo modprobe fuse && sudo umount -a && sudo mount -a
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy


what am I doing wrong?!?!?!?!
argh!

---

### Post by Brando569 on 2006-06-26
i found this thread to be very useful but the way of doing it took too long, just as a suggestion search [www.kde-apps.com](www.kde-apps.com) for debian services control panel, all you have to do is hit 'remove default' and it removes it from startup.

---

### Post by Dojomann on 2006-06-30
Everything works fine and dandy, but the only problem is, I can only access my ntfs stuff by going into "/media/sda2/" (where I mounted it) and there's an icon in the My Computer place, which seems to refer to the old ntfs i had setup which i couldn't write to. I'd like to link this to the new ntfs mount i made with this tutorial. Also, have it appear on the desktop like the original one.

---

### Post by Noahod on 2006-07-04
Hey, I've mounted my drives with ntfs-fuse and I'm having a problem copying files with konqueror. 

When I drag them over I get an error "Could not change permission for:" <filename>. 

However, the file actually seems to copy, and when I try using cp (as my normal user) in terminal, it works fine.. Anyone know a solution?

My fstab is..

> /dev/sdb1       /media/windows  ntfs-fuse    auto,gid=1001,umask=0007    0    0


---

### Post by Triple Threat on 2006-07-04
I am getting a completely different error then what I have seen in this topic. I have a feeling I entered something in wrong. Here is my fstab:

[FONT="Courier New"]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda1       /media/windows  ntfs-fuse auto,gid=1001,unmask=0000     0 0
/dev/hda5       /media/data     ntfs-fuse auto,gid=1001,unmask=0000     0 0
[/FONT]

This is what I get when I run sudo mount -a
[FONT="Courier New"]
sudo mount -a
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting:
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting: Data
aaberg@reginald:~$ sudo mount -a
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting:
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting: Data
[/FONT]

---

### Post by mlind on 2006-07-04
[QUOTE=Triple Threat]I am getting a completely different error then what I have seen in this topic. I have a feeling I entered something in wrong. Here is my fstab:

[FONT="Courier New"]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda1       /media/windows  ntfs-fuse auto,gid=1001,unmask=0000     0 0
/dev/hda5       /media/data     ntfs-fuse auto,gid=1001,unmask=0000     0 0
[/FONT]

This is what I get when I run sudo mount -a
[FONT="Courier New"]
sudo mount -a
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting:
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting: Data
aaberg@reginald:~$ sudo mount -a
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting:
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting: Data
[/FONT][/QUOTE]

shouldn't that be **umask** instead ?

---

### Post by autocrosser on 2006-07-04
Worked perfect for me!! Only thing I needed to do was apt-get fuse-utils--My new install of Dapper didn't have that--Great job!!  Thanks!!

---

### Post by LKRaider on 2006-07-04
[QUOTE=Noahod]When I drag them over I get an error "Could not change permission for:" <filename>. [/QUOTE]

Try adding the **succeed_chmod** option to your fstab, like this:
```
/dev/sdb1 /media/windows ntfs-fuse auto,gid=1001,umask=0007,succeed_chmod 0 0
```

Please report if it works, I'll add that bit to the tutorial then.

---

### Post by Noahod on 2006-07-04
Nope, that broke write support completely. 

> sudo cp libortp1_0.7.1-0ubuntu1_i386.deb /media/windows/
Password:
cp: cannot create regular file `/media/windows/libortp1_0.7.1-0ubuntu1_i386.deb': Input/output error


And from my fstab:

> /dev/sdb1       /media/windows  ntfs-fuse    auto,gid=1001,umask=0007,succeed_chmod    0    0

Read support still works, and it did mount.

---

### Post by LKRaider on 2006-07-05
Try writting at another folder. Fuse-ntfs sometimes fails to write on some of them, and should be unrelated to succeed_chmod.

---

### Post by detinith on 2006-07-05
The drives I want mounted and read/writeable are shown in the Computer directory but I can't mount because it says:
```
mount: only root can mount /dev/sda5 on /media/sda5
```

When I try
```
 sudo mount /dev/sda5
```
I get an error
```
mount: unknown filesystem type 'ntfs-fuse'
```

I tried the command to fix the Dapper bug but it says that the directory doesn't exist. I *am* using Dapper, so is there something I didn't have installed that I needed?

If it helps at all, here are the lines in my fstab:
```
/dev/sda1       /media/sda1     ntfs-fuse    auto,umask=0007,gid=1001 0       1
/dev/sda5       /media/sda5     ntfs-fuse    auto,umask=0007,gid=1001 0       1
```

---

### Post by mlind on 2006-07-06
[QUOTE=detinith]
I get an error
```
mount: unknown filesystem type 'ntfs-fuse'
```

[/QUOTE]

If you check /sbin/mount.ntfs-fuse file, you'll notice it's a broken symlink. You must make it point to the right file
```

sudo ln -df /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

```

Now ntfs-fuse filesystem should be recognized.

---

### Post by Noahod on 2006-07-07
> **LKRaider said:**
> Try writting at another folder. Fuse-ntfs sometimes fails to write on some of them, and should be unrelated to succeed_chmod.

I tried another folder, and it wrote to it this time, but gave the same permission error as before. :(

---

### Post by detinith on 2006-07-07
> **mlind said:**
> If you check /sbin/mount.ntfs-fuse file, you'll notice it's a broken symlink. You must make it point to the right file
```

sudo ln -df /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

```

Now ntfs-fuse filesystem should be recognized.

It says the directory doesn't exist.

---

### Post by mlind on 2006-07-07
> **detinith said:**
> It says the directory doesn't exist.

```

dpkg -S /usr/bin/ntfsmount
**ntfsprogs**: /usr/bin/ntfsmount

```

You did install ntfsprogs package too?
(step II on the HOWTO)

---

### Post by glycerin on 2006-07-12
I have followed these instructions but I am finding that upon reboot my files/folders become corrupt. I have created a full explanation here:

[http://www.ubuntuforums.org/showthread.php?p=1244183#post1244183](http://www.ubuntuforums.org/showthread.php?p=1244183#post1244183)

Please help if you can.

EDIT: Sorted it out - thanks LKRaider

---

### Post by claypole on 2006-07-13
Having succesfully set this up (seems to be working fine albeit I haven't done any major file creation editing yet) I experienced one problem in relation to fuse: for some reason /dev/fuse is not created.  After seaching countless sites I found the solution, this command "sudo mknod /dev/fuse c 10 229" followed by a "sudo mount -a" will correct the problem.  Everytime you reboot you have to do this, so I have created a text file in my home directory, below, and have put this in the startup (system > preferences > sessions > startup programs.  Not the most elegant fix, but until Fuse and/or Ubuntu resolve this, this works.  If anyone is aware of a better way or something I am doing wrong, please advise!

File: /home/correct-fuse


mknod /dev/fuse c 10 229
mount -a



Hope this helps!:D 

Another problem I am now experiencing is that I can no longer see my windows PCs on the network using SMB.  This used to work fine, so I am wondering if the NTFS solution has broken this.  The only doc I can find says that Fuse no longer supports SMB as its not required.  I have loaded Samba and included the IP address of the PC on my firewall but it cannot see the PC or the shares.  Can anyone advise? ](*,)

---

### Post by domino on 2006-07-15
Here's something of interest, which requires FUSE.

[http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697](http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697)

> Hello,
 
 As part of the Linux-NTFS project, I'm happy to announce my contribution
 to ntfsmount and libntfs which resulted ntfs-3g, a read-write ntfs driver,
 capable for unlimited file creation and deletion.
 
 The driver was successfully tested very exhaustively for a longer period of
 time by many ways and methods, creating and destroying millions of files and
 directories on newly created images, and on over 40 real, very diverse NTFS
 images collected over the last four years.

I hope ntfs-3g can be used on top of the tutorial. I tried to install ntfs-3g but got 3 errors along the way. I hope someone has better success with it.

edit: Is it the reason why I got install errors because of an earlier version of fuse installed?

---

### Post by dlai on 2006-07-15
> **domino said:**
> Here's something of interest, which requires FUSE.

[http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697](http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697)



I hope ntfs-3g can be used on top of the tutorial. I tried to install ntfs-3g but got 3 errors along the way. I hope someone has better success with it.

If anyone have any success with this please post a how to, if the ntfs-3g really is as good as described this is a major leap ahead for linux/windows compliance!! Really good for people who wants to dual boot!

---

### Post by Ibbelz on 2006-07-15
Ok here is my problem. I get this error message:

```
Couldn't mount device '/dev/sdb5': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

```

I know this is because I didn't shutdown my windows the correct way (in fact it was a hard reset ;)). And I know I'll have to run scandisk to fix it, but what I also know is that I really don't want to reinstall windows. So I was wondering is there any way to fix this problem _**without reinstalling windows and run scandisk**_. I hope someone can help. :D

---

### Post by dlai on 2006-07-15
I had the exact same problem would like to know how to fix it as well!

---

### Post by LKRaider on 2006-07-15
> Here's something of interest, which requires FUSE.

[http://sourceforge.net/mailarchive/f...&forum_id=2697](http://sourceforge.net/mailarchive/f...&forum_id=2697)

Seems like great news, thanks for bringing it to our attention :D

I will test this now and try to produce a debian package here for distribution, and then add it to the how-to (or completely rewrite it ;) )

Let's see how it goes.

---

### Post by LKRaider on 2006-07-15
> **Ibbelz said:**
> Ok here is my problem. I get this error message:

```
Couldn't mount device '/dev/sdb5': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

```

I know this is because I didn't shutdown my windows the correct way (in fact it was a hard reset ;)). And I know I'll have to run scandisk to fix it, but what I also know is that I really don't want to reinstall windows. So I was wondering is there any way to fix this problem _**without reinstalling windows and run scandisk**_. I hope someone can help. :D

Hmm, well, if you don't use windows, I see no reason why you would keep ntfs anyway ;-P

But if you really need to gain access to the partition you can force mounting it (although it is not recommended), or use a windows cd to run chkdsk on it - no need to install, just get to the repair console and run chkdsk on the disk.

---

### Post by wedderburn on 2006-07-16
> **dlai said:**
> If anyone have any success with this please post a how to, if the ntfs-3g really is as good as described this is a major leap ahead for linux/windows compliance!! Really good for people who wants to dual boot!

i had great results last night with the ntfs-3g driver [http://www.ubuntuforums.org/showthread.php?t=216237](http://www.ubuntuforums.org/showthread.php?t=216237) for a mini brief how to

---

### Post by Anduu on 2006-07-16
> **wedderburn said:**
> i had great results last night with the ntfs-3g driver [http://www.ubuntuforums.org/showthread.php?t=216237](http://www.ubuntuforums.org/showthread.php?t=216237) for a mini brief how to

Ayup...worked like a charm for me too.

---

### Post by domino on 2006-07-16
Re: ntfs-3g

wedderburn's breif how-to worked for me also.

---

### Post by sciyoshi on 2006-07-16
> **domino said:**
> It kind of gets me wondering why HAL doesn't recognize fuse. You already pointed out that the current kernel already implements the feature.

I also added a link pointing to the mounted ntfs directory in Nautilus bookmarks. It should also show up when browsing to open files.

I was wondering that too. A temporary workaround is this:

Paste the following into /etc/hal/fdi/policy/preferences.fdi (before the final </deviceinfo>):

<device>
  <match key="volume.fstype" string="ntfs">
    <merge key="volume.is_mounted" type="bool">true</merge>
    <merge key="volume.mount_point" type="string">/media/Windows</merge>
    <merge key="volume.policy.mount_filesystem" type="strlist">fuse</merge>
    <merge key="storage.removable" type="bool">false</merge>
    <merge key="volume.ignore" type="bool">false</merge>
  </match>
</device>

Changing the mount point, of course. I've updated the bug report with this workaround at [https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/35354](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/35354)

---

### Post by Epperly on 2006-07-17
wth, I got couldn't find "/media/hdc2"...
(hopefully my second hard drive..)

---

### Post by givré on 2006-07-17
> **dlai said:**
> If anyone have any success with this please post a how to, if the ntfs-3g really is as good as described this is a major leap ahead for linux/windows compliance!! Really good for people who wants to dual boot!
Here it is [http://ubuntuforums.org/showthread.php?p=1265741](http://ubuntuforums.org/showthread.php?p=1265741) :cool:

---

### Post by forrestcupp on 2006-07-17
I hope this hasn't already been asked, but how in the world can I mount NTFS with write support if it's an external USB harddrive.  My ext. drive doesn't show up in fstab.

---

### Post by mlind on 2006-07-17
> **forrestcupp said:**
> I hope this hasn't already been asked, but how in the world can I mount NTFS with write support if it's an external USB harddrive.  My ext. drive doesn't show up in fstab.

I would make a custom udev rule for the drive, so it will always get the same device node from /dev.
You can add the drive to /etc/fstab without the rule too, it's usually /dev/sda or /dev/sdb, depending what other external devices are attached that time.

---

### Post by forrestcupp on 2006-07-17
> **mlind said:**
> I would make a custom udev rule for the drive, so it will always get the same device node from /dev.
You can add the drive to /etc/fstab without the rule too, it's usually /dev/sda or /dev/sdb, depending what other external devices are attached that time.

I know this might sound stupid, but how dow I do that?

---

### Post by givré on 2006-07-17
You could create rule for usb device with this howto [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)
and add a line in fstab just like the ntfs one.
Also, you should try this HowTo to profit to the latest improvement of linux-ntfs.org. [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by mlind on 2006-07-17
> **forrestcupp said:**
> I know this might sound stupid, but how dow I do that?

It's not very trivial at first try, but I've used this guide with great success
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

I also made udev rule for my joypad
[http://www.ubuntuforums.org/showpost.php?p=1143335&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1143335&postcount=5)

---

### Post by oiboimike on 2006-07-17
Hey Great HOW-TO Helped Big Time One Question Though Anyone Know What umask You Need for User Write Access?

---

### Post by givré on 2006-07-17
You will need uid and gid to set permission.
uid=1000 will set the owner to you
gid=1000 will set the group to your group
umask=002 eq rwxrwxr-x
umask=022 eq rwxr-xr-x etc...

---

### Post by Epperly on 2006-07-17
Wait, so can I write to my Windows disk from Linux now that I can access it?

In specific, could I add songs to it and torrents, so that I don't have to use room on my Linux HD(which is 20 gigs as opposed to my Window's 80 gigs)?

---

### Post by LKRaider on 2006-07-17
I just tested the new ntfs-3g and it is indeed working much better!

I had prepared the debian packages to install it, but I see someone already did that :)
So, I don't know of what to make of this How-To, since it is now superceded by the new one.

So, for anyone still using this, please try the new How-To avaiable at: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by PeRy_SoY on 2006-07-18
hi, anybody can mount 2 partitions ntfs? I can only mount first partition (first in appear in fstab) the second partition no mount --> /dev/fuse already mount, 

Pd. sorry 4 my english ;) 

Thx 4 helps :)

Byes!!!

---

### Post by LKRaider on 2006-07-18
I am mounting two ntfs partitions with no problems.
Here is my fstab for them:

```
  /dev/hda1     /media/Aalto    ntfs-3g         auto,gid=114,umask=0007,locale=pt_BR.UTF-8      0       0
  /dev/hdb4     /media/Mies     ntfs-3g         auto,gid=114,umask=0007,locale=pt_BR.UTF-8      0       0

```

---

### Post by PeRy_SoY on 2006-07-18
thx 4 u fstab, now i can mount 2 partition :)

byyeS!!!

---

### Post by kleedrac on 2006-07-19
> **LKRaider said:**
> Hmm, well, if you don't use windows, I see no reason why you would keep ntfs anyway ;-P

But if you really need to gain access to the partition you can force mounting it (although it is not recommended), or use a windows cd to run chkdsk on it - no need to install, just get to the repair console and run chkdsk on the disk.

Did this work?  I'm having the same issue and I know I'd need to reinstall windows as I haven't used windows at all in over 6 months and have replaced the mobo/cpu in the interim :)

---

### Post by dlanor78 on 2006-07-22
I tried running chkdsk on the ntfs partition I'm trying to mount and I still get the Windows did not shut down properly message.

If anyone solves this please post!!!

---

### Post by lpawlik on 2006-08-26
please help, how to handle witch such error (I did everything what was written in 'how to'):

[root@lpawlik ~]#mount /dev/sda7
fusermount: unable to open fuse lock file
fuse_mount failed.
Unmounting: Uzytki

line in fstab looks like this:

/dev/sda7 /media/sda7  ntfs-fuse  auto,gid=1001,umask=0002  0  0

Can someone tell mi what's wrong?? Please!!

---

### Post by LKRaider on 2006-08-26
Please refer to this thread now: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

This guide is outdated since there is a new and better ntfs supporting driver now.

---

### Post by unLog!c on 2006-09-16
whoops... Just saw this bug report:
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/35354](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/35354)

yep, thats my problem...

Is there any fix for this bug??

---

### Post by HippyVanMan on 2007-02-16
This is a bit of a newbie question, but I am a newbie, so, It didn't work and i'm missing drives and I cannot write to the NTFS partition, and other partitions are smaller than they should be. How do I restore the system to how it was using the backup I made?

---

### Post by SrEstroncio on 2007-08-26
I did everything but after I reboooted I got this screen:

Unable to mount the selected volume.
mount: only root can mount /dev/hda1 on /media/windows


any help? I'm quite the ubuntu illiterate D: thanks in advance

---

### Post by LKRaider on 2007-09-16
Please refer to this thread now: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

This guide is outdated since there is a new and better ntfs supporting driver now.


Moderator, please close this thread.

---

### Post by chikaku on 2009-11-03
ntfs-3g will be better

---

### Post by smaglio81 on 2009-11-24
> **Triple Threat said:**
> I am getting a completely different error then what I have seen in this topic. I have a feeling I entered something in wrong. Here is my fstab:

[FONT="Courier New"]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda1       /media/windows  ntfs-fuse auto,gid=1001,unmask=0000     0 0
/dev/hda5       /media/data     ntfs-fuse auto,gid=1001,unmask=0000     0 0
[/FONT]

This is what I get when I run sudo mount -a
[FONT="Courier New"]
sudo mount -a
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting:
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting: Data
aaberg@reginald:~$ sudo mount -a
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting:
fusermount: mount failed: Invalid argument
fuse_mount failed.
Unmounting: Data
[/FONT]

It's possible that you may be attempting to mount to a symbolic link.

This information came from a google search result (but, I couldn't find the text on the real web site).
> 
[NTFS-3G Release History at Tuxera]("http://www.tuxera.com/community/release-history/")
Fix: Mount failed with “Invalid argument” error message if the mountpoint was a symlink. If NTFS-3G is compiled with an external FUSE library (non-default ...
[www.tuxera.com/community/release-history/](www.tuxera.com/community/release-history/) - [Cached]("http://74.125.95.132/search?q=cache:p-RYTybmPsoJ:www.tuxera.com/community/release-history/+ntfs+fuse+mount+failed+invalid+argument&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a")


---

