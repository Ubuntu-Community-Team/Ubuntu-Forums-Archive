---
title: "How do I see the amount of free hard drive space on kubuntu?"
date: 2014-11-05
forum: New to Ubuntu
---

### Post by Tom_Carr on 2014-11-05
How do I see the amount of free hard drive space on kubuntu?  I am using dolphin file manager.

---

### Post by ajgreeny on 2014-11-05
Use the command **df -h**
This is one of the many situations where a terminal command is much better than any GUI application.

---

### Post by yancek on 2014-11-05
df -h will show free space on mounted partitions.  If you want to find unallocated space use the parted command:

```
sudo parted
```

You will see the output below, just type in print free at the (parted) prompt
> parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)

If you want to check a drive other than sda enter the drive for example:

> sudo parted /dev/sdb

---

### Post by Hadaka on 2014-11-05
Hi since you asked about how in the file mgmt. Dolphine
try this,,,post #4
```
http://forums.opensuse.org/showthread.php/489595-Dolphin-file-manager-disk-space
```

---

### Post by Rob Sayer on 2014-11-06
That feature is built into dolphin though it may not work as accurately as df -h.

I'm out typing this on my lxle netbook so I don't have kde handy, and it's been a while since I used that setting.  But it's in "configure dolphin" and called something like free space.

---

### Post by deadflowr on 2014-11-06
In a very roundabout way go to Kinfocenter > Device Information > Device Viewer > Storage Devices > Hard Disk Drive > Click on the mounted partition number and in the right side pane at the bottom it will show the Volume Space.

There is probably an easier, quicker way, graphically.
This one just seemed fun...

---

### Post by SeijiSensei on 2014-11-06
In Dolphin, navigate to the "root" directory, then right-click on the window background (not on a folder) and choose Properties.  You'll see the size there.  If you have multiple devices, like a separate /home partition, using df from a command prompt provides a useful summary, but from Dolphin, you can also right-click on the home folder when viewing /root to display the /home partition's properties.

Pretty much every object on the KDE desktop has some sort of properties or options page accessible via right-clicking.  The background of a window in Dolphin represents the containing folder.

---

