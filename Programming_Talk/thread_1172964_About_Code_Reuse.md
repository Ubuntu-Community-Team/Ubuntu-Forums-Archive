---
title: "About Code Reuse?"
date: 2009-05-29
forum: Programming Talk
---

### Post by huangyingw on 2009-05-29
hello,
    I wonder how to reuse another *.c file's function. To have a try and demo, I have written following codes. Would you help me to have a look, and could you give me more suggestion about code reuse in c.
\\192.168.0.7\myproject\c-c++\linux\caller\caller.c
```

#include "../becalled/becalled.h"

int main(void)
{
	int result= myAdd(1, 2);
	printf("result=%d",result);
	return   0;
}

```
\\192.168.0.7\myproject\c-c++\linux\caller\makefile
```

#include ../becalled/makefile #this want to be realized later.
run : caller.o
	gcc -o run caller.o
caller.o : caller.c ../becalled/becalled ../becalled/becalled.h
	gcc -c caller.c ../becalled/becalled.h ../becalled/becalled
clean :
	rm run caller.o

```
\\192.168.0.7\myproject\c-c++\linux\becalled\makefile
```

becalled: becalled.o
	gcc -o becalled becalled.o
becalled.o: becalled.c becalled.h
	gcc -c becalled.c

```
\\192.168.0.7\myproject\c-c++\linux\becalled\becalled.c
```

int myAdd(int a, int b)
{
	int result=0;
	result=a+b;
	return result; 
}

int main(void)
{
	return   0;
}

```
\\192.168.0.7\myproject\c-c++\linux\becalled\becalled.h
```

int myAdd(int a, int b);

```
make command output at:
```

root@linux-programming:~/myproject/c-c++/linux/caller# make
gcc -o run caller.o
caller.o: In function `main':
caller.c:(.text+0x13): undefined reference to `myAdd'
collect2: ld returned 1 exit status
make: *** [run] Error 1

```

---

### Post by Nemooo on 2009-05-29
Just compile the other file, too, i.e if you have a file main.c and it's calling a function inside another file call.c:

```
gcc main.c test.c
```

If you're including a header, you still have to add the file(s) being called from the header:

main.c:
```
#include "header.h"

int main(void)
{
        add(2, 3);

        return 0;
}
```
header.h:
```
int add(int, int);
```
add.c:
```
int add(int a, int b)
{
        return a + b;
}
```

Would be compiled with:
```
gcc main.c add.c
```

You want to read up on [header files]("http://en.wikipedia.org/wiki/Header_file") and [include guards]("http://en.wikipedia.org/wiki/Include_guard").

---

### Post by huangyingw on 2009-05-29
> **Nemooo said:**
> Just compile the other file, too, i.e if you have a file main.c and it's calling a function inside another file call.c:

```
gcc main.c test.c
```

If you're including a header, you still have to add the file(s) being called from the header:

main.c:
```
#include "header.h"

int main(void)
{
        add(2, 3);

        return 0;
}
```
header.h:
```
int add(int, int);
```
add.c:
```
int add(int a, int b)
{
        return a + b;
}
```

Would be compiled with:
```
gcc main.c add.c
```

You want to read up on [header files]("http://en.wikipedia.org/wiki/Header_file") and [include guards]("http://en.wikipedia.org/wiki/Include_guard").
Thanks for your guidance. While, I really don't like to have the add re-compiled again, so I may seek to use the dll instead.

---

