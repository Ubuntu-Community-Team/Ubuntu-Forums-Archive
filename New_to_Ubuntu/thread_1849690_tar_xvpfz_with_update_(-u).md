---
title: "tar xvpfz with update (-u)?"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-25
Hi,

"cp -u source target" can update looking if newer file. It saves lot of time sometimes. 

Could this update check (with any switch/argument) be possible also with tar? 

it states -u into man tar

> tar xvpfz -u mytar.tar.gz returns error

Thank you

---

### Post by gmargo on 2011-09-25
Be sure to read the **tar(1)** man page closely.

The first argument to **tar** is the "function", of which **u** (**--update**) is one.  You've specified **x** (**--extract**) as the first argument instead.

To use the update feature you would need something like this:
```

tar uvzf mytar.tar.gz file1 file2 etc...

-or-

tar uvzf mytar.tar.gz directoryname

```

---

### Post by honeybear on 2011-09-26
thank you, however :( it is not working.

```
cd ; tar uvzf    /mnt/archive.tar.gz 
```
tar: Cannot update compressed archives
Try `tar --help' or `tar --usage' for more information.

---

