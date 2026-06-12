---
title: "What am I really backing up when I use the backup program?"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by J Tinsby on 2014-06-28
I am used to using Acronis to make image backups for my system. Clearly that's not what's being made when I tried the Ubuntu backup program for the first time. I simply get 3 files as the output and the total size is isn't even 46MB total. Clearly that's not the size of the paritions where Linux resides, sure they are a .gz file but that's not enough. Plus there were 3 files it said couldn't be backed up ( screenshot ).

I don't even know how to find these files, I can go to the /home folder and use the search bar typing in the names in the window but I don't get anything.

Maybe I better keep using Acronis and make full images of the parititions I want, this looks a little sketchy. Plus if there was a need to restore a backup and you can't boot the system, I didn't see anything about making a recovery disc to boot from.

Thank you,

J T

---

### Post by deadflowr on 2014-06-28
That looks like deja-dup, which only backs up files in your home folder.
Sidenote, you should set your preferences to exclude those three folder/files.

In the file manager, ctrl+h will show hidden folders/files.
hidden folders/files are listed with a dot, such as /home/user/.config.

---

### Post by J Tinsby on 2014-06-29
> **deadflowr said:**
> That looks like deja-dup, which only backs up files in your home folder.
Sidenote, you should set your preferences to exclude those three folder/files.

In the file manager, ctrl+h will show hidden folders/files.
hidden folders/files are listed with a dot, such as /home/user/.config.

It doesn't say what the name of the program actually is, it just says "Backup" on the icon in ubuntu.

Thanks for the tip on the "." indicating a hidden file.

J T

---

### Post by deadflowr on 2014-06-29
deja-dup is the name of the default backup program for Ubuntu.
Ubuntu simply calls it Backup.

---

### Post by newb85 on 2014-06-29
Deja Dup isn't really designed for full system backups.  The default is to back up your /home directory.  It does give you the flexibility of choosing which files to backup, so you could in theory back up system files or files from other users.  This may, however, cause permissions hurdles in restoring.

For my purposes, I find backing up my /home directory to be sufficient.  If anything happens, Reinstalling the OS and handful of applications I want added doesn't take that long.  Since I generally reinstall at upgrade time, I have a shell script for installing the applications I want, anyways.

---

### Post by Mark Phelps on 2014-06-29
To get full backups, along the line of what Acronis did, use Clonezilla -- and the saveparts option.  It takes me less than 10minutes to backup my entire partition and about the same time to restore it -- which is a LOT less than the hours it would take to reinstall the OS, all the apps, all the settings.

---

### Post by J Tinsby on 2014-06-29
Thanks Mark,

I will look into Clonezilla!

J T

---

