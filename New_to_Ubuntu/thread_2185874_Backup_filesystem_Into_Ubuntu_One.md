---
title: "Backup filesystem Into Ubuntu One"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by ghosthost2 on 2013-11-04
Hello there,

I would like to back up my entire filesystem ( / )onto ubuntu one using deja dup which came preinstalled on my ubuntu 13.04. My question is, are there any files/folders that I would like deja dup to ignore while backing up my filesystem?

Thanks

---

### Post by rihikz on 2013-11-04
I wouldn't recommend just copying your entire filesystem. I think it would be a better Idea to only backup your home folder.

---

### Post by ghosthost2 on 2013-11-04
Yeah but I am worried about when Im installing programs more than once having all these extra folders in the filesystem. I know about $ sudo apt-get remove --purge filename but I am not 100 percent sure it removes all the files. Is there a better way to go about this?

---

### Post by newb85 on 2013-11-04
```
sudo apt-get --purge [packagename]
```
will not remove configuration files within your /home directory.  However, installing the application a second time will just use the previously created configuration files.

---

### Post by ghosthost2 on 2013-11-04
what about the files installed in /

---

### Post by sandyd on 2013-11-04
> **ghosthost2 said:**
> what about the files installed in /

the command above does remove configuration files in /

---

