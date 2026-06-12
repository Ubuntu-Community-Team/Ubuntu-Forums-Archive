---
title: "Dualboot automount &quot;storage&quot; partition?"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by dylan1020 on 2013-04-11
I have a storage partition that I share between Ubuntu 13.04 and Windows 7. I need to be able to automount this said drive. I share firefox profiles and music on this partition so for obvious reasons I need to automount this. I know I need to use fstab and done some research on it but I have no idea what "UUID" is or anything like that. It is a NTFS drive and it is sda7 on my partition table if that helps any. Thank you for your help.

---

### Post by nerdtron on 2013-04-11
Open up the software center and install the "ntfs-config" tool. It's a GUI tool and let me auto mount my partitions.

---

### Post by fantab on 2013-04-11
```
sudo blkid
```

will reveal the [UUID]("http://en.wikipedia.org/wiki/Universally_Unique_Identifier")s of the partitions. its simple.

---

### Post by zrdc28 on 2013-04-11
The first thing you need to know is the name of that partician before you can mount it  "fdisk -l" will give you that name! 
Post the output here and someone will help you.

---

### Post by oldfred on 2013-04-14
The NTFS config has not be maintained for years, so it may not give you the best mount. Better to use template from below and use your UUID and mount point.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
[COLOR=#ff0000]UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0[/COLOR]
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example, but you can use any name you want:
sudo mkdir /media/WinD

      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

---

