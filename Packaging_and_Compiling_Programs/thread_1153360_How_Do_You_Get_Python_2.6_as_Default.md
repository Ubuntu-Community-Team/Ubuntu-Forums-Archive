---
title: "How Do You Get Python 2.6 as Default?"
date: 2009-05-08
forum: Packaging and Compiling Programs
---

### Post by jsmidt on 2009-05-08
I have a very simple python package I am trying to package.  Here is my rules file:

```
#!/usr/bin/make -f

DEB_PYTHON_SYSTEM=pycentral

include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/cdbs/1/class/python-distutils.mk

# Add here any variable or target overrides you need.

```

I is giving these errors: 

```
/usr/lib/python2.5/site-packages/numpy/core/include/numpy/ndarrayobject.h:1571: error: expected ‘;’ before ‘int’
...
make: *** [python-build-stamp-2.5] Error 1

```

I need the packager to look in /usr/lib/python2.6/site-packages/numpy/core/include/numpy
 
and build using Python 2.6.  How do I make that happen?

I am running Jaunty.

---

### Post by jsmidt on 2009-05-09
Forget my first comment, it is garbage.  

If anyone has time, could you look into why healpy won't build on Ubuntu Jaunty: [http://code.google.com/p/healpy/](http://code.google.com/p/healpy/).  (The upstream source)

I thought it would be an easy package to build since it builds flawlessly on Fedora 10 which uses the same gcc version. (4.3)  There are a ton of errors when I build on Jaunty, and it is hard for me to dig through them all.

It would be a big help if someone could take a few minutes and try.  Thanks.

---

### Post by A Feyn Man on 2009-09-24
I am also doing some CMBR research and I'm supposed to get healpy installed and working and I cannot make it work. Any help?



-I'm on Jaunty too

---

### Post by dinxter on 2009-09-27
> **A Feyn Man said:**
> I am also doing some CMBR research and I'm supposed to get healpy installed and working and I cannot make it work. Any help?



-I'm on Jaunty too
the jsmidt above seems to have cracked it sometime after his post (though not on amd64) see
[https://launchpad.net/~jsmidt/+archive/ppa/+packages](https://launchpad.net/~jsmidt/+archive/ppa/+packages)

---

