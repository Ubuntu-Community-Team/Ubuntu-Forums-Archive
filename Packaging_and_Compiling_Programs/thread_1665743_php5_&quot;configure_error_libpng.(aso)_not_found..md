---
title: "php5: &quot;configure: error: libpng.(a|so) not found.&quot;"
date: 2011-01-12
forum: Packaging and Compiling Programs
---

### Post by sawatdee on 2011-01-12
I have a laptop that can only run ubuntu 9.04 (jaunty). I have been able to setup apache2 and php5 on this machine before, but for some reason it won't work now, after a fresh install.

apache2 seems to have installed fine

But trying to install either php 5.2 or php 5.3 gives the following error:
```
configure --with-apxs2=/usr/local/apache2/bin/apxs --with-pdo-mysql --with-zlib --with-gd
.
.
.
checking for fabsf... yes
checking for floorf... yes
If configure fails try --with-jpeg-dir=<DIR>
configure: error: libpng.(a|so) not found.

```

One thing I noticed is that libpng.so is in /usr/lib/compiz. I have no idea why it is in there. But I've tried using **--with-jpeg-dir=/usr/lib** and also **--with-png-dir=/usr/lib/compiz** and neither works.

Also, I tried the following. No luck.
```
sudo apt-get install libpng-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libpng-dev is a virtual package provided by:
  libpng12-dev 1.2.27-2ubuntu2.2
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate
```


I know someone is going to suggest installing from packages. I really don't feel comfortable installing apache and php from packages because the only time I ever did it the configuration files were in weird locations and I gave up long before it ever worked. This is the only time (even with this system, and after a reinstall) that I have ever had such problems installing those two applications.

Any help will be much appreciated as this is the only laptop I can develop on. Please!! Please!! Please!!

---

### Post by MadCow108 on 2011-01-13
well first you should do what apt tells you:
install libpng12-dev (**not** libpng-dev

If that package was missing the problem should be solved.

if not use libpng-12-config --cflags --ldflags installed by above package to find the proper paths

(libpng lies in /usr/lib, the thing in compiz-plugins is probably something else, a shared library should not be bundled in another package)

---

### Post by anglican on 2011-01-14
> **MadCow108 said:**
> 
if not use libpng-12-config --cflags --ldflags installed by above package to find the proper paths
That should be > libpng12-config --cflags --ldflags - there's an extra hyphen in there!

H

---

