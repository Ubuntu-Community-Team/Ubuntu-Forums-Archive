---
title: "Where to place my files?"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by dintu on 2012-03-14
i am new to linux file system. i m learning how it works.
 i dont know where to place my files ,so that it resides securely even after the OS goes down.

my parttiion as follows,
root-20GB
boot-500MB
swap-2GB
others- 59GB

---

### Post by cortman on 2012-03-14
Welcome to GNU/Linux, and Ubuntu in particular!

Not sure exactly what is meant by your question, but the place for your personal files is in your /home/yourname folder. This is the location to which the "Home" bookmark directs you. The rest of the file system requires root permissions to edit, and it's best left alone.
Where to store your files in case the system goes down? An external hard drive.

---

### Post by Holdolin on 2012-03-14
What files are you trying to place.  In Linux, "your" stuff will be in the /home directory somewhere, for example /home/downloads for your...downloads, or /home/documents, and so fourth.  If your running Unity as your desktop enviornment, there should be a home folder icon on the left side (by default) of your screen.  If you are using GNOME as your desktop enviornemt, there will be a drop down menu for you to naviate your file system.

Welcome to the forums, and to Ubuntu as well ):P

---

### Post by dintu on 2012-03-14
So if i place everything in the home folder will it safe and recoverable when my os goes down.

---

### Post by cortman on 2012-03-14
> **dintu said:**
> So if i place everything in the home folder will it safe and recoverable when my os goes down.

Not unless your /home is on a separate partition, and even that doesn't guarantee they'll be safe in the event of an OS crash. Like was said before, always backup your stuff.

---

### Post by Holdolin on 2012-03-14
I *think* dinto referring to a normal shutdown, if so, then yes, your stuff will be safe when your system goes down.  The backup is in case of a system crash (and should be done regularly)

---

### Post by flemur13013 on 2012-03-14
What cortman said: put /home in a separate (ext2,3,4) partition, which can be on the same physical disk drive as the OS.
That be be done when you install ubuntu.

Then you can reinstall/repair/messup ubuntu, or even install another linux using the same /home, without losing any data in /home.  When you reinstall or add linuxes just point the installer to the existing partition with /home on it and DON'T reformat it.  If you already have your /home on a system partition, it's not too difficult to move /home to it's own partition (tho more hassle than setting it up that way at install).

---

### Post by tbhatia4 on 2012-03-14
> **dintu said:**
> So if i place everything in the home folder will it safe and recoverable when my os goes down.

its advisable to backup your system regularly
visit this to learn about backup
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
this way you can easily experiment with ubuntu without bothering for your stuff

---

### Post by Paqman on 2012-03-14
> **dintu said:**
> So if i place everything in the home folder will it safe and recoverable when my os goes down.

It should be, unless the filesystem itself is corrupted. That's why it's important to take regular backups.

---

### Post by The Cog on 2012-03-14
Please note that your home directory is not /home, but /home/username, where username is the name that you log in as. So each user has their own home directory. Normal users do not have write permissions to /home, but only to their own folder inside /home.

---

