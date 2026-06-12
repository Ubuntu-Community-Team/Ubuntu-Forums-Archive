---
title: "chmod, change permissions for directory"
date: 2008-09-14
forum: Programming Talk
---

### Post by airjaw on 2008-09-14
Hi, wondering if I can get some (easy) chmod help..

I downloaded source for djangoproject.com, and I'm browsing through the files.
I don't want to have to use sudo gedit to open them.. i want to change the permissions for the entire folder with chmod.

All the commands I've tried have failed for some reason or another.. can someone post the command here, with the reasoning behind it?


this is the folder:
d-wx-wxrwx 3 airjaw airjaw 4096 2008-09-14 14:32 djangoproject.com


edit::  So I've changed permissions of the folder to allow read write execute, but all the files' permissions still locked
drwx--xrwx 4 airjaw airjaw 4096 2008-09-14 14:32 django_website

**so i try**

$ chmod u=rwx django_website -r
chmod: cannot access `u=rwx': No such file or directory

how come it worked before.. but not now?

---

### Post by slavik on 2008-09-14
run the following command

chmod -r u+r djangoproject.com

I suggest you look up a tutorial on Unix permissions and then read the chmod manpage (man chmod)

---

### Post by airjaw on 2008-09-14
Hello.. thank you for the help..

the chown command doesn't change the file permissions.. they're still locked for common users


edit:: nevermind, seemed to hvae eworked for many of the files.. weird how it didn't work for all of them.. oh well that is enough for me.. thanks!


edit 2 :: ok i found out the problem.. it was the lower case -r .. changing it to uppercase -R worked.. that and using 777

---

### Post by Reiger on 2008-09-14
chown does something entirely different from chmod.

The first is about 'owners' (i.e. the names associated with the various named categories: owner:group); the second about permissions. 'ch' is a short for 'change' IIRC.

---

### Post by slavik on 2008-09-14
> **Reiger said:**
> chown does something entirely different from chmod.

The first is about 'owners' (i.e. the names associated with the various named categories: owner:group); the second about permissions. 'ch' is a short for 'change' IIRC.
you are correct.

on another note, I would not advise 777 permissions ...

---

