---
title: "[SOLVED] &amp;quot;Root&amp;quot; reclaimed my Partitions - files are missing!"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Bruce M. on 2008-07-09
Hi Folks,

What the heck happened? "Root" has reclaimed my partitions that I took ownership of, and my personal files are missing.

First I asked how to get ownership here: [[SOLVED] fstab - how do I modify it to get permissions?]("http://ubuntuforums.org/showthread.php?t=851377")

I just did a reboot as I changed my language options, and it was required.

Low and behold, "Root" has rebelled and taken ownership of these partitions again and all my stuff is gone.

Also as seen in the attached image, my 80G HD (/dev/sdb1/) that has one partition is being reported as a 20G volume and only 14.8G free, but I can see, 2nd image, **[COLOR="Red"]NOTHING!!!!!!!!![/COLOR]** :confused::confused::confused:

Anyone have any idea what happened?

Thanks,
CHIMO!
Bruce

---

### Post by indytim on 2008-07-09
Does this coincide with a boot to GParted Live (or LiveCD)?  I'd recommend starting there to determine what real estate you actually have on the H/D.

IndyTim

---

### Post by unutbu on 2008-07-09
Please post
```

sudo fdisk -l
cat /etc/fstab
```

---

### Post by bab1 on 2008-07-09
See below (sorry for the double post)

---

### Post by bab1 on 2008-07-09
Bruce,

What have you done now?

A partition is different than a filesystem (files and directories). Root does not own partitions.  

Have you checked to see if the "hidden" files switch is on or off When looking at the files on sda1 (80GB)  I'll bet a "lost+found" directory is where your "lost' files are.  This could cause your loss on the 80GB drive.

---

### Post by Elfy on 2008-07-09
> **bab1 said:**
> Bruce,

What have you done now?

A partition is different than a filesystem (files and directories). Root does not own partitions.  

Have you checked to see if the "hidden" files switch is on or off When looking at the files on sda1 (80GB)  I'll bet a "lost+found" directory is where your "lost' files are.  This could cause your loss on the 80GB drive.
Wouldn't explain why it's being reported as a 20Gb volume though afaik.

---

### Post by bab1 on 2008-07-09
The size of the device is not nessesarily the size of either the partition or the available space on a partition.  If there are no hidden files that are taking up space, then I would check to see what is on the device.  By that I mean device=sda1 and what ii the size or the partition shown by fdisk -l.  You can check the amount data on the partition with df -h.

---

### Post by Bruce M. on 2008-07-09
**[CENTER]WoW, people, thanks kindly for your responses.[/CENTER]**

> **indytim said:**
> Does this coincide with a boot to GParted Live (or LiveCD)?  I'd recommend starting there to determine what real estate you actually have on the H/D.

IndyTim

No, last night I did a "clean install" of 8.04 Gnome (from 8.04 Xfce).
The setup was identical except for the names of the partitions.

> **unutbu said:**
> Please post
```

sudo fdisk -l
cat /etc/fstab
```

OK, here you go...
```
bruloo@bruloo:~$ sudo fdisk -l
[sudo] password for bruloo: 

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a722a72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   b  W95 FAT32
/dev/sda2            1217       24792   189374220    5  Extended
/dev/sda5            1217        3648    19535008+  83  Linux
/dev/sda6            3649        9727    48829536   83  Linux
/dev/sda7            9728       17022    58597056   83  Linux
/dev/sda8           17023       24317    58597056   83  Linux
/dev/sda9           24318       24792     3815406   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002692a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
bruloo@bruloo:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=17db159b-0bc1-44f6-a43f-98c2cbff7f52 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=abe0a2a8-f436-43a9-b2fc-205c9b262010 /80G            ext3    relatime,auto.users        0       2
# /dev/sda7
UUID=03140209-9a32-41a0-8cd4-fa833f435349 /Bruce          ext3    relatime,auto.users        0       2
# /dev/sda8
UUID=0fcd7982-ac98-4536-9e85-9fa67bc7978f /Liloo          ext3    relatime,auto.users        0       2
# /dev/sda6
UUID=c75514d9-e01c-482b-91d8-eef7a8576f24 /home           ext3    relatime        0       2
# /dev/sda1
UUID=608E-A91B  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=a96dbddd-143b-44ee-b438-36311df4bcf5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
bruloo@bruloo:~$ 
```

> **bab1 said:**
> Bruce,

What have you done now?

ME: The Champion of Tweak It Until it Breaks.  :lolflag:

Installed Ubuntu 8.04 last night as I was told it was easier on resources than Ubuntu 7.10. The only reason I was using Xfce is it's lighter on resources. OK, I've used it enough to like it, but there are a couple of things I miss with GNOME!

> **bab1 said:**
> A partition is different than a filesystem (files and directories). Root does not own partitions.

