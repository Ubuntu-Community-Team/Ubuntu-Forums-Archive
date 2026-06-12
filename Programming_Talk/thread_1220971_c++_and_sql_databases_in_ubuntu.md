---
title: "c++ and sql databases in ubuntu"
date: 2009-07-23
forum: Programming Talk
---

### Post by slaiyer on 2009-07-23
Hello,

I have been continuously searching for methods of getting my compiler to compile sql code from mysql or postgresql.

I started with anjuta and mysql and i kept getting 

```
undefined refrence "mysql_init"

undefined refrence "mysql_real_connect"

undefined refrence "mysql_error"

```

when i try to build. I then tried everything, from adding the include files to adding the library files, till i gave up and download Netbeans.

The it was the same error with Netbeans IDE 6.5, so i decided to try postgresql, and i see to be facing the same errors, even after adding the includes and library files also.

```

/home/wanjohi/test/testing/main.cc:17: undefined reference to `PQconnectdb'
/home/wanjohi/test/testing/main.cc:22: undefined reference to `PQstatus'

```

so could some one please point out where i am going wrong with the compiler?

and yes i do call all the right headers, this is after 2 days of internet searching and even trying sample codes which give the same error too.

using ubuntu 9.04

---

### Post by MadCow108 on 2009-07-23
are you sure you provide the right linker flags and have the correct libraries installed?

maybe try compiling it over command line and see if that works and then try getting the IDE to work.
Under Anjuta you have to do Configure project -> Regenerate project so that it will apply package/library changes to the makefiles/libtool

---

### Post by slaiyer on 2009-07-23
Me building it in terminal

```
gcc -o main main.c -g -I/usr/include/postgresql -I/usr/lib/postgresql/8.3/lib

```

and the result i get:

```
/tmp/ccYNhLcT.o: In function `main':
/home/wanjohi/test/testing/main.c:17: undefined reference to `PQconnectdb'
/home/wanjohi/test/testing/main.c:22: undefined reference to `PQstatus'
collect2: ld returned 1 exit status

```

this is a c file from an example, since i cant get c++ to work, decided to first try c.

---

### Post by MadCow108 on 2009-07-23
the -I only defines the include path where it looks for header files.
you need to link the library with the -l flag
the -L flag gives the search path for libraries.

g++ -I/usr/include/postgresql -L/usr/lib/postgresql/8.3/lib -lpostgresql main.cpp

if the library has the name: libpostgresql.* (-l only needs the name without lib and ending)

you could also check if postgres or mysql is configured in pkg-config:
pkg-config --list-all | grep -i postgresql

if it finds something you can do the following (assuming what is found is called postgesql):
g++ `pkg-config --libs --cflags postgresql` main.cpp
pkg-config will add all necessary flags and libraries
adding that name to the packages in your anjuta project properties and regenerating should also allow you to compile with anjuta.

---

### Post by slaiyer on 2009-07-23
oh, thanks. learnt something new there, plus found out that my library file was actually in /usr/bin and the file was libpq.


thought i would just write that down incase some other poor bloke is suffering as i did.

---

