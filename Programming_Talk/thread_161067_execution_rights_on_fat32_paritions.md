---
title: "execution rights on fat32 paritions"
date: 2006-04-16
forum: Programming Talk
---

### Post by leonardoo on 2006-04-16
Hello, i've mounted my windows partition (that i'm obliged to preserve for studies need, i've got the code block ide, and i've tried to execute a c program, the mather is the shell tell me that i've not the right to do it. I've tried to look in my fstab, to see how can I manage to execute my C programs, but in vein.
  Can someone help me, Cordially.

---

### Post by xenmax on 2006-04-16
This thread tells you how to modify your accesses for FAT32 partition.
After you have read through it, if you dont mind having read,write and exec permissions for user,group and everyone, use umask=0000. If you only want read and execute permissions for any reason, you can use umask=0222. 
For more info, try 
```
man fstab
man mount

```
EDIT: forgot the thread :)
[http://www.ubuntuforums.org/showthread.php?t=144321](http://www.ubuntuforums.org/showthread.php?t=144321)

---

### Post by leonardoo on 2006-04-16
thanks for your reply :)  Actually, I've cheked using the nautilus with the right button, and i've found out that the programs have the rights to be executed, i've edited my fstab, i had the umask : 022 i've put 02222, umount then mount, useless, i've set the umask to 0000 then umount, mount, then reboot, but i've the same problem. Once i compile with code block , i get the file, all is fine, but when i launch the program : a line command one, i get : "acces denied : no permession", with the label sh, and i get the line that code block adds autmaticaly working : "press enter to continue".  I've used the console to go to directory, and to launch the file with the no extension file, i get a message kind of "it is not a valid command".  Thanks for your help. cordially, leo.

---

### Post by xenmax on 2006-04-17
Can you post the exact command you are trying and the error message you get?

---

### Post by Sutekh on 2006-04-17
Also can you post the output of this command, so we can check that the permissions were set correctly
```
ls -l /media/
```
Where /media is the parent folder that partition is mounted to (ex /media/fat_files)

---

### Post by DoktorSeven on 2006-04-17
You have to pass the **exec** option to mount to execute things on vfat partitions.

e.g.

```

/dev/hda1           /media/windows       vfat          exec,umask=0        0    0

```

---

### Post by leonardoo on 2006-04-17
Hello. with the ls -l, i get this on the parition i'm programming on : 

drwxrwxrwx 32 leo users  8192 2006-04-17 22:33 hdb5


i've added exec to all the partitions, and reboted.  The exact error i'm getting with a simple "hello world" in code block is : 
sh : /media/hdb5/console : permission denied
press enter to continue;

it's code block that adds "press enter to continue automatically".  
Thanks for your help, cordially.

---