Maybe so but when I did the "clean install" I gave my partitions "Labels" in the partition editor part of the setup. That put those partitions in **[SIZE="5"]/[/SIZE]** as folders. See image below (80G, Bruce and Liloo).

> **bab1 said:**
> Have you checked to see if the "hidden" files switch is on or off When looking at the files on sda1 (80GB)  I'll bet a "lost+found" directory is where your "lost' files are.  This could cause your loss on the 80GB drive.

See below ... I see "nothing" on those partitions, or in those folders. Take your pick, they are partitions, not folders, and I have NO idea as to why they are in my **[SIZE="5"]/[/SIZE]** as folders.

Time to go back to Gutsy Xfce I think.

Thanks for all the responses.
CHIMO!
Bruce

---

### Post by bab1 on 2008-07-09
I do not see any /dev/sdb in your fstab file.  Are you manually mounting it?

---

### Post by bab1 on 2008-07-09
I see the answer now.  You have named 2 things the same and you are looking at the wrong thing.  Mount the drive and you will see.

Oooops! [COLOR="Red"]the above is wrong.[/COLOR]  I found sdb1 in the fstab file.

---

### Post by bab1 on 2008-07-09
I will still say that you have labled the partitions and the mount point is also of the same name ie: 80G.  It is always good to name things distinctly.  Another point to try is to manually unmount the drive with```
umount *dir* *device*
``` and see what is in the directory.

---

### Post by unutbu on 2008-07-09
(1) In your /etc/fstab, change "auto.users" to "auto,users". (change period to comma). I think this might be why root has taken over your partitions. The users (and maybe the auto) options are not taking effect. Reboot (to test that the auto option takes effect). If things are not any better, please post the output of 

```
mount
```

(2) If your /windows is mounting properly, ignore this. Otherwise, please post output of 

```
blkid
```

Your /windows partion has a rather short UUID. I would have expected something longer.

(3) If your 80GB partition is still showing up as 20GB, run

```
sudo resize2fs /dev/sdb1
```

This should expand the ext3 filesystem on /dev/sdb1 to the size of the partition.

---

### Post by cariboo on 2008-07-09
You really should not have your partitions mounted in / they should be mounted in /media or the old skool way in /mnt. the reason behind that is that most file managers are set to look on media for your mounted partitions. I would unmount the drives, create the proper mount points:

```
/media/80G
/media/Bruce
/media/Lilo
/media/windows
```

One question though are /Bruce and /Lilo home directories? if so mount them in /home. If not mount them as in the above example.

Change /etc/fstab to reflect the proper mount points and remount your drives.

Jim

---

### Post by bab1 on 2008-07-09
Jim,

I agree with you that the partitions should not all be mounted at /.  That being said, you can mount them anywhere successfully.  My samba directories are on a separate partition mounted under /smb.  In addition (muddying the water a bit) I have another partition mounted at /smb/backup.  Yes a mount on a mount!  I can hear it now what happens if....  The answer is: Yes it crashes.  But I want it to.  No windows backups if there is no Samba share available.  I have never had any problems with file managers.

