---
title: "&quot;My Computer&quot;"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-05-19
One thing I haven't figured out about Ubuntu is the "My Computer" area which is found on Windows...and I realize this is not Windows, it's Linux.  So, that's my question, where is the area in Linux where the user can see the space, and whats on the hard drive, and other properties?  
Thanks
Ubuntu 12.10

---

### Post by ibjsb4 on 2013-05-19
Your there :)  In my computer just right click on your drive.

If you want some more, open a terminal and enter:

```
df -h
```

---

### Post by GUZZLR on 2013-05-19
When I go to computer, I'm given the following choices, what are the Root A's, and I can see the pie chart when I right click on the 320 GB Hard Disk: 26 GB Volume, so I like this, but why when I click on permisions, on every one, Ubuntu tells me the permissions can not be determined?  The "File System" is another mystery...what folder are the programs stored in?
Thanks for the help

---

### Post by mastablasta on 2013-05-19
my computer is widnows explorer which is a file manager. nautilus is default ubuntu file manager.

what do you actually  need? there are GUI for disk and system data as well as command line tools.

if you are looking for windows like GUI interface try Kubuntu. and if you try i,t also try classic K menu (right click K and select classic).

---

### Post by mastablasta on 2013-05-19
> **GUZZLR said:**
> When I go to computer, I'm given the following choices, what are the Root A's, and I can see the pie chart when I right click on the 320 GB Hard Disk: 26 GB Volume, so I like this, but why when I click on permisions, on every one, Ubuntu tells me the permissions can not be determined?  The "File System" is another mystery...what folder are the programs stored in?
Thanks for the help
  how did you install Ubuntu? via wubi?

if those are NTFS file system drives then you can't set permissions on them.

root drives are owned by root i believe. you can change their ownership to user.

programmes are stored all over the place. all is organized though. but mostly in bin i believe:
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)
.

---

### Post by mcduck on 2013-05-19
That's because drives don't have permissions, the files and directories within them do. (And in case of FAT and NTFS filesystems, they don't even support UNIX permissions so they are set for the whole filesystems at the time it's mounted, and can't be changed individually)

---

