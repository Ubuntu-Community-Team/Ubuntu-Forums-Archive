---
title: "[SOLVED] Package manager problem error"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Unotforme on 2008-07-20
When I hover my mouse over the package manager I get the message:
'A problem occurred when checking for the updates'

When I try to start the PM, it runs for a second then shuts down, no error message or anything (except the existing one in the toolbar).

I've gone to terminal, ran sudo apt-get update, that works.
then when I try to run sudo apt-get upgrade or install this is what I get:

```

larry@home:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%
larry@home:~$ sudo apt-get install
Reading package lists... Done
Segmentation faulty tree... 50%
larry@home:~$ 

```

What do I do from here?

---

### Post by iaculallad on 2008-07-20
Open your terminal:

```
sudo rm /var/cache/apt/*.bin
```

Then:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Unotforme on 2008-07-20
> Open your terminal:

[CODE]sudo rm /var/cache/apt/*.bin[/CODE}

Thanks, now what exactly does that command do?

---

### Post by iaculallad on 2008-07-20
> **Unotforme said:**
> Thanks, now what exactly does that command do?

It will delete/remove all files with the extension of BIN in your /var/cache/apt directory.

---

### Post by Unotforme on 2008-07-20
Actually, I figured that out after I thought about it! Perhaps the question I *should* have asked is: How and why did those files get in there in the first place, and why should I delete them?

---

### Post by iaculallad on 2008-07-21
> **Unotforme said:**
> Actually, I figured that out after I thought about it! Perhaps the question I *should* have asked is: How and why did those files get in there in the first place, and why should I delete them?

> Dir::Cache
pkgcache - Apt's memory mapped package cache location, normally /var/cache/apt/pkgcache.bin
srcpkgcache - Apt's memory mapped source package cache location, normally /var/cache/apt/srccache.bin


You should delete it since it has been corrupted. Actually, 2 binary files are located within that folder, namely  pkgcache.bin and srcpkgcache.bin.

---

### Post by undoIT on 2008-09-18
I just got this error and indeed, clearing the cache of the .bin files fixed the problem. Thanks!

Another question, is it safe to clear the .deb files in the archive folder?

---

