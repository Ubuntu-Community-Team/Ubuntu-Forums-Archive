---
title: "GCC Compiler does not work?"
date: 2007-06-29
forum: Packaging and Compiling Programs
---

### Post by Noodels on 2007-06-29
Hi, I'm fairly new to ubuntu, linux and unix but I have done a little C programming before. My problem is this, when I try to use ./configure for a new program I have downloaded it checks for a few things. Among those things is a GCC compiler which it DOES detect but then says : 

checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

I expect the problem is probably with my GCC setup which just came with ubuntu so I have posted here. The whole error sequence is as follows:

noodels@noodels-desktop:~/Programs/circle-3.1$ ./configure
loading cache ./config.cache
checking for less... less
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

Not really sure what to do, help would be nice.

---

### Post by justin whitaker on 2007-06-29
GCC is not installed by default, but it is on the disk you used to install Ubuntu. 

Put:
> sudo apt-get install build-essential

In a terminal, and let apt do its thing.

---

### Post by Noodels on 2007-06-29
Okay, I'll try that, but two things :

1 - It's detecting the GCC but says it's not working implying that it's there.

2 - I've looked on the Synaptic Package Manager and it says GCC is installed, in fact different versions of GCC are installed even.

---

### Post by Noodels on 2007-06-29
No, sudo apt-get install build-essential doesn't work, with or without the ubuntu cd in.

---

### Post by praxis22 on 2007-06-29
This is what I get when I do it, what do you get?

```

$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Have you tried telling synaptic to re-install the package?

What package did you download? Are you sure it requires C, and not some other language, gcc isn't just a C compiler.

---

### Post by praxis22 on 2007-06-29
OK, this is what I get:

```

