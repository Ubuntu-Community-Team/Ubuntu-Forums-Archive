---
title: "&quot;Error renaming temporary file&quot; in gedit"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by Soheyl on 2013-03-25
I have a windows share folder that I mount with the following line in fstab:

```
//192.168.1.11/data-share /mnt/Server cifs auto,iocharset=utf8,uid=1000,gid=1000,credentials=/home/soheyl/.cifspwd 0 0
```

When I create a file in this folder, and modify it in gedit, I cannot save it, getting the following error message:

```
Could not save the file /mnt/Server/myfolder/myfile
Unexpected error: Error renaming temporary file: Invalid argument
```

However, I can do the same task in command line using nano for example. 

Any idea what's going on?

---

### Post by solarghost on 2013-03-27
Just a shot in the dark but try going to GEdit then:

Edit->Preferences->Editor 

Un-check the "Create a backup copy of files before saving" option. I don't think windows allows files with ~ in the names and if I remember correctly the backup file created by gedit contains a ~

Let me know.

---

