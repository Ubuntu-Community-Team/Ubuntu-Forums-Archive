---
title: "dpkg-genchanges problems"
date: 2008-07-12
forum: Packaging and Compiling Programs
---

### Post by houbysoft.xf.cz on 2008-07-12
Hi all.
I want to create my own .deb package, so I installed and prepared all that I needed (I think :)). So then I tried to make the package and everything by running this command:
```
$ dpkg-buildpackage -rfakeroot
```
But it keeps saying this rather annoying error because I can't fix it... I've googled a lot...
That error is :
```
dpkg-genchanges: failure: cannot read files list file: No such file or directory
```

Can anyone help me please?
Thanks!

---

### Post by plugwash on 2008-07-13
It would help to know how you created this package.

---

