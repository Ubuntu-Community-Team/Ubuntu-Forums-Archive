---
title: "how to delete directory inside another directory"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by Taati_Barao on 2013-11-30
Hi

I had created directory using the command mkdir -p a/{b,c,d/e/f,g}, and  my questions is how can i delete the directory 'b,c,d and g' only with  the single command.

i already try this command

rmdir -p a/{b,c,g}
rm -f a/{b,c,g}

with no luck

Thanks

---

### Post by sudodus on 2013-11-30
You can remove a directory tree with ```
rm -r directory-name
``` (but be careful, because it is not going to any trashcan, it is really deleted).

---

### Post by Impavidus on 2013-11-30
Use **rm -r a/{b,c,d,g}**, which will recursively remove a/d/e/f and a/d/e. If you haven't made other directories in a/, you can also use **rm -r a/***

---

### Post by steeldriver on 2013-11-30
If the directories are empty, then you can use rmdir - but without the -p, because the parent won't be empty if you are not removing all of the subdirs

```

$ mkdir -p a/{b..g}
$ ls a
b  c  d  e  f  g
$ 
$ rmdir a/{b,c,g}
$ ls a
d  e  f

```

If the subdirs are non-empty, then you will need to use rm -r as sudodus says

```

$ mkdir -p a/{b..g}
$ **touch -p a/{b..g}/afile**
$ rmdir a/{b,c,g}
rmdir: failed to remove `a/b': Directory not empty
rmdir: failed to remove `a/c': Directory not empty
rmdir: failed to remove `a/g': Directory not empty
$ 
$ **rm -r a/{b,c,g}**
$ ls a
d  e  f

```

---

