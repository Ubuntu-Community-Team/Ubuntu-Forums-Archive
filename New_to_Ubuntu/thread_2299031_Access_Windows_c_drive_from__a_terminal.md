---
title: "Access Windows c: drive from  a terminal"
date: 2015-10-15
forum: New to Ubuntu
---

### Post by mervynb on 2015-10-15
I have Ubuntu 14.04 and Windows XP on my computer.

On the launcher there is an icon to open a window showing the folders and files on the Windows c: drive.  This serves its purpose but I cannot limit the display of files to those with a selected extension.   I can open the various files but finding specific content is a case of trial and error.

I would like to be able to use a terminal to access the c: drive so that I can use it to access individual folders and selectively list files.  This would also give me the ability to use grep to find contents.  If this is possible how do I go about it?

---

### Post by coffeecat on 2015-10-15
Either use the launcher icon or the left pane in any nautilus window to mount and view the C:drive. Then press ctrl-L to see what the mount path is - something like /media/yourusername/partitionLabel. Or you can run the mount command in the terminal to find the mountpoint. Then:

```
cd /path/to/mountpoint
```

Then grep away to your heart's content.

---

### Post by mervynb on 2015-10-15
> **coffeecat said:**
> Either use the launcher icon or the left pane in any nautilus window to mount and view the C:drive. Then press ctrl-L to see what the mount path is - something like /media/yourusername/partitionLabel. Or you can run the mount command in the terminal to find the mountpoint. Then:

```
cd /path/to/mountpoint
```

Then grep away to your heart's content.

Magic!  Thanks for the help.

---

