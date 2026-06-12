---
title: "Changing permissions on USD external HD"
date: 2014-12-04
forum: New to Ubuntu
---

### Post by rod52 on 2014-12-04
HD is a seagate.  I am trying to change permissions because I just want to use it for back files.  File manager says I do not have permissions.  When I plug it in, I do not get an indication that it is connected.  The file manager sees it. When I right click, I choose mount. If I choose Safely Remove Device, I get the following message. Unable to stop Seagate, Unable to find  block device for drive.  So I think when I try various commands in xterm, it fails because I suspect that it is not really mounted. xterm says no such file or directory.  This is before trying to safely remove the device.  In properties, permissions are User: root, group: root. If look at the path, computers/media/name/, I see a folder name that consists of a long string of numbers.  Any ideas?

---

### Post by yancek on 2014-12-04
> If look at the path, computers/media/name/, I see a folder name that consists of a long string of numbers.  Any ideas? 		

That's the UUID, universally unique identifier.  When you access a file/directory inside it what are the permission, owner:group.  Do you have any partitions or filesystem on it?  Is it formatted?

---

### Post by rod52 on 2014-12-04
Yancey,  I think I resolved it.  In part of the CHMOD command, /media/dsk, I thought dsk was the dev name such as sdf.  Turned out, it was the subfolder name within the media folder.  I have not rebooted to see if it is fixed permanently, as I have seen others say that after reboot, the HD reverted back to original permissions.  But at least I can copy files to that HD now.  As far as I can tell, the permissions were root:root.  Still are.  The HD was formatted to EXT4.  I did not do anything with partitions.  However, I still do not get an indication that it is connected, nor can I "Safey Remove Device".  I still get the "Unable to stop Seagate, Unable to find  block device for drive" message.

---

### Post by yancek on 2014-12-04
I don't use Ubuntu as my primary system but, when I have used it the /media/user directory is root:root but if I go into /media/user/folder the folders are owned by my user.  The sdf or whatever you get is the drive, usually it will have a number after it indicating the partition (sdf1) and the mount point is either a UUID under /media/user/ or an assigned label.  If you want to copy to a directory or mount point owned by root, just use sudo.

---

### Post by rod52 on 2014-12-05
Thanks Yancek

---

### Post by haplorrhine on 2014-12-06
I haven't been able to "safely remove drive" since I upgraded from 14.04.
If it's root, you can still eject it with "sudo eject /media/username/name-of-drive". // *Maybe sudo is superfluous there??*

---

