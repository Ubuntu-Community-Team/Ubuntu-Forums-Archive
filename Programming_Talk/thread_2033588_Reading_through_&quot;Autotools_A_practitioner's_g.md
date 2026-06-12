---
title: "Reading through &quot;Autotools: A practitioner's guide&quot;"
date: 2012-07-26
forum: Programming Talk
---

### Post by musasabi on 2012-07-26
I'm not new to Linux or C, but I am fairly new to hand-writing makefiles and have never touched the autotools.

That said, I'm reading through John Calcote's book and experiencing some weirdness in the middle of Chapter 2.

```
gfi@ubuntu:~/Autotools/jupiter$ ls
Makefile  src
gfi@ubuntu:~/Autotools/jupiter$ make distcheck 
rm jupiter-1.0.tar.gz &> /dev/null
rm -rf jupiter-1.0 &> /dev/null
mkdir -p jupiter-1.0/src
rm: cannot remove `jupiter-1.0.tar.gz': No such file or directory
cp Makefile jupiter-1.0
cp src/Makefile jupiter-1.0/src
cp: accessing `jupiter-1.0/src': Not a directory
make: *** [jupiter-1.0] Error 1
gfi@ubuntu:~/Autotools/jupiter$ ls -alh
total 20K
drwxr-xr-x 3 gfi gfi 4.0K 2012-07-25 15:53 .
drwxr-xr-x 3 gfi gfi 4.0K 2012-07-25 13:28 ..
-rw-r--r-- 1 gfi gfi  660 2012-07-25 15:53 jupiter-1.0
-rw-r--r-- 1 gfi gfi  660 2012-07-25 15:48 Makefile
drwxr-xr-x 2 gfi gfi 4.0K 2012-07-25 14:56 src 
gfi@ubuntu:~/Autotools/jupiter$ rm jupiter-1.0 
gfi@ubuntu:~/Autotools/jupiter$ make distcheck 
rm jupiter-1.0.tar.gz &> /dev/null
rm -rf jupiter-1.0 &> /dev/null
mkdir -p jupiter-1.0/src
rm: cannot remove `jupiter-1.0.tar.gz': No such file or directory
cp Makefile jupiter-1.0
cp src/Makefile jupiter-1.0/src
cp src/main.c jupiter-1.0/src
tar -zcvf jupiter-1.0.tar.gz jupiter-1.0
jupiter-1.0/
jupiter-1.0/Makefile
jupiter-1.0/src/
jupiter-1.0/src/Makefile
jupiter-1.0/src/main.c
rm -rf jupiter-1.0
tar -zxvf jupiter-1.0.tar.gz
jupiter-1.0/
jupiter-1.0/Makefile
jupiter-1.0/src/
jupiter-1.0/src/Makefile
jupiter-1.0/src/main.c
make -C jupiter-1.0 all clean
make[1]: Entering directory `/home/gfi/Autotools/jupiter/jupiter-1.0'
make -C src all
make[2]: Entering directory `/home/gfi/Autotools/jupiter/jupiter-1.0/src'
gcc -g -O0 -o jupiter main.c
make[2]: Leaving directory `/home/gfi/Autotools/jupiter/jupiter-1.0/src'
make -C src clean
make[2]: Entering directory `/home/gfi/Autotools/jupiter/jupiter-1.0/src'
rm jupiter
make[2]: Leaving directory `/home/gfi/Autotools/jupiter/jupiter-1.0/src'
make[1]: Leaving directory `/home/gfi/Autotools/jupiter/jupiter-1.0'
rm -rf jupiter-1.0
*** Package jupiter-1.0.tar.gz ready for distribution.
gfi@ubuntu:~/Autotools/jupiter$
```

As you can see, if I run make distcheck, it'll create a non-directory file and then try to treat it like a directory. Seemingly randomly, if I simply remove the file and run the command again, it'll go through and properly complete it's task.

What's actually happening?

For reference, here's the Makefile, per the book's guidance:
```
package = jupiter
version = 1.0
tarname = $(package)
distdir = $(tarname)-$(version)

all clean jupiter:
        $(MAKE) -C src $@

dist: $(distdir).tar.gz

$(distdir).tar.gz: FORCE $(distdir)
        tar -zcvf $(distdir).tar.gz $(distdir)
        rm -rf $(distdir)

$(distdir):
        mkdir -p $(distdir)/src
        cp Makefile $(distdir)
        cp src/Makefile $(distdir)/src
        cp src/main.c $(distdir)/src

distcheck: $(distdir).tar.gz
        tar -zxvf $(distdir).tar.gz
        $(MAKE) -C $(distdir) all clean
        rm -rf $(distdir)
        @echo "*** Package $(distdir).tar.gz ready for distribution."

FORCE:
        -rm $(distdir).tar.gz &> /dev/null
        -rm -rf $(distdir) &> /dev/null

.PHONY: FORCE all clean dist distcheck
```

---

### Post by scu-ba-de-buntu on 2012-07-28
> **musasabi said:**
> 
```

gfi@ubuntu:~/Autotools/jupiter$ make distcheck 
rm jupiter-1.0.tar.gz
```

```

distcheck: $(distdir).tar.gz
        tar -zxvf $(distdir).tar.gz
        $(MAKE) -C $(distdir) all clean
        rm -rf $(distdir)
        @echo "*** Package $(distdir).tar.gz ready for distribution."

```

Where is jupiter-1.0.tar.gz? The makefile defaults to using "distdir".tar.gz, first trying to unzip/untar it. 

distdir is defined as $(package)-$(version), so the file would be: "$(package)-$(version).tar.gz" in this case, a tarred/gunzipped file.


EDIT: it looks like you are trying to check the creation before creating. you should look up use of tar via "man tar" in terminal. -x is used for extracting, -c for creating, etc. so you should try make for first creating.

---

### Post by spjackson on 2012-07-28
Note that make uses /bin/sh to execute its commands, not bash.
```

FORCE:
        -rm $(distdir).tar.gz &> /dev/null
        -rm -rf $(distdir) &> /dev/null

```That &> is a bash-ism. In sh these rm commands are run in background.

Note that the error message
rm: cannot remove `jupiter-1.0.tar.gz': No such file or directory
occurs after mkdir -p jupiter-1.0/src

Therefore rm -rf jupiter-1.0 also occurs after mkdir -p jupiter-1.0/src
So when we get to cp Makefile $(distdir), the directory no longer exists, so cp does a simple file copy, and then the rest of it goes wrong.

I don't know why the book would give you bash syntax, but running rm in the background is definitely the cause of your problem.

---

### Post by scu-ba-de-buntu on 2012-07-28
> **spjackson said:**
> Note that make uses /bin/sh to execute its commands, not bash.

If your system is not configured already to treat make with bash, can you use something like: CONFIG_SHELL=/bin/bash  ?

---

### Post by steeldriver on 2012-07-28
one possible workaround is to relink /bin/sh to bash (it's a symlink to dash by default)

```
sudo ln -sf bash /bin/sh
```

you can always revert it after with

```
sudo ln -sf dash /bin/sh
```

---

