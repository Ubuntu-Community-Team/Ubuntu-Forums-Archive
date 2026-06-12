---
title: "Ogre 3d and libxf86vm"
date: 2006-09-18
forum: Programming Talk
---

### Post by pikeblodd on 2006-09-18
Hi all.  Im trying to comipile Ogre 3d from the tarball off [www.ogre3d.org](www.ogre3d.org) site.  I found most of the dependencies ./configure asked for except this one.  Any ideas on where I might track this little bugger down?

---

### Post by pikeblodd on 2006-09-19
/bump

---

### Post by llonesmiz on 2006-09-19
You need to install the package: libxxf86vm-dev. Good luck.

Edit: You should install libtiff4-dev and libmng-dev too. "Configure" worked without them, but then the compilation failed. Installing them solved the problem.

---

### Post by pikeblodd on 2006-09-19
sweet, thank you, p.s. is there some sadistic coder out there that names these lib's slightly different than their names?

---

### Post by Choad on 2007-06-23
ok im trying to do this too, and i get some more dep problems

first i had to get libxrandr-dev

now it's asking for freeimage. libfreeimage-dev doesnt exist in the feisty repos. how can i get it? dont really want to go breaking my system installing gusty packages

---

### Post by Choad on 2007-06-23
ok it compiled straight away from the sourceforge download. compiling OGRE now. then on to pyOGRE!

---

### Post by zettai on 2008-07-26
> **pikeblodd said:**
> sweet, thank you, p.s. is there some sadistic coder out there that names these lib's slightly different than their names?

I'd love an answer to this one as well...why are the names different?

---

