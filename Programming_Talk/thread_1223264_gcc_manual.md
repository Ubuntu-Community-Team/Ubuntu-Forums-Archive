---
title: "gcc manual"
date: 2009-07-26
forum: Programming Talk
---

### Post by mfrancis107 on 2009-07-26
in this thread [here]("http://ubuntuforums.org/showthread.php?t=773526") someone mentions accessing gcc manuals.

```
$ man gcc
$ man pow

```

the *man gcc* comes up but the *pow* does not.  Is there something I need to download to get it?

I don't really need it now, but I don't want to be missing out on various manuals if I ever need them.

Thanks

---

### Post by c0mput3r_n3rD on 2009-07-26
The way the man command works is man -programName.  So pow must be some program, and I doubt it has to do directly with the g++ compiler.

---

### Post by abhilashm86 on 2009-07-26
> **mfrancis107 said:**
> in this thread [here]("http://ubuntuforums.org/showthread.php?t=773526") someone mentions accessing gcc manuals.

```
$ man gcc
$ man pow

```

the *man gcc* comes up but the *pow* does not.  Is there something I need to download to get it?

I don't really need it now, but I don't want to be missing out on various manuals if I ever need them.

Thanks
for some commands, you don't have man entry, use this
```


info pow

```
this gives information and usage of that command........

---

### Post by unknownPoster on 2009-07-26
pow isn't an external program so I doubt it has a full man-page for itself.

pow() is a c function defined in <math.h>

For example, in the following code snippet:

```


double x;
x = pow(3, 2);

```

x would be 9. I hope this points you in the right direction.

---

### Post by MadCow108 on 2009-07-26
yes they do have man pages
but you need to install the manpages-dev package

---

