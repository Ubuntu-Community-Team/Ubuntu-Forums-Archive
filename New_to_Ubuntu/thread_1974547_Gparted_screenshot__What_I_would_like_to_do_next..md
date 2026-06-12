---
title: "Gparted screenshot:  What I would like to do next."
date: 2012-05-06
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-06
[http://i348.photobucket.com/albums/q339/BoyntonStu/16GBpartition.jpg](http://i348.photobucket.com/albums/q339/BoyntonStu/16GBpartition.jpg)

These are my 11.10 present partitions.

Please elaborate on what is shown.

I would like to create a 4 GB /home partition and delete the SWAP partition.  (no flag shown)

The goal is to have 12 GB for / and all apps and 4 GB /Home for data.

I save most of my data on a HDD.

AFAIK I would be able to copy/cut the entire /Home partition and move it to another USB flash or HDD.  Correct?

Is my goal sound?

How would you do it?

Edit:

I just did the following:

Created "UBUNTU HOME" folder on my PC C: drive.

Copied the entire Ubuntu Home to the PC.

By clicking properties I discovered that the Home file system is 146 MB.

What can I use in Ubuntu to determine the Home size?

---

### Post by Boyntonstu on 2012-05-06
Bump

---

### Post by oldfred on 2012-05-06
Use gparted to delete swap and create the new partition. You will have to do that from a liveCD or another install as you cannot do it from your install. The little keys show it mounted. 
Often liveCDs also mount swap, so you may have to click on swap and right click swap off.
Resize & Create new partition. See link on moving /home.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you have /home fully backed up. You can just start over, totally repartion the way you want and reinstall. I would copy data into the newhome first and using manual install also mount the /home but DO NOT format it.

---

### Post by Hadaka on 2012-05-06
to look at the folder size

du -sh /home #human readable#
du -sb /home #output in bytes#
du -sk /home #output in kilobytes#
du -sm /home #output in megabytes#

hope this helps.

---

### Post by Boyntonstu on 2012-05-07
> **Hadaka said:**
> to look at the folder size

du -sh /home #human readable#
du -sb /home #output in bytes#
du -sk /home #output in kilobytes#
du -sm /home #output in megabytes#

hope this helps.

Thanks, it answers the question, but begs another.

Why does Nautilus lack this basic function?

Linux/Ubuntu is very powerful, and it can do most things if you have Hadaka to help. lol

---

### Post by Zill on 2012-05-07
> **Boyntonstu said:**
> ...Why does Nautilus lack this basic function?
Err.. it doesn't.  Just right-click on your required folder and select "Properties".

---

