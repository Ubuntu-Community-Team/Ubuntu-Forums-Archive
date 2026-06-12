---
title: "How to do a recursive search of files by filename?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by inktri on 2008-09-16
do i use find?

if i want to find a file called apache2.conf starting at root, recursing, and stopping once one file is found. what command would i use?

---

### Post by roquefilipe on 2008-09-16
to find files you can use "find" but to find files by name I like to use "locate" is quite easy. It uses a database, which you can update by running "updatedb" (it takes a few minutes).

---

### Post by iaculallad on 2008-09-16
To find apache2.conf file in the whole filesystem, use:

```
find / -name apache2.conf
```

EDIT: If it prompts for permission denied messages, insert the sudo command:

```
sudo find / -name apache2.conf
```

---

### Post by trestevenson on 2011-08-10
I was trying to find all M4P files in my Home directory, and I was able to type "find -name *.m4p" to retrieve the list!  I've been wondering how to do this for a while now.  Thanks!

---

