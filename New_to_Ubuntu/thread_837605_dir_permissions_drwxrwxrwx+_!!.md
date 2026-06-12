---
title: "dir permissions: drwxrwxrwx+ !!"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Gourgi on 2008-06-22
i have a  samba folder writable for my LAN's users (name _full_)
and today i noticed this weird permissions:
```

cd full
ls -la : 
**drwxrwxrwx+**  2 nobody   data       61 2008-06-16 14:52  Persia
cd Persia
ls -la:
total 6855980
**drwxr-xr-x+**  2 nobody   data         32 2008-06-16 14:52 .
drwxrwxrwx  10 penny    data       4096 2008-06-22 23:43 ..
-rwxr-xr-x   1 nobody   data 7020511232 2008-05-20 20:50 Persia.iso

```
what is this plus '+' stands for?
is there a way to remove it ?
i tried chmod, chown , moving to new dir  but the '+' still exists !

---

### Post by UltraMathMan on 2008-06-22
I'd recommend taking a look at [this thread]("http://www.mail-archive.com/gnhlug-discuss@mail.gnhlug.org/msg15608.html"). 

Seems the + means an ACL permission has been set for the file.

-Hope this helps :)

---

### Post by Gourgi on 2008-06-22
of course i saw that ,
> acl_clear_perms is a command line util that will clear the ACLs on a file.  There is also acl_get_perms, set, etc..

Not sure how Samba explicity uses there internally.  I know samba supports ACL's itself, but I'm unsure if it uses the file system ACL's, or emulate them itself.

  Thomas


the only result from google that helped , but where can i find acl_clear_perm ?
is it available in ubuntu ?

---

### Post by UltraMathMan on 2008-06-22
To get the acl_clear_perms utility you need to install libacl1-dev.

```
sudo apt-get install libacl1-dev
```

Never really used Samba so I'm not too sure where to go from there, but I expect man acl_clear_perms may be of some help.

---

