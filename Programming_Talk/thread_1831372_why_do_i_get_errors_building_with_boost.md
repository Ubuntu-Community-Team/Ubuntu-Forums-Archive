---
title: "why do i get errors building with boost?"
date: 2011-08-23
forum: Programming Talk
---

### Post by jebsector on 2011-08-23
I get the following errors when building a project that makes use of boost::filesystem, regardless of whether I'm pointing to boost v. 1.42 or boost v. 1.46..

```

build/Debug/GNU-Linux-x86/idx/idx_utility.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:208: undefined reference to `boost::system::get_system_category()'
/usr/include/boost/system/error_code.hpp:209: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::get_generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::get_system_category()'
build/Debug/GNU-Linux-x86/idx/idx_utility.o: In function `error_code':
/usr/include/boost/system/error_code.hpp:315: undefined reference to `boost::system::get_system_category()'
build/Debug/GNU-Linux-x86/idx/idx_utility.o: In function `boost::system::errc::make_error_code(boost::system::errc::errc_t)':
/usr/include/boost/system/error_code.hpp:476: undefined reference to `boost::system::get_generic_category()'
build/Debug/GNU-Linux-x86/idx/idx_utility.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::exists<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:293: undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, boost::system::error_code&)'
build/Debug/GNU-Linux-x86/idx/idx_utility.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::is_directory<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:303: undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, boost::system::error_code&)'
build/Debug/GNU-Linux-x86/idx/idx_utility.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::create_directory<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:423: undefined reference to `boost::filesystem::detail::create_directory_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/datacarbon] Error 1
make[1]: *** [.build-conf] Error 2
make: *** [.build-impl] Error 2

```

Do you guys know what this is about?  Other things seem to work fine, like regex, shared_ptr, etc..

Thanks,

---

### Post by matrronchi on 2011-08-23
Did you correctly link all the libraries when building?Probably it's missing some dependency..
Check in the make file, or post it..

---

### Post by Zugzwang on 2011-08-23
@OP: Copying a suitable part from your error message into your favourite search engine would have helped. For example, this is what I've found, which answers your question: [http://stackoverflow.com/questions/2167149/error-while-compiling-simple-code-in-boost-how-to-find-the-name-of-the-library](http://stackoverflow.com/questions/2167149/error-while-compiling-simple-code-in-boost-how-to-find-the-name-of-the-library)

---

### Post by jebsector on 2011-08-23
Unfortunately, I'm using netbeans just for the code assist.  

Maybe I should do it the old-school way and build from gedit and the command line.. netbeans' makefile is kind of blah.

When I get back to my house i'll see what happens if I build outside of netbeans with a proper makefile.  Using g++ but this will need to port to windows as well.

---

### Post by jebsector on 2011-08-23
zugzwang - thanks for checking.  I never thought to try googling the entire error string.  

I'll try putting in the flag to netbeans and see what happens.  I'll be checking back in around noon mountain time today to see what happens. 

btw - is this the same for things like threads?  I've noticed multiple people having portable thread compilation problems, i'll have to look into that as well...

---

### Post by jebsector on 2011-08-23
I've tried various ways of trying to get -lboost_filesystem to take.  It looks from other forums that I'll also need to do this for boost_system.  

I'm kind of new to c++, so sorry for the confusion.  This is where I stopped trying different things with the build process.. (output from make)

```

g++ -lboost_filesystem    -o dist/Debug/GNU-Linux-x86/datacarbon build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/idx/idx_utility.o /home/jeremiah/boost_1_46_1/bin.v2/libs/filesystem/build/gcc-4.4.5/release/link-static/libboost_filesystem-gcc44-1_46_1.a 
/usr/bin/ld: cannot find -lboost_filesystem
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/datacarbon] Error 1
make[1]: *** [.build-conf] Error 2
make: *** [.build-impl] Error 2

```

I had to re-build boost with using a complete flag, and the new directory at least has an .so that I was assuming needed to be used in order for -lboost_filesystem to take.  But I don't see where to add it in netbeans.  It exists on my machine at the following directory:

/boost_1_46_1/bin.v2/libs/filesystem/build/gcc-4.4.5/release/libboost_filesystem-gcc44-1_46_1.so.1.46.1  

I also have this file in a similar directory, don't know if it helps me..
/boost_1_46_1/bin.v2/libs/filesystem/build/gcc-4.4.5/release/link-static/libboost_filesystem-gcc44-1_46_1.a

Thanks,

---

### Post by dwhitney67 on 2011-08-23
> **jebsector said:**
>   
I'm kind of new to c++, so sorry for the confusion.

New to C++ and using Boost already?  And a later version than is offered by your system's Synaptic Package Manager?

Typically with older Ubuntu releases (eg. Ubuntu 9.10), the entire Boost library was provided with the libboost-dev package; however I have found that with my Ubuntu 11.04 release that this is not the case.  I had to install a distinct package to get the file-system library.
```

sudo apt-get install libboost-filesystem-dev

```
Or if you want the whole enchilada:
```

sudo apt-get install libboost*

```

I would suggest that you install the bare minimum of what you require; you should be able to verify the existence of libboost_filesystem.so in /usr/lib.  If it is not there already, then follow the suggestion above to get the library.

As for NetBeans (NB), why are you using it in the infancy of your learning process of Linux (or Unix)?  If a project depends on a particular library, it should not be that difficult to assign it to the list of libraries that NB uses for a particular project.  Of course, my experience is from developing in Java, and occasionally using NB to debug my projects.


