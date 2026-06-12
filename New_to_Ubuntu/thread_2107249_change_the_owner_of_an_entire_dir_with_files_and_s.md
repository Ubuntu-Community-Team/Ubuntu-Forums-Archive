---
title: "change the owner of an entire dir with files and subdirectories"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by herbert tamayo on 2013-01-21
hi, I had unzipped an file that using the root account, the unzipped result was a main directory that has several files and subdirs, i waht to change the owner to my user account, i use this comand:

chown user.user /dir

but it only change the owner of the directory but the content it always belongs to the root, my question is:

what parameter should I use to change the owner of all objects inside that dir?

regards

---

### Post by hydn79 on 2013-01-21
use:
chown -R user:user /dir

---

### Post by audiomick on 2013-01-21
Some more info, a bit more general:

You can find things like options for commands by looking at the man page. In this case
```
man chown
```


For people who are looking for a way to do this from the GUI, you can start an instance of the file manager, Nautilus, using gksudo

```
gksudo nautilus
```

This instance will have root privileges, and will allow you to change permissions of root owned directories and files by right clicking and going to "preferences" on the permissions tab. Be careful using Nautilus like this. It will also allow you to completely break your system if you do the wrong thing with it. ;)

---

