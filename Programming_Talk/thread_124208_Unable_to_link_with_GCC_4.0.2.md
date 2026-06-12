---
title: "Unable to link with GCC 4.0.2"
date: 2006-01-31
forum: Programming Talk
---

### Post by grajea01 on 2006-01-31
Hello,

It seems to be a frequently-reported problem, according to good ole Google, but I haven't seen any solution yet. Strangely according to google no one reported it on this forum :

While I compile a simple C++ app on my AMD64 with GCC 4.0.2 on Ubuntu 5.10 I get this:

---
g++ -L/usr/local/mysql/lib -lmysqlclient -lz -lcrypt -lnsl -lm -lstlport -o addServer-linux
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/crt1.o: In function `_start':
../sysdeps/x86_64/elf/start.S:109: undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [all] Error 1
---

The undefined reference has been reported at many places, but as I said, I couldn't find any workaround this.

This program is being ported from a Sun Ultra 10 running Solaris 10 and using SunStudio 11. No code modification has been necessary, only on the Makefile. I'm saying this to show that the code is not an issue here. It clearly seems to be a linker issue -unless I'm being badly mistaken ?

Anyway.. anyone got a way to go pass this vexing problem ?

Regards,

Jeff

---

### Post by toojays on 2006-02-01
Where do you expect the main function to come from? It looks like you haven't actually passed your source code to gcc.

---

### Post by grajea01 on 2006-02-01
I did - I'm not that dumb :). Above I just copy/pasted the error message, above.

Here's a full make session :

grajea01@helsinki:/usr/src/projets/inventaire/addServer-linux$ make clean;make all
rm -rf core *o addServer-linux
g++ -c -I. -I/usr/local/mysql/include -m64 -Wall -g mainfile.cpp
g++ -c -I. -I/usr/local/mysql/include -m64 -Wall -g mysqlServerClass.cpp
mysqlServerClass.cpp: In member function int mysqlServerClass::verifie_motdepasse(char*, char*):
mysqlServerClass.cpp:75: warning: unused variable uiFields
mysqlServerClass.cpp:75: warning: unused variable uiRows
mysqlServerClass.cpp:76: warning: unused variable ulLengths
g++ -L/usr/local/mysql/lib -lmysqlclient -lz -lcrypt -lnsl -lm -lstlport -o addServer-linux
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/crt1.o: In function `_start':
../sysdeps/x86_64/elf/start.S:109: undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [all] Error 1


and main() is the very first function in mainfile.cpp

-- Jeff

---

### Post by Mis_Uszatek on 2006-02-01
You've said that you've done changes to the makefile.

>>g++ -L/usr/local/mysql/lib -lmysqlclient -lz -lcrypt -lnsl -lm -lstlport -o addServer-linux

I am not an expert in makefiles, but where do you have in this line object files? I think you should tell the linker that it should add 'mainfile.o' to linking. In other case it is not possible for him to find main function.

---

### Post by toojays on 2006-02-01
But you haven't passed your objects to the linker. Your link command should look like:```
g++ mainfile.o mysqlServerClass.o -L/usr/local/mysql/lib -lmysqlclient -lz -lcrypt -lnsl -lm -lstlport -o addServer-linux
```

---

### Post by grajea01 on 2006-02-01
/me sits in front of his computer, red-faced and feelling totally stupid, really...

How could I forget $(OBJS) ??

the very first line in the Makefile is

OBJS=mainfile.o mysqlServerClass.o

so that later I could use a line like:

$(CC) $(OBJS) $(LINKFLAGS) -o addServer-linux

Except that I _did_ forget to put the variable on my linking line...

Lesson learned: never again will I write my Makefile late in the evenings !

Oh well.. thanks to anyone !

-- Jeff

---

### Post by slavik on 2006-02-01
I'd let an IDE (Anjuta/Kdevelop/Dev-C++) maintain my makefiles ... :p

---

### Post by toojays on 2006-02-01
I wouldn't. :P

---

