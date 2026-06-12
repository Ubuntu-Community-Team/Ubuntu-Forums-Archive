---
title: "Toolchain build error..."
date: 2008-02-26
forum: Packaging and Compiling Programs
---

### Post by iharrold on 2008-02-26
So I am trying to build up a tool for a processor that I am working on.  I get the following build error.

> [b]WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.[/b]
mv: target `.//home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/binutils-2.16.92/bfd/doc/' is not a directory: No such file or directory
make[3]: *** [/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/binutils-2.16.92/bfd/doc/bfd.info] Error 1
make[3]: Leaving directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd/doc'
Making info in po
make[3]: Entering directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd/po'
( if test 'x/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/binutils-2.16.92/bfd/po' != 'x.'; then \
            posrcprefix='/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/binutils-2.16.92/bfd/'; \
          else \
            posrcprefix="../"; \
          fi; \
          rm -f SRC-POTFILES-t SRC-POTFILES \
            && (sed -e '/^#/d' \
                    -e '/^[     ]*$/d' \
                    -e "s@.*@   $posrcprefix& \\\\@" < /home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/binutils-2.16.92/bfd/po/SRC-POTFILES.in \
                | sed -e '$s/\\$//') > SRC-POTFILES-t \
            && chmod a-w SRC-POTFILES-t \
            && mv SRC-POTFILES-t SRC-POTFILES )
( rm -f BLD-POTFILES-t BLD-POTFILES \
            && (sed -e '/^#/d' \
                    -e '/^[     ]*$/d' \
                    -e "s@.*@   ../& \\\\@" < /home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/binutils-2.16.92/bfd/po/BLD-POTFILES.in \
                | sed -e '$s/\\$//') > BLD-POTFILES-t \
            && chmod a-w BLD-POTFILES-t \
            && mv BLD-POTFILES-t BLD-POTFILES )
cd .. \
          && CONFIG_FILES=po/Makefile.in:po/Make-in \
             CONFIG_HEADERS= /bin/sh ./config.status
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing default commands
make[3]: Leaving directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd/po'
make[3]: Entering directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd/po'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd/po'
make[3]: Entering directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd'
make[3]: Nothing to be done for `info-am'.
make[3]: Leaving directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd'
[b]make[2]: *** [info-recursive] Error 1
make[2]: Leaving directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils/bfd'
make[1]: *** [all-bfd] Error 2
make[1]: Leaving directory `/home/iharrold/temp_Marvell/toolchain/build/arm-iwmmxt-linux-gnueabi/gcc-4.1.1-glibc-2.5/build-binutils'
make: *** [all] Error 2[/b]

I believe the errors are due to the 'makeinfo' message.  However, i have tried:
```

sudo apt-get install makeinfo
sudo apt-get install Texinfo
sudo apt-get install GNU make
sudo apt-get install make

```

None are able to find the package to install.  

Anyone have some experience with this?  I did have to install 'bison' and 'flex' to get this far though.  How do I get 'makeinfo'?  Excuse me but this is the first time I have tried to build a toolchain before.

EDIT:

```

