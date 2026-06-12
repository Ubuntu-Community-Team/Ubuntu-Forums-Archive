---
title: "Banshee -1-0.98.1 Alpha"
date: 2008-03-16
forum: Packaging and Compiling Programs
---

### Post by b3n87 on 2008-03-16
Hi guys and gals

Im trying to build a binary package of the new alpha release if anyones interested

Im having problems making the package tho - im using checkinstall

i get this error:

> make[1]: Entering directory `/home/ben/banshee-1-0.98.1/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[1]: *** [ar.gmo] Error 127
make[1]: Leaving directory `/home/ben/banshee-1-0.98.1/po'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

I tried as a normal user than as root but it still doesnt work, anyone got any ideas where im going wrong?

---

### Post by rigol on 2008-03-17
I'm assuming you have the required packages for compiling already installed. 

While compiling, I ran into a similar problem recently. The same issue was reported here: [http://ubuntuforums.org/archive/index.php/t-578513.html](http://ubuntuforums.org/archive/index.php/t-578513.html) - like erginemr in the linked thread adviced, I solved it by installing **gettext package**. Then do a reconfigure and make/checkinstall.

---

### Post by b3n87 on 2008-03-19
ok thanks, ill give it a try

---

