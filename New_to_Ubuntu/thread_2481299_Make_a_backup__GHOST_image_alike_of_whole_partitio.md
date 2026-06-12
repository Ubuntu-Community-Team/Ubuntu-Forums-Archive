---
title: "Make a backup / GHOST image alike of whole partition of UBUNTU (/dev/sda) ?"
date: 2022-11-24
forum: New to Ubuntu
---

### Post by patrick2957672 on 2022-11-24
Hello,

I installed the ubuntu standard on my harddisk of notebook. 

How to make a backup / "GHOST" image alike of whole partition of UBUNTU (/dev/sda) ?

dd is way to slow. alternative?

kind regards
Patrick

---

### Post by VMC on 2022-11-24
'fsarchiver' is very easy to use. So is 'clonezilla'. I find 'Macrium' to be outstanding for any filesystem, and that includes their free version.

---

### Post by Impavidus on 2022-11-26
An image type backup means copying the entire contents of the harddrive to a backup drive. Some tools are smart enough to skip the unused parts of the filesystem or the unallocated parts. That makes them a lot faster on almost empty drives, but it makes no difference on fuller drives. dd isn't that smart (and shouldn't be), but some of the tools mentioned above are.

Anyway, disk images are usually not considered that good as backups. With file based backups, you can keep multiple versions of each file and when creating new backups, you only copy the things that were changed. Restoring the image of your Ubuntu partition probably takes more time than reinstalling Ubuntu and the image will be outdated within a day, so many (including I) don't create backups of the OS. Of course, we do create backups of our documents.

BTW, sda is your entire harddisk. The Ubuntu partition will be called sda1 or sda2 or something like that.

---

### Post by patrick2957672 on 2022-11-27
To restore a disk, fully sda, that is on an clonezilla image stored on external WD usb drive, it is: 

```
 
 /usr/sbin/ocs-sr   restoredisk   ubuntu-amd64-sda-harddisk   sda  

``` 
<---- works !!

How to clone the sda then?

---

