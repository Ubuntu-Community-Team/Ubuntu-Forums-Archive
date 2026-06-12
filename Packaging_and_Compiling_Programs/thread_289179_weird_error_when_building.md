---
title: "weird error when building"
date: 2006-10-30
forum: Packaging and Compiling Programs
---

### Post by tenshu on 2006-10-30
hello all,

i'm actually getting an error when trying to build a small tool.

here is the result of : 

```
$ sudo pbuilder build *dsc
```

```
# Add here commands to install the package into debian/ciso.
/usr/bin/make install DESTDIR=/tmp/buildd/ciso-1.0.0/debian/ciso
make[1]: Entering directory `/tmp/buildd/ciso-1.0.0'
install -m 755 ciso /tmp/buildd/ciso-1.0.0/debian/ciso/usr/bin
install: cannot create regular file `/tmp/buildd/ciso-1.0.0/debian/ciso/usr/bin': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/tmp/buildd/ciso-1.0.0'
make: *** [install] Error 2
pbuilder: Failed autobuilding of package
 -> Aborting with an error
```

here is the the install line in debian/rules :

```
# Add here commands to install the package into debian/ciso.
	$(MAKE) install DESTDIR=$(CURDIR)/debian/ciso
```

I'm still getting an error when trying to replace DESTDIR by PREFIX


I'm quite confused since this is the very first time i'm packaging something

Tenshu

---

### Post by zgornel on 2006-11-29
Is the /tmp/buildd/ciso-1.0.0/debian/ciso dir present ?

---

