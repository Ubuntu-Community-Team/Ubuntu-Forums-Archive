---
title: "Compiling stand alone programs"
date: 2010-08-13
forum: Packaging and Compiling Programs
---

### Post by pulseplanet on 2010-08-13
Hello All,

 I have some libraries installed (ROOT, [http://root.cern.ch/drupal/](http://root.cern.ch/drupal/)) and created a static library when compiling and installing it). I am writing to ask how I use that to create a static executable that I can distribute it to other computers with no ROOT installed. 

My makefile looks like this:


```
CPPFLAGS +=  -Wall
CPPFLAGS +=  -DDEBUG=1
CPPFLAGS +=  -DSIMULATION
#CPPFLAGS +=  -DUSEGATEPOSITION
CPPFLAGS += -DHISTOGRAM

CPPFLAGS += -pthread -m64
CPPFLAGS += -I/home/ROOT-STATIC-BUILD/include
CPPFLAGS += -L/home/ROOT-STATIC-BUILD/lib
CPPFLAGS += -lRoot -lCore -lCint -lRIO -lNet -lHist -lGraf -lGraf3d -lGpad -lTree -lRint -lPostscript -lMatrix -lPhysics -lMathCore -lThread -lGui -pthread -lm -ldl -rdynamic
CPPFLAGS += -static

CC = g++

DIR = /home/Testing

$(DIR)/5 : 1.o 2.o 3.o 4.o 5.C
        $(CC) -c -o $@ $(CPPFLAGS)

1.o : 1.C
        $(CC) $(CPPFLAGS) -c -o $@ $<

2.o : 2.C
        $(CC) $(CPPFLAGS) -c -o $@ $<

3.o : 3.C
        $(CC) $(CPPFLAGS) -c -o $@ $<

4.o : 4.C
        $(CC) $(CPPFLAGS) -c -o $@ $<

.PHONY: clean
clean:
        rm -f *.o 



```

My make file runs ok and produces the .o file. When I link it however, it complains that it cannot find -lCore and -lRoot.

```
ld -o output `ls *.o` -lm -lCore -lRoot
```

I do have a libCore.so and libRoot.a in my $LD_LIBRARY_PATH.

Can you please help. 

Thanks.

Karthik.

---

### Post by MadCow108 on 2010-08-14
compile a static version of the root libraries:
./configure --someflags
make
make static

and link your application with libRoot.a libpcre.a ncurses and whatever else your application still needs:
-L$ROOTSYS/lib -lRoot -lpcre -lncurses

If stuff like ncurses, xpm, libz are already installed on your client systems you can also skip the static flag.

---

### Post by linux18 on 2010-08-14
you can also use " checkinstall --install=no " to turn it into a deb package

---

