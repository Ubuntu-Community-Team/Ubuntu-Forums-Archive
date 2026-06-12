---
title: "what does backup back up?"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by jonabark on 2012-09-28
This is just a general question about ubuntu backup and the Ubuntu One cloud storage I. I opened  the backup program and told it to do a backup to the Ub 1 cloud, which it is now doing. This computer is new and came with Windows 7 starter which we have not messed with except to download Ubuntu, BUT I am hoping Backup only backs up the ubuntu OS in its current arrangement and not the entire computer with windows. How does that work? When you set the ub 1 cloud storage to  do a regular sync with  the computer  does it just sync files and apps added to ubuntu or does it sync any changes to the OS.? Completely new to ubuntu and the cloud thing.

---

### Post by jonabark on 2012-09-28
so I just checked  the backup which showed it was done and  then checked my ubuntu one cloud account and there are several duplicity-full files totaling about 33 MB. So what exactly was stored there-obviously not the whole ubuntu package on my computer? And is this enough to do a system restore if there is a problem in the future?

---

### Post by deadflowr on 2012-09-28
I'm guessing you're using the default installed backup porgram, deja-dup.
I believe, by default it only backs up your home directory. It doesn't backup apps and programs.
However, you can configure it to backup only that which you want to back up. 
In the utility for the program, select the folder tab, and from there pick and choose which folders/files you want to back up, and which ones to ignore.
There are ways to backup applications, but can seem unnecessary, since reinstalling them is a simple task(backing up apps just makes reinstalling quicker.)

---

### Post by jonabark on 2012-09-28
So what exactly is my home directory? Is that the code for how the operating system, internet settings are done? Does it include emails? files?  Can I do a backup that would allow restoration of everything in the ubuntu partition?

---

### Post by deadflowr on 2012-09-28
The home directory is where your home folder is.
It contains all your user data. Such as your documents, music, videos, pictures, and also user-specific configuration files.
The configration files are hidden by default. To see them press ctrl+h, or menu,view,show hidden files.

To open the home folder, either select the icon in the lefthand side( Home Folder), or press the windows(known as super) key on your keyboard and type home and select it.
This will open the file manager, nautilus. From here you can see the various files you've stored, and make simple changes.

---

