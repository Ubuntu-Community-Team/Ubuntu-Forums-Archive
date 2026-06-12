---
title: "Can not write to my partition"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-27
I have two ext3 partition which are always empty since I setup my hard drive. Only today I realize that i can not write to these partitions today. When I right click on them, Create Folder option is gray out. Simply speaking, these partitions is readable only. Ironically, I can write to my WinXP ntfs partition (weird right?). What is the problem? All these partition (namely  ext3 sda5, ext3 sda6 and ntfs WinXP) are auto mount on start up. Please assist me. Btw, I deleted lost+found folder in these partition using sudo nautilus

This is error message i get if try to move any file to these partition 

The folder "untitled folder" cannot be copied because you do not have permissions to create it in the destination.

---

### Post by Sarah L on 2008-05-27
It sounds like that you're encountering a permissions error. Check to see the ownership and permissions of the files and directories in your drive using ```
ls -l
```

Make sure that you have sufficient privileges to read and write to your partition. If you want to change the ownership of a file, use ```
sudo chown username filename
```

To grant write privileges to a file, you can use ```
sudo chmod a+x filename
```

Hope this helps,
Sarah

---

### Post by spiderbatdad on 2008-05-27
> **Sarah L said:**
> It sounds like that you're encountering a permissions error. Check to see the ownership and permissions of the files and directories in your drive using ```
ls -l
```

Make sure that you have sufficient privileges to read and write to your partition. If you want to change the ownership of a file, use ```
sudo chown username filename
```

To grant write privileges to a file, you can use ```
sudo chmod a+x filename
```

Hope this helps,
Sarah

Sort of correct:
chown uses the params "owner:group" So the basic command without options is:```
sudo chown user:group filename
```
typically group name is the same as username.

chmod a+x makes a file executable, not writable. That would be chmod +w filename.

---

### Post by spiderbatdad on 2008-05-27
> **wariskampar said:**
> I have two ext3 partition which are always empty since I setup my hard drive. Only today I realize that i can not write to these partitions today. When I right click on them, Create Folder option is gray out. Simply speaking, these partitions is readable only. Ironically, I can write to my WinXP ntfs partition (weird right?). What is the problem? All these partition (namely  ext3 sda5, ext3 sda6 and ntfs WinXP) are auto mount on start up. Please assist me. Btw, I deleted lost+found folder in these partition using sudo nautilus

This is error message i get if try to move any file to these partition 

The folder "untitled folder" cannot be copied because you do not have permissions to create it in the destination.

Sounds like more configuration is needed in /etc/fstab
See bodhi.zazen's guide to fstab:[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Or check your disk mounting tool.

---

### Post by wariskampar on 2008-05-28
ok. now I can utilize my partition using sudo chown -R partitionname. 

However, when i look into sda5,sda6 and WinXP property, i can not set permission. Under Permission Tab, i get this message:

The permission of "" can not be determine.

How to enable this so that i can easily set rule to my partition

---

