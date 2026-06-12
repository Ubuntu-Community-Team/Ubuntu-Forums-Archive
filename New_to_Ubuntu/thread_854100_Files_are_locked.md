---
title: "Files are locked"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Gloominati on 2008-07-09
I downloaded some music files from the CD to my computer, but now i cannot delete them because i do not have permission. I have just one user on my computer.

---

### Post by pedro_orange on 2008-07-09
Have you tried sudo rm'ing the folder?

Or opening nautilus in gksudo and then trying?

---

### Post by billgoldberg on 2008-07-09
Open up a terminal (applications -> accessories) and copy/paste this:

```
gksudo nautilus
```

This will open the file manager with root privileges.

After you deleted the music files, close the file browser, as this isn't meant for normal usage.

---

### Post by ibuclaw on 2008-07-09
Run
```
sudo chmod +w **folder_name**
```
in the terminal (replace "folder_name" with the actual name of the folder).
And try again.

Regards
Iain

---

### Post by mc4man on 2008-07-09
Here's short thread on 'issue'. You don't need to use sudo because you own the files/folders, it's just in hardy when you copy from read only media you're only given read and access permissions.
[http://ubuntuforums.org/showthread.php?p=5259083#post5259083](http://ubuntuforums.org/showthread.php?p=5259083#post5259083)

---

### Post by VargasTheBlind on 2008-07-09
What about if you get this error message when trying to give write permission to files that won't be deleted?

"The permissions could not be changed.

Sorry, couldn't change the permissions of "DSC01453.JPG": Operation not supported by backend"

---

