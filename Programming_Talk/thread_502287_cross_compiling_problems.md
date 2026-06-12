---
title: "cross compiling problems"
date: 2007-07-16
forum: Programming Talk
---

### Post by madeupname on 2007-07-16
I am trying to cross compile an embedded version of Konqueror to a blackfin processor. I have already done this using a SuSE configured host machine. Granted I am using a slightly newer version of software for the uClinux and cross compiling toolchain, but I fear this particular issue may be related to my Ubuntu host machine. I am very new to the Ubuntu distribution, this is my first exposure.

Does anyone have any clue as to why I might be seeing this error and/or how the best way for me to figure out the solutuion?

make[5]: Entering directory `/project/video/uclinux/elf_flat/uClinux-dist/konqueror/konq-embed/dropin/kio'
if /bin/bash ../../../libtool --silent --tag=CXX --mode=compile bfin-linux-uclibc-g++ -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../../konq-embed/kdesrc/kdecore -I../../../konq-embed/kdesrc/kjs -I../../../konq-embed/kdesrc/kssl -I./.. -I./../khtml -I../../../konq-embed/kdesrc/kdecore -I../../../konq-embed/kdesrc -I../../../konq-embed/kdesrc/kio/http -I../../../konq-embed/kdesrc/kio -I../../../konq-embed/kdesrc/kio/http -I../../../konq-embed/kdesrc/interfaces -I../../../konq-embed/kdesrc/kssl -I../../../konq-embed/kdesrc/khtml -I../../../konq-embed/kdesrc/kssl -I/usr/include -I/home/vocal/project/QT/include -I../staging/usr/include -DQT_THREAD_SUPPORT -DQWS -D_REENTRANT -Wno-long-long -Wundef -Wall -W -Wpointer-arith -DNDEBUG -DNO_DEBUG -O2 -mfdpic -D__linux__ -DNOMMU -DQT_THREAD_SUPPORT -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -fno-rtti -DQT_CLEAN_NAMESPACE -DQT_NO_COMPAT -DQT_NO_ASCII_CAST -MT slavebase.lo -MD -MP -MF ".deps/slavebase.Tpo" -c -o slavebase.lo slavebase.cpp; \
then mv -f ".deps/slavebase.Tpo" ".deps/slavebase.Plo"; else rm -f ".deps/slavebase.Tpo"; exit 1; fi
In file included from ./../kglobal.h:27,
from ./../klibloader.h:30,
from ../../../konq-embed/kdesrc/kparts/factory.h:23,
from ./../kio/mimehandler.h:5,
from ./../kio/jobclasses.h:34,
from job.h:25,
from slavebase.cpp:27:
./../kapplication.h:46:1: warning: "KDE_VERSION_STRING" redefined
In file included from ./../kconfig.h:34,
from slavebase.h:34,
from slavebase.cpp:26:
../../../konq-embed/kdesrc/kdecore/kdeversion.h:25:1: warning: this is the location of the previous definition
In file included from /usr/include/bits/socket.h:310,
from /usr/include/sys/socket.h:35,
from /usr/include/netinet/in.h:24,
from ../../../konq-embed/kdesrc/kio/http/http.h:27,
from slavebase.cpp:32:
/usr/include/asm/socket.h:9:4: warning: #warning This machine appears to be neither x86_64 nor i386.
In file included from /usr/include/linux/errno.h:4,
from /usr/include/bits/errno.h:25,
from /usr/include/errno.h:36,
from slavebase.cpp:54:
/usr/include/asm/errno.h:9:4: warning: #warning This machine appears to be neither x86_64 nor i386.
slavebase.cpp: In member function 'void KIO::SlaveBase::dispatchLoop()':
slavebase.cpp:265: error: 'pthread_exit' was not declared in this scope
slavebase.cpp:277: error: 'pthread_exit' was not declared in this scope
make[5]: *** [slavebase.lo] Error 1
make[5]: Leaving directory `/project/video/uclinux/elf_flat/uClinux-dist/konqueror/konq-embed/dropin/kio'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/project/video/uclinux/elf_flat/uClinux-dist/konqueror/konq-embed/dropin/kio'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/project/video/uclinux/elf_flat/uClinux-dist/konqueror/konq-embed/dropin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/project/video/uclinux/elf_flat/uClinux-dist/konqueror/konq-embed'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/project/video/uclinux/elf_flat/uClinux-dist/konqueror'
make: *** [all] Error 2
__________________
Reply With Quote

---

### Post by madeupname on 2007-07-17
Actually in retrospect the "error" is probably a porting issue.  I don't think my patch was installed quite right.  However the "warning":

/usr/include/asm/errno.h:9:4: warning: #warning This machine appears to be neither x86_64 nor i386.

I fear is related to my Ubuntu distribution. So if anyone can enlighten me as to why I might be seeing this warning I would appreciate it.

I continue to struggle with various issues using Ubuntu that I haven't seen elsewhere.

Bill

---

### Post by madeupname on 2007-07-17
I understand now what is going on.  I corrected the code for a proper port to uClinux and the pthread_exit error disappeared.  The other problem (within socket.h),persists and  that also will throw a fatal error.  The problem occurs because the cross compiler is picking up the Ubuntu system level /usr/include/asm/socket.h when it should be picking up the uClinux-kernel/include/asm-blackfin/socket.h.  On my other host machine apparently the same thing occured but that was a SuSE box on a 32-bit machine and the system level socket.h was close to the embedded linux version.... close enough to compile.  However my Ubuntu box is 64-bit and there is nothing but a stub at the system level /asm/socket.h hence a catastrophic failure....

Now that I understand it, I still am not overly clear on how to fix it.  However, understanding the problem is half the battle right?

Bill

---

