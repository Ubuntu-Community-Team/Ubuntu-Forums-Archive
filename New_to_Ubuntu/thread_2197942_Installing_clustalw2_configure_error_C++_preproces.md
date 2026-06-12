---
title: "Installing clustalw2 configure: error: C++ preprocessor &quot;/lib/cpp&quot; fails sanity check"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by ebarongo82 on 2014-01-06
Dear all, this is my first post here. I'm glad there is a user community which can help with my issues.

I want to install Clustalw2 but somewhere along the steps I'm not being successful. When I typed configuration command below is what I got:

edson@samsung:~/clustalw-2.0.12$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
building for linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C++ preprocessor... /lib/cpp
configure: error: in `/home/edson/clustalw-2.0.12':
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

What do I need to do? Any comment will be highly appreciated.
Thanks.

---

### Post by spjackson on 2014-01-06
Welcome to the forums.
> 
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no

It appears that you don't have g++ installed. You need to install it. The minimum you require is the g++ package, but I suggest you install build-essential package.

---

### Post by ebarongo82 on 2014-01-06
Thanks a lot. That was helpful.

---

### Post by ebarongo82 on 2014-01-13
@spjackson, please would you also help me here?

I am about to install clustalw after succesfull configuration. But the following steps 'make' and 'make install' seems to not be working perfectly. Here are the error messages:
edson@samsung:~/clustalw-2.0.12$ make install
Making install in m4
make[1]: Entering directory `/home/edson/clustalw-2.0.12/m4'
make[2]: Entering directory `/home/edson/clustalw-2.0.12/m4'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/aclocal" || /bin/mkdir -p "/usr/local/share/aclocal"
/bin/mkdir: cannot create directory &#8216;/usr/local/share/aclocal&#8217;: Permission denied
make[2]: *** [install-m4dataDATA] Error 1
make[2]: Leaving directory `/home/edson/clustalw-2.0.12/m4'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/edson/clustalw-2.0.12/m4'
make: *** [install-recursive] Error 1

Thanks.

Ps. As a follow-up to my difficulty I typed in a debug command as such:
edson@samsung:~/clustalw-2.0.12$ make install --debug
and this is what I get:
edson@samsung:~/clustalw-2.0.12$ make install --debug
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i686-pc-linux-gnu
Reading makefiles...
Updating goal targets....
 File `install' does not exist.
   File `install-recursive' does not exist.
  Must remake target `install-recursive'.
Making install in m4
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i686-pc-linux-gnu
Reading makefiles...
Updating goal targets....
 File `install' does not exist.
   File `install-am' does not exist.
     File `all-am' does not exist.
    Must remake target `all-am'.
    Successfully remade target file `all-am'.
  Must remake target `install-am'.
make[1]: Entering directory `/home/edson/clustalw-2.0.12/m4'
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i686-pc-linux-gnu
Reading makefiles...
Updating goal targets....
 File `install-exec-am' does not exist.
Must remake target `install-exec-am'.
Successfully remade target file `install-exec-am'.
make[2]: Entering directory `/home/edson/clustalw-2.0.12/m4'
make[2]: Nothing to be done for `install-exec-am'.
 File `install-data-am' does not exist.
   File `install-m4dataDATA' does not exist.
  Must remake target `install-m4dataDATA'.
test -z "/usr/local/share/aclocal" || /bin/mkdir -p "/usr/local/share/aclocal"
/bin/mkdir: cannot create directory &#8216;/usr/local/share/aclocal&#8217;: Permission denied
make[2]: *** [install-m4dataDATA] Error 1
make[2]: Leaving directory `/home/edson/clustalw-2.0.12/m4'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/edson/clustalw-2.0.12/m4'
make: *** [install-recursive] Error 1

What's going on? How do I fix it?

---

### Post by spjackson on 2014-01-13
You need permission to write to /usr/local/... Therefore:
```

sudo make install

```

---

### Post by ebarongo82 on 2014-01-14
> **spjackson said:**
> You need permission to write to /usr/local/... Therefore:
```

sudo make install

```

Thanks. Successfully done.

---