~/build/circle-3.1$** ./configure --help**
Usage: configure [options] [host]
Options: [defaults in brackets after descriptions]
Configuration:
  --cache-file=FILE       cache test results in FILE
  --help                  print this message
  --no-create             do not create output files
  --quiet, --silent       do not print `checking...' messages
  --version               print the version of autoconf that created configure
Directory and file names:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [same as prefix]
  --bindir=DIR            user executables in DIR [EPREFIX/bin]
  --sbindir=DIR           system admin executables in DIR [EPREFIX/sbin]
  --libexecdir=DIR        program executables in DIR [EPREFIX/libexec]
  --datadir=DIR           read-only architecture-independent data in DIR
                          [PREFIX/share]
  --sysconfdir=DIR        read-only single-machine data in DIR [PREFIX/etc]
  --sharedstatedir=DIR    modifiable architecture-independent data in DIR
                          [PREFIX/com]
  --localstatedir=DIR     modifiable single-machine data in DIR [PREFIX/var]
  --libdir=DIR            object code libraries in DIR [EPREFIX/lib]
  --includedir=DIR        C header files in DIR [PREFIX/include]
  --oldincludedir=DIR     C header files for non-gcc in DIR [/usr/include]
  --infodir=DIR           info documentation in DIR [PREFIX/info]
  --mandir=DIR            man documentation in DIR [PREFIX/man]
  --srcdir=DIR            find the sources in DIR [configure dir or ..]
  --program-prefix=PREFIX prepend PREFIX to installed program names
  --program-suffix=SUFFIX append SUFFIX to installed program names
  --program-transform-name=PROGRAM
                          run sed PROGRAM on installed program names
Host type:
  --build=BUILD           configure for building on BUILD [BUILD=HOST]
  --host=HOST             configure for HOST [guessed]
  --target=TARGET         configure for TARGET [TARGET=HOST]
Features and packages:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --x-includes=DIR        X include files are in DIR
  --x-libraries=DIR       X library files are in DIR
~/build/circle-3.1$ **./configure**
creating cache ./config.cache
checking for less... less
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc -Wall also needs -Wno-char-subscripts... no
checking whether gcc accepts -Wno-char-subscripts... yes
checking whether gcc accepts -fno-builtin... yes
checking for gethostbyaddr... yes
checking for socket... yes
checking for malloc... yes
checking for crypt... no
checking for crypt in -lcrypt... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for fcntl.h... yes
checking for sys/fcntl.h... yes
checking for errno.h... yes
checking for net/errno.h... no
checking for string.h... yes
checking for strings.h... yes
checking for limits.h... yes
checking for sys/time.h... yes
checking for sys/select.h... yes
checking for sys/types.h... yes
checking for unistd.h... yes
checking for memory.h... yes
checking for crypt.h... yes
checking for assert.h... yes
checking for arpa/telnet.h... yes
checking for arpa/inet.h... yes
checking for sys/stat.h... yes
checking for sys/socket.h... yes
checking for sys/resource.h... yes
checking for netinet/in.h... yes
checking for netdb.h... yes
checking for signal.h... yes
checking for sys/uio.h... yes
checking for mcheck.h... yes
checking whether crypt needs over 10 characters... no
checking for working const... yes
checking for pid_t... yes
checking for size_t... yes
checking for ssize_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for struct in_addr... yes
checking for typedef socklen_t... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for gettimeofday... yes
checking for select... yes
checking for snprintf... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strerror... yes
checking for stricmp... no
checking for strlcpy... no
checking for strncasecmp... yes
checking for strnicmp... no
checking for strstr... yes
checking for vsnprintf... yes
checking for inet_addr... yes
checking for inet_aton... yes
checking if accept is prototyped... yes
checking if atoi is prototyped... yes
checking if atol is prototyped... yes
checking if bind is prototyped... yes
checking if bzero is prototyped... yes
checking if chdir is prototyped... yes
checking if close is prototyped... yes
checking if crypt is prototyped... yes
checking if fclose is prototyped... yes
checking if fcntl is prototyped... yes
checking if fflush is prototyped... yes
checking if fprintf is prototyped... yes
checking if fputc is prototyped... yes
checking if fputs is prototyped... yes
checking if fread is prototyped... yes
checking if fscanf is prototyped... yes
checking if fseek is prototyped... yes
checking if fwrite is prototyped... yes
checking if getpeername is prototyped... yes
checking if getpid is prototyped... yes
checking if getrlimit is prototyped... yes
checking if getsockname is prototyped... yes
checking if gettimeofday is prototyped... yes
checking if htonl is prototyped... yes
checking if htons is prototyped... yes
checking if inet_addr is prototyped... yes
checking if inet_aton is prototyped... yes
checking if inet_ntoa is prototyped... yes
checking if listen is prototyped... yes
checking if ntohl is prototyped... yes
checking if perror is prototyped... yes
checking if printf is prototyped... yes
checking if qsort is prototyped... yes
checking if read is prototyped... yes
checking if remove is prototyped... yes
checking if rewind is prototyped... yes
checking if select is prototyped... yes
checking if setitimer is prototyped... yes
checking if setrlimit is prototyped... yes
checking if setsockopt is prototyped... yes
checking if snprintf is prototyped... yes
checking if socket is prototyped... yes
checking if sprintf is prototyped... yes
checking if sscanf is prototyped... yes
checking if strcasecmp is prototyped... yes
checking if strdup is prototyped... yes
checking if strerror is prototyped... yes
checking if stricmp is prototyped... no
checking if strlcpy is prototyped... no
checking if strncasecmp is prototyped... yes
checking if strnicmp is prototyped... no
checking if system is prototyped... yes
checking if time is prototyped... yes
checking if unlink is prototyped... yes
checking if vsnprintf is prototyped... yes
checking if write is prototyped... yes
updating cache ./config.cache
creating ./config.status
creating src/Makefile
creating src/util/Makefile
creating src/conf.h
Configuration completed.  To compile, type:  cd src; make
~/build/circle-3.1$** gcc -v**
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
```

---

### Post by Noodels on 2007-06-30
I've put the error message at the top. I've now tried writing a very very basic C program that should definitely work as follows.

```
#include <stdio.h>

int main()
{
 printf("Random jabber.");
 return 0;
}
```

And when trying to compile using GCC it tells me that stdio.h is not recognised. I also tried loading another Mud and it told me that stdio.h is not present. So the problem is there, I just need to figure out which part of the GCC compiler I need to re-install.

---

