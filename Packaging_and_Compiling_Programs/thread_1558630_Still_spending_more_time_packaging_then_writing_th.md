---
title: "Still spending more time packaging then writing the app"
date: 2010-08-22
forum: Packaging and Compiling Programs
---

### Post by danwsc on 2010-08-22
I am trying to package a piece of software I wrote.  Having completed the source packaging, I am now trying to finish off
$ sudo pbuilder build ../*.dsc
I was previously stuck in this because of some build-dependency issues which with some well-needed advice, I have now cleared.  The program now seems to be downloading stuff from the net.  But when it tries to build gnulib/lib, it doesn't seem to recognize a @ in stdio.h.

I would appreciate some help here please.
I admit that I did a lot of cut and paste to get the compilation running, but the program compiles (and runs) okay on my system, which is a Karmic Ubuntu.  The problem only happens in pbuilder.

Regards.

/usr/bin/make  all-recursive
make[4]: Entering directory `/tmp/buildd/vrdo-1.1/gnulib/lib'
make[5]: Entering directory `/tmp/buildd/vrdo-1.1/gnulib/lib'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -Wall         -pedantic -ansi -std=c99     -g -O2 -MT localcharset.o -MD -MP -MF .deps/localcharset.Tpo -c -o localcharset.o localcharset.c
In file included from localcharset.c:27:
./stdio.h:21: error: stray '@' in program
./stdio.h:21: error: stray '@' in program
In file included from ./stdio.h:40,
                 from localcharset.c:27:
/usr/lib/gcc/i486-linux-gnu/4.4.1/include/stdarg.h:40: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'typedef'
In file included from ./stdio.h:40,
                 from localcharset.c:27:
/usr/lib/gcc/i486-linux-gnu/4.4.1/include/stdarg.h:102: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'va_list'
In file included from localcharset.c:27:
./stdio.h:43:7: error: operator '&&' has no left operand
./stdio.h:101:5: error: #if with no expression
.
.
.
./stdio.h:509:5: error: #if with no expression
./stdio.h:531:5: error: #if with no expression
In file included from localcharset.c:28:
./string.h:23: error: stray '@' in program
./string.h:23: error: stray '@' in program
In file included from localcharset.c:28:
./string.h:82:5: error: #if with no expression
./string.h:102:5: error: #if with no expression
.
.
.
./string.h:601:5: error: #if with no expression
./string.h:616:5: error: #if with no expression
In file included from localcharset.c:29:
./stdlib.h:20: error: stray '@' in program
./stdlib.h:20: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'PRAGMA_SYSTEM_HEADER'
./stdlib.h:20: error: stray '@' in program
In file included from localcharset.c:29:
./stdlib.h:41:6: error: operator '&&' has no left operand
./stdlib.h:47:5: error: #if with no expression
.
.
.
./stdlib.h:364:5: error: #if with no expression
./stdlib.h:385:5: error: #if with no expression
localcharset.c: In function 'get_charset_aliases':
localcharset.c:116: error: 'charset_aliases' undeclared (first use in this function)
.
.
.
localcharset.c:484: warning: incompatible implicit declaration of built-in function 'strlen'
localcharset.c:485: warning: implicit declaration of function 'strcmp'
make[5]: *** [localcharset.o] Error 1
make[5]: Leaving directory `/tmp/buildd/vrdo-1.1/gnulib/lib'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/tmp/buildd/vrdo-1.1/gnulib/lib'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/tmp/buildd/vrdo-1.1/gnulib/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/buildd/vrdo-1.1'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/buildd/vrdo-1.1'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
E: Failed autobuilding of package
W: no hooks of type C found -- ignoring
I: unmounting /home/bloomingdalebear/pbuilder/result filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//19157 and its subdirectories

---

### Post by MadCow108 on 2010-08-23
In file included from localcharset.c:27:
./stdio.h:21: error: stray '@' in program
./stdio.h:21: error: stray '@' in program

this indicates that you have some string in one of **your** files which messes up everything (probably something with an @ ;) )
all other errors are a consequence of this
maybe some copy paste error e.g.
myaddress@sdasd/*code starts here ...*/
#include <stdio.h>
...

---

### Post by SevenMachines on 2010-08-23
I think, but i dont use it so i cant be sure, that its an issue with the way you're using gnulib (gnulib is *different* :) ). it shouldnt included in the package source, and it shouldnt be included in configure and makefile in the way it is (see gnulib-tool). Looks like you're only using getttext which doesn't require full gnulib dependencies anyway so it can probably be simplified. Haven't had time to have a proper look at it but i'll try to towards the middle of the week

---

### Post by danwsc on 2010-08-24
You are right.  The gnulib went on there because the gettext is therer and I was trying to follow an example.  Thanks again for looking into the packaging.

Regards.

---

### Post by danwsc on 2010-08-24
Hi Madcow, thanks I will look into it but I don't even use stdio.h so I doubt I could have done anything to affect it.  Still, I have done stranger things .....

The style of the error messages suggest that I have left out an include somewhere....

Regards.

---

### Post by SevenMachines on 2010-08-24
This works for me,

$ gnulib-tool --import gettext

$ autoreconf          # Might be needed depending on the release you use 

$ debuild -b -us -uc

---

### Post by danwsc on 2010-08-25
Hi,

Did you try it with pbuilder please?

I tried but still seemed to get the same error messages ...
.
.
.
In file included from localcharset.c:27:
./stdio.h:21: error: stray '@' in program
./stdio.h:21: error: stray '@' in program
In file included from ./stdio.h:40,
                 from localcharset.c:27:
/usr/lib/gcc/i486-linux-gnu/4.4.1/include/stdarg.h:40: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'typedef'
In file included from ./stdio.h:40,
                 from localcharset.c:27:
.
.
.

The debuild -b -us -uc worked on my system too.
But I had already achieved this before trying the pbuilder.

Regards.

---

### Post by SevenMachines on 2010-08-25
I can get past that error in pbuilder if the source tarball is recreated. What I actually did was, before adding the packaging in

// just recreate the gnulib stuff altogether
$ rm -rf gnulib
$ gnulib-tool --source-base=gnulib/lib/ --m4-base=gnulib/m4/ --import gettext closeout
$ autoreconf

// recreate the source tarball. since i recreated the gnulib stuff, files will 
// be deleted from the original tarball, these are ignored by debuild so the source package needs to be refreshed
$ tar -zcf ../vrdo_1.1.orig.tar.gz  ../vrdo-1.1.orig

// add in the packaging and actually do the build
$ patch -p1 <../vrdo_1.1-0ubuntu1.diff
$ debuild -S -us -uc -sa
$ pbuilder-dist maverick build ../vrdo_1.1-0ubuntu1.dsc

Unfortunately although i get past the errors you mention, i get stuck in a strangle build loop when making the po files. I really dont understand gnulib :)

---

### Post by danwsc on 2010-08-26
Thanks to SevenMachines!

---

