---
title: "source code"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by lucky.developer on 2008-05-01
i checked out this directory  usr/src/   it has two directories which say like.. linux headers":(

:confused:do these directories actually contain the UBUNTU sourcecode ???

:confused:or do these contain the linux kernel source code ???

if not... what are these folders ...?

---

### Post by kellemes on 2008-05-01
> **lucky.developer said:**
> i checked out this directory  usr/src/   it has two directories which say like.. linux headers":(

:confused:do these directories actually contain the UBUNTU sourcecode ???

:confused:or do these contain the linux kernel source code ???

if not... what are these folders ...?


kernel sources..

---

### Post by lucky.developer on 2008-05-01
sources means..you say them as source code ??? of the linux or ubuntu kernel ???

---

### Post by Bothered on 2008-05-01
If you're looking for the source code for ubuntu packages you can download them with apt-get:

```
apt-get source [package]
```

---

### Post by nrs on 2008-05-01
> **lucky.developer said:**
> i checked out this directory  usr/src/   it has two directories which say like.. linux headers":(

:confused:do these directories actually contain the UBUNTU sourcecode ???

:confused:or do these contain the linux kernel source code ???

if not... what are these folders ...?

With the exception of a few patches and utilities, there isn't really such a thing as Ubuntu source code. Ubuntu (and all other Linux distributions) are more of an amalgamation of the GNU system and the Linux kernel + tons of other projects. linux-headers contains just that -- the headers, if confused. > [COLOR="DeepSkyBlue"]A header file commonly contains forward declarations of subroutines, variables, and other identifiers. Identifiers that need to be declared in more than one source file can be placed in one header file, which is then included whenever its contents are required.[/COLOR] There is a package available which contains the source, unfortunately I don't have access to my Ubuntu machine so I can't tell you for certain what it is, I think it's just linux-source, which you can grab using either apt-get or synaptic. 

Most other packages you'll have to get using > apt-get source packagename

---

### Post by hyper_ch on 2008-05-01
you can't just apt-get source... you first need to add the src-repos first :)

---

