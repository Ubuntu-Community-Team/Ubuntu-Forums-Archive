---
title: "boot up did not mount all of my drives?"
date: 2016-12-21
forum: New to Ubuntu
---

### Post by michael351 on 2016-12-21
I am running Ubuntu version 16.04 LTS and recently updated the packages as per the boot up notifications.
I noticed that one of my external USB drives did not mount ... and the directory tied to that drive was listed as owned by root instead of my login ID.

I don't understand the behavior. I notice this only when I remote log in via putty. I don't see the drive anywhere (i.e. "sudo df -ka").

However, when I boot up, log in and start the desktop, this issue is gone. All of my drives are mounted and available and ownership is set to me.
I use the system mostly for Kodi - but now I am loving Ubuntu and want to learn more and do more with the desktop.

---

### Post by SeijiSensei on 2016-12-21
Is the drive being mounted by an entry in [/etc/fstab]("https://help.ubuntu.com/community/Fstab")?  That's the only reliable way to mount filesystems at boot.

---

### Post by michael351 on 2016-12-21
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=24af3e43-a0b1-4376-87b7-7c0cfad2d050 /               ext4    errors=remount
-ro 0       1
# swap was on /dev/sda7 during installation
UUID=b93d264a-92c0-4646-90c9-052cc0f12021 none            swap    sw
  0       0


This is all that /etc/fstab has in it ....

Additional info: 
When I log in to my account via the desktop, log out and then open a putty console. The disk shows up and is available. 

The disk should be mounted as /dev/sdb1

I can mount it manually .... i.e. mount /dev/sdb1 /home/name2/directory  .... 
and it shows up fine, but the owner is listed as root instead of my account (probably need an owner flag to be set).

I'm just puzzled why it was no issue before and now this behavior ... 
What entry do I need to have in the fstab file to set this properly.

thanks

---

### Post by michael351 on 2016-12-22
I placed an entry in the fstab file and it seems to work fine now. Still not sure I understand why desktop boot mounts the drive, but when I boot and open a terminal the drive does not mount.
Regardless it now works. Thanks to posts in other threads in how to properly set up fstab for external disks.

---

