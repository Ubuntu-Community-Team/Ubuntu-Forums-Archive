---
title: "umount from adb"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by unibroker on 2012-11-20
I have pushed a zip to my device and now want to safely detach my usb cable.  When I'm in adb I get ```
$ adb shell
# umount /sdcard
umount: can't umount /mnt/sdcard: Device or resource busy
```.  When I'm at the BASH prompt I get ```
$ umount /sdcard
umount: /sdcard is not mounted (according to mtab)
```

Any thoughts?

---

### Post by Bashing-om on 2012-11-20
unibroker;
I may be of little help, but sometimes bouncing things off of others proves productive.
Hence: I do not recognize the term "adb" -> but when in adb what is the result of terminal code ```
mount
``` as compared to the same in Bash.
Looking at how "adb" could mount the sdcard device.
[INDENT]seeking a way to help <== BDQ

[/INDENT]

---

### Post by unibroker on 2012-11-20
> **Bashing-om said:**
> unibroker;
I may be of little help, but sometimes bouncing things off of others proves productive.
Hence: I do not recognize the term "adb" -> but when in adb what is the result of terminal code ```
mount
``` as compared to the same in Bash.
Looking at how "adb" could mount the sdcard device.
[INDENT]seeking a way to help <== BDQ

[/INDENT]

The reason I asked is that I have corrupted more files in just physically disconnecting the usb cable instead of being sure that I had unmounted whatever files I had been working on.  This time I just entered "exit" until I got back to the BASH prompt and then disconnected.  The files seem okay and LOST.DIR hasn't filed up with corrupted files!  Next time I use adb I'll try to mount and then umount and see what messages I get.  Couldn't hurt.

---

### Post by Bashing-om on 2012-11-20
Linux caches data that is not written to the device until the device is properly (un)mounted-> thus the practice to always insure devices are "safely" removed.

[INDENT]my 1 pounds worth <== BDQ

[/INDENT]

---

### Post by unibroker on 2012-11-23
I'm currently just going to nautilus and right-clicking on the device to unmount (called "eject").  It must be effective because the device does not show the adb link anymore AND I haven't ended up with a full LOST.DIR (corrupted files).  The "eject" did give me pause though because when I want to unmount my external hard drive by right-clicking, "unmount" is listed instead.  That led me to think the two options had different results.

---

### Post by Bashing-om on 2012-11-23
confusion understandable -over the years I have seen various nomenclatures to describe the same function - In my experience "unmount" and "eject" or "safely remove" and others all perform the same function; namely to write out that cache -to-disk. (one function performed amongst several)

Anyway, glad ya got it sorted out !

[INDENT][INDENT][INDENT]happy ubuntu'n <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by unibroker on 2012-11-29
This morning I've have successfully pushed a zip to my device but when I try to unmount from the adb shell I get the following <code># umount /sdcard
failed: Device or resource busy</code>

When I exit the shell and get back to the terminal prompt it tells me nothing is mounted.  I know it is because when in adb shell I can see the contents of the sdcard.

Using nautilus like before is not an option as the device doesn't appear in Devices (therefore the message that no sdcard is not mounted).

Thanks in advance for any advice.

---

### Post by unibroker on 2012-11-29
I'm trying to unmount the following device ```
Bus 001 Device 004: ID 18d1:2d03 Google Inc.
```

The bash prompt says there in nothing mounted when I ```
umount /sdcard/
``` which is on the Google device.

Any ideas?

---

### Post by TheFu on 2012-11-29
If there is any program - or a shell using the storage, you cannot umount it safely.
What is the output of the 'df' command?  The left column, usually with /dev/ or the exact directory are used to umount something.
For example, a few mount points on my box.

```
/dev/md1             1912523780 710009192 1105364048  40% /raid
/dev/sdf6            957536072 854729812  54166252  95% /Data/mb2
```I can** umount /raid** or **umount /dev/md1** or **umount /Data/mb2**.
root auth is usually mandatory too.

---

### Post by unibroker on 2012-11-29
> **TheFu said:**
> If there is any program - or a shell using the storage, you cannot umount it safely.
What is the output of the 'df' command?  The left column, usually with /dev/ or the exact directory are used to umount something.
For example, a few mount points on my box.

```
/dev/md1             1912523780 710009192 1105364048  40% /raid
/dev/sdf6            957536072 854729812  54166252  95% /Data/mb2
```I can** umount /raid** or **umount /dev/md1** or **umount /Data/mb2**.
root auth is usually mandatory too.




There is a device connected to the computer through adb.  From adb shell it tells me sdcard is busy (has been all morning) so I thought maybe I could umount outside the shell.

```
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda6       11533592  4656572   6291140  43% /
udev             1016296        4   1016292   1% /dev
tmpfs             410040      920    409120   1% /run
none                5120        0      5120   0% /run/lock
none             1025096      564   1024532   1% /run/shm
/dev/sda7      174498536 46651388 118983100  29% /home
/dev/sdf2       55296404 48582404   3905068  93% /media/6e9ac323-45f6-4cb0-acca-8277530a3584
/dev/sdf5       19868320  2028836  17839484  11% /media/HP Pocket Media Drive
```

---

### Post by TheFu on 2012-11-29
Well, adb probably automatically mounts your android devices when you connect - though I don't know. I've only used adb from a Windows PC.  

Why not just shutdown the android device and unplug it from the PC?

---

### Post by unibroker on 2012-11-29
> **TheFu said:**
> Well, adb probably automatically mounts your android devices when you connect - though I don't know. I've only used adb from a Windows PC.  

Why not just shutdown the android device and unplug it from the PC?

Because on the device end there was always an emphatic message to make sure I've unmounted from the pc before I turn off adb.  Lacking any better recommendations turning the device off is what I ended up doing.  On boot it seems no damage was done because I have a folder in my sdcard named LOST.DIR.  It usually fills up with corrupted files and it's still empty.

Thanks for your input.

---

### Post by unibroker on 2012-11-29
I will hazard a guess that simply turning off the device does not properly unmount it.  I just tried to flash the zip that I had pushed from my computer and it failed.  The log said that the file was empty.  What I have researched is that this happens when devices aren't properly unmounted.  Cheap lesson because I still have the file on my pc so can push it again.  Before that I've got to make sure I know the procedure to properly unmount.

---

### Post by Bashing-om on 2012-11-29
Don't know what could possibly be going on, but, try this; See if it gives us any hint.
When you next use the adb device and get the "busy" indicator. run this:
--
As a better way is to learn which process uses the device:

# umount /dev/sdb1 <where sdb1 is the adb device's name>
```
umount: /dev/sdb1
```: device is busy
```
fuser -m /dev/sdb1
```/dev/sdb1: 3322 --this is the example output--
(3322 is id of the process that uses the device. in order to find out  what it is, do this:
```
 ps aux | grep 3322
