---
title: "installing NACHOS"
date: 2010-02-13
forum: Packaging and Compiling Programs
---

### Post by bloodofangels302 on 2010-02-13
Hello,
I'm looking for some help on installing NachOS (Not Another Completely Heuristic Operating System) in Ubuntu.  I am doing it for one of my classes but the instructions I received from my professor won't quite work for me.  The instructions are as follows: 

> b. Download the compressed code of NACHOS from the Blackboard
c. Decompress, modify the Makefile, and run it.
                Execute: gtar -xvf nachos.tar.gz
                Execute: cd nachos40uwv11/code/build.linux
                Execute: make depend
                Execute: make
                To run nachos execute: ./nachos

I have extracted the tar file, but when I ran make depend in the nachos40uwv11/code/build.linux directory I get the following output:

> 
[email]michael@dell-desktop:~/NACHOS/nachos40uwv11/code/build.linux[/email]$ make depend
g++ -g -Wall -Wno-deprecated -fwritable-strings -I../network -I../filesys -I../userprog -I../threads -I../machine -I../lib -DRDATA -DSIM_FIX -DFILESYS_STUB -DRR_QUANTUM -Dx86 -DLINUX -DCHANGED -M ../lib/bitmap.cc ../lib/debug.cc ../lib/hash.cc ../lib/libtest.cc ../lib/list.cc ../lib/sysdep.cc ../machine/interrupt.cc ../machine/stats.cc ../machine/timer.cc ../machine/console.cc ../machine/machine.cc ../machine/mipssim.cc ../machine/translate.cc ../machine/network.cc ../machine/disk.cc ../threads/alarm.cc ../threads/kernel.cc ../threads/main.cc ../threads/scheduler.cc ../threads/synch.cc ../threads/thread.cc ../userprog/addrspace.cc ../userprog/exception.cc ../userprog/synchconsole.cc ../userprog/proctable.cc ../userprog/synchbitmap.cc ../userprog/table.cc ../filesys/directory.cc ../filesys/filehdr.cc ../filesys/filesys.cc ../filesys/pbitmap.cc ../filesys/openfile.cc ../filesys/synchdisk.cc  ../network/post.cc > makedep
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
cc1plus: error: unrecognized command line option "-fwritable-strings"
make: *** [depend] Error 1



Please let me know if you have any suggestions, Thanks.

---

### Post by Yellow Pasque on 2010-02-13
[http://hub.opensolaris.org/bin/view/Community+Group+tools/bug_fixing_notes](http://hub.opensolaris.org/bin/view/Community+Group+tools/bug_fixing_notes)

Ask your professor why he told you to use a program that needs gcc 3.x to compile. You could try to remove the -fwritable-strings flag, but it may cause the program to crash if you do get it compiled.

EDIT: Seems there are Java versions of NachOS if they will work for your assignment.

---

### Post by bloodofangels302 on 2010-02-14
Thanks for the reply!

agh... my instructor said specifically we need to use the version he provided. Any ideas for a workaround?  I understand it is unwise to install an old version of gcc on a modern system.  Suggestions from anyone would be helpful, Thanks

---

### Post by Yellow Pasque on 2010-02-14
You could always try virtualbox. Maybe install a minimal installation of Hardy or some other older Linux distro that has gcc3 easily installable.

---

### Post by katestevedip on 2010-10-22
I have some similiar issues with NachOS. Its 4.0. When I am trying to resolve the dependencies by writing make depend, it shows the following error. Can you please guide me ?

[slave5c2@slave5c2 build.linux]$ make depend
g++ -I../network -I../filesys -I../userprog -I../threads -I../machine -I../lib -I- -DFILESYS_STUB -DRDATA -DSIM_FIX -Dx86 -DLINUX -DCHANGED -M ../lib/bitmap.cc ../lib/debug.cc ../lib/hash.cc ../lib/libtest.cc ../lib/list.cc ../lib/sysdep.cc ../machine/interrupt.cc ../machine/stats.cc ../machine/timer.cc ../machine/console.cc ../machine/machine.cc ../machine/mipssim.cc ../machine/translate.cc ../machine/network.cc ../machine/disk.cc ../threads/alarm.cc ../threads/kernel.cc ../threads/main.cc ../threads/scheduler.cc ../threads/synch.cc ../threads/synchlist.cc ../threads/thread.cc ../userprog/addrspace.cc ../userprog/exception.cc ../userprog/synchconsole.cc ../filesys/directory.cc ../filesys/filehdr.cc ../filesys/filesys.cc ../filesys/pbitmap.cc ../filesys/openfile.cc ../filesys/synchdisk.cc  ../network/post.cc > makedep
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
In file included from /usr/include/linux/posix_types.h:47,
                 from /usr/include/linux/types.h:8,
                 from /usr/include/asm/sigcontext.h:5,
                 from /usr/include/bits/sigcontext.h:28,
                 from /usr/include/signal.h:339,
                 from ../lib/sysdep.cc:51:
/usr/include/asm/posix_types.h:2:30: error: posix_types_32.h: No such file or directory
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
cc1plus: note: obsolete option -I- used, please use -iquote instead
make: *** [depend] Error 1

---

### Post by SevenMachines on 2010-10-22
Make sure you have build-essential installed. 
>  /usr/include/asm/posix_types.h:2:30: error: posix_types_32.h: No such file or directoryperhaps needs,
$ sudo apt-get install linux-libc-dev

---

