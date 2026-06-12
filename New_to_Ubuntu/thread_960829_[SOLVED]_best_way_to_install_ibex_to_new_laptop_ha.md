---
title: "[SOLVED] best way to install ibex to new laptop harddrive ?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by whitethorn on 2008-10-27
I bought a new harddrive to replace the one in my laptop, I also bought an USB box in which to store my old harddrive.  I'm just wondering what's the best way to get this done.  At the moment I don't have a seperate /home partition which I want to do with the HDD. I'm not quite sure what's the best way of going about this.  I'm not sure which way I should try

1) Partitioning my harddrive (the new one) the way I want it later, then swap harddrives install xp, install ibex while placing /home on a partition, then copying my old home folder over. 

2) This would probably be easier, copy my whole root over to the hdd then swapping harddrives, upgrading (wouldn't have to go and reinstall all the programs / settings I had. but then I don't know if it'll work because there won't be any grub to boot from...), then install xp and reinstall grub.  My laptop ain't that great which is why I keep xp around to play games on. 

If there's another way of doing this I'm open to suggestions.

---

### Post by Amarsingh0793 on 2008-10-28
Copying and Pasting your whole root folder is not a good idea. It will be read-only on another computer/installation (probably). Just backup the things you need. You can copy and paste your /home/xxxxx folder too.

---

### Post by cariboo on 2008-10-28
The way I do it when I am doing a complete fresh install, is to install windows first, I use the windows installer to partition the drive. I usually use about half of the harddrive for Windows and leave the rest of the drive unpartitioned. I then maually partition the rest of the drive during the Ubuntu install. I normally set 15Gb for / and the rest of the dirve as /home. When its time to copy the files from the old home  partition to the new, I don't copy any of the hidden files and directories except for ~/.mozilla-thunderbird. it usually takes less time to set up new configuration files than it does to deal with any other problems that turn up due to old config files. The other thing about doing it the way I do is that you only have to change ownership and permissions of the files and directories that have been copied over.

Jim

---

### Post by ajparker on 2008-10-28
Good point with regards to the hidden files (those starting with a dot) Sometimes you can generate a lot of headaches by migrating your config files from one version to another.  It's better to grab the real data files in bulk (Documents) and then go back and cherry pick any particular "dot" files or "dot" folders after the fact.

It is possible to migrate to a new hard drive via a copy of the root folder and home folder.  In fact many times I've replaced hard drives that way.  Yes, you usually have to go in and reinstall grub - so if you don't know what you're doing it can be a hairy process.... It's certainly not a beginner tip though and would strongly suggest that you follow the basic outline from cariboo907 above.

---

### Post by handydan918 on 2008-10-28
> **whitethorn said:**
> I bought a new harddrive to replace the one in my laptop, I also bought an USB box in which to store my old harddrive.  I'm just wondering what's the best way to get this done.  At the moment I don't have a seperate /home partition which I want to do with the HDD. I'm not quite sure what's the best way of going about this.  I'm not sure which way I should try

1) Partitioning my harddrive (the new one) the way I want it later, then swap harddrives install xp, install ibex while placing /home on a partition, then copying my old home folder over. 

2) This would probably be easier, copy my whole root over to the hdd then swapping harddrives, upgrading (wouldn't have to go and reinstall all the programs / settings I had. but then I don't know if it'll work because there won't be any grub to boot from...), then install xp and reinstall grub.  My laptop ain't that great which is why I keep xp around to play games on. 

If there's another way of doing this I'm open to suggestions.

Check out ```
man rsync
```
This is a pretty friendly man page, and easy to read.
I recently copied an entire linux install to a replacement disk, with no problem at all. Multiple users, root, whole ball of wax.

---

