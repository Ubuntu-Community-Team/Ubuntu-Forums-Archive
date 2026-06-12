---
title: "compile sqlite in eclipse ubuntu"
date: 2011-02-27
forum: Programming Talk
---

### Post by rockbuntu on 2011-02-27
hi,

i am a newbie to ubuntu and need help with below error

1) installed vmware on my windows vista pc and ubuntu 10.4 in it
2) installed eclipse galileo in ubuntu
3) copied the sqlite3 source code to documents folder
4) created a makefile C++ project in eclipse
5) copied sqlicite.c / h and makefile.am and makefile.in the project 
6) compiled the project and got the below errors

undefined reference to dlclose / dlopen / dlsync and so on


**** Build of configuration Default for project SQLite3 ****

make all 
Building target: SQLite3
Invoking: GCC C++ Linker
g++  -o"SQLite3"  ./shell.o ./sqlite3.o   
./sqlite3.o: In function `pthreadMutexTry':
/root/workspace/SQLite3/Default/../sqlite3.c:17120: undefined reference to `pthread_mutex_trylock'


compile invocation arguments
-lpthread -E -P -v -dD ${plugin_state_location}/specs.cpp

seems like lpthread is not recognized as part of build process

---

### Post by gmargo on 2011-02-27
"-lpthread" should be on the link line, not the compile line.

---

### Post by rockbuntu on 2011-02-27
tried that but same error again...

make all 
Building target: SQLite3
Invoking: GCC C++ Linker

g++ -lpthread -o"SQLite3"  ./sqlite3.o   

/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
./sqlite3.o: In function `unixDlError':
/home/user/workspace/SQLite3/Default/../sqlite3.c:27947: undefined reference to `dlerror'

---

### Post by gmargo on 2011-02-27
You need "-ldl" to pull in the dynamic linking loader library (which contains dlerror).

---

