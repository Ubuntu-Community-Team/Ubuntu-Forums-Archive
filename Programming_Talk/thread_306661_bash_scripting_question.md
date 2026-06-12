---
title: "bash scripting question"
date: 2006-11-25
forum: Programming Talk
---

### Post by munkyeetr on 2006-11-25
I am trying my hand at automating a backup script in BASH.
I can copy all the system directories and personal documents no problem.

What is stumping me is I want to copy all the hidden configuration files in my Home Directory, but I want to exclude certain directories. ( like .Trash) ](*,) 

So instead of specifying every file that I want to copy, I want to blanket-copy everything, but exclude certain files and folders.

Can someone point me in the right direction?

Also currently I am completely backing up the following system directories:
     /bin, /boot, /dev, /etc, /sbin, /usr/bin, /usr/sbin

Are there any others that I should be backing up, or any in this list that don't need to be backed up?

Thanks in advance for the help and advice.

---

### Post by po0f on 2006-11-25
munkyeetr,

How are you creating your backup?  With tar?  tar has an exlcude option, so something like this should work:
```
$ cd ~
$ tar -cvf home_backup.tar --exclude=.Trash .
```

It might be easier to write separate home and system backup scripts.  This is what I'm doing, as I'm currently in the process of writing my own backup scripts in bash as well.  It makes it easier to transfer just your settings after a reinstall, or a fresh install on another box.

It is pointless to backup /dev (and /sys and /proc) as this is a filesystem that will be repopulated on reboot.

Hope this helps, and let me know how you get along.

---

### Post by munkyeetr on 2006-11-26
that helped. thank you.

---

### Post by Eric_T on 2006-11-27
You can also use rsync, which basically only copies the files that have been changed since your last backup. rsync have the same --exclude option as tar.

I've created a backup-script that makes a fresh copy every week, then uses rsync every day to update the files. It's pretty simple, but works great for my needs.

---

