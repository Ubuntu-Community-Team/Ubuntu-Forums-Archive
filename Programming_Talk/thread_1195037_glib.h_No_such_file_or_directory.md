---
title: "glib.h: No such file or directory"
date: 2009-06-23
forum: Programming Talk
---

### Post by huangyingw on 2009-06-23
hello, 
    I met this problem when using following sentence:
    ```

   #include <glib.h>
    
```
According a previous thread, I have run folloiwng command:
```

sudo apt-get install libglib2.0-dev

```
And this is my makefile:
```

run : jpg.o
	gcc -o run jpg.o
jpg.o : jpg.c regulator.c fprintf.c
	gcc -c `pkg-config --libs glib-2.0` jpg.c
clean :
	rm run jpg.o

```
the output of 
```

pkg-config --libs glib-2.0

```

---

### Post by dwhitney67 on 2009-06-23
Fix this statement:
```

gcc -c `pkg-config --libs glib-2.0` jpg.c

```
to be:
```

gcc -c `pkg-config --cflags glib-2.0` jpg.c

```
when you are compiling.

When you are linking your application (to build 'run'), then use the original pkg-config statement... you need that you get the library path.

Basically...
```

run : jpg.o
	gcc -o run jpg.o `pkg-config --libs glib-2.0`

jpg.o : jpg.c regulator.c fprintf.c
	gcc -c `pkg-config --cflags glib-2.0` jpg.c

clean :
	rm run jpg.o

```

P.S.  What is regulator.c and fprintf.c??

---

### Post by huangyingw on 2009-06-25
> **dwhitney67 said:**
> Fix this statement:

P.S.  What is regulator.c and fprintf.c??
     Yes, thank you. I am reading the man pkg-config. A little confusion at the difference between --cflags and --libs option.
While, regulator.c and fprintf.c are just another file, which contain funtions that I would like to use in jpb.c.
     I am not familiar with code reuse in linux c. So, I use such a stupid method of just copy the regulator.c and fprintf.c here.

---

