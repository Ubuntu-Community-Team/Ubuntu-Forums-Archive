---
title: "C: Printing Address of variable"
date: 2006-12-10
forum: Programming Talk
---

### Post by akudewan on 2006-12-10
Hi,

I'm writing a small program to print the address of a variable. From what I have learned, the address assigned to a variable is an unsigned integer, so to print the address, I'm writing the following code:

```

#include<stdio.h>
int main()
{
	int x=10;
	printf("\n The address of x is %u ",&x);
	return 0;
}


```

This works flawlessly in Turbo C, which we use in college. But I use gcc at home (since Turbo C is ancient, and I love ubuntu), and it gives me this warning:
```

akudewan@ranjan404:~/c $ gcc -Wall -o ./temp ./temp.c
./temp.c: In function ‘main’:
./temp.c:5: warning: format ‘%u’ expects type ‘unsigned int’, but argument 2 has type ‘int *’
akudewan@ranjan404:~/c $ ./temp

 The address of x is 3215712688

```

It seems to print the address allright, but whats the meaning of this warning ?

---

### Post by duff on 2006-12-10
just use %p instead of %u

---

### Post by lloyd_b on 2006-12-10
> This works flawlessly in Turbo C, which we use in college. But I use gcc at home (since Turbo C is ancient, and I love ubuntu), and it gives me this warning:

```
akudewan@ranjan404:~/c $ gcc -Wall -o ./temp ./temp.c 
./temp.c: In function ‘main’: 
./temp.c:5: warning: format ‘%u’ expects type ‘unsigned int’, but argument 2 has type ‘int *’ 

akudewan@ranjan404:~/c $ ./temp The address of x is 3215712688
```

It seems to print the address allright, but whats the meaning of this warning ?

In Turbo C (and most older C compilers), a pointer is *always* the same size as an "int".  With newer C compilers (running on newer processors), this isn't necessarily so.  For instance, on some 64 bit processors, ints are 32 bits, but pointers are 64 bits.

The warning is just an advisory that you specified an integer data type (via the %u), but what you supplied was a pointer.  On that machine, it apparently makes no difference, but on a different system you may get different results.

You can easily eliminate the warning with a cast:

```
printf("\n The address of x is %u ", (int) &x);
```

But be advised - if you're running in an environment where ints and pointers are different sizes, the printf statement may not accurately print the address - it's like casting an int to a char - something has to be discarded to make it fit.

Lloyd B.

---

### Post by akudewan on 2006-12-11
thanks for the replies :)

Edit: Is there a list of standard library functions, datatypes etc. that I can get for gcc? I tried man gcc, but it doesn't have that kind of info.

Thanks again.

---

### Post by slavik on 2006-12-11
[http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/sr=8-1/qid=1165843806/ref=pd_bbs_1/103-2299422-8673425?ie=UTF8&s=books](http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/sr=8-1/qid=1165843806/ref=pd_bbs_1/103-2299422-8673425?ie=UTF8&s=books)

C says that char must be 8bits (1 byte) and that int must be at least as big.

adresses are of type 'size_t' I believe ... do sizeof(size_t); and sizeof(int); and let us know what you get.

---

### Post by akudewan on 2006-12-17
Here's what I got:

```

 size of size_t: 4
 size of int: 4

```

I also got a good resource for gcc: [http://www.gnu.org/software/libc/manual/html_node/index.html](http://www.gnu.org/software/libc/manual/html_node/index.html)

Thanks!

---

### Post by kabch on 2010-03-20
I know the thread is out of date, but someone eventually will find it helpful.

As stated above the size_t can differ on different platforms. To avoid that problem, you can make an explicit type casting to an unsigned long.

```

printf("Some string: Address of var a=%lu\n", (unsigned long) &a);

```

This is also lint safe. It is always a good idea to check the source *.c file with a static code analyzer. The program **splint** (aptitude install splint , splint myFile.c) is a very helpful program.

Also note, that the **printf** function is not always secure. Please also consider snprintf, sprintf, asprintf and g_strdup_printf as secure alternatives.

---

### Post by Compyx on 2010-03-20
> **kabch said:**
> I know the thread is out of date, but someone eventually will find it helpful.

As stated above the size_t can differ on different platforms. To avoid that problem, you can make an explicit type casting to an unsigned long.


Correct.

```

printf("Some string: Address of var a=%lu\n", (unsigned long) &a);

```

Incorrect. By using the address-of operator on an object, you get a pointer to that object, the correct way to use this pointer in printf and friends is (as stated in a previous reply) with '%p' while casting the pointer to void*:
```

printf("Some string: Address of var a=%p\n", (void*)(&a));

```

Also note that the name 'address' is misleading, the C standard makes no guarantees that a pointer contains a physical address, it may have other information stored in it, padding bits, whatever.

---

### Post by MadCow108 on 2010-03-20
> **kabch said:**
> I know the thread is out of date, but someone eventually will find it helpful.

As stated above the size_t can differ on different platforms. To avoid that problem, you can make an explicit type casting to an unsigned long.

```

printf("Some string: Address of var a=%lu\n", (unsigned long) &a);

```

This is also lint safe. It is always a good idea to check the source *.c file with a static code analyzer. The program **splint** (aptitude install splint , splint myFile.c) is a very helpful program.

Also note, that the **printf** function is not always secure. Please also consider snprintf, sprintf, asprintf and g_strdup_printf as secure alternatives.

if you dig out old threads at least provide correct information...
unsigned long is not guaranteed to have the right size on all platforms

to print pointer portably in a format other than hex you need the C99 header inttypes.h and its weird macros.
[http://linux.die.net/man/3/prixptr](http://linux.die.net/man/3/prixptr)

```

#include <inttypes.h>
printf("%"PRIuPTR"\n", (uintptr_t)&a); // decimal
printf("%"PRIoPTR"\n", (uintptr_t)&a); // octal
printf("%"PRIxPTR"\n", (uintptr_t)&a); // hex
printf("%p\n", &a); // hex, should also be possible in C89

```

---

