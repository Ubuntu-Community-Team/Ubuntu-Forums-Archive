---
title: "Enable secondary drive at startup"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by lagarkane on 2013-04-12
Hi everyone,

Here's my problem:

I'm in dual boot with a windows seven and a Linux system, and I have my data (both for Windows and Linux) on an ntfs drive.
This is not a problem, I can access it without problems in /media, but I have some startup applications using resources on this drive (my wallpapers, my dropbox folder, etc..), and Linux cannot acces them as long as I don't go on my secondary drive using the file browser for instance.
I tried to make a startup shell script (I've put it into /etc/rc2.d) that makes a simple `cd /media/<mySecondaryDrive>`, but it doesn't solve my problem.
Do you know how I can handle this?

Thanks in advance!

---

### Post by oldfred on 2013-04-12
Best to permanent mount with fstab.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

You have to use your UUID and can have any name you like to mount point instead of WinD.

 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

Lots of details, with NTFS you do not have permission issues as that is set by the mount in fstab.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Another explanation:

 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by lagarkane on 2013-04-12
Thanks a lot for this answer,
Works perfectly, of course =)
I was starting to execute the mount command through a shell script running at startup, like i did with cp at the first time, but it is much more "clean" to do it your way.

Thanks again =)

---

### Post by oldfred on 2013-04-12
Glad it worked. :)

---

