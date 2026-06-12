---
title: "Do i really need the kernel source?"
date: 2012-07-16
forum: Programming Talk
---

### Post by nidzo732 on 2012-07-16
I'm writing some modules and instructions say that i need the entire source code to compile them, but the modules compile even if i point it to /usr/src/linux-headers-(uname -r) instead of source tree. Why do they say I need the source?

---

### Post by TheFu on 2012-07-16
Since you didn't get any responses .... 

If you aren't in a hurry, try it without the source, just the headers, and see if it works. Really, this should work until some dependency in your code fails to locate a library at link time, right?  

It isn't like the kernel source is really all that large by file size for today, though it is pretty large and deep for pure-text files.

This article [http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html) from 2008 says you don't need the entire source code, just the headers, but that you'll have to edit a makefile.  The edit looks minor.

---

### Post by Bachstelze on 2012-07-16
That's because normally, the headers are part of the source and are not distributed separately. They are in Debian/Ubuntu, so you only need the headers, not the full source.

---

### Post by nidzo732 on 2012-07-17
So I guess I could just stick with the headers unless it fails to compile. Thanks!

---

