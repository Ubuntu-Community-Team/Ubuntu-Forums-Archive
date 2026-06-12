---
title: "Moving My Folders"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by jacobroecker on 2008-09-23
Ok I've been looking for an answer and can't find it online--at least not one that seems to be in English.  I got rid of vista and backed up my folders on a network drive.  Now I'd like to move the folders on to this computer.

Each time I copy and paste them I get an error.  It says that it can't move directories around.

How do I fix it so I can move directories?

-Jacob
[http://trailbrain.com/wiki]("http://trailbrain.com/wiki")

---

### Post by jemate18 on 2008-09-23
what directory(location) are you trying to paste your files/folders.

Because you might not have write privileges to it.

---

### Post by jacobroecker on 2008-09-23
> **jemate18 said:**
> what directory(location) are you trying to paste your files/folders.

Because you might not have write privileges to it.


I'm just trying to move them into the /music folder.  I can move the files themselves--but not the entire librar  :-(

---

### Post by digitzero on 2008-09-23
What error do you get?  Are you moving from the backup drive to an Ubuntu installation (ext2) or to a Windows installation (ntfs)?

---

### Post by jacobroecker on 2008-09-23
> **digitzero said:**
> What error do you get?  Are you moving from the backup drive to an Ubuntu installation (ext2) or to a Windows installation (ntfs)?

"Error while copying "Aaron Copland".

There was an error copying the file into /home/jacobroecker/Music

Show more details
(displayed)
is a directory


This is what it looks like.

-Jacob

---

### Post by amac777 on 2008-09-23
> **jacobroecker said:**
> How do I fix it so I can move directories?

I would recommend that you don't use "move" to restore your backups in case something goes wrong. "copy" them first and make sure everything works before you delete your backups. Better yet, don't delete your backups so you have a backup. :)

If you did try to move them, you might not have permission to delete the originals due to the originals being an another disk so that might be why the move operation is failing. Try copying them instead.

Anyway, maybe when you said "move directories" you actually meant "copy directories". If that's the case, ignore this post.

---

### Post by amac777 on 2008-09-24
Another couple tips:

1. Make sure you have read permission on all the source directories including the directories and files that are within other directories.

2. Make sure you have write permission on the destination directory.

---

### Post by jacobroecker on 2008-09-24
> **amac777 said:**
> Another couple tips:

1. Make sure you have read permission on all the source directories including the directories and files that are within other directories.

2. Make sure you have write permission on the destination directory.

I have permission in all the directories.  The things just don't want to get copied.  I've googled the problem a bit and all the solutions are greek to me.

Whether I want to 'move' or 'copy' is irrelevant to the folders not wanting to be created.

I'm trying to go from an Apple Time Capsule with folders I created in Windows to Ubuntu.

---

### Post by jacobroecker on 2008-09-24
The problem doesn't exist when I use an external hard drive--just network shares.

---

### Post by amac777 on 2008-09-24
Are you using nautilus to copy the files? Because I see this bug: "Unable to copy directory FROM remote location", which is similar to what your experiencing.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/229587](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/229587)

If that is what the problem is, try using the command line to copy the files instead of nautilus.

---

### Post by jacobroecker on 2008-09-24
> **amac777 said:**
> Are you using nautilus to copy the files? Because I see this bug: "Unable to copy directory FROM remote location", which is similar to what your experiencing.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/229587](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/229587)

If that is what the problem is, try using the command line to copy the files instead of nautilus.

That bug seems to be accurate.  Although I don't have the AMD 64 shindig going on here.   It looks like I'll use another computer on the network and copy everything to an external drive.

Hopefully the linux community will address the issue soon.  My network handles most of my backups.  Very sad it's not working

-Jacob

---

