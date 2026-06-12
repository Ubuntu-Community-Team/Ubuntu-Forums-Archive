---
title: "[SOLVED] Howto eliminate a C compiler warning"
date: 2008-03-22
forum: Programming Talk
---

### Post by quandary on 2008-03-22
Hi. Question:

The following little code:

```

static int PASSFLOAT(float x)
{
    float floatTemp;
    floatTemp = x;
    return *(int *) &floatTemp;
}

```

ui_syscalls.c:34: warning: dereferencing type-punned pointer will break strict-aliasing rules

line 34 is the return ... line

What do I have to change for this warning to get away?

---

### Post by ruy_lopez on 2008-03-22
> **quandary said:**
> 
What do I have to change for this warning to get away?

I've no idea what you're trying to do. Any particular reason you are trying to return a reference, and cast to a different type?

---

### Post by keratos on 2008-03-22
unless I'm very much mistaken, the floatTemp object will be derefenced on exit of the function because it is not static memory thus why are you returning a pointer to a heap object that will be derefenced thus meaningless.

what ARE you trying to do?

---

### Post by supirman on 2008-03-22
He's trying to convert the float to an int.  Have you guys never seen type casting before?

He gets the address of floatTemp, casts the resulting pointer to a pointer to an int, then dereferences that int pointer to get the integer value.  


To OP - newer versions of gcc do strict aliasing which causes this warning.  The compiler does additional optimizations when using strict-aliasing, and the example breaks the rules.  To suppress it, you could always compile with '-fno-strict-aliasing'.

---

### Post by ruy_lopez on 2008-03-22
> **supirman said:**
> He's trying to convert the float to an int.  Have you guys never seen type casting before?

No. When I mentioned type casting above it was a typo.

---

### Post by NiklasV on 2008-03-22
I assume you're trying to convert a float to an int?
floats are stored in a completely different manner than ints, you can't just cast a float pointer as an int pointer, dereference and expect it to work.
This is how floats are stored: [http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754)

---

### Post by keratos on 2008-03-22
> **supirman said:**
> He's trying to convert the float to an int.  Have you guys never seen type casting before?

He gets the address of floatTemp, casts the resulting pointer to a pointer to an int, then dereferences that int pointer to get the integer value.  


To OP - newer versions of gcc do strict aliasing which causes this warning.  The compiler does additional optimizations when using strict-aliasing, and the example breaks the rules.  To suppress it, you could always compile with '-fno-strict-aliasing'.

excuse me. we bloody well know what a type cast is.
the question was not relating to the typecast but to the purpose of the entire function.

Read the posts.

If he's trying to convert float to int then this is a nogo as correctly identified above and is a meaningless/erroneous function, that is why we were asking what he is trying to do .... there is logic in our questions!

---

### Post by supirman on 2008-03-22
> **keratos said:**
> excuse me. we bloody well know what a type cast is.
the question was not relating to the typecast but to the purpose of the entire function.

Read the posts.

If he's trying to convert float to int then this is a nogo as correctly identified above and is a meaningless/erroneous function, that is why we were asking what he is trying to do .... there is logic in our questions!


Your original post was off in the weeds.  He's not trying to return a pointer as you apparently thought.  Also, automatic allocation uses the stack, not the heap.  Finally, a local variable will be 'deallocated' on scope exit, not dereferenced.

---

### Post by Jessehk on 2008-03-22
I'm going to ignore all the previous arguing and make the (possibly wrong assumption) that this is all the OP wants:

```

static_cast<int>( floatingPointVar );

```

to replace the function.

EDIT: Oops, I thought this was a C++ question. If it's C, then this
```

(int)floatingPointVar

```

Should be all that's necessary.

---

### Post by POW R TOC H on 2008-03-22
See gcc manual for turning off warnings. If you want to turn aff all warnings (not recommended) compile with 
```

-w

```
Is that what you wanted to know?

---

### Post by ruy_lopez on 2008-03-22
> **Jessehk said:**
> 
```

(int)floatingPointVar

```


That would be my suggestion, too. 

Referencing a float, casting the float pointer to int pointer, then dereferencing - if it worked - would be a wacky way of casting (int) float. Don't get me wrong. I like wacky, when it works. This form of address jujitsu doesn't work. Maybe it should. Maybe we should start a campaign.

---

### Post by WW on 2008-03-22
quandary: I only get the warning if I specifically use the option **-fstrict-aliasing**.  I don't get the warning if I compile (using either gcc 4.0.1 on a Mac or gcc 4.1.3 in Ubuntu 7.10) with just **-Wall**.  The rest of this post you can ignore; it continues the wild speculation begun by your original post :)

As most of the posters probably realize, the original poster's code will not convert a float to an int, at least not in the way we usually want to do such a conversion.  What it *will* do is return an int that has the same binary representation as the float.  This may, in fact, be the intent of the original poster.  This could be used to pull apart the binary representation of the floating point number, as in the following example.  (In the following, I used unsigned instead of int.  The code assumes that floats and unsigneds are both 32 bits.)

fc.c
```

#include <stdio.h>

// Return an unsigned with the same binary pattern as x
static unsigned PASSFLOAT(float x)
{
unsigned *p;
p = (unsigned *) &x;
return *p;
}

//
//  binstr assumes an unsigned is 32 bits!
//  buf must be at least 33 characters
//
char *binstr(unsigned m, char *buf)
{
int k;
unsigned i = 1;

buf[32] = '\0';
for (k = 0; k < 32; ++k)
    {
    if (m & i)
        buf[31-k] = '1';
    else
        buf[31-k] = '0';
    i = i << 1;
    }
return buf;
}


int main(int argc,char *argv[])
{
float z;
unsigned k;
char buf[33];
int i;

z = -5.625;
k = PASSFLOAT(z);
printf("Floating point number is %f\n",z);
printf("Binary representation is %s\n",binstr(k,buf));
printf("Sign bit: %c\n",buf[0]);
printf("Exponent: ");
for (i = 1; i < 9; ++i)
    printf("%c",buf[i]);
printf("\n");
printf("Mantissa: ");
for (i = 9; i < 32; ++i)
    printf("%c",buf[i]);
printf("\n");

return 0;
}

```

Compile and run:
> 
$ gcc -Wall -fstrict-aliasing fc.c -o fc
fc.c: In function 'PASSFLOAT':
fc.c:7: warning: dereferencing type-punned pointer will break strict-aliasing rules
$ gcc -Wall fc.c -o fc     # NOTE: no warning
$ ./fc
Floating point number is -5.625000
Binary representation is 11000000101101000000000000000000
Sign bit: 1
Exponent: 10000001
Mantissa: 01101000000000000000000
$ 


---

### Post by slavik on 2008-03-22
Quake3 had a piece of code to find 1/sqrt(x) by converting a float pointer to an int pointer and shifting it one place to get cheap division by 2. Turned out that the function was linear instead of really really slow :P

---

### Post by quandary on 2008-03-31
Yes, it's a piece of code from the quake virtual machine.

I got it: you cannot convert directly, you must convert the address to unsigned long first:

static int PASSFLOAT(float x)
{
    float floatTemp ;
    floatTemp = x   ;
    return *(int*) ((unsigned long) &floatTemp) ;
}

---

