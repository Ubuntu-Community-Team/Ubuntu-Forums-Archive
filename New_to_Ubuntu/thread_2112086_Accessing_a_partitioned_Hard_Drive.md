---
title: "Accessing a partitioned Hard Drive"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by nbrown104 on 2013-02-03
I just installed ubuntu 12.10 on a computer already running Windows 7. I needed the original operating system to run certain programs, but before dual-booting with ubuntu I partitioned the harddrive and named it "Shared". I can access it from either OS, but how do I access it from command line (ubuntu)?

i.e, "cd ~/Shared" doesn't seem to work, as it would with a simple directory.

Much appreciated!

---

### Post by Bashing-om on 2013-02-03
nbrown104; Hi ! Welcome to the forum.

In order to access that partition from the command line one has to mount it to the file system. Try this:
```
sudo fdisk -l # to identify the partition
 sudo mkdir /mnt/Shared #make a mount point -note that linux is case sensitive "S" does not = "s"
sudo mount /dev/sda5 /mnt/Shared # attach to the file system - change "sda5" to "fdisk's" identification
ls -la /mnt/Shared/<directory>/<file> # to list contents

```The partition must be cleanly (un)mounted prior to shutting the system down:
```
sudo umount /mnt/Shared
```[INDENT]advise results
[/INDENT]

---

### Post by nbrown104 on 2013-02-04
Thanks! That worked fine! Will this have to be done each time I start up the computer?

---

### Post by Impavidus on 2013-02-04
No, you can put it in /etc/fstab. It will be mounted and unmounted automatically at boot/shutdown. Add the line```
/dev/sdaX /mnt/Shared ntfs <options> 0 0
```

---

### Post by oldfred on 2013-02-04
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

Above example is mounting to /media. If you mount to /media or /home directly it will also show in left panel of Nautilus. If you mount in /mnt it will not be in Nautilus but you have to drill down to find it. But Then you can link folders from the shared into your /home. I actually have all the standard data folders like Music Documents etc in shared partitions, one NTFS and the other Linux formats and link folders into /home.
       
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

    Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

---

