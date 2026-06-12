---
title: "/usr/bin/ld: cannot find -lgb"
date: 2007-03-08
forum: Programming Talk
---

### Post by Alexkid on 2007-03-08
Hi, I need to install NS2 on ubuntu edgy. I'm following instructions from [http://ns-2.blogspot.com/2006/08/howto-install-ns-2-allinone-onto.html](http://ns-2.blogspot.com/2006/08/howto-install-ns-2-allinone-onto.html) 
I am at the following point in the instructions-

....
gt-itm requires a bin dir to be created.

$ cd ../gt-itm
$ mkdir bin
$ cd src
$ make
...

When I type 'make' I get an error /usr/bin/ld: can not find -lgb

/...
Alexkid@pc123:~/ns2/ns-allinone-2.30/gt-itm/src$ make
gcc  -I../include -L../lib  -DFBSD -o ../bin/itm itm.o geog.o ts.o dfs.o -lm -lgb
/usr/bin/ld: cannot find -lgb
collect2: ld returned 1 exit status
make: *** [itm] Error 1
Alexkid@pc123:~/ns2/ns-allinone-2.30/gt-itm/src$ 
.../

Could anyone help?

Extra info - Stepping through instructions I installed packages of missing files. There is a LGB (upper case) in package 'groff' which I installed but no lgb (lower case). There is no LGB or lgb in folder /usr/bin/ld

Hope someone can help.
Thanx.
Alexkid

---

### Post by lnostdal on 2007-03-08
sudo aptitude install sgb

---

### Post by Alexkid on 2007-03-08
Thanx lnostal. seemed to have worked :) 

I have got to the end of the steps in [http://ns-2.blogspot.com/2006/08/howto-install-ns-2-allinone-onto.html](http://ns-2.blogspot.com/2006/08/howto-install-ns-2-allinone-onto.html) 

What do I do once I finish all the steps? 

If someone has installed NS2 before, could you look at the link and see what must be done after all the steps in [http://ns-2.blogspot.com/2006/08/howto-install-ns-2-allinone-onto.html](http://ns-2.blogspot.com/2006/08/howto-install-ns-2-allinone-onto.html) are completed?

Alexkid

---

