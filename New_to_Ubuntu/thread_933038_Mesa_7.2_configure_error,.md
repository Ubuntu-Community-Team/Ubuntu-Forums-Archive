---
title: "Mesa 7.2 configure error,"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Nasa01 on 2008-09-29
Hi

I'm trying to install Mesa-7.2 on my ix86-64. However, when I'm running the configure script i get the following error:

checking for GLUT... configure: error: Package requirements (x11 xmu xi) were not met:

No package 'xi' found

What do I need to do to fix this?

Cheers!

---

### Post by klemperal on 2008-09-29
I believe you need to first install the dependency "xspecs".  Just search for xspecs in the package manager and install.  Give it a try and let us know if it works out.

---

### Post by Nasa01 on 2008-09-29
I installed the 'xspecs' via the package handler but I still get the same error message... :(

But thanks for your idea! New ones??

Cheers!

---

### Post by Nasa01 on 2008-09-29
Hi again

Sorry about this but I realized that I just had missed installing libxi-dev. After installing this package via the package handler the configure script worked!

Cheers!

---

