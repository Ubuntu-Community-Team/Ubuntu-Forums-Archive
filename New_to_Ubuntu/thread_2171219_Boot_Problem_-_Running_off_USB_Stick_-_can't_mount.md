---
title: "Boot Problem - Running off USB Stick - can't mount"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by zootoxin on 2013-08-29
Hi Ubuntu-ers

I created a USB stick for booting my Pro-liant microserver following this guide - [http://ubuntuforums.org/showthread.php?t=2060493&p=12250188#post12250188](http://ubuntuforums.org/showthread.php?t=2060493&p=12250188#post12250188)

I also had a 250gb drive and a 3TB drive and everything was just lovely. 

Then I added a 4tb drive, I added lines to the fstab and an auto start command

fstab

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/media/250GB_	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
/dev/sdb1	/media/3TERA1	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
/dev/sdb2	/media/3TERA2	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
/dev/sdc2	/	ext4	errors=remount-ro	0	1
/dev/sdc3	/home	ext2	defaults	0	2
/dev/sdc1	/windows	vfat	utf8,umask=007,gid=46	0	1
/dev/sdc4	none	swap	sw	0	0
[COLOR=#008000]/dev/sde1	/media/T4P1	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0[/COLOR]
[COLOR=#008000]/dev/sde2	/media/T4P2	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0

[/COLOR]Start-up
udisks --mount /dev/sde
[COLOR=#008000]
[/COLOR]The Problem I am having is whenever I reboot I get an error on
/Windows - skip
/home - skip
Hang.

I can't get booted up and logged in unless I remove the T4 drive, removing the T4 drive changes the error to /T4P1 - Skip T4P2 Skip 
then its ok.

As this is a server I dont want to have a monitor attached but with these problems thats not possible.

Any ideas whats wrong?

Thanks

PS. I hope that makes sense[COLOR=#008000]



[/COLOR]

---

### Post by oldfred on 2013-08-29
It looks like you are using device not UUID to mount partitions. But the entire reason for changing to UUIDs was to avoid the kind of issue you are having.

I find with my system that drives regularly change drive letter. I did not realize until later but I skipped a port on motherboard. So sda is always sda, but if I reboot with a flash drive in it becomes sdb and every other drive is one letter later. But if I plug in flash drive it normally is sde. But I do not have any mount issues as I use UUIDs.

       sudo blkid -c /dev/null -o list

better to use example from this:

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