``````
kill -9 3322
``````
umount /dev/sdb1
```#

that should work.. 
[INDENT][INDENT][INDENT]puzzle'n it out ==> BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by unibroker on 2012-11-29
> **Bashing-om said:**
> Don't know what could possibly be going on, but, try this; See if it gives us any hint.
When you next use the adb device and get the "busy" indicator. run this:
--
As a better way is to learn which process uses the device:

# umount /dev/sdb1 <where sdb1 is the adb device's name>
```
umount: /dev/sdb1
```: device is busy
```
fuser -m /dev/sdb1
```/dev/sdb1: 3322 --this is the example output--
(3322 is id of the process that uses the device. in order to find out  what it is, do this:
```
 ps aux | grep 3322
``````
kill -9 3322
``````
umount /dev/sdb1
```#

that should work.. 
[INDENT][INDENT][INDENT]puzzle'n it out ==> BDQ

[/INDENT][/INDENT][/INDENT]

This is what I get inside the adb shell ```
root@android:/ # umount /sdcard/
failed: Device or resource busy
1|root@android:/ # umount /dev/sdg
failed: No such file or directory
```

When the device was viewable from nautilus and gparted it was assigned sdg and sdh for the sdcard and emmc storage.

I read about just running the command mount for the bash prompt so I thought I might try it from the adb shell thinking that it might show me what is "busy" ```
1|root@android:/ # mount          
rootfs / rootfs ro,relatime 0 0
tmpfs /dev tmpfs rw,nosuid,relatime,mode=755 0 0
devpts /dev/pts devpts rw,relatime,mode=600 0 0
proc /proc proc rw,relatime 0 0
sysfs /sys sysfs rw,relatime 0 0
none /acct cgroup rw,relatime,cpuacct 0 0
tmpfs /mnt/asec tmpfs rw,relatime,mode=755,gid=1000 0 0
tmpfs /mnt/obb tmpfs rw,relatime,mode=755,gid=1000 0 0
none /dev/cpuctl cgroup rw,relatime,cpu 0 0
/dev/block/mmcblk0p2 /rom vfat rw,noatime,nodiratime,uid=1000,gid=1000,fmask=0117,dmask=0007,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/block/mmcblk0p5 /system ext4 ro,relatime,user_xattr,acl,barrier=1,data=ordered 0 0
/dev/block/mmcblk0p6 /data ext4 rw,nosuid,nodev,noatime,user_xattr,acl,barrier=1,data=ordered,noauto_da_alloc 0 0
/dev/block/mmcblk0p7 /cache ext4 rw,nosuid,nodev,noatime,user_xattr,acl,barrier=1,data=ordered 0 0
/sys/kernel/debug /sys/kernel/debug debugfs rw,relatime 0 0
/dev/block/vold/179:49 /storage/sdcard1 vfat ro,dirsync,relatime,uid=1000,gid=1015,fmask=0702,dmask=0702,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro 0 0
/dev/block/vold/179:49 /mnt/secure/asec vfat ro,dirsync,nosuid,nodev,noexec,relatime,uid=1000,gid=1015,fmask=0702,dmask=0702,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro 0 0
tmpfs /storage/sdcard1/.android_secure tmpfs ro,relatime,size=0k,mode=000 0 0
/dev/block/vold/179:8 /storage/sdcard0 vfat rw,dirsync,nosuid,nodev,noexec,relatime,uid=1000,gid=1015,fmask=0702,dmask=0702,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro 0 0
```  Means next to nothing to me.  You?

Like I said in the OP of this morning, I was successful in pushing the zip to my sdcard.  However, when I went to flash it the operation failed because "zip file is empty".  I read this morning that this is the result of improper umount ing.

Thanks for your input.

---

### Post by nothingspecial on 2012-11-29
Merged.

---

### Post by Bashing-om on 2012-11-29
Well, the output is a new one on me, I also do not understand what it is telling us.
Let's approach from another direction:
```
sudo fdisk -l
``` <lower case "L">
with the android device connected.

That will tell us how ubuntu sees the device to get the device identifier for the fuser command sequence.

[INDENT][INDENT]poke'n and alook'n <== BDQ

[/INDENT][/INDENT]

---

### Post by unibroker on 2012-11-29
> **Bashing-om said:**
> Well, the output is a new one on me, I also do not understand what it is telling us.
Let's approach from another direction:
```
sudo fdisk -l
``` <lower case "L">
with the android device connected.

That will tell us how ubuntu sees the device to get the device identifier for the fuser command sequence.

[INDENT][INDENT]poke'n and alook'n <== BDQ

[/INDENT][/INDENT]

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81922047    40960992+   7  HPFS/NTFS/exFAT
/dev/sda2       470270745   488392064     9060660    c  W95 FAT32 (LBA)
/dev/sda3        81924094   470269951   194172929    5  Extended
/dev/sda5       459929600   470269951     5170176   82  Linux swap / Solaris
/dev/sda6        81924096   105359359    11717632   83  Linux
/dev/sda7       105361408   459923455   177281024   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c8b9b3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1           16126    43943935    21963905    f  W95 Ext'd (LBA)
/dev/sdf2        43943936   156301311    56178688   83  Linux
/dev/sdf5           16128    39752781    19868327    7  HPFS/NTFS/exFAT
/dev/sdf6        39753728    43943935     2095104   82  Linux swap / Solaris
```

