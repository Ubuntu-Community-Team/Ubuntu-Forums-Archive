---
title: "LOCK icon on folder. Where did it come from?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by paker on 2008-07-04
I had a couple of folders with lock icon. I searched this forum and used "sudo rm filename" to remove the files within the folder first, and then removed the empty folder. But where did the lock come from in the first place?

---

### Post by geek_Man on 2008-07-04
It's probably because it's owned by root. If it's set so that only root can look through it, it appears "locked".

---

### Post by lukjad on 2008-07-04
Probably you move a file as root or in a live CD that is usually logged in a root.

---

### Post by Teber on 2008-07-04
the lock may appear on files and folders copied from a data cd. it would still be a matter of ownership i think.

---

### Post by whitethorn on 2008-07-04
you can change the owner of the folder, from root to yours by running 

sudo chown user:group name of file or /folder

you should only use this for folders which aren't system folders.  Pretty much when you copied something as root into your home folder ...  I only use it for files in my home folder.

---

### Post by paker on 2008-07-11
Thanks. The folders were copied from data DVD. I thought I pushed wrong buttons somewhere.

---

### Post by mc4man on 2008-07-11
Actually it's a permissions issue not ownership, you own the files or folders. The new way with hardy is when you copy from media that's mounted read only you only get read permissions for files and access for folders. See here for add. info
[http://ubuntuforums.org/showthread.php?p=5259083#post5259083](http://ubuntuforums.org/showthread.php?p=5259083#post5259083)

---