P.S.  If you want to take a simple program that uses the Boost File System library, and compile/link it from the command line, something like this is employed:
```

g++ -Wall -pedantic MyProg.cpp -lboost_filesystem

```
------------------------

EDIT:

Silly me... if you want all of the Boost library files, then this is the appropriate package (at least I think so):
```

sudo apt-get install libboost-all-dev

```

---

### Post by jebsector on 2011-08-27
So I started over with a makefile, downloaded the boost libraries from synaptec, and some sources.  Here's the makefile I currently have:
```

CC = g++
DEBUG = -g
CFLAGS = -Wall -c $(DEBUG)
LFLAGS = -Wall $(DEBUG)
FILESYS = -L/usr/lib -lboost_filesystem
SYS = -L/usr/lib -lboost_system
BOOSTDIR = -I/usr/include/boost -I/usr/include

all : datacarbon

datacarbon : main.o idx_utility.o
	$(CC) $(LFLAGS) main.o idx_utility.o -o datacarbon

main.o : main.cpp idx/idx_utility.h
	$(CC) $(CFLAGS) $(BOOSTDIR) main.cpp -o main.o

idx_utility.o : idx/idx_utility.h idx/idx_utility.cpp
	$(CC) $(CFLAGS) $(BOOSTDIR) idx/idx_utility.cpp -o idx_utility.o $(SYS) $(FILESYS)

clean:
	\rm *.o *~datacarbon

```

libboost_filesystem.so is at /usr/lib/libboost_filesystem.so, /usr/lib/libboost_filesystem.so.1.42.0 (libboost_filesystem.so seems to be a shortcut)
libboost_system is as /usr/lib/libboost_system.so, etc.
the boost sources (.hpp, .h) are at /usr/include/boost.

The result of building the started project are that it gets an undefined reference to the includes of filesystem in idx/idx_utility.o.

Thinking I have my makefile wrong, and I'm new to writing makefiles, especially when they depend on external libraries..

..so i guess i'm back to where i started, only this time without netbeans and an incompatible boost library..

---

### Post by dwhitney67 on 2011-08-27
Before presenting you with a corrected Makefile, let me remind you that when *compiling*, you do not need to specify the library (-ies) that will be needed for the project.  Only when *linking* the object file(s) together do you finally specify any library files.

Also, it is not necessary to indicate /usr/include nor /usr/lib as viable paths when using GCC.  These are already known, or should I say built-in, to GCC.

So here's a simple Makefile that you should be able to use:
```

APP      = datacarbon

SRCS     = $(shell find . -name '*.cpp')
OBJS     = $(SRCS:.cpp=.o)

INCLUDES = -I./idx
DEBUG    = -g
CXXFLAGS = -Wall -pedantic -c $(DEBUG) $(INCLUDES)

LDFLAGS  = -lboost_filesystem -lboost_system

.PHONY: all


# Generic rule (somewhat superflous)
#
all : $(APP)


# Rule for linking object files together to form APP
#
$(APP) : $(OBJS)
    $(CXX) $^ $(LDFLAGS) -o $@


# Rule for compiling an individual .cpp module
#
%.o : %.cpp
    $(CXX) $(CXXFLAGS) $< -o $@


# Rule for cleaning up
#
clean:
    $(RM) $(OBJS) $(APP)

```

Btw, from what I understood from your original Makefile, you have a directory containing a main.cpp file, and then a subdirectory called idx, which contains idx_utility.h and idx_utility.cpp.  If this is not correct, please let me know.  You may need to adjust the INCLUDES setting in the Makefile posted above.

If you require a more elaborate Makefile (eg. to keep track of dependencies), let me know.


P.S.  Your files, idx_utility.h and/or idx_utility.cpp, should include the appropriate boost header files in a manner similar to:
```

#include <**boost**/filesystem.hpp>

```

---

### Post by MadCow108 on 2011-08-27
depending with what your boost was compiles with you may have to adapt to the v2 or v3 api.
See the big box here:
[http://www.boost.org/doc/libs/1_47_0/libs/filesystem/v3/doc/index.htm](http://www.boost.org/doc/libs/1_47_0/libs/filesystem/v3/doc/index.htm)


a note on dwhitneys makefile:
```
LDFLAGS  = -lboost_filesystem -lboost_system
```
should be 
```
LIBS  = -lboost_filesystem -lboost_system
```
+ the use of this variable later changed to LIBS too.

_For this template its just cosmetic_ as it is used correctly later, but its very important for e.g. autotools. Autotools will put LDFLAGS before objects, and thus **must not** contain libraries to link the objects with, these belong in LIBS which gets placed behind objects.
This is required for the --as-needed linker flag which will be default from ubuntu 11.10 onwards.
LDFLAGS is just for flags, like --no-copy-dt-needed etc. LIBS or LDADD is for libraries to link with.

---

### Post by jebsector on 2011-08-27
That works perfectly now.  The program runs fine.  

So now a couple of questions on the makefile you gave - should this generally be the same case for redhat-based systems?  And, I'm assuming all i need to do to include threads is add that flag, and for my own code add it to the include directories if it exists in a separate folder than where the makefile is?

Thanks,  I'm still using netbeans, just using my own makefile and ignoring their stuff, seems to give me what i wanted - an ide that gives code assist and also good control over compilation.  I'm coming from a lot of java background, i would say netbeans could use some work covering c++..

but it's a lot simpler looking for libraries on linux now that i know where they are.  I haven't done much programming specifically for certain systems, so a lot of this stuff is a little new, even though i had most of the information.  (dah..)

---

