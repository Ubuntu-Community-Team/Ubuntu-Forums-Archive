---
title: "cos() function not working on gcc (C language)"
date: 2010-04-02
forum: Programming Talk
---

### Post by cirobr on 2010-04-02
Hello,

I have a simple program in C as follows that is compiled and executed as predicted:

```
#include <stdio.h>
#include <math.h>

main()
{
float i=3.14,j;
	j = cos(3.14);
	printf("%f %f \n", i, j);
}

```

However, when I change the argument in cos() to a variable, compilation fails. For instance:

```
#include <stdio.h>
#include <math.h>

main()
{
float i=3.14,j;
	j = cos(i);
	printf("%f %f \n", i, j);
}

```

And the error message is:

> collect2: ld returned 1 exit status

GCC runs on Ubuntu Karmic, all updates installed.

Any help on this is appreciated.

Thanks.

---

### Post by Ancanus on 2010-04-02
Try this:
[http://ubuntuforums.org/showpost.php?p=9065184&postcount=3](http://ubuntuforums.org/showpost.php?p=9065184&postcount=3)

:D

---

### Post by sisco311 on 2010-04-02
The error you get is that the linker cannot link in the mathematical functions in the final executable.

```
gcc -lm filemane.c
```

The "-lm" option means to link in the library with the mathematical functions (lib**m**.a).

[http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html)

---

### Post by cirobr on 2010-04-02
It works. Thanks.

---

### Post by sisco311 on 2010-04-02
You're welcome!

Please mark this thread as [SOLVED]: at the top of the page, click the [COLOR="Red"]Thread Tools[/COLOR] Menu and then "Mark this thread as Solved".

Thanks.

---

### Post by Cracauer on 2010-04-02
The reason why the first example works (although it should have been rejected based on indentation :)) is that the compiler will actually evaluate the whole expression at compile time.

One more thing: when quoting the error messages, don't give just the last line. The actual error message that would have been useful was there but you didn't quote it.

---

### Post by sisco311 on 2010-04-02
> **cracauer said:**
> the reason why the first example works (although it should have been rejected based on indentation :)) is that the compiler will actually evaluate the whole expression at compile time.

+1


> **cracauer said:**
> 
one more thing: When quoting the error messages, don't give just the last line. The actual error message that would have been useful was there but you didn't quote it.

++1

---

### Post by cirobr on 2010-04-02
> **Cracauer said:**
> The reason why the first example works (although it should have been rejected based on indentation :)) is that the compiler will actually evaluate the whole expression at compile time.

One more thing: when quoting the error messages, don't give just the last line. The actual error message that would have been useful was there but you didn't quote it.

There has not been any further error message than the one mentioned.

---

### Post by sisco311 on 2010-04-02
preceding error messages are valuable too...
```
sisco@acme:~$ gcc  1.c 
/tmp/cc82U5r4.o: In function `main':
1.c:(.text+0x19): undefined reference to `cos'
collect2: ld returned 1 exit status

```

The more we know, the better we can help!

---