### Post by Noodels on 2007-06-30
> **praxis22 said:**
> This is what I get when I do it, what do you get?

```

$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Have you tried telling synaptic to re-install the package?

What package did you download? Are you sure it requires C, and not some other language, gcc isn't just a C compiler.

This is odd, because on the first time I tried this it didn't work. Now however, the following came up:

```
noodels@noodels-desktop:~$ sudo apt-get install build-essential
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-gfx1.2-4 libsdl-ttf2.0-0 libsdl-mixer1.2 libsdl-image1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 8053kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 http://gb.archive.ubuntu.com feisty/main libc6-dev 2.5-0ubuntu14 [3018kB]
Get: 2 http://security.ubuntu.com feisty-security/main linux-libc-dev 2.6.20-16.29 [667kB]
Get: 3 http://gb.archive.ubuntu.com feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4 [1632kB]
Get: 4 http://gb.archive.ubuntu.com feisty/main g++-4.1 4.1.2-0ubuntu4 [2581kB]
Get: 5 http://gb.archive.ubuntu.com feisty/main g++ 4:4.1.2-1ubuntu1 [1428B]   
Get: 6 http://gb.archive.ubuntu.com feisty/main dpkg-dev 1.13.24ubuntu6 [147kB]
Get: 7 http://gb.archive.ubuntu.com feisty/main build-essential 11.3 [6974B]   
Fetched 8053kB in 2m15s (59.3kB/s)                                             
Selecting previously deselected package linux-libc-dev.
(Reading database ... 107416 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-16.29_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-16.29) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
noodels@noodels-desktop:~$ 

```

After this I tried to compile the C file mentioned earlier and it worked, I just don't know how to run them in ubuntu.

---

### Post by praxis22 on 2007-06-30
Hi,

The problem you were having is that the basic system headers were not installed, (libc, I think) without them nothing will compile, and as the average user doesn't need them, they are not installed by default. By deciding to compile a program from source you've stepped into a larger world, much knowledge awaits you, give yourself a brownie point :)

```

Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
```

As you can see from the above many of the new packages were **-dev** short for development. Which means they contained header files, the other packages were the GNU C++ compiler and it's meta package. If you're going to be doing a lot of this you may want to install the other packages it suggested. They look like library call man pages and documentation. Install them then try this:

```

 man -s 3c stdio

```

By default all program man pages are in section 1 of the manpages section 3c holds all the system call references, just in case you ever get stuck for an operand or a modifier :)

If you open synaptic and type "development" (no quotes) into the search bar it will list all the headers you can download. If you wanted to compile a Gnome program, you need the base Gnome and GTK headers for instance, same if you wanted to compile an X package. Actually if you wanted to compile a Gnome package you may well require the X headers as well.

Generally speaking to compile and build stuff you do the following:

```

**./configure --help** (to see what options you have)
**./configure --<options>** (To speciy program and build specific options such as what to include and where to put  the final product, etc.)
**make** (to compile the source)

The following are sometimes usefull, but not always present/possible (remove the + at the start)
+make dep 
+make depend
+make test
+make check
+make <name> (use this one to build a particular program or subsystem, usefull if you only want to recompile one program from a whole suite of programs, you normally have to go into the individual directory to run this one.)

**make install** (Install the program you've just made, often renaming the binary on the process.)

```
This will usually copy the package and any support libraries & docs, etc. into your system in a place of your choising, (or /usr/local/bin, by default)

As to what you do next, on very small or simple programs you can usually tell by looking at the output of **ls**, anything that shows up bolder or brighter than the rest of the names is usually executable, directories are usually blue. To run it you type it's name. UNIX/Linux is a command line driven OS, get used to it, you'll be doing a lot of typing from now on. If you MUD you should be used to this by now. :)

Oh, and you should probably RTFM ;)

---

### Post by Noodels on 2007-07-01
Okay, thanks for all the help everyone, the compiling hassle is over. It still does not work but I'm sure I can figure it out.

---

### Post by aquavitae on 2007-07-02
I think Praxis forgot to mention that if the program you've compiled is not in your path (which it probably isn't), you need to specify the path when you run it, e.g. "./foo" to run "foo" from the current directory.

---

