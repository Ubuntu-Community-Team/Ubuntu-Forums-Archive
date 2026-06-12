---
title: "Segmentation fault in very basic c program using pointers"
date: 2009-03-21
forum: Programming Talk
---

### Post by s_raghu20 on 2009-03-21
Hi,

while teaching basics of C to my sister, I wrote this program.
```

#include <stdio.h>
void main()
{  
   	int *p1,*p2,*p3;

	int a = 8;
	p1 = &a;
	*p2 = 5;
	printf("initial values = %d \n %d",*p1, *p2);
	*p3 = *p1 + *p2;
/*
printf("enter the value");

scanf("%d",p1);
p3 = *p1 + *p2;
*/
//printf("c = %d",*p3);

}

```

it compiles fine, but when I execute the output, it just says, "Segmentation fault" and terminates.

Any idea why ?

---

### Post by nvteighen on 2009-03-21
It's clear. You declare a pointer p2, but to an unknown place. Then, you try to access that place by using ***p2 = 5**... a place you don't know whether it is yours or even if it exists (you haven't allocated it for your program).

The same occurs with p3.

Also, use **int main(void)** and make it return an integer (usually 0). That way you'll have modern C code.

---

### Post by namaku0 on 2009-03-21
> Since a null-valued pointer does not refer to a meaningful object, an attempt to dereference a null pointer usually causes a run-time error. If this error is left unhandled, the program terminates immediately. In the case of C, execution halts with a segmentation fault because the literal address of NULL is never allocated to a running program.
[http://en.wikipedia.org/wiki/Pointer_(computing)#The_null_pointer](http://en.wikipedia.org/wiki/Pointer_(computing)#The_null_pointer)

---

### Post by Habbit on 2009-03-21
The problem should not be a NULL pointer, but an uninitialized pointer that thus can point anywhere in memory. These are even more dangerous because they are not guaranteed to fail (they could point to perfectly good memory if you happen to reuse a past, good activation record or are just unluck). Some compilers initialize local variables to default values  (0 for integers, NULL for pointers, 0.0 or NaN for floats, etc.) when in debug mode, but most do not.

---

### Post by Can+~ on 2009-03-21
> **s_raghu20 said:**
> Hi,

while teaching basics of C to my sister, I wrote this program.

You should finish learning yourself rather than start teaching others. The mistake is pretty obvious.

---

### Post by s_raghu20 on 2009-03-21
I guess 10 years of gap can result in something as basic as that.

Thanks for your replies, I rectified my basic error... :)

---

