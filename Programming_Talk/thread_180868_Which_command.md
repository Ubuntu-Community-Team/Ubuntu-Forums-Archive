---
title: "Which command?"
date: 2006-05-23
forum: Programming Talk
---

### Post by meniscus on 2006-05-23
Hi everybody. Im installing rrdtool at this link [http://oss.oetiker.ch/rrdtool/doc/rrdbuild.en.html](http://oss.oetiker.ch/rrdtool/doc/rrdbuild.en.html)
and im down at the end where it says


This time you tell configure where it should be looking for libraries and include files. This is done via environment variables. Depending on the shell you are running, the syntax for setting environment variables is different. 

[COLOR="Red"]Under csh/tcsh you use:

set IR=-I$BUILD_DIR/lb/include
setenv CPPFLAGS "$IR $IR/libart-2.0 $IR/freetype2 $IR/libpng"
setenv LDFLAGS  -L$BUILD_DIR/lb/lib
setenv CFLAGS -O3[/COLOR]

OR

[COLOR="Lime"]If you are running bash/sh/ash/ksh/zsh use this:

IR=-I$BUILD_DIR/lb/include
CPPFLAGS="$IR $IR/libart-2.0 $IR/freetype2 $IR/libpng"
LDFLAGS="-L$BUILD_DIR/lb/lib"
CFLAGS=-O3
export CPPFLAGS LDFLAGS CFLAGS
[/COLOR]


Im running Ubuntu on a dual boot system with windows. Which set of commands do i use?

Thanks in advance
meniscus

---

### Post by gborzi on 2006-05-23
The default shell in ubuntu is bash, so you should use the second set. Just to be sure on what shell you are using type
> echo $SHELL
the output will probably be
> /bin/bash

Regards.

---

