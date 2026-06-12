---
title: "Error while installing libgraph-1.0.2"
date: 2013-10-12
forum: Programming Talk
---

### Post by Rahul04789 on 2013-10-12
Hi friends,

I am trying to install libgraph-1.0.2
After running **./configure** command and then running **make** command, I got following error:

Makefile:934: warning: overriding commands for target `libgraph.pc'
Makefile:409: warning: ignoring old commands for target `libgraph.pc'
if /bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -I.   -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DFONTDIR=\""/usr/local/share/libgraph/Font/"\" -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT guile-libgraph.lo -MD -MP -MF ".deps/guile-libgraph.Tpo" -c -o guile-libgraph.lo guile-libgraph.c; \
    then mv -f ".deps/guile-libgraph.Tpo" ".deps/guile-libgraph.Plo"; else rm -f ".deps/guile-libgraph.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -I. -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DFONTDIR=\"/usr/local/share/libgraph/Font/\" -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT guile-libgraph.lo -MD -MP -MF .deps/guile-libgraph.Tpo -c guile-libgraph.c  -fPIC -DPIC -o .libs/guile-libgraph.o
guile-libgraph.c:25:22: fatal error: libguile.h: No such file or directory
compilation terminated.
make[2]: *** [guile-libgraph.lo] Error 1
make[2]: Leaving directory `/home/rahul/Downloads/libgraph-1.0.2'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rahul/Downloads/libgraph-1.0.2'
make: *** [all] Error 2


Thereafter , I installed guile from Synaptic Package Manager, but still the same error is shown.
What should I do???



Regards

---

### Post by Bachstelze on 2013-10-12
You need to install *guile-dev*. (In general, header files (.h) are provided by *-dev* packages.)

---

### Post by Rahul04789 on 2013-10-13
@Bachstelze:

I have already installed guile-2.0-dev  
Now, tell me what should I do....

---

### Post by Rahul04789 on 2013-11-06
Hi Bachstelze,

I did the same but no effect took place.
So what should I do?

Regards

---

### Post by Bachstelze on 2013-11-06
Which version of Ubuntu are you running?

---

### Post by spjackson on 2013-11-06
After installing guile-dev, did you rerun configure?

---

### Post by Rahul04789 on 2013-11-13
Hi,
I am using ubuntu 12.04 LTE

---

### Post by Rahul04789 on 2013-11-13
@spjackson:

Yes I reran the configure

---

### Post by spjackson on 2013-11-15
If you have installed the prerequisites properly, I am afraid I've no idea what your problem is.

I did a fresh install of 12.04
```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:   precise

```

Installed the prerequisites thus
```

$ sudo apt-get install build-essential
$ sudo apt-get install guile-1.8-dev
$ sudo apt-get install libsdl1.2-dev
$ sudo apt-get install libsdl-image1.2-dev

```

Checked I'd got libguile.h
```

$ find /usr/include -name "*guile*"
/usr/include/libguile.h
/usr/include/libguile
/usr/include/guile

```
Yes, I have, so get the source and build it...
```

$ wget http://download.savannah.gnu.org/releases/libgraph/libgraph-1.0.2.tar.gz
$ tar xf libgraph-1.0.2.tar.gz
$ cd libgraph-1.0.2/
$ ./configure
$ make

```
and it builds without error. What are you doing differently?

---

### Post by Rahul04789 on 2013-11-16
@spjackson:

Thanks  for the help. Now it has been installed
Actually I had installed guile-2.0.
So, I followed your steps again, and now it's done.
Thank you.

But, now while compiling a .cpp file for graphics I encountered the following error:

rahul@rahul-VPCEG28FN:~/CProgram/Graphics$ g++ aa.cpp -lgraph

/usr/bin/ld: error: cannot find -lgraph
/tmp/ccntOaHb.o:aa.cpp:function main: error: undefined reference to 'initgraph'
/tmp/ccntOaHb.o:aa.cpp:function main: error: undefined reference to 'line'
/tmp/ccntOaHb.o:aa.cpp:function main: error: undefined reference to 'closegraph'
collect2: ld returned 1 exit status


Please tell me where doing wrong.....
Thanks

---

### Post by spjackson on 2013-11-18
If your library is not in one of the default places searched by the g++ link command, then you need to tell it where it is.

./configure by default normally results in "make install" putting libraries in /usr/local/lib. I haven't checked whether this is the case here, but assuming that it is, then you need
```

$ g++ aa.cpp -lgraph -L/usr/local/lib

```
Then when you come to run your executable, you will need to set  LD_LIBRARY_PATH (see "man ld.so") or add you library via ldconfig (see "man ldconfig").

---

