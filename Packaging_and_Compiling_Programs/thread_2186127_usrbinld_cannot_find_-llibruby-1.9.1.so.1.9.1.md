---
title: "/usr/bin/ld: cannot find -llibruby-1.9.1.so.1.9.1"
date: 2013-11-05
forum: Packaging and Compiling Programs
---

### Post by morganfraughton on 2013-11-05
I am trying to compile and install GEOS-3.4.2 for in Saucy Salamander (configured with PHP, PYTHON, and RUBY.) The problem arises when I try the "make" command and I get this message:


/usr/bin/ld: cannot find -llibruby-1.9.1.so.1.9.1
collect2: error: ld returned 1 exit status
make[5]: *** [geos.la] Error 1
make[5]: Leaving directory `/home/morgan/Downloads/geos-3.4.2/swig/ruby'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/morgan/Downloads/geos-3.4.2/swig/ruby'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/morgan/Downloads/geos-3.4.2/swig/ruby'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/morgan/Downloads/geos-3.4.2/swig'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/morgan/Downloads/geos-3.4.2'
make: *** [all] Error 2




Its says it "/usr/bin/ld: cannot find -llibruby-1.9.1.so.1.9.1" but  libruby-1.9.1.so.1.9.1 exists as /usr/lib libruby-1.9.1.so.1.9.1. Just like every other library does. 


Why cant /usr/bin/ld find libruby-1.9.1.so.1.9.1???

---

### Post by oldos2er on 2013-11-06
Moved to Packaging & Compiling Programs.

---

