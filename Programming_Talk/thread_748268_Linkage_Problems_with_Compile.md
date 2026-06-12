---
title: "Linkage Problems with Compile"
date: 2008-04-07
forum: Programming Talk
---

### Post by JonWasHere42 on 2008-04-07
Hey,

Ive got a C program for work that Ive written, and to run it requires calling several other programs..

In my Makefile, Ive linked these programs with 

-lpgplot -lcpgplot -lcfitsio 

When I run make, everything compiles perfectly but then i see the response:

> /usr/bin/ld: cannot find -lcfitsio
collect2: ld returned 1 exit status


And if I rearrange the order in which ive linked them will determine which one of the three it can not find. 
Ive searched for this problem, and all the responses seem to talk about problems with one of the three links, but I think my problem might be with ld.

Oh yes..due to a massive partition failure, I had to reinstall Ubuntu. These programs and their makefiles worked before the crash, but now they dont.

Any advice?
Thanks,
--Jon

---

### Post by dwhitney67 on 2008-04-07
From the error message you are getting, it would seem to me that your system is missing the library for libcfitsio.a (or libcfitsio.so?), or that you have not correctly specified the path where this library is located at.  For the latter, you must use the -L option when compiling with gcc.

For instance:
```
gcc ... -L/path/to/lib ... -lcfitsio ...
```

---

### Post by heikaman on 2008-04-07
> **JonWasHere42 said:**
> 
And if I rearrange the order in which ive linked them will determine which one of the three it can not find. 


try this:

```
-lcfitsio -lpgplot -lcpgplot -lcfitsio 
```

assuming that you tried to compile with:

```
-lpgplot -lcpgplot -lcfitsio 
```

and the error was:

```
/usr/bin/ld: cannot find -lcfitsio
collect2: ld returned 1 exit status
```

---

### Post by dwhitney67 on 2008-04-07
Reordering the libraries will NOT resolve the problem.  This is not an issue with undefined references; the error clearly states that the library could not be found.

This implies that the library does not exist on the system, or that it is not in a typical location (e.g. /usr/lib) and thus the library's path must be explicitly specified using the -L option.

---

### Post by JonWasHere42 on 2008-04-08
Ok, that was right I had to manually link it.

So (for simplicity) I have put in symbolic links to these libraries in /usr/lib/
But I still need to include the line  -I/usr/lib/
in my Makefile.  (where that is a -[capital i ], not a one or lowercase L)
While this is not the end of the world, is there a way I can make the compiler automatically search in /usr/lib/
Since this is a pretty standard place?
I thought it was to change the file /etc/ld.so.conf, so this is what i have..

> jon@jon:/usr/lib$ cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf
include /usr/lib/
include /usr/local/lib/


If there is something else I should do let me know.

Thanks,
--Jon

---

### Post by dwhitney67 on 2008-04-08
Under most circumstances, you should not have to modify the /etc/ld.so.conf.  Furthermore, you should not have created symbolic links within /usr/lib if the libraries you want to reference are stored elsewhere.  Use the -L gcc option to specify the path leading to the libraries.

The -I gcc option is useful for specifying the path leading to header files that are not in /usr/include or other standard header-file directories.

If you post again, please include your Makefile and the path where your 3rd-party library and header files reside.

---

### Post by JonWasHere42 on 2008-04-09
Ok, so I moved my .h files in /usr/inclue
Which i guess the compiler didnt do, when I compiled those program.
I guess what im wondering, is when i run my Makefile, (and when i make new Makefiles) I dont want to alwyas have to manually link -lcfitsio wtih its location, is there somewhere where i can have that done automatically?

--Jon

---

