---
title: "Have an automount script running, now am not allowed access to my addtional drives"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by Colonel Forbin on 2012-07-01
I have been trying to get my additional drives to automount. I tried several solutions in the forum, til I found one where someone had written a gui to set up automount. I chose automount (the other option is not to automount). Now it mounts my drives in /media, but will not allow me to access them. I ran the "don't automount" option but it changed nothing. they still automount in /media, with no access. Help, I need access to these drives.

Thanks, 
Forbin

---

### Post by oldfred on 2012-07-01
Only if drives are slow coming up and you boot really fast should you need a script after booting.

You add the partitions you want to mount to fstab. You have to set your permissions & ownership so you can read & write correctly. 

Caution:
Do not run any command with the -R (for recursion) on any system folder or else you will be reinstalling. Only run on data folders, so you also update the data folders inside the top level folder.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

---

### Post by Colonel Forbin on 2012-07-01
I used the fstab instructions, and some of them automounted with me having access to them. However, this script that I used initially that brought up the gui to automount is still running, and mounted two of the drives before fstab got to them. In my boot up it then said that <mydiskname> was not ready or present and I had to select Skip mounting. I've found that when they mount using this script, I can umount them from a root terminal, then remount them in nautilus. I'd rather not have to do that everytime though. Let me see if I can find the thread I picked up this script in.

---

### Post by Colonel Forbin on 2012-07-04
bump

---

### Post by oldfred on 2012-07-04
Have you tried turning script off?

---

