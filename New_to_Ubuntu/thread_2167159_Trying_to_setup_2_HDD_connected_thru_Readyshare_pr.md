---
title: "Trying to setup 2 HDD connected thru Readyshare properly"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by csswormy on 2013-08-12
I've managed to mount the HDD by reading through the forums, but I can't cut and paste things I've saved into the HDD.  Pretend I don't know anything about Ubuntu or Linux (cause I don't) and please show me how to set permissions.

This is one error when I try to share the folder I'm trying to save to (which I'm not even sure I should be doing):

"'net usershare' returned error 255: net usershare add: cannot share path /home/csswormy11/Media_Drive/Stephen's Pics/Pics & Stuff/photos/Unknown/Real/ToD as we are restricted to only sharing directories we own.    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this."

I don't even begin to know where to put that or if that is even what I need to be doing.  I don't think I should, because the HDD's are not connected to the computer and therefore shouldn't need to share them.  I'm assuming that its some setting or permission that's causing the problem.

I followed the directions from this post to setup a folder to mount to (maybe that is causing the problems?):

[http://ubuntuforums.org/showthread.php?t=1163683&page=2](http://ubuntuforums.org/showthread.php?t=1163683&page=2)

Here's my fstab to show what worked in case its ok:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d6f09af4-c5a0-4129-bbab-5bb2fd17af2d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5f034008-d8c0-42eb-9e36-6fa553a22050 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


//192.168.1.1/Media_Drive /home/csswormy11/Media_Drive smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.1/Data_Drive /home/csswormy11/Data_Drive smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Any and ALL help is GREATLY appreciated (except the unhelpful trolls...lol.)

---

