---
title: "Make error on KBrain"
date: 2005-12-09
forum: Packaging and Compiling Programs
---

### Post by dieselpower on 2005-12-09
I am trying to compile KBrain on my Kubuntu Breezey box and ran into a problem I cant get past. I downloaded the KBrain source from a Gentoo site because the file on the maintainers site will not download. I finally got ./configure to go, had some problems with qt, and now it stops with this. Anyone got any clue why?

```

g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -O2 -fno-exceptions -fno-check-new  -c kbrainedit.cpp
In file included from /usr/include/c++/4.0.2/backward/stream.h:31,
                 from kbrainedit.cpp:18:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -O2 -fno-exceptions -fno-check-new  -c kbraindrag.cpp
kbraindrag.cpp:20: error: default argument given for parameter 2 of &#8216;KBrainDrag::KBrainDrag(const char*, QWidget*, const char*)&#8217;
kbraindrag.h:39: error: after previous specification in &#8216;KBrainDrag::KBrainDrag(const char*, QWidget*, const char*)&#8217;
kbraindrag.cpp:20: error: default argument given for parameter 3 of &#8216;KBrainDrag::KBrainDrag(const char*, QWidget*, const char*)&#8217;
kbraindrag.h:39: error: after previous specification in &#8216;KBrainDrag::KBrainDrag(const char*, QWidget*, const char*)&#8217;
make[2]: *** [kbraindrag.o] Error 1
make[2]: Leaving directory `/home/lawrence/kbrain-0.1.3/kbrain'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lawrence/kbrain-0.1.3'
make: *** [all-recursive-am] Error 2


```

Maybe I'll just have to switch over to gentoo ;) :D :D

---

### Post by gord on 2005-12-10
it could be because the gentoo maintainers changed some sources or it could be because it was designed to run with an earlyer version of GCC than you are using (or older)

try typing this before ./configure 
```

export CC=gcc-3.4

```

of course it depends on what versions of gcc you have installed, if you don't have gcc-3.4 that won't work at all.

---

