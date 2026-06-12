---
title: "Updating packages using package manager throws syntax error"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by jinchuriki on 2013-02-22
Hi,

I'm not able to update packages as I kept getting this error during update:-

installArchives() failed: dpkg: error: syntax error in triggers deferred file `/var/lib/dpkg/triggers/Unincorp' at character `'

Error in function: 

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

I have tried running these commands successfully but still getting the same error after that:-

apt-get clean up
apt-get clean all

Info:

Ubuntu 11.10

Linux ______ 3.0.0-29-generic #46-Ubuntu SMP Tue Dec 4 12:16:46 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Sealbhach on 2013-02-22
Ok, try this, as suggested in a [previous thread]("http://ubuntuforums.org/showthread.php?t=681675&page=3http://").

First open Nautilus in root mode using:-
     
     ```
gksudo nautilus 
```Then navigate to /var/lib/dpkg/triggers and make a backup of the Unincorp file or copy it somewhere else.

After you have made a backup of the Unincorp file open the current Unincorp file for editing using:-
    
     ```
gksudo gedit /var/lib/dpkg/triggers/Unincorp 
```Then remove everything that is there to make it blank and save the file.

---

### Post by jinchuriki on 2013-02-23
Thanks Sealbhach! That solves my problem.


For those out there who encounter the same error as mine, try these:-

1. sudo rm /var/lib/dpkg/triggers/Unincorp
2. sudo touch /var/lib/dpkg/triggers/Unincorp

I ran gedit as root to remove the contents of Unincorp but somehow there was 20byte still in that file. Therefore I tried removing the file and recreate an empty file -> voila !!

---

### Post by jinchuriki on 2013-02-23
Set the thread to solved.

---

### Post by Sealbhach on 2013-02-24
Nice one jinchuriki, thanks for writing down the solution you found and marking the thread SOLVED.

.

---

