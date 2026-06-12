---
title: "Installing python from source broke python-gtk2"
date: 2008-02-03
forum: Programming Talk
---

### Post by aashay on 2008-02-03
Yesterday I installed python from source. I'm not sure what happened but now when importing gtk i get the error 
```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gtk
```
I tried reinstalling python and python-gtk2 from synaptic to no avail. I can't find any way to remove the source installation or revert back to my previous configuration. Can anyone please assist me to get python-gtk2 back?
EDIT: /usr/bin/python2.5 seems to be working fine. The default "python" interpreter (don't know where it is located) is having the problem. I am thinking of removing "python" and linking python2.5 to it. Would it work? How would I do it?
Edit 2: Alright, I ended up removing " python" binaries from /usr/local/bin and /usr/bin and copying python2.5 as python . Stuff works now, but I would still like to know what the proper solution would have been

---

### Post by Compyx on 2008-02-03
The 'proper' solution of installing stuff from source which already is installed through a package manager is to install into a different prefix. Usually one would use /usr/local for stuff installed from 'alien' sources and /usr for stuff installed by the package manager.
However, the distinction between /usr and /usr/local is not very clear in most distributions, so choosing a prefix such as /opt might be safer.

You could for example pass this to ./configure:
```

./configure --prefix=/opt

```
this ensures all files will be installed into /opt/{bin,etc,lib,..}. This way you keep a clear distinction between the different installs of a package. Ofcourse this assumes the installer playing nice and not having hard-coded paths.

After building a package (make), you can then do a
```

make -n install

```
which will output all commands issued by install but will not execute them. You can then review what changes will be made to your system.
To be even more safe, create an empty directory /var/tmp/fakeroot and issue:
```

make DESTDIR=/var/tmp/fakeroot install

```
This will install all files into /var/tmp/fakeroot as if they where installed into the root (/) directory of your system.
If you see anything other than opt/ in /var/tmp/fakeroot, the installer is flaky and you need to be extra careful.

This /opt approach also means you need to update /etc/ld.so.conf and the PATH environment variable, along with adding MANDATORY_MANPATH entries to man_db.conf and extending or creating the PKG_CONFIG_PATH environment variable to point to the newly installed *.pc files (if any).

Ofcourse, you're usually better off using your package manager unless you really know what you're doing. ;)

---

### Post by aashay on 2008-02-03
got it... i tried installing python from source thinking it came with an IDE. Guess I need to read stuff more carefully :)

---

### Post by pmasiar on 2008-02-03
You can install Python ide separately, I like IDLE as simple Python IDE.

---

