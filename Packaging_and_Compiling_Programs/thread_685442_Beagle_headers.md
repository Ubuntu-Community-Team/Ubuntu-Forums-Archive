---
title: "Beagle headers"
date: 2008-02-02
forum: Packaging and Compiling Programs
---

### Post by gmclachl on 2008-02-02
I am having problems compiling some c. It complains about

#include <beagle/beagle.h>

saying 

 beagle/beagle.h: No such file or directory

I have the beagle-dev package installed and the header files seem to be in the right place. 

George

---

### Post by dbera on 2008-02-02
> **gmclachl said:**
> I am having problems compiling some c. It complains about

#include <beagle/beagle.h>

saying 

 beagle/beagle.h: No such file or directory

I have the beagle-dev package installed and the header files seem to be in the right place. 

George

How are you building it ? What CFLAGS are you using ? I think you should use "-I `pkg-config --cflags libbeagle1.0`" (similarly for libs).

---

### Post by gmclachl on 2008-02-03
Hmmm,
            I still can't seem to get it to work I tried

gcc  -o libbeaglelib.so -shared -Wl,-soname,libbeagle.so  -I/usr/lib/jvm/java-6-sun/include -I/usr/lib/jvm/java-6-sun/include/linux beagle-indexer.c -static -lc -I `pkg-config --cflags libbeagle-0.0`

I also have the following entry in pkgconfig

/usr/lib/pkgconfig/libbeagle-0.0.pc

Thanks
George

---

### Post by dbera on 2008-02-03
What is the output of pkg-config --cflags libbeagle-0.0 ?
What is the location of beagle.h ?
What is the exact error message you are getting from gcc ?

---

### Post by gmclachl on 2008-02-03
pkg-config --cflags libbeagle-0.0 returns 

gmclachl@scotty:~$ pkg-config --cflags libbeagle-0.0
-I/usr/include/libbeagle -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  

gmclachl@scotty:~$ locate beagle.h
/usr/include/libbeagle/beagle/beagle.h


gmclachl@scotty:$ gcc  -o libbeaglelib.so -shared -Wl,-soname,libbeagle.so  -I/usr/lib/jvm/java-6-sun/include -I/usr/lib/jvm/java-6-sun/include/linux beagle-external-indexer.c -static -lc -I `pkg-config --cflags libbeagle-0.0`

beagle-external-indexer.c:1:27: error: beagle/beagle.h: No such file or directory

---

### Post by dbera on 2008-02-03
Ah... my typo. Try:
$ gcc -o libbeaglelib.so -shared -Wl,-soname,libbeagle.so -I/usr/lib/jvm/java-6-sun/include -I/usr/lib/jvm/java-6-sun/include/linux beagle-external-indexer.c -static -lc `pkg-config --cflags libbeagle-0.0`

or

$ gcc -o libbeaglelib.so -shared -Wl,-soname,libbeagle.so -I/usr/lib/jvm/java-6-sun/include -I/usr/lib/jvm/java-6-sun/include/linux beagle-external-indexer.c -static -lc -I/usr/include/libbeagle -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include

---

### Post by gmclachl on 2008-02-04
Awesome,
                   Thanks for that the first option worked a treat

---

