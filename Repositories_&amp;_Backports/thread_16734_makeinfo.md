---
title: "makeinfo?"
date: 2005-02-23
forum: Repositories &amp; Backports
---

### Post by hemlock on 2005-02-23
It doesn't look like the makeinfo utility is available in Ubuntu "warty". Is this true? One post suggested:

sudo apt-get install build-essential

I tried this, but still no makeinfo...

---

### Post by avnbsuresh on 2005-06-13
I had the same issue with unbuntu. You can fix it by installing texinfo

sudo apt-get install texinfo

---

### Post by yygyt on 2009-08-17
I have the same issue with ubuntu, too but installing texinfo does not solve the problem.
Does anyone have an idea? 
I get the following error


```


for f in standards.info configure.info; do \
          if test -f ../../newlib-1.15.0/etc/`echo $f | sed -e 's/.info$/.texi/'`; then \
            if make "MAKEINFO=/home/.../aibo/newlib-1.15.0/missing makeinfo --split-size=5000000 --split-size=5000000" $f; then \
              true; \
            else \
              exit 1; \
            fi; \
          fi; \
        done
make[3]: Entering directory `/home/.../aibo/bld-newlib-1.15.0/etc'
/home/.../aibo/newlib-1.15.0/missing makeinfo --split-size=5000000 --split-size=5000000 --no-split -I../../newlib-1.15.0/etc -o standards.info ../../newlib-1.15.0/etc/standards.texi
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
make[3]: *** [standards.info] Error 1
make[3]: Leaving directory `/home/.../aibo/bld-newlib-1.15.0/etc'
make[2]: *** [info] Error 1
make[2]: Leaving directory `/home/.../aibo/bld-newlib-1.15.0/etc'
make[1]: *** [all-etc] Error 2
make[1]: Leaving directory `/home/.../aibo/bld-newlib-1.15.0'
make: *** [all] Error 2


```

---

### Post by shakty on 2009-09-29
It worked for me

---

### Post by robertjd on 2009-12-14
Installing the texinfo package worked for me also (Ubuntu 9.10)

---

### Post by jamshid on 2010-02-27
I was getting this makeinfo error when trying to build and install emacs 23.1 on Ubuntu 8.04. (painful!)

After doing "sudo apt-get install texinfo" to get the "makeinfo" command, make sure you run "./configure" on a freshly unpacked source directory. "configure" apparently caches information and "remembers" you don't have makeinfo, so you'll keep getting that error about a missing makeinfo.

Btw, I wanted emacs23, instead of emacs22, to get nice looking [antialiased] fonts. To build you need to "sudo apt-get install libgtk2.0-dev" along with "libjpeg62-dev" and "libjpeg62-dev".

---

### Post by Vi3GameHkr on 2010-03-11
> **jamshid said:**
> I was getting this makeinfo error when trying to build and install emacs 23.1 on Ubuntu 8.04. (painful!)

After doing "sudo apt-get install texinfo" to get the "makeinfo" command, make sure you run "./configure" on a freshly unpacked source directory. "configure" apparently caches information and "remembers" you don't have makeinfo, so you'll keep getting that error about a missing makeinfo.

Btw, I wanted emacs23, instead of emacs22, to get nice looking [antialiased] fonts. To build you need to "sudo apt-get install libgtk2.0-dev" along with "libjpeg62-dev" and "libjpeg62-dev".

I hope I won't get in trouble for letting everyone know that this worked for me.

---

### Post by dakshbhatt21 on 2013-02-09
thank you, it works for me

---

### Post by overdrank on 2013-02-09
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