This is what is so mystifying (to me); the device doesn't appear.  I assume that is why I can't "Safely Unmount" from Nautilus anymore.  However it does appear when I ```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 03f0:110c Hewlett-Packard 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 18d1:2d03 Google Inc.
```

The device is Google Inc.

From adb shell ```
root@android:/ # lsusb
Bus 001 Device 001: ID 1d6b:0002
```
I have tried using vendor ID with umount but with no success.

---

### Post by Bashing-om on 2012-11-29
what to me is really strange;  Bus 001 Device 001: ID 1d6b:002 --you identify as "google"
whereas lsusb -> Bus 001 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub --
[INDENT] I gonna do some rooting around later and see what I can find as to how android is attatched to the file system.


[INDENT]scratch'n and look'n ==> BDQ

[/INDENT][/INDENT]

---

### Post by Bashing-om on 2012-11-29
oh unibroker, The world of adb is so confusing to me !
From what I can gather the identifier "sdcard" is valid from ubuntu's perspective; but do not know what you will have to set up in adb's world to relate with ubuntu;
"andriod tools" package (adb and fastboot) installed on the andriod device ?
Are the rules set up properly on the adb ?
see this link for some insight or guidance:
[http://ubuntuforums.org/showthread.php?t=1918512](http://ubuntuforums.org/showthread.php?t=1918512)

I know nothing, and for that reason I can not help you, But I will continue to follow this thread to further my knowledge -> this ole man may need it in the world that is coming !

[INDENT][INDENT]just plain out of date ==> BDQ

[/INDENT][/INDENT]

---

### Post by unibroker on 2012-11-29
> **Bashing-om said:**
> oh unibroker, The world of adb is so confusing to me !
From what I can gather the identifier "sdcard" is valid from ubuntu's perspective; but do not know what you will have to set up in adb's world to relate with ubuntu;
"andriod tools" package (adb and fastboot) installed on the andriod device ?
Are the rules set up properly on the adb ?
see this link for some insight or guidance:
[http://ubuntuforums.org/showthread.php?t=1918512](http://ubuntuforums.org/showthread.php?t=1918512)

I know nothing, and for that reason I can not help you, But I will continue to follow this thread to further my knowledge -> this ole man may need it in the world that is coming !

[INDENT][INDENT]just plain out of date ==> BDQ

[/INDENT][/INDENT]

Very much appreciate the effort!  I have gone in and added the 1d6b to my existing udev rules.  I thought I was making progress when I got this from the adb shell ```
# su mount /sdcard                                            
sh: /sdcard: Permission denied
```  Kind of surprised because I'm already in the shell at root level (without the "su" I get that device is busy).

Thanks again.

---

### Post by Bashing-om on 2012-11-30
still hanging in there;
Present situation as I see it :
1. -as you now know- can not (un)mount the adb from within it as the adb device is held busy because you are in it. Can only be (un)mounted from within the ubuntu os.
2. Root in adb: "su" is not to be used as already root user has been set.
3. What info does /etc/mtab give for mounting info ?
4. How to safely (un)mount the device?

I am working on some method to identify the adb device.
[INDENT][INDENT]still learning even after all these years ==> BDQ

[/INDENT][/INDENT]

---

### Post by unibroker on 2012-11-30
> **Bashing-om said:**
> still hanging in there;
Present situation as I see it :
1. -as you now know- can not (un)mount the adb from within it as the adb device is held busy because you are in it. Can only be (un)mounted from within the ubuntu os.
2. Root in adb: "su" is not to be used as already root user has been set.
3. What info does /etc/mtab give for mounting info ?
4. How to safely (un)mount the device?

I am working on some method to identify the adb device.
[INDENT][INDENT]still learning even after all these years ==> BDQ

[/INDENT][/INDENT]

I found something interesting while in adb shell

```
root@android:/ # ls -l /mnt/sdcard
lrwxrwxrwx root root 2012-11-30 12:59 sdcard -> /storage/sdcard1

```

The last item, "sdcard1" is how both file managers on the device now label the sdcard. What does "sdcard -> /storage/sdcard1" mean?

---

### Post by TheFu on 2012-11-30
> **unibroker said:**
> I found something interesting while in adb shell

```
root@android:/ # ls -l /mnt/sdcard
lrwxrwxrwx root root 2012-11-30 12:59 sdcard -> /storage/sdcard1

```The last item, "sdcard1" is how both file managers on the device now label the sdcard. What does "sdcard -> /storage/sdcard1" mean?

That means it is a softlink ... the real mount point is under /storage. You can't mount/umount anything under /mnt if that is true.

I havne't read all the new comments - seems you may have had 2 questions going at once on the forums.
Is there a reason you don't just open a shell on the device and run commands there?  For android, I like "Terminal IDE".

---

### Post by unibroker on 2012-11-30
> **TheFu said:**
> That means it is a softlink ... the real mount point is under /storage. You can't mount/umount anything under /mnt if that is true.

I havne't read all the new comments - seems you may have had 2 questions going at once on the forums.
Is there a reason you don't just open a shell on the device and run commands there?  For android, I like "Terminal IDE".

They were merged; bad practice on my part cross-posting.

I think I'm onto something.  Under storage there are directories for what I assume are the sdcard and emmc.  They are sdcard0 and sdcard1.  I assume sdcard1 is the sdcard because it lists the file I pushed this morning.  sdcard0 does not.

---

### Post by Bashing-om on 2012-11-30
That is the path , and with a symlink (yikes)! How and why (not in media ??) Why is it mounting from "mnt" -> have you made a different mount point for the adb device ?
Why it would be linked I can not fathom, presently, going to do some testing here and looking.

back note : irt having to my having to (un)mount a usb twice in nautilus, that is only in ubuntu 12.04 ...ubuntu 10.04 works as expected. AND I just tried to (un)mount a usb thumb drive in 12.04 from the CLI and was not able to power it down (hummm??) at that time nautilus does not recognize the device.

At a later time I will boot up lubuntu 12.04 and see what transpires. Maybe a bug in ubuntu 12.04 (??)

[INDENT][INDENT]back in a bit <== BDQ

[/INDENT][/INDENT]

---

### Post by unibroker on 2012-11-30
> **Bashing-om said:**
> That is the path , and with a symlink (yikes)! How and why (not in media ??) Why is it mounting from "mnt" -> have you made a different mount point for the adb device ?
Why it would be linked I can not fathom, presently, going to do some testing here and looking.

back note : irt having to my having to (un)mount a usb twice in nautilus, that is only in ubuntu 12.04 ...ubuntu 10.04 works as expected. AND I just tried to (un)mount a usb thumb drive in 12.04 from the CLI and was not able to power it down (hummm??) at that time nautilus does not recognize the device.

At a later time I will boot up lubuntu 12.04 and see what transpires. Maybe a bug in ubuntu 12.04 (??)

[INDENT][INDENT]back in a bit <== BDQ

[/INDENT][/INDENT]

This all goes back to setting up my environment.  It was a disjointed affair following tutorials from different sources.  I do recall blindly typing in a symlink in setting up the sdk.

---

### Post by Bashing-om on 2012-11-30
OK, I am back..
on my ubuntu 12.04 system, with a usb thumb drive inserted.
```
ls -la /media
``` has no symlinks- just the expected directories.

so ........... from your ubuntu system with the adb device connected what results:
```
ls -la /media
```
as I look for ubuntu to mount the device in the media directory.
then we compare that to what sdb shows for mounting.

[INDENT]think'n and look'n ==>BDQ

[/INDENT]

---

### Post by unibroker on 2012-11-30
> **Bashing-om said:**
> OK, I am back..
on my ubuntu 12.04 system, with a usb thumb drive inserted.
```
ls -la /media
``` has no symlinks- just the expected directories.

so ........... from your ubuntu system with the adb device connected what results:
```
ls -la /media
```
as I look for ubuntu to mount the device in the media directory.
then we compare that to what sdb shows for mounting.

[INDENT]think'n and look'n ==>BDQ

[/INDENT]

```
ls -la /media
total 100
drwxr-xr-x  4 root root  4096 Nov 30 12:36 .
drwxr-xr-x 25 root root  4096 Nov 30 05:30 ..
drwxr-xr-x 22 jim  root  4096 Nov 27 06:10 6e9ac323-45f6-4cb0-acca-8277530a3584
drwx------  1 jim  jim  90112 Nov 23 06:40 HP Pocket Media Drive
```

The device is not listed.

This is a partial output from BASH:

```
$ ls -la android-sdk-linux/platform-tools/
total 23272
drwxrwxr-x  5 jim jim     4096 Nov  3 10:21 .
drwxr-x--- 11 jim jim     4096 Oct 30 12:48 ..
-rwxrwxr-x  1 jim jim   929400 Oct 30 12:09 aapt
-rwxrwxr-x  1 jim jim   204436 Oct 30 12:09 adb
```

The last line; does this mean the adb has 1 symlink?

---

### Post by Bashing-om on 2012-11-30
hruump...if it is not mounting in /media ------------where is adb mounting at ??It has to mount somewhere, have you made a mount point -else wise- for it in ubuntu ?

one more time from the ubuntu install, adb connected:
```
mount
```see if I can decipher how it is mounted, enabling us to (un)mount it from the cli.

---

### Post by unibroker on 2012-11-30
> **Bashing-om said:**
> hruump...if it is not mounting in /media ------------where is adb mounting at ??It has to mount somewhere, have you made a mount point -else wise- for it in ubuntu ?

one more time from the ubuntu install, adb connected:
```
mount
```see if I can decipher how it is mounted, enabling us to (un)mount it from the cli.

```
$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda7 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/jim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jim)
/dev/sdf2 on /media/6e9ac323-45f6-4cb0-acca-8277530a3584 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf5 on /media/HP Pocket Media Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
```

If I unknowingly made a mount point it would have been during the setup of the Android SDK.  I recall entering some code in as a last part of one of the tutorials and not understanding why he was adding symlinks (I recall 2).  It was some months ago.  This morning I was thinking of just uninstalling the sdk and reinstalling it but thought that might break other things.

---

### Post by Bashing-om on 2012-11-30
Blows me away. Your "mount" output is near identical to mine without a usb device connected, with the obvious differing sdf2/5 and a final "gvfs-fuse-daemon" entry.

I do not have a clue as to how the adb device can possibly be mounted and there exist no entry from "mount" !!!

Maybe that last "gvfs-fuse-daemon" -> root is where/how it is mounted ??


[INDENT]gonna go and get smarter ==> BDQ

[/INDENT]

---

### Post by unibroker on 2012-11-30
> **Bashing-om said:**
> Blows me away. Your "mount" output is near identical to mine without a usb device connected, with the obvious differing sdf2/5 and a final "gvfs-fuse-daemon" entry.

I do not have a clue as to how the adb device can possibly be mounted and there exist no entry from "mount" !!!

Maybe that last "gvfs-fuse-daemon" -> root is where/how it is mounted ??


[INDENT]gonna go and get smarter ==> BDQ

[/INDENT]

As a last gasp measure I could do one more dirty umount, run another mount and see where they differ.  sdf2/5 are my external hard drive partitions.

---

### Post by Bashing-om on 2012-11-30
Think I am on the right path looking at gvfs (Gnome Virtual File System), cifs and samba mounts through it ...betcha adb does too !

While I am pursuing my present course of study, How bout you google'n 
"gvfs-fuse-daemon android ubuntu" see what you can find for the mounting.
will meet back here when I have gained more knowledge.

---

### Post by unibroker on 2012-11-30
> **Bashing-om said:**
> Think I am on the right path looking at gvfs (Gnome Virtual File System), cifs and samba mounts through it ...betcha adb does too !

While I am pursuing my present course of study, How bout you google'n 
"gvfs-fuse-daemon android ubuntu" see what you can find for the mounting.
will meet back here when I have gained more knowledge.

[http://mikebeach.org/2011/04/23/accessing-media-and-gvfs-mounts-from-the-command-line-in-ubuntu-linux/]("http://mikebeach.org/2011/04/23/accessing-media-and-gvfs-mounts-from-the-command-line-in-ubuntu-linux/")

From my BASH ```
:~/.gvfs$ ls -l
total 0
```

Apparently the problem is that Jellybean or Android 4.+ doesn't support mass storage anymore.  That's why I could see the device under Gingerbread or Android 2.7 but not under Jellybean.  I have the umount problem under Jellybean.

[http://askubuntu.com/questions/215528/galaxy-note-ii-mtp-on-ubuntu-12-04]("http://askubuntu.com/questions/215528/galaxy-note-ii-mtp-on-ubuntu-12-04") and even better [http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access]("http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access")

I just checked my "USB computer connection" under settings on my device and Media device (MTP) is ticked.

---

### Post by Bashing-om on 2012-11-30
This link, while not answering my quest, may be just what you are looking for !
If you are running MTP (Media Transfer Protocol) on the android,
[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

later I get back to the links you provided. I still on a quest to see how to find that path.

---

### Post by unibroker on 2012-11-30
To gladly mark this thread closed, I have to tell you that the answer was on the device running jellybean under Settings, Storage.  Then select menu (3 dots in upper right hand corner) under Storage and select "USB computer connection".  You then have 3 options, MTP, PTP and Mass Storage.  My MTP was ticked which is why I couldn't see the device in nautilus and therefore couldn't Safely Remove it.  As soon as I ticked Mass Storage my nautilus refreshed and the device's emmc and sdcard both appeared.

Thanks to all for their input but most especially Bashing-om.  I hope you find your PATH.

---

### Post by TheFu on 2012-12-01
Is there a difference in mount points between the 3 different ways you are connecting?

[LIST=1]
[*]locally **on** the android device
[*]remotely through adb
[*]from an attached Linux or Windows "host" system?
[/LIST]
I think the answer is 100% yes.  Expecting Android to behave the same from each of these different connection doesn't make sense.


Personally, I avoid using adb unless required. It is easier to ssh into the device to accomplish things. With the appropriate shell available, Android can feel enough like Linux to be useful. My android devices feel more like Linux than dd-wrt, tomato or ESXi shells, THAT is certain.


OTOH, I probably completely missed the point of these merged threads.

---

### Post by unibroker on 2012-12-01
> **TheFu said:**
> Is there a difference in mount points between the 3 different ways you are connecting?

[LIST=1]
[*]locally **on** the android device
[*]remotely through adb
[*]from an attached Linux or Windows "host" system?
[/LIST]
I think the answer is 100% yes.  Expecting Android to behave the same from each of these different connection doesn't make sense.


Personally, I avoid using adb unless required. It is easier to ssh into the device to accomplish things. With the appropriate shell available, Android can feel enough like Linux to be useful. My android devices feel more like Linux than dd-wrt, tomato or ESXi shells, THAT is certain.


OTOH, I probably completely missed the point of these merged threads.

My main purpose for having the device is as a learning tool.  It is a rooted Barnes and Noble Nook Color to which I've been feeding other people's roms.  I've recently "built", and I use that term loosely because the pc does most of the building, a rom and want to continue to tinker/learn with the Android OS.  The one way I know of to do that is through adb.  

As mentioned, the administrators merged the threads.  I originally had posted in Development and Programming but later felt that I might be more successful in my search if I posted in Absolute Beginners Section.  Didn't realize until later that they would move your thread if asked.

---

### Post by Bashing-om on 2012-12-01
Glad you got it fingered out !
Be advised it is also "possible" to (un)mount the device via cli with the command
"gvfs-mount -u <path>: I am still looking for a means to identify that path as established by the gvfs daemon.

I have to thank you for this opportunity to learn a bit more about this operating system !
I will be engrossed with this aspect for some time to come.
[INDENT][INDENT]still learning after all these years ==> BDQ

[/INDENT][/INDENT]

---

