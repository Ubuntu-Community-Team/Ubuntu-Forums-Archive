---
title: "behaviour of &quot;unsigned&quot; in C programming"
date: 2011-01-07
forum: Programming Talk
---

### Post by vksingh on 2011-01-07
Hi,

#include<stdio.h>

[B]
int main()
{
        int x=5;
        x=(unsigned)-1;
        printf("x=%d",x);

}
[/B]
In the above program, the output is -1. Can some body tell, how?


But, in the following program,

#include<stdio.h>


[B]int main()
{
        int x=5;
       
        printf("x=%d",unsigned);

}
                              
[/B]
The output is error. Can some body tell why it is an error?


Thanks,

Vivek
                                                 
~

---

### Post by worksofcraft on 2011-01-07
> **vksingh said:**
> Hi,

#include<stdio.h>

[B]
int main()
{
        int x=5;
        x=(unsigned)-1;
        printf("x=%d",x);

}
[/B]
In the above program, the output is -1. Can some body tell, how?


Yes, you used %d in your format so that tells printf runtime library to format the value as a signed decimal quantity. Use %u for unsigned... remember printf is NOT checking **actual** parameter types: *what you **ask for** is what you get* ;)

> **vksingh said:**
> 
But, in the following program,

#include<stdio.h>


[B]int main()
{
        int x=5;
       
        printf("x=%d",unsigned);

}
                              
[/B]
The output is error. Can some body tell why it is an error?


Thanks,

Vivek
                                                 
~
Well you do need to supply some kind of value to print. "unsigned" isn't a value so the poor thing doesn't know what to do :shock:


p.s. you can run this to see what I mean:
[php]
#include <cstdio>
int main() {
	return !printf("-1 = %u\n", -1);
}
[/php]
... -1 = 4294967295
;)

---

### Post by nvteighen on 2011-01-08
Oh my...

Signed data types (which are the default case) allow representation of negative values at the cost of halving the maximum value the data type can hold. For example, a signed char allows any value in the interval [-127, 127], while an unsigned char allows any value in the interval [0, 255].

Now, this can be a bit confusing: unsigned is a type qualifier, not a type... But a type qualifier added to a type creates a new type, different to the original type. But, in C some type qualifiers can be used without stating the type, because int is used as "default". If you declare a variable as a long, you actually are declaring a long int. The same for unsigned: if you declare something as unsigned, it actually is an unsigned int.

This explains why your first code outputs -1. What you're doing there is declaring x as a signed int. Then you cast -1 to an unsigned int, something that yields the value max_uint - 1, where max_uint is the maximum unsigned int value for your architecture (it's not the same in 32-bit and 64-bit). But you try to save that value back into x, which is a signed int, therefore max_uint - 1 is casted back to signed int, yielding -1 again.

What I mean is that unsigned isn't a function and that its effects are a bit tricky. If you want to take the absolute value of an integer variable, you should use abs() from stdlib.h.

Now that you know what unsigned is, you'll probably understand why your second code doesn't even compile.

---

