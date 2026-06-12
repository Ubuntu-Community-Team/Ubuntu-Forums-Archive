---
title: "C language: recursive calling"
date: 2012-04-13
forum: Programming Talk
---

### Post by DaviesX on 2012-04-13
```

#include <stdio.h>

int Function ( int exit )
{
    return exit || Function ( 1 );
}

int main ( int argv, char *argc[] )
{
    Function ( 0 );
    return 0;
}

```
I don't understand the sample code, can you please explain to me about if the return value affects the recursive calling ? The code above would leave after it called itself once, but the following code will never exit, 
```

#include <stdio.h>

int Function ( int exit )
{
    return exit || Function ( 0 );
}

int main ( int argv, char *argc[] )
{
    Function ( 0 );
    return 0;
}

```

Can you tell me what is the cause ? You can even explain with assembly if necessary :-)

Thank you !

---

### Post by satsujinka on 2012-04-13
When using ||, if the first term is >0 then it won't evaluate the second term. So in 1 || somefunc(),  somefunc() will never execute because the first term is 1.

So...
Function(0) = 0 || Function(1)
Function(1) = 1

So by substitution Function(0) = 1.

Whereas in the second example || never encounters a value >0 so execution never stop.

---

### Post by DaviesX on 2012-04-14
Ok, I get it, thanks a lot !

So this one would never stop either, because Function ( 1 ) will be evaluated first, right ?
```

#include <stdio.h>

int Function ( int exit )
{
    return Function ( 1 ) || exit;
}

int main ( int argv, char *argc[] )
{
    Function ( 0 );
    return 0;
}

```

---

### Post by satsujinka on 2012-04-14
Run it and find out!;)

---

### Post by Bachstelze on 2012-04-14
> **satsujinka said:**
> Run it and find out!;)

It's actually not that simple. In theory this code should run indefinitely or crash with a stack overflow, but some compilers will do weird things with it...

---

### Post by DaviesX on 2012-04-14
Yeah, that code compiled by GCC will overflow as the stack used up :-)

---

### Post by satsujinka on 2012-04-14
@Bachstelze
on the contrary, it is exactly that simple. A basic part of learning code is predicting what will happen, and what better way then to run the code and find out.

in a other examples it might be the case that nothing would happen (a true infinite loop,) but C doesn't have tail call optimization so infinite recursive calls are equivalent to a crash (after an arbitrary number of calls.)

---

### Post by Barrucadu on 2012-04-14
> **satsujinka said:**
> in a other examples it might be the case that nothing would happen (a true infinite loop,) but C doesn't have tail call optimization so infinite recursive calls are equivalent to a crash (after an arbitrary number of calls.)

Except, GCC can do tail-call optimisation for you. Thus, the behaviour can be compiler-specific.

---

### Post by Zugzwang on 2012-04-14
> **satsujinka said:**
> ... but C doesn't have tail call optimization so infinite recursive calls are equivalent to a crash (after an arbitrary number of calls.)

A quick google search suggests that the GNU C compiler can perform tail-call optimization: [http://stackoverflow.com/questions/3514283/c-tail-call-optimization](http://stackoverflow.com/questions/3514283/c-tail-call-optimization) and [http://stackoverflow.com/questions/490324/how-do-i-check-if-gcc-is-performing-tail-recursion-optimization](http://stackoverflow.com/questions/490324/how-do-i-check-if-gcc-is-performing-tail-recursion-optimization) 

Thus, I'd like to second Bachstelze's post.

---

### Post by CptPicard on 2012-04-14
> **Bachstelze said:**
> It's actually not that simple. In theory this code should run indefinitely or crash with a stack overflow, but some compilers will do weird things with it...

In this case it really depends on how much the compiler actually peeks into the recursion and essentially inlines things. If it does, then it can short-circuit the ||, otherwise not.

---

### Post by satsujinka on 2012-04-14
> **Zugzwang said:**
> A quick google search suggests that the GNU C compiler can perform tail-call optimization: [http://stackoverflow.com/questions/3514283/c-tail-call-optimization](http://stackoverflow.com/questions/3514283/c-tail-call-optimization) and [http://stackoverflow.com/questions/490324/how-do-i-check-if-gcc-is-performing-tail-recursion-optimization](http://stackoverflow.com/questions/490324/how-do-i-check-if-gcc-is-performing-tail-recursion-optimization) 

Thus, I'd like to second Bachstelze's post.
Your links, however, support doing as I said and running it. Since aside from looking through the generated assembly (which is well out of the scope of this thread) the only way to find out what the above code does is to run it.

On a more nit-picky note, while GCC is probably what's being used here... there are other compilers. And it is the case that none of the C specs state that there should be tail-call optimization. Which means simply that you shouldn't expect it to be there.

---

### Post by Barrucadu on 2012-04-15
We're not expecting it to be there, we're just saying that it's not as simple as looking at the code in all cases. Behaviour can be compiler-dependent.

---

### Post by DaviesX on 2012-04-15
Ok, I get it. Thanks you guys.
So, different compilers might perform different results even if I use the same code which is not that standardized, isn't it ?

---

