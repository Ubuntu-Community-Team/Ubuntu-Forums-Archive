---
title: "[SOLVED] Restore files emptied from trash?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by bronner on 2008-08-23
Hey, somebody told me that you can recover files emptied from the trash in Ubuntu? How would one go about getting files that have been emptied from the trash back? I'm using Ubuntu 8.04, for reference. Thanks!

---

### Post by halitech on 2008-08-23
if they have been emptied from the trash then they are gone and there is no way of getting them back.

---

### Post by nitro_n2o on 2008-08-23
There are always ways of getting data from disks!! 
but since you've emptied the trash it is a very hard to recover!! 

I know of commercial programs as well as companies to recover your lost files..

There are also some free software that will recover your lost files on linux 

search in google for hard disk recovery in linux 
you'll get lots of results

---

### Post by ibuclaw on 2008-08-23
There is a package called testdisk in the repos.
```
sudo apt-get install testdisk
```
It is an ncurses base application, so a terminal is required.

```
cd ~/Desktop
sudo photorec /d restore

```
Select the partition and filesystem.
There is a "**File Opt**" menu selection, if you recall what type of file you accidentally removed, then you can set it to restore only those types of files.

Regards
Iain

---

### Post by Shazaam on 2008-08-23
Also, look in /root/.local/share/trash/files. Sometimes you can recover deleted files from there.

---

### Post by gjoellee on 2008-08-23
this is installed in Intrepid:)

---

### Post by bronner on 2008-08-23
Thanks guys, when I get back to my computer I'll try this stuff... if not, I can probably restore them from my flash drive fairly easily... :)

---

### Post by bronner on 2008-08-24
OK, but when I use photorec, the folders it recovers to are locked, they say I don't have permission to enter and I can't change the permissions because 'I am not the owner...' anyone know what I can do?

---

### Post by t0p on 2008-08-24
> **bronner said:**
> OK, but when I use photorec, the folders it recovers to are locked, they say I don't have permission to enter and I can't change the permissions because 'I am not the owner...' anyone know what I can do?

You need to manage those files with admistrative privileges.  In a the terminal, type
```
gksudo nautilus
```

A file manager window will open.  Use that window to navigate to the files in question and change their permissions - I think a right-click, then click on Properties.

---

### Post by bronner on 2008-08-24
> **t0p said:**
> You need to manage those files with admistrative privileges.  In a the terminal, type
```
gksudo nautilus
```

A file manager window will open.  Use that window to navigate to the files in question and change their permissions - I think a right-click, then click on Properties.

If we were in prison, I'd protect you in the shower, THANK YOU SO MUCH!!! :)

---

