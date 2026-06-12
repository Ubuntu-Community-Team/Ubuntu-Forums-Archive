---
title: "Compiling, fixing segmentation fault"
date: 2010-02-26
forum: Programming Talk
---

### Post by dragos2 on 2010-02-26
I have a program written in C and compiled on Solaris 10 like this and it works:
```

c99 ma.c ac.c an.c au.c output.c es.c lf.c  e.c ed.c -o program `pkg-config --libs --cflags gtk+-2.0`

```

Now on Ubuntu 8.04 64 bits I am trying the same using c99 or gcc, everything goes well
during compilation but when running the program I get a segmentation fault, and gdb
spots it here:

```

(gdb) run
0x00007f40f049bc54 in fread () from /lib/libc.so.6

```

a quick grep shows that the program is using fread in 2 files and it appears only once.

What compiler flags should I pass in order to don't receive that error ? Or any other ideas 
that will make this program work under Ubuntu ?

---

### Post by noway2 on 2010-02-26
First, are you sure you are posting to the correct forum?  This one is for server discussions and you will get better responses under the programming one.  Perhaps you should ask the moderator to move it.

Second, you compile flags look correct.  I don't normally call c99 directly, instead use gcc or g++ when appropriate as these will call the correct compiler for the system automatically.  A segmentation fault on a fread sounds like your trying to read from a file that hasn't been opened or writing to a location (pointer) that isn't correct.

---

### Post by Simon17 on 2010-02-26
What's probably happening is that the program is trying to open some file without checking if it exists, and it doesn't on your ubuntu system. There is no compiler flag that will fix this.

Of course it's impossible to tell without seeing the code.

---

### Post by MadCow108 on 2010-02-26
compile it with -g and do
run
backtrace
in gdb
this won't fix the error but will give you a better indication of error source

---

### Post by radeon21 on 2010-02-26
fread() is a system call that is probably being called indirectly by other code you're using (fscanf, for example).  Can you post your source?

---

### Post by dragos2 on 2010-03-01
Thanks all, it seems that backtrace did the job and the problem was in a wrong path that was working on the old system and after being adapted it worked.

Thanks again :)

---

### Post by dragos2 on 2010-03-01
The problem is still not completely fixed, it seems that another one popped out related to GTK I guess. I will make another thread.

---

