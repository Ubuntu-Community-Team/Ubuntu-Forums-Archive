---
title: "Can not delete a folder in my user and when I run nautilus as root it is not there"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-13
Hi
Thank you for reading my post.
I want to delete a folder name .gvfs in my home directory but I can not delete it. problem is that I can not change its permissions (I have read and execute over the folder and all permissions ,only green boxes and not the correct marks, for file permission).

Problem goes bigger when I want to delete the folder using root (gksudo nautilus /home/legolas/ and pressing CTRL+H to show hidden file) the file is not shown at all :O, 

What should I do?

---

### Post by midgetwithamatch on 2008-11-13
Run your favorite file browser as root and go up to View -> Show Hidden Files (Ctrl+h)(nautilus) and then navigate to your directory of choice and delete your file of choice. Files that start with periods are hidden unless you have configured your file browser to show them all the time or for that session.

---

### Post by legolas_w on 2008-11-13
problem is that it only exists in nautilus running in my user, it is not there when I run


```


ls -a .v*

```

and it is not there when running nautilus as root and pressing CTRL+H
I think my sound system is not working because of this error.
Thanks.

---

### Post by mcduck on 2008-11-13
The .gvfs directory is part of Gnomes virtual file system, it's created when user logs in and removed when the user logs out. This is also the rewason for it's "strange" permissions, that's how it needs to be.

You shouldn't try to remove it, most likely that will only result in things breaking.

(and no, I don't think GVFS has anything to do with your sound not working..)

---

### Post by midgetwithamatch on 2008-11-13
Have you tried deleting the folder manually through command prompt? With ```
rm -R .gvfs
``` or ```
sudo rm -R .gvfs
``` if needed

---

