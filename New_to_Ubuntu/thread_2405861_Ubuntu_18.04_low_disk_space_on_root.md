---
title: "Ubuntu 18.04 low disk space on root"
date: 2018-11-12
forum: New to Ubuntu
---

### Post by zhurma on 2018-11-12
Recently I upgraded from 16.04 to 18.04. And since then I constantly get notifications about low disk space on root. I have an 1Tb hdd, so space shouldn't be a problem. Attaching screenshots of gparted and baobab. Is there any additional info needed?

[ATTACH=CONFIG]281621[/ATTACH][ATTACH=CONFIG]281622[/ATTACH]

---

### Post by Dennis N on 2018-11-12
Look at the root partition sdc2  - it only shows 2 gB of available space in gparted. That's why you get the warning. I have seen it too on 18.04.

Added comment:
Your computer can't use the big partition sdc4 since it's not mounted to the file system yet. You could mount it and use it for storage - some kind of data is already on it.

---

### Post by zhurma on 2018-11-12
How should I do that properly?

---

### Post by ajgreeny on 2018-11-12
Firstly you need to be sure what is on that /dev/sdc4 partition; there's almost 218GB of files sitting there, some of which I imagine must be data files, ie, documents, photos, music, etc etc.  Did you have a separate /home partition when using 16.04 which you have now lost in 18.04 as that seems the most likely situation?

That partition will appear as an icon in your file manager's left hand pane and clicking on that will mount it, allowing you to see everything on it, though you may not yet be able to write any files to it, depending on its permissions and ownership.
Mount that partition by clicking on its icon then use command ```
ls /media/*
``` to see what folders it contains with what files inside them.  The output may be huge so you  may have to create a text file in order to see it all with ```
ls /media/* >scd4-files
``` then open that **sdc4-files** in a text editor

I suspect that you will be best served by using that large sdc4 partition as either a separate data or /home partition, but let's see what is on it first; we can then give you some better ideas that we can at present about how to proceed.

---

### Post by zhurma on 2018-11-12
> **ajgreeny said:**
> Firstly you need to be sure what is on that /dev/sdc4 partition; there's almost 218GB of files sitting there, some of which I imagine must be data files, ie, documents, photos, music, etc etc.  Did you have a separate /home partition when using 16.04 which you have now lost in 18.04 as that seems the most likely situation?

That partition will appear as an icon in your file manager's left hand pane and clicking on that will mount it, allowing you to see everything on it, though you may not yet be able to write any files to it, depending on its permissions and ownership.
Mount that partition by clicking on its icon then use command ```
ls /media/*
``` to see what folders it contains with what files inside them.  The output may be huge so you  may have to create a text file in order to see it all with ```
ls /media/* >scd4-files
``` then open that **sdc4-files** in a text editor

I suspect that you will be best served by using that large sdc4 partition as either a separate data or /home partition, but let's see what is on it first; we can then give you some better ideas that we can at present about how to proceed.

The only thing that ```
ls /media/*
``` reuturned after mounting sdc4 was ```
a7e29965-1d52-44c6-bab4-179115b79ec4
```.
I checked partition and it contained some old files from 16.04. What's interesting it wheighs about 65Gb. Not 200Gb+.
I don't need any of those files.
What should I do next?

---

### Post by ajgreeny on 2018-11-13
OK, now let's see what the output is of command ```
ls /media/a7e29965-1d52-44c6-bab4-179115b79ec4
``` which I expect will show all the usual subdirectories of a /home partition such as Documents, Downloads, Music, etc etc.

---

### Post by zhurma on 2018-11-13
> **ajgreeny said:**
> OK, now let's see what the output is of command ```
ls /media/a7e29965-1d52-44c6-bab4-179115b79ec4
``` which I expect will show all the usual subdirectories of a /home partition such as Documents, Downloads, Music, etc etc.

Yep, it contains ```
lost+found  zhurik
``` with "zhurik" being the name of my home partition. It contains old data from 16.04

---

### Post by yancek on 2018-11-13
Copy any data you want to save from the partition (if any) then boot the Ubuntu 18.04 install media, open a terminal and GParted and simply format sdc4.  You then need to create a mount point for it and put an entry in /etc/fstab file for it.  You could do this from the installed Ubuntu as long as the partition (sdc4) is not mounted.

---

### Post by Impavidus on 2018-11-13
As this was a /home partition on 16.04 and your root partition is full, you probably want to use it as a /home partition again. Read this: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by zhurma on 2018-11-13
I formatted it and mounted everything. Thank You very much!

---

### Post by ajgreeny on 2018-11-13
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

