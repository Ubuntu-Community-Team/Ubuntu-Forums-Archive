---
title: "? Compile app that includes SQLite"
date: 2007-11-15
forum: Programming Talk
---

### Post by cogitordi on 2007-11-15
I've been trying to build an executable that includes SQLite. I can't get the SQLite C sample code to compile and I would appreciate some help. 

I've compiled SQLite itself and have libsqlite3.la.

I run 
gcc sqlitetest1.c -Llibs -lsqlite3 -static

"libs" is a copy of the .libs directory from my SQLite build location.

The error is that "ld" can't find the library. I've modified /etc/ld.so.conf but still no success.

---

### Post by geirha on 2007-11-15
What are you trying to do? libsqlite3.la is not a library, it contains metadata about the library (it's a text file you can read). If you want to staticly link the sqlite3 library, you need the **.a**-file.

---

### Post by cogitordi on 2007-11-15
I want to compile sqlite statically. Thanks for pointing out my error.

Now it looks as though I'm missing the pthreads library: lots of "undefined references to pthread_" + various.

---

### Post by tyoc on 2007-11-15
Only for be rought, I remember that sqlite has the possibility to be in 1 big file (all the headers and code in 1 file) I think htat is the normal way to "embed" sqlite in own application... I think they still give taht 1 big source file somewhere in they page.

---

### Post by seetho on 2007-11-15
> **tyoc said:**
> Only for be rought, I remember that sqlite has the possibility to be in 1 big file (all the headers and code in 1 file) I think htat is the normal way to "embed" sqlite in own application... I think they still give taht 1 big source file somewhere in they page.

You have to "make" the big .C and .H file out of the regular source files.  You can find the instructions on the web-site: [http://www.sqlite.org/cvstrac/wiki?p=SqliteBuildProcess](http://www.sqlite.org/cvstrac/wiki?p=SqliteBuildProcess)

It's easier if everything is in one large file.  They even say that optimisation is better this way.

Good luck.

---

### Post by geirha on 2007-11-15
> **cogitordi said:**
> I want to compile sqlite statically. Thanks for pointing out my error.

Now it looks as though I'm missing the pthreads library: lots of "undefined references to pthread_" + various.

Only a matter of adding "-lpthread" to the gcc-line I should think

---

### Post by cogitordi on 2007-11-16
> **geirha said:**
> Only a matter of adding "-lpthread" to the gcc-line I should think

That didn't work (ld complaint) but I did succeed by fully qualifying the location of libpthread and libsqlite libraries. 

Is there something wrong with my environment if ld doesn't find libpthread? 

To other comments: yes, I'm using the "amalgamation" source files.

Merci, les amis!

---

### Post by tyoc on 2007-11-16
perhaps you forget run ldconfig like root... but before that, you can do something like the following IIRC:

```

ldconfig -p |grep sq

```That will print the list of actual libraries in the pathy if Im not wrong... after that try to do 

```

sudo ldconfig

```Also perhaps you may want to see at 

> /etc/ld.so.conf and related

or try man ldconfig and perhaps man ld.so.conf

---

### Post by cogitordi on 2007-11-16
Thank you, running "sudo ldconfig" enabled me to remove the -lpthread parameter.  Why is it so?

Running "ldconfig -p | grep sq" does show me the slqlite libraries, you're right.

---

### Post by seetho on 2007-11-17
I just compiled the standalone sqlite3 utility a while ago just fine:

```
cc -O2 -ldl -lpthread -o sqlite3 shell.c sqlite3.c
```

---

### Post by seetho on 2007-11-29
I did some research on this topic just out of curiosity because i'm also trying to use sqlite in my latest project.  I'm not by any means an expert in SQLite or Linux programming, so this information is only what I know (so far).  Any 'experts' here may want to correct or comment about it.

After installing the source of sqlite say in ~/dev/sqlite, the SQLite documentation recommends doing the actual build in another sibling directory.  So let create ~/dev/build

cd to ~/dev/build and execute the configure script:

```
~/dev/build$ ../sqlite/configure
```

You'll end up with a Makefile (and several other files) in this directory.  Edit this mmakefile and comment out the line:

TCC += -DSQLITE_OMIT_LOAD_EXTENSION=1

I found this to be necessary to avoid errors later when I compile the shell.c (the sqlite3 CLP).

You may also what to edit the line "TLIBS = " to read

TLIBS = -ldl

Now do the following to compile and install:

```
~/dev/build$ make
```

After the make you will have a directory full of object files and the sqlite CLP executable called sqlite3

```
~/dev/build$ sudo make install
```

New libraries will be installed as /usr/local/lib/libsqlite3.a and /usr/local/lib/libsqlite3.so.0.8.6  (The former being the static lib and the later the shared lib).  The sqlite3 executable is also installed in /usr/local/bin/.

Now make the amalgamated sqlite source file:

```
~/dev/build$ make sqlite3.c
```

You end up with a very large source file sqlite3.c and the header sqlite3.h which are essentially what you need to embed sqlite in your applications.  You also have individual source files under the ~/dev/build/tsrc/.  You will also find shell.c here - this is the source used to build the CLP.

To build the CLP using shared library:
```

~/dev/build$ gcc -O2 -o sqlite3 tsrc/shell.c -ldl -lsqlite3
```

Note that -lpthread is not required since shell.c does not require it.

You'll end up with a 39k sqlite3 executable file.

To build the CLP with the sqlite embedded:

```
~/dev/build$ gcc -O2 -o sqlite3 tsrc/shell.c sqlite3.c -ldl -lpthread
```

I end up with and executable of just under 380k size.  Note that -lpthread needs to be specified since sqlite3.c uses it (I think).

I'm not sure how the static library can be used.  When I try

```
~/dev/build$ gcc -O2 -o sqlite3 tsrc/shell.c -ldl -lpthread  -l:libsqlite3.a
```

I end up with an executable of 1.4MB in size.  It still works but I think it's not right.

Now I try using -static option:

```
~/dev/build2$ gcc -O2 -o sqlite3 tsrc/shell.c sqlite3.c -ldl -lpthread -static
/tmp/ccJwxK50.o: In function `unixDlOpen':
sqlite3.c:(.text+0x43212): warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/tmp/ccsofMPw.o: In function `find_home_dir':
shell.c:(.text+0xdb8): warning: Using 'getpwuid' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking

```

I get 2 warnings about 2 instances where reference is made to shared glibc library.  The executable is 1.1MB in size.

So that's my experience with playing around with sqlite so far.  I've not really built any applications with it yet beyond the test with compiling the shell.c

---

### Post by Amr_not_Amr on 2008-11-23
Thank you all, and special thanks to you, "seetho"!
Your reply helped me a lot .. Finally I can have a statically linked command line tool on x86_64 Linux ..


Based on your post;
You can download the amalgamation package;

wget [http://www.sqlite.org/sqlite-amalgamation-3.6.6.1.tar.gz](http://www.sqlite.org/sqlite-amalgamation-3.6.6.1.tar.gz)

Then do;
./configure --enable-static --disable-shared --enable-tempstore &&  make ; echo $?

Then;
gcc -O3 -o sqlite3 shell.c sqlite3.c -ldl -lpthread -static

Then;
strip sqlite3

---

