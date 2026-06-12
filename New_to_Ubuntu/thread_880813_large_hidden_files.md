---
title: "large hidden files"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by RavUn on 2008-08-05
My disk usage analyzer is showing 55 gigs used but my file system only shows 37 gigs.  Where's the extra 18 gigs?  I only have the one partition.  I've been burning a lot of dvds recently and making iso's and that's when the disk usage seemed to jump.  Some files were around 7 gigs.  I deleted the entire directory containing the isos and emptied the trash but I don't know what's up with that.

---

### Post by LowSky on 2008-08-05
check for the DVD progrma you have been using and see if its caching the DVDs to a certain place. that could be raw data just sitting there if the program wasn't set to delete it after the burn process.

---

### Post by RavUn on 2008-08-05
I used manDVD to convert avi files and create iso images.  I burned the videos to DVDs through my brother's computer using samba.  Could it have been using buffers during the burn process and that was stored somewhere or do you think manDVD could have been the culprit?  I checked mandvd and could not find many settings other than video settings.

I don't really know where to check.

---

### Post by cariboo on 2008-08-05
You could always try:

```
du -h
```

In a terminal, in your home directory, this will list files sizes you may be able to find which files are using up all your hdd space.

Jim

---

### Post by RavUn on 2008-08-05
> **cariboo907 said:**
> You could always try:

```
du -h
```

In a terminal, in your home directory, this will list files sizes you may be able to find which files are using up all your hdd space.

Jim

du shows a total of 35gigs used but I have 55gigs in use according to conky and disk usage analyzer.



When I was doing the DVD burning I allowed open access to my home directory (stupid, yes I already know) and someone was logged on my PC I'm pretty sure.  Could they have done something?

---

### Post by CatKiller on 2008-08-05
You can run the Disk Usage Analyser as root with ```
gksudo baobab
``` This will show you all the usage of your filesystem. If you were running your DVD-creation program as a normal user, the files can only be in either your Home folder (Ctrl-H to see hidden files) or in /tmp. If you want to check to see if any .isos were created and left behind for later use, you could run ```
locate .iso
``` to find them. This will return a list of filenames that contain ".iso".

EDIT: Another possibility is that you have another partition mounted. Baobab will tell you the usage for your filesystem as a whole. Nautilus (the file manager) will display the usage for the partition that contains the directory that's currently being shown.

---

### Post by RavUn on 2008-08-05
awesome... the first part worked.  The files were still in the trash under root.  I emptied the trash but I don't know why they were still in there as root.

I navigated to the folder as root and tried to delete and they disappeared then reappeared.  I had to use the rm -rf command to actually get rid of them completely.  That seems weird to me.

---

### Post by billkamp on 2009-06-11
I found this thread on Google, and see it is solved. I had the same symptoms, but in my case the solution was to unmount all NFS mounts. The nfs mount of /mnt/bu was hiding the local directory /mnt/bu :-) (Made a backup when NFS was not running.) So when the hidden dir was revealed, I could delete it, and then remount my NFS version.


> **RavUn said:**
> awesome... the first part worked.  The files were still in the trash under root.  I emptied the trash but I don't know why they were still in there as root.

I navigated to the folder as root and tried to delete and they disappeared then reappeared.  I had to use the rm -rf command to actually get rid of them completely.  That seems weird to me.

---

