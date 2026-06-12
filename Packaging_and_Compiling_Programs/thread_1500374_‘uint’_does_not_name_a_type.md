---
title: "‘uint’ does not name a type"
date: 2010-06-03
forum: Packaging and Compiling Programs
---

### Post by masoodstar on 2010-06-03
This is the error I encountered during make command of a package called 'LBflow' which is attached to this post.

[SIZE=2][B]group@group-desktop:~/lbflow-1.1$ make
make  all-recursive
make[1]: Entering directory `/home/group/lbflow-1.1'
Making all in src
make[2]: Entering directory `/home/group/lbflow-1.1/src'
source='lbflow.cpp' object='lbflow-lbflow.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/bash ../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I. -I..         -c -o lbflow-lbflow.o `test -f 'lbflow.cpp' || echo './'`lbflow.cpp
In file included from lbflow.cpp:27:
parser.h:67: error: ‘uint’ does not name a type
make[2]: *** [lbflow-lbflow.o] Error 1
make[2]: Leaving directory `/home/group/lbflow-1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/group/lbflow-1.1'
make: *** [all] Error 2

[/B]I don't know why I could shoot my trouble by changing distribution to CentOS which is very hard for me.

By the way I want to use it in Ubuntu. Does anyone have any idea?

Thanks friends[/SIZE]

---

### Post by SevenMachines on 2010-06-03
its less a ubuntu thing and more due to how newer version of standard libraries have been cleaned up, you need to actually add the headers you need instead of including them implicitly. I think (from memory, eeek!) you need to add <sys/types.h>

---

### Post by SevenMachines on 2010-06-03
actually downloading it (and deleting it for the reasons to follow!) it seems that this isnt a distributable licence

* This file may not be copied or shared without permission              
 *   Contact [EMAIL="ed@lbflow.co.uk"]ed@lbflow.co.uk[/EMAIL] or visit [www.lbflow.co.uk]("http://www.lbflow.co.uk") 

i think you might need to delete the link to the file
If you have the authors permission and you have any compiling questions related to it i think thats ok though. Distributing the file looks like a no-no though

---

### Post by masoodstar on 2010-06-03
Please explain more.

I know that this package has been compiled in several clients with CentOS in my office.

So it doesn't matter with author permission (I think)

....

---

### Post by SevenMachines on 2010-06-03
gcc has cleaned up header dependencies, so whereas before with some headers you might have had 
#include <A>
in your own header which also ended up including <B> since system header <A> included <B>. Some of these header dependencies have been removed when not necessary (ie, when system header <A> didnt actually require <B> ) so you would need to change your own includes to explicitly use <B> if you make use of it, ie
#include <A>
#include <B>

Theres an explanation in this ['porting to' guide for gcc 4.3]("http://gcc.gnu.org/gcc-4.3/porting_to.html") in the section 'Header dependency cleanup'. theres also a quick table with some of the more common errors caused by the respective missing  headers.

So no matter what distribution, if it uses gcc >=4.3 then the source code needs to be fixed up

---

