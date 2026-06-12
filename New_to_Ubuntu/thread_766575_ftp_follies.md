---
title: "ftp follies"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Dev'olution on 2008-04-25
Hey guys...

Just set up vsftpd.

I've set it so users can log in but they are jailed to their /home/username folders.

the question i have is, is there a way to set up a link to allow them to upload stuff to their own designated folder in /var/www e.g /var/www/username ??? :confused:

Cheers,
Kristian :popcorn:

---

### Post by HereInOz on 2008-04-25
Just set up a symbolic link within the user's home directory, linking to the location where you want the files to be able to be put.  You may also need to give them ownership of the destination directory as well.

---

### Post by Dev'olution on 2008-04-25
> **HereInOz said:**
> Just set up a symbolic link within the user's home directory, linking to the location where you want the files to be able to be put.  You may also need to give them ownership of the destination directory as well.


Forgive me for being daft, but how do i do that?

---