sudo apt-get install texinfo
```

That installs makeinfo

---

### Post by Jon_Bagg on 2008-02-26
I am getting the same error when tiring to build newlibc in cross compiler gnuarm in Ubuntu 7.04

Using instructions

[http://www.mcuprogramming.com/blog/2007/04/22/build-your-own-arm-cross-compiler-toolchain-2/#more-155](http://www.mcuprogramming.com/blog/2007/04/22/build-your-own-arm-cross-compiler-toolchain-2/#more-155)

> jonathanb@jonathanb-desktop:/usr/local/gnuarm/newlib-1.14.0$ sudo make all
make[1]: Entering directory `/usr/local/gnuarm/newlib-1.14.0'
Configuring in ./etc
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
creating ./config.status
creating Makefile
make[2]: Entering directory `/usr/local/gnuarm/newlib-1.14.0/etc'
for f in standards.info configure.info; do \
          if test -f .././etc/`echo $f | sed -e 's/.info$/.texi/'`; then \
            if make "MAKEINFO=/usr/local/gnuarm/newlib-1.14.0/missing makeinfo --split-size=5000000 --split-size=5000000" $f; then \
              true; \
            else \
              exit 1; \
            fi; \
          fi; \
        done
make[3]: Entering directory `/usr/local/gnuarm/newlib-1.14.0/etc'
/usr/local/gnuarm/newlib-1.14.0/missing makeinfo --split-size=5000000 --split-size=5000000 --no-split -I.././etc -o standards.info .././etc/standards.texi
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
make[3]: *** [standards.info] Error 1
make[3]: Leaving directory `/usr/local/gnuarm/newlib-1.14.0/etc'
make[2]: *** [info] Error 1
make[2]: Leaving directory `/usr/local/gnuarm/newlib-1.14.0/etc'
make[1]: *** [all-etc] Error 2
make[1]: Leaving directory `/usr/local/gnuarm/newlib-1.14.0'
make: *** [all] Error 2
jonathanb@jonathanb-desktop:/usr/local/gnuarm/newlib-1.14.0$

**Update:**
I was building and installing to the same directory.  Once I built from my home directory and installed to a separate directory (/usr/local/gnuarm) and built as root, all was fine.

---

### Post by skrzyp on 2008-08-08
I have the same problem. I'm doing everything on kubuntu 8.04. 
None of your solutions work. 

make all install always fails.

I've just downloaded newlib 1.16, and it finally works (i mean - i'm able to compile it). However i'm not sure if that is a good idea to use newer library. I've never worked with arm before. Will this produce valid code?

---

### Post by InfinityCircuit on 2008-08-08
Please remember that Linux is case-sensitive and that per debian policy there are only lowercase package names in the repository.  Thus, apt-get install Texinfo will never work.

Remember also that you can use apt-file to find binaries:

```
dmr@skynet:~$ apt-file search /bin/makeinfo
texinfo: /usr/bin/makeinfo
```

---

### Post by piob on 2008-08-09
Hi guys,

a short summary of an odyssey compiling GNUARM GCC-4.2 toolchain :

- follow [http://www.gnuarm.org/support.html](http://www.gnuarm.org/support.html)

- watch out -> there are two different GNUARM sites .com and .org
  gnuarm.org offers the newest and up-to-date packages!

- there is another good tutorial : [http://repo.intilinux.com/str/Using%20Open%20Source%20Tools%20for%20STR7xx%20Cross%20Development.zip](http://repo.intilinux.com/str/Using%20Open%20Source%20Tools%20for%20STR7xx%20Cross%20Development.zip)
written by Giacomo Fazio and Gabriele Nasca

- the main Makefile of newlib-1.15.0 has a bug resulting in :

[B]make[1]: Entering directory `/opt/GNUARM/newlib-1.15.0'
Configuring in ./etc
configure: creating cache ./config.cache
checking for a BSD-compatible install... /usr/bin/install -c
updating cache ./config.cache
configure: creating ./config.status
config.status: creating Makefile
make[2]: Entering directory `/opt/GNUARM/newlib-1.15.0/etc'
for f in standards.info configure.info; do \
	  if test -f .././etc/`echo $f | sed -e 's/.info$/.texi/'`; then \
	    if make "MAKEINFO=/opt/GNUARM/newlib-1.15.0/missing makeinfo --split-size=5000000 --split-size=5000000" $f; then \
	      true; \
	    else \
	      exit 1; \
	    fi; \
	  fi; \
	done
make[3]: Entering directory `/opt/GNUARM/newlib-1.15.0/etc'
/opt/GNUARM/newlib-1.15.0/missing makeinfo --split-size=5000000 --split-size=5000000 --no-split -I.././etc -o standards.info .././etc/standards.texi
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
make[3]: *** [standards.info] Error 1
make[3]: Leaving directory `/opt/GNUARM/newlib-1.15.0/etc'
make[2]: *** [info] Error 1
make[2]: Leaving directory `/opt/GNUARM/newlib-1.15.0/etc'
make[1]: *** [all-etc] Error 2
make[1]: Leaving directory `/opt/GNUARM/newlib-1.15.0'
make: *** [all] Error 2
[/B]

my solution was a brutal one - the Makefile has been modified as folows:

MAKEINFO = /opt/GNUARM/newlib-1.15.0/missing makeinfo
to
MAKEINFO = makeinfo

One has to be sure if there is a makeinfo in the system!

The bug is caused by a wrong "missing" BASH script, but I have no time and desire to seek for real cause... (KISS :)).

All this was possible after only 2 days of fighting with the GCC 4.2.3 suite. The problem was a polish GCC port which feeded the ld linker with not-anymore-supported option --hash-style=both. Unfortunately I couldn't localize and alter the default system wide linker options for GCC compiler. Reinstall was the only solution.:lolflag:

Cheers

PioB

PS: insight-6.6 source code has a little problem with missing termcap library. One has to install the Ubuntu libcurses-dev package.

---

### Post by skrzyp on 2008-08-10
As you said, there is a tutorial on gnuarm.org site. What is kindof strange is that it says to compile just gdb (in the end). However, on the "files" page, they put link to whole insight. 

First i was trying to compile gdb together with insight, but the  error from newlib (the makeinfo issue) appeared. So finally i've compiled pure gdb. 

I believe it is working as it produces some code. However i still didn't have a chance to test it on a real ARM. After i come home, I will try your trick with trimming down newlib and insight makefiles :)

---

### Post by waipotn on 2008-09-29
> **piob said:**
> 
PS: insight-6.6 source code has a little problem with missing termcap library. One has to install the Ubuntu libcurses-dev package.

Thanks for your solutions piob.
By the way, in Ubuntu 8.04, I installed libncurses5-dev to solve the problems.

PS. There is a GNU ARM installer which build the toolchain automatically ([please see here]("http://forum.mcuprogramming.com/arm/gnu-arm-toolchain-installer/0/"))

---

### Post by tommpogg on 2010-11-17
> **piob said:**
> 

my solution was a brutal one - the Makefile has been modified as folows:

MAKEINFO = /opt/GNUARM/newlib-1.15.0/missing makeinfo
to
MAKEINFO = makeinfo

One has to be sure if there is a makeinfo in the system!


This worked for me: I had to install texinfo through apt-get.

I just love brutal solutions

---

