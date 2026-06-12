---
title: "Error when trying to unzip on Font Custom install."
date: 2014-07-16
forum: New to Ubuntu
---

### Post by webmeist on 2014-07-16
Hey all.
I'm on a new Ubuntu install,
I think I have all the required packages installed, for Font Custom,
but when I try to run the command to unzip the file from the installation section of this page:
fontcustom.com
I get the following error:

Philly@Claras:~$ unzip woff-code-latest.zip -d sfnt2woff && cd sfnt2woff && make && sudo mv sfnt2woff /usr/local/bin/
Archive:  woff-code-latest.zip
replace sfnt2woff/Makefile? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: sfnt2woff/Makefile      
replace sfnt2woff/sfnt2woff.c? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: sfnt2woff/sfnt2woff.c   
replace sfnt2woff/woff.c? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: sfnt2woff/woff.c        
replace sfnt2woff/woff2sfnt.c? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: sfnt2woff/woff2sfnt.c   
replace sfnt2woff/woff-private.h? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: sfnt2woff/woff-private.h  
replace sfnt2woff/woff.h? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: sfnt2woff/woff.h        
replace sfnt2woff/woff-2009-10-03.html? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: sfnt2woff/woff-2009-10-03.html  
cc    -c -o woff.o woff.c
woff.c:43:18: fatal error: zlib.h: No such file or directory
 #include <zlib.h>
                  ^
compilation terminated.
make: *** [woff.o] Error 1
Philly@Claras:~/sfnt2woff$ 

Can anyone tell me why?
Thanks so much.

---

### Post by Impavidus on 2014-07-16
Have you installed the package **zlib1g-dev**? That provides zlib.h on 14.04. It's in the repositories.

Besides, the error is not caused by the unzip command but by the make command you gave on the same line. The unzip command (and the cd command) worked and doesn't have to be redone. It seems you already unpacked the archive multiple times.

---

### Post by webmeist on 2014-07-16
Thank you!
:)

---

