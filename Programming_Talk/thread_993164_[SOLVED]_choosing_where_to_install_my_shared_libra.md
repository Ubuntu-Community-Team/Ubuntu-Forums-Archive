---
title: "[SOLVED] choosing where to install my shared library with autotools"
date: 2008-11-25
forum: Programming Talk
---

### Post by Bulletbeast on 2008-11-25
I'm working on my first shared library (which I'm planning to distribute as a part of a bigger application) using GNU autotools. My problem is as follows.

```
./configure
make
make install
```
installs the library in /usr/local/lib, a directory which, as I suspect, isn't in your average search path. Googling through documentation and tutorials on autotools has been futile for now, so how do I make my library install in, say, /usr/lib? Or determine where to install depending on the platform? Not to mention, how do I handle /usr/lib, /usr/lib32 and /usr/lib64?

---

### Post by snova on 2008-11-25
Pass the --prefix option to configure, set to /usr. There are more specific options to change individual installation paths, use --help to get a list.

In general, you should leave it to install to /usr/local, though. That's what the directory tree is for. /usr is for the package manager to use, /usr/local is for your own purposes.

Oh, and I'm pretty sure GCC will search /usr/local/lib for libraries the same as it will /lib and /usr/lib.

---

### Post by dwhitney67 on 2008-11-25
> **snova said:**
> ...
Oh, and I'm pretty sure GCC will search /usr/local/lib for libraries the same as it will /lib and /usr/lib.
Not necessarily on all platforms (e.g. Fedora).  Under Fedora, one will have to create /usr/local/lib (and if necessary /usr/local/include), and then either update /etc/ld.so.conf or insert a file into /etc/ld.so.conf.d.  Then follow up by running 'ldconfig'.

I know this to be true because I had to do it myself to replicate the default setup that is available with Ubuntu.


P.S.  Here are the steps that I had in my Makefile to install a library for personal use:
```

install: depend $(LIBNAME)
        @echo Makefile - installing $(LIB)
        @if [ ! -d $(DEST)/lib ]; then \
                mkdir -p $(DEST)/lib; \
        fi
        @if [ ! -d $(DEST)/include ]; then \
                mkdir -p $(DEST)/include; \
        fi
        @$(RM) $(DEST)/lib/$(LIBNAME)*
        @install -m 444 $(LIBREL) $(DEST)/lib
        @ln -s $(DEST)/lib/$(LIBREL) $(DEST)/lib/$(LIBNAME)
        @install -m 444 $(HDRS) $(DEST)/include
        @if [ `id -u` -eq 0 ]; then \
                echo running ldconfig...; \
                /sbin/ldconfig; \
        fi

```
By default, DEST is set to /usr/local, but it can be overridden by the operator when running the 'make' command.

---

