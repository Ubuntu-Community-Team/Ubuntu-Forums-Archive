---
title: "Cross Compiling help"
date: 2008-05-28
forum: Programming Talk
---

### Post by LostinLinux on 2008-05-28
Hi, 

I have my app which I am compiling using g++ in kdevelop IDE.

My system is 64bit Hardy - However, I need to compile 32bit version of the app aswell...

Is this possible? I am yet to find a setting in kdevelop for this...perhaps the makefile?

All suggestions appreciated.

Thanks

---

### Post by skullmunky on 2008-05-29
Yes, it's possible, but probably not from a setting in KDevelop... there are an assortment of linker and compiler flags that should do this, but for me anyway it's always kind of a headache.  It was easier just to throw a 32bit install on another partition and compile with that :)

---

### Post by LostinLinux on 2008-05-29
Thanks for the reply :) I guess I will partition  a 32bit copy as a last resort. 

After a little research it seems I have to use the 'CC' flag in the makefile...

Any examples of this?

---

### Post by dwhitney67 on 2008-05-29
Have you looked into using the -m32 gcc option?

---

### Post by dwhitney67 on 2008-05-29
Below is a sample Makefile.  There is no need to explicitly define/use a CC variable.  CXX is automatically understood by the Makefile.  Concerning compiling 32-bit code, add -m32 to the CXXFLAGS.

```

SRCS       := $(wildcard *.cpp)
OBJS        = $(SRCS:.cpp=.o)
CXXFLAGS    = -O2
INCLUDES    = -I./
LIBS        = -lpthread
LIBPATH     =

DEP_FILE    = .depend
APPS        = threaded

.PHONY: all clean distclean


all: depend $(APPS)

$(APPS): $(OBJS)
	@echo Makefile - linking $@
	@$(CXX) $(LIBPATH) $(LIBS) $^ -o $@

.cpp.o:
	@echo Makefile - compiling $<
	@$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@

clean:
	$(RM) $(OBJS)

distclean: clean
	$(RM) $(APPS)
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CXX) -E -MM $(INCLUDES) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif
```

---

### Post by LostinLinux on 2008-06-07
Hi, I am still fighting with this issue I just cant get it to compile a 32bit version :( - here is my makefile:

```

NAME = app1
HOST ?= linux
RELEASE ?= 0
GUI ?= 1

CFLAGS += -Wall -g -Iinc -Iinc/core

ifeq ($(RELEASE), 1)
CFLAGS += -DRELEASE
endif

LIBS += 
EXT =

include make-$(HOST).inc

BIN = $(NAME)$(EXT)
SRC = $(shell echo src/core/*.cpp src/main/*.cpp)
SRCH = $(shell echo inc/core/*.h src/core/*.h)

ifeq ($(GUI), 1)
CFLAGS += -Iinc/gui -DGUI
SRC += $(shell echo src/gui/*.cpp)
SRCH += $(shell echo inc/gui/*.h)
endif

OBJ = $(SRC:.cpp=.o)
CXXFLAGS = $(CFLAGS)

.PHONY : all clean run win32 mac linux

all : $(BIN)

win32 : clean
	HOST=windows make

linux : clean
	HOST=linux make

mac : clean
	HOST=mac make

$(BIN) : $(OBJ)
	 $(CXX) -o $(BIN) $(OBJ) $(LIBS)

.cxx.o :
	 $(CXX) -c -o $@ $< $(CXXFLAGS)

-include .deps

.deps : $(SRC) $(SRCH)
	$(CXX) -M $(SRC) $(CXXFLAGS) > $@

clean :
	rm -f $(OBJ) $(BIN) $(NAME) $(NAME).exe

run : all
	$(EXECUTOR) ./$(BIN)


```

And the linux ext...

```

CFLAGS += -D__LINUXBUILD__ `fltk-config --cflags` 
LIBS += -lusb `fltk-config --ldflags`
EXECUTOR =

```

Any help much appreciated :)

---

### Post by dwhitney67 on 2008-06-07
Have you tried specifying the "-m32" compiler option?

This should create a 32-bit application, but for your architecture.  If you are trying to compile for a different architecture, then you will require a cross-compiler.

Cross-compiler's are not trivial to make.  I've done it myself following instructions on the web, and was successful in compiling 586 code on a dual-core 686.

Here's the site:  [http://cross-lfs.org/files/BOOK/1.0.0/CLFS-1.0.0-x86.html](http://cross-lfs.org/files/BOOK/1.0.0/CLFS-1.0.0-x86.html)

Pay careful attention to Chapters 4 and 5.  If you are new to *nix, then the subject matter may possibly prove difficult to follow/understand.  Don't jump into it until you understand more about cross-compiling!

---

### Post by Vadi on 2008-06-07
I recommend just getting Virtualbox, and installing 32bit Ubuntu in there. While compiling your app is pretty much as easy as adding -m32, you'd also need the 32bit version of the libraries you're using - and it can get nasty there. Virtualbox makes it a lot easier.

---

### Post by JupiterV2 on 2008-06-08
If porting to windows, you can DL the mingw-win32 compiler for linux to cross-compile to win32. Else, (and likely the easiest route if packages for the libraries you're using already exist for windows) install wine and compile the libraries as if you were running native Windows.

---

### Post by LostinLinux on 2008-06-22
Thanks all, im still working on this. I managed to compile 32bit app using another system - all fine. 

On porting to windows I am struggling...

I retrieved mingw-win32 from the repo however I get a:

> inc/core/config.h:24:23: error: Windows.h: No such file or directory

compile error. :(

Can someone point me in the right direction...again :)

Thanks.

---

### Post by LostinLinux on 2008-06-29
Any ideas guys?

The code compiles perfectly on windows using Msys and mingw32. 

All help much appreciated :)

---

### Post by LostinLinux on 2008-07-07
Any ideas at all why windows.h is not found? Im having to compile on windows all the time :(

---

### Post by Vadi on 2008-07-07
Maybe you need to set the include directory to be where windows.h is. I think the syntax is *-I"**location**"* or something.

---