I think  the mount /media automagically shows up on the desktop.  I popular enhancement (unless you have 5 or 6 of 'em).

---

### Post by Bruce M. on 2008-07-10
> **unutbu said:**
> (1) In your /etc/fstab, change "auto.users" to "auto,users". (change period to comma). I think this might be why root has taken over your partitions. The users (and maybe the auto) options are not taking effect. Reboot (to test that the auto option takes effect). If things are not any better, please post the output of 

**That did it. DUH! A typo. How dumb.**
They are back ... **[COLOR="Green"]Thank you.[/COLOR]**

And I tell people I don't make typos, my keys move around to confuse me. :)

> **unutbu said:**
> ```
mount
```

(2) If your /windows is mounting properly, ignore this. Otherwise, please post output of 

```
blkid
```

Your /windows partion has a rather short UUID. I would have expected something longer.

That /windows partition is empty, prepared incase I have to do a quick install as my ISP doesn't support Linux. In a year with Linux I have never needed it so I didn't waste time installing it. I have a SuperGurb disk in case I ever need to install it.

> **unutbu said:**
> (3) If your 80GB partition is still showing up as 20GB, run

```
sudo resize2fs /dev/sdb1
```

This should expand the ext3 filesystem on /dev/sdb1 to the size of the partition.

With the replacing of "auto.user" to "auto,user" it is working fine.

One more question, is "realtime" putting these partitions in my / as folders, or is it because I gave them labels?

I want them back as /media/sdaX.

Someone said they still use "default" can I change:
```
realtime,auto,user
```
to
```
default,auto,user
```

Thanks kindly for you help.

A typo ... (hanging head in shame) ... sigh!
CHIMO!
Bruce

---

### Post by Bruce M. on 2008-07-10
> **cariboo907 said:**
> You really should not have your partitions mounted in / they should be mounted in /media or the old skool way in /mnt. the reason behind that is that most file managers are set to look on media for your mounted partitions. I would unmount the drives, create the proper mount points:

```
/media/80G
/media/Bruce
/media/Lilo
/media/windows
```

One question though are /Bruce and /Lilo home directories? if so mount them in /home. If not mount them as in the above example.

Change /etc/fstab to reflect the proper mount points and remount your drives.

Jim

Hi Jim,

No they aren't home directories, just partitions for my wife and I to use for personal use.
I've changed the /etc/fstab and will be doing the remount stuff now and will reboot to see what happens.

X'ing fingers here.
CHIMO!
Bruce

---

### Post by bab1 on 2008-07-10
As bodhi.zazen (forum staff) has stated:

> Ubuntu now defaults to "relatime" in the options.

Anyways, use options :

relatime,auto,users


Let's use the Linux default.

---

### Post by unutbu on 2008-07-10
The relatime option means that the last time a file has been accessed is only written to disk if that time is earlier than the modification time. In short, this behavior causes your Linux kernel to write fewer times to disk, giving you snappier performance. (See [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)) 

Each line in fstab (besides those that start with #) consists of 6 whitespace-separated fields. The second field defines the directory where the partition gets mounted. 
So for example, the fstab line which reads

```
UUID=03140209-9a32-41a0-8cd4-fa833f435349 /Bruce          ext3    relatime,auto.users        0       2
```

mounts the partition with UUID=03140209-9a32-41a0-8cd4-fa833f435349  at /Bruce.

When fstab is in charge of mounting, the partition label has no effect on where the partition gets mounted. Only the second field matters.

When HAL is in charge of automounting hotswappable devices, HAL creates a directory in /media whose name coincides with the partition label. I'm not entirely clear on how fstab and HAL cooperate, but my experience has been that whenever there is an fstab entry, HAL does not try to automount. When there is no fstab entry, HAL tries to automount.

Since you already have fstab working and it doesn't sound like you need HAL's automounting feature, the easiest way to get your partitions mounted at /media/sdaX is to

```
sudo mkdir /media/sdaX
```

and then change the second field in fstab from /Bruce to /media/sdaX.

> 
Someone said they still use default,auto,user...


According to [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), 
defaults is short hand for rw, suid, dev, exec, auto, nouser, and async
(see below for the meaning of all these options).

Saying default,auto is redundant. "default,user" means the user option overrides "nouser".
That's fine. You can do "default,relatime,user" if you wish too.
According to [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), the relatime option is the default option for Hardy. 

Here is a short summary of common options:
```
defaults        rw, suid, dev, exec, auto, nouser, async.
user            Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden.
ro 		Mount read-only.
rw 		Mount read-write.
auto         	The filesystem can be mounted automatically at bootup. This is really unnecessary as this is the default action of mount -a anyway.
noauto       	The filesystem will NOT be automatically mounted at startup, or when mount passed -a. You must explicitly mount the filesystem.
dev/nodev    	Interpret/Do not interpret character or block special devices on the file system.
exec/noexec     Permit/Prevent the execution of binaries from the filesystem.
suid/nosuid     Permit/Block the operation of suid, and sgid bits.
nouser          Only permit root to mount the filesystem. This is also a default setting.
sync/async   	All I/O to the file system should be done (a)synchronously.

```

---

### Post by Bruce M. on 2008-07-10
**@ unutbu**

WOW!!!!!!!!!!  GREAT READ!!  Thanks unutbu.

To continue ... for all who have helped.

Now to make things right. I got everything working thanks to the help here and would like to say:

[CENTER]**[COLOR="Blue"][SIZE="6"]Thank you all![/SIZE][/COLOR]**[/CENTER]

Then after I got it all fixed up, I had a .gvfs problem and something with SCIM popped up and wouldn't allow me to type properly in gedit. That ended up being the straw that broke the camels back.

I backed up my /home and reinstalled Xubuntu 8.04 today, and made things easier:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c6866abf-2476-475a-96a4-0d6dc5804ddb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=E531-3CB1  /media/W2K            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=16468fa0-2f49-4b96-b552-4a3ad834654a /home           ext3    relatime        0       2
# /dev/sdb2
UUID=bbc1fb95-5fa9-4638-9421-2fa13f4a2af2 /media/Data     ext3    relatime,auto,user        0       2
# /dev/sdb1
UUID=54f6405d-de40-4c38-ad04-993565e8d36a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
As you can see, /, /home and /media/W2K are on the 200G HD and /media/Data and "swap" on the 80G HD.

Next I'm going to unmount (should have done that at Install Setup) the /media/W2K partition as it is "empty" and I'm hoping I can keep it that way. Maybe that's why the UUID is so short?

I'm Windows Free, no offense Bill, Windows served me well (?¿?) for many years, now I'm going to give Linux the same amount of run time.

**Thank you everyone for all your help and input. I've learned a lot with these two threads.**

CHIMO!
Bruce

---

