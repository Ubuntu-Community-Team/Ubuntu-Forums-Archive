---
title: "boost static linking problem"
date: 2012-09-01
forum: Programming Talk
---

### Post by marcimatz on 2012-09-01
Hello,

I just installed boost on Ubuntu 12.04 64 bit. I used following instructions to do it:

sudo apt-get install libboost-all-dev

I can use the include parts of the boost library, but when I try to do a static linking with libboost_thread.a, I get following error message:

/usr/bin/ld: /usr/lib/libboost_thread.a(thread.o): relocation R_X86_64_32 against `tls_destructor' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libboost_thread.a: could not read symbols: Bad value
collect2: ld returned 1 exit status

In my makefile, I have following:

CFLAGS = -I./include -I./v_repExtRemoteApi -Wall -fPIC
LDFLAGS = -lpthread -ldl

CFLAGS += -D__linux
OPTION = -shared
EXT = so
BOOST_LIB_PATH = /usr/lib
OBJS_ADDITIONAL = $(BOOST_LIB_PATH)/libboost_thread.a

From my understanding, I need to recompile libboost_thread.a
Why do I need to recompile it? Because it is the 32 bit version?
And the other question is, how do I recompile it? In the past I would download the library manually and build it manually from the install directory, but by installing it with 'sudo apt-get install libboost-all-dev' I got confused.

Any help is appreciated, thanks a lot!

---

### Post by matt_symes on 2012-09-01
Thread moved to "programming Talk".

---

### Post by dwhitney67 on 2012-09-01
> **marcimatz said:**
> 
Any help is appreciated, thanks a lot!

It appears that you are using a Makefile to build your project; since you did not post it in its entirety I will not be able to help you 100%.  But you will need to indicate to the linker that you want to link the static version of the boost_thread library; you don't actually explicitly list the file name.

Something like this:
```

g++ MyObjectFile.o **-static -pthread -lboost_thread**

```
The part above that is in bold text should be added to your LDFLAGS.  I don't see a need to continue using BOOST_LIB_PATH and OBJS_ADDITIONAL.

---

### Post by spjackson on 2012-09-01
> **marcimatz said:**
> 
CFLAGS = -I./include -I./v_repExtRemoteApi -Wall -fPIC
OPTION = -shared
OBJS_ADDITIONAL = $(BOOST_LIB_PATH)/libboost_thread.a

The static library is incompatible with the -shared -fPIC options. Either use the shared library, or compile you project -static (as per dwhitney67).

> 
From my understanding, I need to recompile libboost_thread.a
Why do I need to recompile it? Because it is the 32 bit version?
And the other question is, how do I recompile it? In the past I would download the library manually and build it manually from the install directory, but by installing it with 'sudo apt-get install libboost-all-dev' I got confused.

Any help is appreciated, thanks a lot!If you really want to compile the library, and I suggest that you don't, then you would either need to get the package source or get the source from [http://boost.org/](http://boost.org/) . The libboost-all-dev package itself does not provide the library source code.

---

### Post by marcimatz on 2012-09-02
Thank you very much dwhitney67 and spjackson.

Sorry, I didn't realize that I should have posted the full makefile. I am actually trying to build a library. Following is the makefile, modified according to your suggestions:

CFLAGS = -I./include -I./mySources -Wall
LDFLAGS = -lpthread -lboost_thread -ldl

OBJS = mySources/fileA.o mySources/fileB.o mySources/fileC.o mySources/fileD.o mySources/fileE.o mySources/fileF.o mySources/fileG.o mySources/fileH.o mySources/fileI.o common/fileJ.o

ECHO=@

CFLAGS += -D__linux
OPTION = -static
EXT = so

TARGET = libmyLibrary.$(EXT)

all: myLibrarylib

myLibrarylib: $(OBJS)
        @echo "Linking $(OBJS) to $(TARGET)"
        $(ECHO)$(CXX) $(CFLAGS) $(OBJS) $(OPTION) -o $(TARGET) $(LDFLAGS)

%.o: %.c
        @echo "Compiling $< to $@"
        $(ECHO)$(CXX) $(CFLAGS) -c $< -o $@

%.o: %.cpp
        @echo "Compiling $< to $@"
        $(ECHO)$(CXX) $(CFLAGS) -c $< -o $@

clean:
        @echo "Cleaning $(OBJS) $(TARGET)"
        $(ECHO)rm -rf $(OBJS) $(TARGET)

But the compiler now complains about several other things, for instance:

**warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
**warning: Using 'gethostbyaddr' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
**/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
**/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../../lib/libboost_thread.a(thread.o): In function `void boost::call_once<void (*)()>(boost::once_flag&, void (*)()) [clone .constprop.98]':
(.text+0x73): undefined reference to `pthread_cond_wait'

and so on.

Sorry, now I am very confused ;)

---

