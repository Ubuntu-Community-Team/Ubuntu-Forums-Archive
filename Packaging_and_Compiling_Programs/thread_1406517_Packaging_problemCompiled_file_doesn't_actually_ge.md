---
title: "Packaging problem:Compiled file doesn't actually get included in deb"
date: 2010-02-14
forum: Packaging and Compiling Programs
---

### Post by SoftwareExplorer on 2010-02-14
I'm trying to package a single .c file that only came with instructions on what command to run to compile it and then copy it into /usr/lib/gtk-2.0/modules/. I had to make a makefile and package it. 
Here's the problem:When I try to build it with pbuilder, the resulting deb doesn't have the file that I'm trying to install. So, what am I doing wrong? I will attach the files for it. (I had to add .txt to the end of a few of them)
Thanks in advance, I'm really confused why it isn't working.

---

### Post by SoftwareExplorer on 2010-02-14
Update:I tried adding ls ${DESTDIR}${PREFIX}/lib/gtk-2.0/modules/ to the list of commands to run when make install is called, and when make install is called in pbuilder, it says librgba.so , so it seems like the makefile is putting it in the correct place, however, it still doesn't show up in the deb file.

---

### Post by Dies on 2010-02-14
Your rules file neither compiles nor installs the module, at least not as far as I can tell from looking at your diff.



Edit - Look at this diff for an example that does exactly what your trying to do

[http://launchpadlibrarian.net/38676677/libappstyle_0.1.1-2.diff.gz](http://launchpadlibrarian.net/38676677/libappstyle_0.1.1-2.diff.gz)

---

### Post by SoftwareExplorer on 2010-02-14
> **Dies said:**
> Your rules file neither compiles nor installs the module, at least not as far as I can tell from looking at your diff.
Edit - Look at this diff for an example that does exactly what your trying to do
[http://launchpadlibrarian.net/38676677/libappstyle_0.1.1-2.diff.gz](http://launchpadlibrarian.net/38676677/libappstyle_0.1.1-2.diff.gz)
As far as the rules file, I think it was just calling make which was running my makefile. However, the file that you pointed out is part of a package that is really similar to what I'm trying to do, so I tried taking the packaging from that package and modifying it as little as possible for my package, but I got the same result:no binary file in the deb. Not only that, but the the package I was trying to copy worked perfectly fine in my pbuilder. I attached the new versions of everything to this post.

By the way, the command that needs to be run to compile it is
```
gcc -fPIC -shared librgba.c -o librgba.so `pkg-config --cflags --libs gtk+-2.0`

```
and to install it the file librgba.so needs to end up in ```
/usr/lib/gtk-2.0/modules/
```

---

### Post by Dies on 2010-02-15
Yeah, my bad I kind of skimmed your first post, seems I completely missed the part about you using a Makefile. But in any case, I still think it's easier not to. ;)


Your problem, I didn't spend too much time figuring out why, is that you're installing to a different folder. Anyways try this new rules file, it should work.

---

### Post by SoftwareExplorer on 2010-02-15
> **Dies said:**
> Yeah, my bad I kind of skimmed your first post, seems I completely missed the part about you using a Makefile. But in any case, I still think it's easier not to. ;)


Your problem, I didn't spend too much time figuring out why, is that you're installing to a different folder. Anyways try this new rules file, it should work.

It works! Thanks so much!

---

