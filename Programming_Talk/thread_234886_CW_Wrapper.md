---
title: "CW Wrapper"
date: 2006-08-12
forum: Programming Talk
---

### Post by wuhaa on 2006-08-12
Hi,

I'm trying to install the color wrapper on Ubuntu 6.06. I have gcc installed, but keep getting this error:

* Compiling cw(color wrapper)...
src/cw.c: In function ‘execot’:
src/cw.c:1445: warning: missing sentinel in function call
src/cw.c: In function ‘execcw’:
src/cw.c:1541: warning: missing sentinel in function call
* Compiling cwu(color wrapper directive updater)...
* Installing color wrapper...
/bin/sh: -c: line 1: syntax error near unexpected token `do/usr/bin/install'
/bin/sh: -c: line 1: `/usr/bin/install -c -o 0 -g 0 -m 755 $FILE /usr/local/bin;\'
make: *** [install] Error 2


Is there a specific lib missing? If so, which one?

Thanks..

---

