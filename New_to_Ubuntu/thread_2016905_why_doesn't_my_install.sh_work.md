---
title: "why doesn't my install.sh work ?"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by hmazuji on 2012-07-04
i need to make this install thing work, now apparently i need autoconf and automake.  is there an enthusiast willing to walk me through this ?
[B]
Re: Ubuntu friendly printer.. Canon PIXMA MX320?[/B] 			
 			 			 		   		 		 		install.sh doesn't work:

root@debian:/home/lou/Downloads/cnijfilter-source-3.10# cd cnijfilter
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# ls
acconfig.h  autogen.sh    configure.in  include  LICENSE        NEWS    src
AUTHORS     ChangeLog    COPYING       INSTALL  Makefile.am  README
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# INSTALL
bash: INSTALL: command not found
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# ./INSTALL
./INSTALL: line 1: To: command not found
./INSTALL: line 3: syntax error near unexpected token `newline'
./INSTALL: line 3: `        ./autogen.sh --program-suffix=<Printer Model Name>'
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# ./autogen.sh

**Error**: You must have `autoconf' installed to.
Download the appropriate package for your distribution,
or get the source tarball at [ftp://ftp.gnu.org/pub/gnu/](ftp://ftp.gnu.org/pub/gnu/)

**Error**: You must have `automake' installed.
Get [ftp://ftp.gnu.org/pub/gnu/automake-1.3.tar.gz](ftp://ftp.gnu.org/pub/gnu/automake-1.3.tar.gz)
(or a newer version if it is available)
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# cd ..
root@debian:/home/lou/Downloads/cnijfilter-source-3.10# install.sh
bash: install.sh: command not found
root@debian:/home/lou/Downloads/cnijfilter-source-3.10#

i need to make this install thing work, now apparently i need autoconf and automake.  is there an enthusiast willing to walk me through this ?

---

### Post by MG&amp;TL on 2012-07-04
Okay, install automake:

```
sudo apt-get install automake
```

then try:

```
./autogen.sh
```

again and we'll go from there. :)

---

