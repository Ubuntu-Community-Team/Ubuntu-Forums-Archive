---
title: "Makefile doubt"
date: 2013-04-19
forum: Programming Talk
---

### Post by Dirich on 2013-04-19
I know very little about makefiles, so it may very well be (and probably is), some sort of very basic thing I'm doing wrong. I have a single source file that needs 3 libaries to be compiled (gmp, mpfr (built over gmp), stdc++). No header file.

```

CC      := g++
CFLAGS  := -g -Wall
LIBS    := -lgmp -lmpfr -lstdc++

CSRC:=\
AnalyticHEXARM.cpp

#HSRC:=\



OBJS=$(CSRC:.c=.o)

all:    AnalyticHEXARM

run:    all
    ./AnalyticHEXARM

TransportAnalysis:    $(OBJS)
    $(CC) $(CFLAGS) -o $@ $(OBJS) $(LIBS)




# Cleanup
clean:
    -rm -f AnalyticHEXARM

test:
    @echo "CSRC=$(CSRC)"
#    @echo "HSRC=$(HSRC)"
    @echo "OBJS=$(OBJS)"
```

The compiler gets angry because it says that the wrapper header calls undefined functions (in the mpfr library). The wrapper header is one of the "library headers" that I do not need to specify in the makefile (I have other programs in which I do that and have no problem, also, it would be madness since I use Eigen which is an entire library only made of headers).

---

### Post by dwhitney67 on 2013-04-19
Let's start by cleaning up the Makefile:
```

APP = AnalyticHEXARM

SRCS = AnalyticHEXARM.cpp
OBJS = $(SRCS:.cpp=.o)

INCLUDES =

CXXFLAGS  = -g -Wall $(INCLUDES)
LDFLAGS =
LIBS = -lgmp -lmpfr

.PHONY : all run clean

all : $(APP)

# This won't work if your libraries are not in a known area.
# You would need to augment the definition of LD_LIBRARY_PATH to specify
# the locations of all libraries that cannot be referenced.
run:    all
    ./$(APP)

$(APP) : $(OBJS)
    $(CXX) -o $@ $^ $(LDFLAGS) $(LIBS)

clean:
    $(RM) $(OBJS) $(APP)

```
Now, if you are still having trouble referencing header files, then you need to specify the location of such using the -I (uppercase eye) option.  For example:  -I/usr/local/include/foodir.  I suggest that you insert these -I statements, if required, in the INCLUDES definition above.

If the library file(s) you are trying to reference are not in standard locations, then you need to specify where to find these using the -L linker option.  For example:  -L/home/me/libdir.  I suggest that you insert these -L statements, if required, in the LDFLAGS definition above.

P.S.  You can deduce whether the system is aware of your external libraries by running the command '/sbin/ldconfig -v'.  If your library appears in the list, then you do not need to employ the use of the -L option.  Otherwise you do.

---

