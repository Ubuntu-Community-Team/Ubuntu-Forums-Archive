---
title: "gcc and shared libraries"
date: 2006-08-15
forum: Programming Talk
---

### Post by gmclachl on 2006-08-15
I am trying to embed PHP into an application I am writing. However I am having problems with linking to a shared object. 

 I use the following makefile 

 CC = gcc-4.0
 CFLAGS = -c -I/usr/local/include/php/ \
	-I/usr/local/include/php/main \
	-I/usr/local/include/php/Zend \
	-I/usr/local/include/php/TSRM \
	-Wall -g 
 LDFLAGS = -L/usr/local/lib -lphp5

 all: testphpembed.c
	$(CC) -o phpembed.o phpembed.c $(CFLAGS)
	$(CC) -o phpembed phpembed.o $(LDFLAGS)


 It compiles fine, but as soon as I try to run it I get.

  ./phpembed: error while loading shared libraries: libphp5.so: cannot open shared object file: No such file or directory

  I tried running LD_DEBUG and got the following output 
     23693:
     23693:     file=libphp5.so [0];  needed by ./phpembed [0]

  So it doesn't seem to be finding it, but it's there!

 George

---

### Post by gmclachl on 2006-08-15
Scratch that, I just ran LD_DEBUG=libs and it looks as if it isn't searching on the right path.Not sure why though as I am using the -L flag in the make file.

 George

---

### Post by hod139 on 2006-08-15
It's because you need to tell LD where the library is when you execute the binary, as the library isn't linked in until execution.  There are 2 options, you can add /usr/local/lib to the default search path of LD, or tell gcc where the library is at compile time.  For option 1, edit (or create) /etc/ld.so.conf and add /usr/local/lib to the file.  Then run the command 
```
 sudo ldconfig 
```

For option 2, you can add
```

LDFLAGS += -Wl,--rpath /usr/local/bin

```
to your makefile.

Hope this helps

---

### Post by gmclachl on 2006-08-15
Hi,
    That's that solved my problem thanks. One more thing. 

 I need to bundle this with an application so need to statically link to the library (I think). I have libhp5.a and I try to compile it with the -static flag but it fails with  undefined reference errors. 

 Is there a way of doing this?

 George

---

### Post by LordHunter317 on 2006-08-15
Statically compiling PHP is going to be dangerous and bad.  I would build a version of PHP adequate for your needs and include that.  As a rule, statically compiling on Linux in general is dangerous and bad.

[Be careful when using -rpath, as it can lead to trouble.](http://people.debian.org/~che/personal/rpath-considered-harmful)

---

