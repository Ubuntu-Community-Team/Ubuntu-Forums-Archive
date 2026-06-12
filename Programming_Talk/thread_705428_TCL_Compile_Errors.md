---
title: "TCL Compile Errors"
date: 2008-02-23
forum: Programming Talk
---

### Post by xelapond on 2008-02-23
Hello everyone.  I have been trying to compile my own linux distro so I can have it exactly as I want it.  I have been following the LFS guide from [www.linuxfromscratch.org](www.linuxfromscratch.org).  It has been going great so far, except when I got to section 5.8.1, where you compile TCL, I get the following errors:

```

/mnt/lfs/tcl18.4.15/unix/../compat/memcmp.c: In function 'memcmp':
/mnt/lfs/tcl18.4.15/unix/../compat/memcmp.c:55: warning: dereferencing 'void *' pointer
/mnt/lfs/tcl18.4.15/unix/../compat/memcmp.c:55: error: void value no ignored as it ought to be
/mnt/lfs/tcl18.4.15/unix/../compat/memcmp.c:55: warning: dereferencing 'void *' pointer
/mnt/lfs/tcl18.4.15/unix/../compat/memcmp.c:55: error: void value no ignored as it ought to be
make: *** [memcmp.o] Error 1
```

I am using the Linux From Scratch LiveCD that they provide.  Does anybody know any way around these errors?

Thanks, 

Alex

---

### Post by stevescripts on 2008-02-25
> **xelapond said:**
> Hello everyone.  I have been trying to compile my own linux distro so I can have it exactly as I want it.  I have been following the LFS guide from [www.linuxfromscratch.org](www.linuxfromscratch.org).  It has been going great so far, except when I got to section 5.8.1, where you compile TCL, I get the following errors:


Alex, 

Can you give me a more specific link to section 5.8.1 - a few minutes
of searching around that site didn't find it for me.

In general, to build tcl from scratch - 
```

cd /path/to/tclsources/unix
./configure
make
make test
make install

```

(make test optional ...)

Hope this helps.

Steve
(You must be root to run make install - use sudo or su
as appropriate...)

---

### Post by terrapisces on 2008-05-30
I too am getting this exact error at this exact point. Every post on the LFS mailing list about it has been ignored. The book does not state that you need to be root to build it's package. If that were a required step, I'm sure they would have included it. 

I have run though the first steps on 3 seperate systems(real+virtual), and still come to the same result. The book says this may be a compile problem from the previous builds for the toolchain, but after 3 or 4 solid run throughs I doubt it. Up to this point, all the checks and balances are checking out fine. 

BTW stevescripts, regarding the book and section 5.8.1(page 60)... Take a look at the PDF or HTML version of the book. The step in reference is while compiling the toolchain to build the base system. TCL is the first of three packages of the test suite used later in section 6.x of the book.

I have extensively searched and come up with no info on this problem. Can anyone help?

---

### Post by plettpc on 2008-06-07
[QUOTE=terrapisces;5081174]I too am getting this exact error at this exact point. Every post on the LFS mailing list about it has been ignored. The book does not state that you need to be root to build it's package. If that were a required step, I'm sure they would have included it. 

I have run though the first steps on 3 seperate systems(real+virtual), and still come to the same result. The book says this may be a compile problem from the previous builds for the toolchain, but after 3 or 4 solid run throughs I doubt it. Up to this point, all the checks and balances are checking out fine. 

[B]This has got me too,,, I've tried searching and came accross a post from the dev's which believe the prob is not with tcl at all but the tool adjust stage, apparently the test is not thorough enough.

Got me stumped tho.[/B]

---

### Post by geirha on 2008-06-07
Line 55 in memcmp.c has a silly mistake. Change the line that reads 
```
	unsigned char u1 = *s1, u2 = *s2;
```
to read
```
	unsigned char u1 = *ptr1, u2 = *ptr2;
```

However, the standard c library should allready have a memcmp() (in string.h). What does the configure script say about string.h ?

---

