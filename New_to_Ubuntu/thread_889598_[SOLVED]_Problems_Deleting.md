---
title: "[SOLVED] Problems Deleting"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by mr wilson on 2008-08-14
I am having great difficulty in removing some AVI files from my my computer. I have moved a folder of them to the garbage bin, but I cannot empty the garbage bin. When I try to delete the folder, an error message pops up (Error moving file: permission denied). I tried to change the permission of the individual files (and the folders) but I can not ("operation not supported by backend"). I can't even move the folder back out of the garbage. 

 I am a fair novice at ubuntu / linux.

---

### Post by Elfy on 2008-08-14
Run nautilus as root

```
gksudo nautilus
``` then navigate to the folder, File System not root home > /home/*user*/.local/share/Trash/ and delete or use the command line, change user to your username

```
sudo rm /home/*user*/.local/share/Trash/files/*
```

if they are in folders

```
sudo rm -R /home/*user*/.local/share/Trash/files/*
```


Edit - I've never thought of putting the path in drs305 - thanks

---

### Post by drs305 on 2008-08-14
the files are probably owned by root, so open your file browser with root privileges to delete the files:
```
gksu nautilus $HOME/.local/share/Trash/
```

'gksu' is preferred over 'sudo' for graphical apps such as nautilus. use nautilus to navigate to the folders and delete the 'files' and 'info' folders. be careful as opening nautilus in this manner allows you to delete any files/folders on your system.

---