### Post by Zugzwang on 2008-04-09
If I see it correctly, you might want to use "pkg-config". Search this forums or the web for examples. The pkg-config tools automatically adds the library & include paths for a library you specify (provided that it's installed correctly, but the Ubuntu package manager will take care of that).

However, I have no clue how to use it in a Makefile. Someone else here might be willing to help...

---

### Post by dwhitney67 on 2008-04-09
I was trying, but now I give up.

---

### Post by WW on 2008-04-09
How did you install pgplot and cfitsio?

If you installed the Ubuntu packages pgplot5 (from the multiverse repository) and libcfitsio3-dev (from the universe repository), the headers should all be in /usr/include, and the libs should all be in /usr/lib.  You should not have to mess around with symbolic links, and the **-l** options that you gave should work.  (The file lists for these packages do not show any .pc files, so they are not configured to use pkg-config.)

---

### Post by lost09 on 2011-07-14
So, here's to dredging up long-dead threads...

I've experienced the same problem, namely that the compiler isn't able to locate libcfitsio.a. I've been operating under dwhitney67's advice of specifying the path with -L, to no avail. Here's the makefile:

```

HDRS = $(wildcard *.h)
SRCS = $(filter-out driver.cpp, $(wildcard *.cpp))
OBJS = $(filter-out driver.o, $(patsubst %.cpp, %.o, $(SRCS)))

# Command name
CMD = myExecutable
# Library name
LIBS = myLibrary.a

CFITSIO = /path/to/cfitsio/libcfitsio.a
CXX = gcc

# Compiling Flags
CXXFLAGS = -O3 -funroll-loops -m64 -Wall -march=core2 -fomit-frame-pointer -falign-functions -mfpmath=sse -msse4.1 -fno-stack-protector -I $(CFITSIO)

# Linking Flags
LDFLAGS = $(CXXFLAGS) -L$(CFITSIO)

all: $(CMD)

lib: $(LIBS)

$(CMD): $(LIBS) driver.o
	$(CXX) $(LDFLAGS) -o $(@) $(LIBS) driver.o -lcfitsio

$(LIBS): $(OBJS) $(HDRS)
	ar rcs $(@) $(OBJS)

```

Running "make" results in the following:

```

gcc -O3 -funroll-loops -m64 -Wall -march=core2 -fomit-frame-pointer -falign-functions -mfpmath=sse -msse4.1 -fno-stack-protector -I /path/to/cfitsio/libcfitsio.a -L/path/to/cfitsio/libcfitsio.a -o myExecutable myLibrary.a driver.o -lcfitsio
/usr/bin/ld: cannot find -lcfitsio
collect2: ld returned 1 exit status
make: *** [myExecutable] Error 1

```

Additional information:
libcfitsio.a is indeed located at the specified location.
I can successfully compile this code on Mac OS X 10.6; this problem arises when trying to compile on Ubuntu 10.04.

Any insight would be most appreciated.
-l

---

### Post by karlson on 2011-07-14
> **lost09 said:**
> 
```

CFITSIO = /path/to/cfitsio/libcfitsio.a
LDFLAGS = $(CXXFLAGS) -L$(CFITSIO)

```


If you want to link libcfitsio you should set CFITSIO as follows
```

CFITSIO=/path/to/cfitsio

```

and keep LDFLAGS as is or set LDFLAGS as:
```

LDFLAGS=$(CXXFLAGS) $(CFITSIO)

```

---

### Post by lost09 on 2011-07-14
Thanks for the response, karlson. Making the first change only:

```

CFITSIO=/path/to/cfitsio

```

results in the following:

```

gcc -O3 -funroll-loops -m64 -Wall -march=core2 -fomit-frame-pointer -falign-functions -mfpmath=sse -msse4.1 -fno-stack-protector -I /path/to/cfitsio -L/path/to/cfitsio -o myExecutable myLibrary.a driver.o -lcfitsio
/usr/bin/ld: skipping incompatible /path/to/cfitsio/libcfitsio.a when searching for -lcfitsio
/usr/bin/ld: cannot find -lcfitsio
collect2: ld returned 1 exit status
make: *** [myExecutable] Error 1

```

So clearly it locates the file, but I don't understand the source of the incompatibility. On the other hand, making both changes:

```

CFITSIO=/path/to/cfitsio
LDFLAGS=$(CXXFLAGS) $(CFITSIO)

```

results in:

```

gcc -O3 -funroll-loops -m64 -Wall -march=core2 -fomit-frame-pointer -falign-functions -mfpmath=sse -msse4.1 -fno-stack-protector -I /path/to/cfitsio /path/to/cfitsio -o myExecutable myLibrary.a driver.o -lcfitsio
/usr/bin/ld: /path/to/cfitsio: No such file: File format not recognized
collect2: ld returned 1 exit status
make: *** [myExecutable] Error 1

```

Which leads me to suspect faulty syntax here. I'm leaning towards option 1, but suffice to say, I'm still confused. I don't suppose you can shed some light on the source of this supposed incompatibility?

---

### Post by karlson on 2011-07-14
> **lost09 said:**
> Thanks for the response, karlson. Making the first change only:

```

CFITSIO=/path/to/cfitsio

```

results in the following:

```

gcc -O3 -funroll-loops -m64 -Wall -march=core2 -fomit-frame-pointer -falign-functions -mfpmath=sse -msse4.1 -fno-stack-protector -I /path/to/cfitsio -L/path/to/cfitsio -o myExecutable myLibrary.a driver.o -lcfitsio
/usr/bin/ld: skipping incompatible /path/to/cfitsio/libcfitsio.a when searching for -lcfitsio
/usr/bin/ld: cannot find -lcfitsio
collect2: ld returned 1 exit status
make: *** [myExecutable] Error 1

```


Do you have libcfitsio.so?  -l<library> links the program dynamically.  If you don't you need to set as follows:

```

CFITSIO=/path/to/cfitsio/libcfitsio.a
LDFLAGS=$(CXXFLAGS) $(CFITSIO)

```

> 

So clearly it locates the file, but I don't understand the source of the incompatibility. On the other hand, making both changes:

```

CFITSIO=/path/to/cfitsio
LDFLAGS=$(CXXFLAGS) $(CFITSIO)

```

results in:

```

gcc -O3 -funroll-loops -m64 -Wall -march=core2 -fomit-frame-pointer -falign-functions -mfpmath=sse -msse4.1 -fno-stack-protector -I /path/to/cfitsio /path/to/cfitsio -o myExecutable myLibrary.a driver.o -lcfitsio
/usr/bin/ld: /path/to/cfitsio: No such file: File format not recognized
collect2: ld returned 1 exit status
make: *** [myExecutable] Error 1

```

Which leads me to suspect faulty syntax here. I'm leaning towards option 1, but suffice to say, I'm still confused. I don't suppose you can shed some light on the source of this supposed incompatibility?

Making both changes is wrong.  Apologies if I wasn't clear.

The changes are mutually exclusive.  If you are changing LDFLAGS you should keep CFITSIO variable unchanged.  If you change CFITSIO you should keep LDFLAGS unchanged.

But in addition if you are changing LDFLAGS to what I have described previously you should remove -lcfitsio from the linking.

---

### Post by lost09 on 2011-07-15
No, I don't have libcfitsio.so. To the extent of my knowledge, the library doesn't need to be dynamically linked. I tried this:

```

CFITSIO=/path/to/cfitsio/libcfitsio.a
LDFLAGS=$(CXXFLAGS) $(CFITSIO)

```

with the result:

```

cc1plus: error: /path/to/cfitsio/libcfitsio.a: not a directory

```

Forgive me if I'm being dense, but why can I not simply link the library (statically) by explicitly providing the path as above?

---

### Post by karlson on 2011-07-15
> **lost09 said:**
> No, I don't have libcfitsio.so. To the extent of my knowledge, the library doesn't need to be dynamically linked. I tried this:

```

CFITSIO=/path/to/cfitsio/libcfitsio.a
LDFLAGS=$(CXXFLAGS) $(CFITSIO)

```

with the result:

```

cc1plus: error: /path/to/cfitsio/libcfitsio.a: not a directory

```

Forgive me if I'm being dense, but why can I not simply link the library (statically) by explicitly providing the path as above?

That's because you have in your CXXFLAGS -I $(CFITSIO)

That should not be there.

---

### Post by lost09 on 2011-07-15
> 
That's because you have in your CXXFLAGS -I $(CFITSIO)

That should not be there. 


But removing "-I $(CFITSIO)" from the CXXFLAGS definition causes the compiler to not recognize any of the fitsfile instructions contained in the cfits library.

---

### Post by karlson on 2011-07-15
> **lost09 said:**
> But removing "-I $(CFITSIO)" from the CXXFLAGS definition causes the compiler to not recognize any of the fitsfile instructions contained in the cfits library.

Then what you should do is to have this:

```

CFITSIO_DIR = /path/to/cfitsio
CFITSIO = $(CFITSIO_DIR)/libcfitsio.a
CXXFLAGS = <flags> -I$(CFITSIO_DIR)

```

---

### Post by lost09 on 2011-07-16
Making progress, but the resulting library doesn't seem to be linking correctly. Here's the entire makefile, with your most recent suggestion:

```

HDRS = $(wildcard *.h)
SRCS = $(filter-out driver.cpp, $(wildcard *.cpp))
OBJS = $(filter-out driver.o, $(patsubst %.cpp, %.o, $(SRCS)))

# Command name
CMD = myExecutable
# Library name
LIBS = myLibrary.a

CFITSIO_DIR = /path/to/cfitsio
CFITSIO = $(CFITSIO_DIR)/libcfitsio.a
CXX = g++

# Compiling Flags
CXXFLAGS = -O3 -funroll-loops -m64 -Wall -march=core2 -fomit-frame-pointer -falign-functions -mfpmath=sse -msse4.1 -fno-stack-protector -I $(CFITSIO_DIR)

# Linking Flags
LDFLAGS = $(CXXFLAGS) $(CFITSIO)

all: $(CMD)

lib: $(LIBS)

$(CMD): $(LIBS) driver.o
	$(CXX) $(LDFLAGS) -o $(@) $(LIBS) driver.o -lcfitsio

$(LIBS): $(OBJS) $(HDRS)
	ar rcs $(@) $(OBJS)

```

Note that I also changed gcc to g++ in order to link the standard c++ libraries correctly. The above makefile successfully compiles the individual files, but doesn't seem to link them properly; it fails with about 40 "driver.cpp: (.text+0x210b): undefined reference to `EveryClass::EveryMethod(args)'" errors. Incidentally, the result is identical if I define LDFLAGS as

```

LDFLAGS = $(CXXFLAGS) -L$(CFITSIO)

```

---

### Post by Bachstelze on 2011-07-16
The command is:

```
gcc -I/path/to/include/dir -L/path/to/lib/dir -o output object1.o object2.o -llib
```

Note that -I and -L are followed by *directory* paths, not file paths. The name of the library is given with -l, -L only gives the path where to look for it. I'll let you correct your Makefile accordingly.

Also -I parameters go in CPPFLAGS, -L parameters go in LDFLAGS and -l parameters go in LIBS.

---

### Post by lost09 on 2011-07-16
I suppose it's obvious by now that I'm learning makefiles as I go, so I apologize for my obtuseness. The below is both my first attempt at correcting the file, and demonstrably wrong.

```

HDRS = $(wildcard *.h)
SRCS = $(filter-out driver.cpp, $(wildcard *.cpp))
OBJS = $(filter-out driver.o, $(patsubst %.cpp, %.o, $(SRCS)))

# Command name
CMD = myExecutable
# Library name
LIBS = myLibrary.a -llibcfitsio.a

CFITSIO_DIR = /path/to/cfitsio
CXX = gcc

# Compiling Flags
CXXFLAGS = <flags> -I$(CFITSIO)

# Linking Flags
LDFLAGS = $(CXXFLAGS) -L$(CFITSIO)

all: $(CMD)

lib: $(LIBS)

$(CMD): $(LIBS) driver.o
	$(CXX) $(LDFLAGS) -o $(@) driver.o $(LIBS) 

$(LIBS): $(OBJS) $(HDRS)
	ar rcs $(@) $(OBJS)

```

In a hypothetical correct version of the above, are the two libraries (mine, consisting of my code, and the existing cfitsio library) linked as equals, so to speak, or is the latter linked in and then compiled along with my code into the former?

---

### Post by Bachstelze on 2011-07-16
When I said -l parameters go in LIBS, I should have added that ONLY -l parameters go in LIBS. Moreover, library filenames *must* start with "lib", and for a library file named libfoo.a, the correct -l parameter is -lfoo. So rename myLibrary.a to e.g. libmylib.a and do something like:

```
LIBS = -lcfitsio -lmylib
LDFLAGS = -L$(CFITSIO_DIR) -L.
```

-L. is needed so that the linker will also look for library files in the current directory, since that's presumably where libmylib.a is. Needless to say, you can't use LIBS as a target name, so you'll have to create other variables or hardcode libmylib.a.

---

