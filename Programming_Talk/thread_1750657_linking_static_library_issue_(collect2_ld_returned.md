---
title: "linking static library issue (collect2: ld returned 1 exit status)"
date: 2011-05-05
forum: Programming Talk
---

### Post by _joachim_ on 2011-05-05
Hey there I'm having trouble linking a static lib in my app (C program), I don't understand why this won't work as I am following the instructions from the "Programming Linux Games", Page 29 "Working with Libraries"

For simplicity's sake I'm trying to link the following source as a static lib to a main.c:

```

/* myCharLib.c */
#include "myCharLib.h"
const char get_char(){
	return MY_CHAR;
}

```
```

#ifndef MYCHARLIB_H_
#define MYCHARLIB_H_
const char MY_CHAR = 'J';
const char get_char();
#endif

```
```

/* myIntLib.c */
#include "myIntLib.h"
const int get_integer()
{
	return MY_INT;
}

```
```

#ifndef MYINTLIB_H_
#define MYINTLIB_H_
const int MY_INT = 84;
const int get_integer();
#endif

```

And here is the make file I'm using:
```

CC=gcc
CFLAGS=-W -Wall -pedantic

libcMyLib.a: myCharLib.c myIntLib.c
	$(CC) $(CFLAGS) -c myCharLib.c myIntLib.c
	ar rcs libcMyLib.a myCharLib.o myIntLib.o
	ranlib libcMyLib.a

.PHONY: clean

clean:
	rm *.o
	rm *.a

```

And my main.c file:
```

#include <stdio.h>
const int get_int();
const char get_char();
int main()
{
	get_int();
	get_char();
	return 0;
}

```

So my working directory has these files after running make:
```

libcMyLib.a  main.c  makefile  myCharLib.c  myCharLib.h  myCharLib.o  myIntLib.c  myIntLib.h  myIntLib.o

```

Now I try compiling main.c and linking with libMyLib.a and this is what I get:
```

gcc -static main.c -L. -lcMyLib -o main 
/tmp/cc0wiQCm.o: In function `main':
main.c:(.text+0x7): undefined reference to `get_int'
main.c:(.text+0xc): undefined reference to `get_char'
collect2: ld returned 1 exit status

```

Where exactly am I going wrong here?

*Edit, yes I am aware of the sticky, but I've also tried following that advice and end up with the same linking problem

---

### Post by SledgeHammer_999 on 2011-05-05
I didn't test your code but shouldn't "get_int()" be "get_integer()" in your main?

(But I doubt that this is your main problem.)

---

### Post by _joachim_ on 2011-05-05
> **SledgeHammer_999 said:**
> I didn't test your code but shouldn't "get_int()" be "get_integer()" in your main?

(But I doubt that this is your main problem.)

Oh ffs, you are right, goddammit I've been up all night wondering and trying to figure out why it wouldn't link, and it was a typo this whole time, fml

---

### Post by dwhitney67 on 2011-05-05
You have additional issues...

The first issue is quite obvious... you should not be redeclaring the library's function in your main.c file; what you should do is include the header files that you desire from the library.  For example:
```

[B]#include "myCharLib.h"
#include "myIntLib.h"[/B]

int main(void)
{
   ...
}

```

The second issue is that you are not declaring the const values in your header file as static.  Thus if you follow the suggestion above, then the linker will complain that there are multiple definitions for your const values.  To remedy the situation, do something like:
```

#ifndef MYCHARLIB_H_
#define MYCHARLIB_H_
**static** const char MY_CHAR = 'J';
const char get_char();
#endif

```

---

