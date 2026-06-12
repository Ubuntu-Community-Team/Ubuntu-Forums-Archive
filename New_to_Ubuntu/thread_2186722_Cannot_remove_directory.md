---
title: "Cannot remove directory"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by vgezer on 2013-11-08
Hi,

I have a directory in my home dir, but I am unable to remove it in any ways.

Using rm -rf JsZ-r6K.50/ crashes the konsole. I also tried to use sudo rm, but it is the same.

```
drwxr-xr-x  3 volkan volkan     4096 Nov  5 03:19 .installjammerinfo/
drwxrwxr-x  4 volkan volkan     4096 Aug  6 15:28 .java/
drwxr-xr-x  2 volkan volkan 86122496 Nov  8 22:25 JsZ-r6K.50/
drwx------  5 volkan volkan     4096 Nov  8 02:58 .kde/

```

How can I remove this directory?

Thanks,

---

### Post by TheFu on 2013-11-08
It appears to be a non-ASCII directory name.  Perhaps trying
**\rm ~/*.50**
might work?

Once in a while, strange characters in filenames are not interpreted by the shell properly, so we have to find a _trick_. Hope this works, but it may not.

---

