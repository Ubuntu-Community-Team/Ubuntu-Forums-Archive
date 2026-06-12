---
title: "[C] Memory deallocation question"
date: 2011-03-01
forum: Programming Talk
---

### Post by cguy on 2011-03-01
Given this code (ignore the fact that I didn't check if the allocations were successful):
[php]int *a = malloc(sizeof (int));
*a = 10;
	
int *b = malloc(sizeof (int));
*b = 20;
	
a=b;
	
printf("%p %d\n",a,*a);
	
free(a);[/php]


What happens with the space initially allocated to a? Will it be available for future allocations or does it stay "busy"?

---

### Post by foxmuldr on 2011-03-01
> **cguy said:**
> Given this code (ignore the fact that I didn't check if the allocations were successful):
[php]int *a = malloc(sizeof (int));
*a = 10;
	
int *b = malloc(sizeof (int));
*b = 20;
	
a=b;
	
printf("%p %d\n",a,*a);
	
free(a);[/php]


What happens with the space initially allocated to a? Will it be available for future allocations or does it stay "busy"?

It will remain there until the app closes and the OS reclaims everything that was allocated.  But in your app, since you've lost your pointer to it, it will be out in no-man's land inaccessible.

I've used debug functions in Windows which let you traverse the heap and reclaim it by the pointers returned there, but it's yucky, and I don't know if Linux supports the same functions.

- Rick C. Hodgin

---

### Post by gnusci on 2011-03-01
> **cguy said:**
> Given this code (ignore the fact that I didn't check if the allocations were successful):
[php]int *a = malloc(sizeof (int));
*a = 10;
	
int *b = malloc(sizeof (int));
*b = 20;
	
a=b;
	
printf("%p %d\n",a,*a);
	
free(a);[/php]


What happens with the space initially allocated to a? Will it be available for future allocations or does it stay "busy"?

free will release the block of memory pointed by **a**, thus the allocated memory will be then available for future allocation.

---

### Post by nvteighen on 2011-03-02
This may sound very silly, but it was very useful for me back then: when learning about pointers in general, think of them of a rope that you hold in your hand in one end and in the other it's bound to some value. When doing a = b, what you're doing is releasing your rope and tying it to the object also tied up by the rope 'b'.

---

### Post by cgroza on 2011-03-02
> **gnusci said:**
> free will release the block of memory pointed by **a**, thus the allocated memory will be then available for future allocation.
And this will render the b pointer invalid because the object it was pointing to does not exist anymore?

---

### Post by nvteighen on 2011-03-03
> **cgroza said:**
> And this will render the b pointer invalid because the object it was pointing to does not exist anymore?

Yes, because both were pointing to the same memory address.

---

### Post by Portmanteaufu on 2011-03-03
I've drawn some ASCII diagrams to illustrate what's happening at each point in the code.

> **cguy]
```

int *a = malloc(sizeof (int)) said:**
> 

```

[ ] <--- a

```

[QUOTE=cguy]
```

*a = 10;

```


```

[ 10 ] <--- a

```

> **cguy]
```

int *b = malloc(sizeof (int)) said:**
> 

```

[ 10 ] <--- a       [   ] <--- b

```

[QUOTE=cguy]
```

*b = 20;

```


```

[ 10 ] <--- a       [ 20 ] <--- b

```

> **cguy]
```

a=b said:**
> 

```

[ 10 ]      a --->  [ 20 ] <--- b

```

[QUOTE=cguy]
```

free(a);

```


```

[ 10 ]      a --->    NULL   <--- b

```

As you can see, the memory that 'a' once pointed to is still considered to be in use, but we have nothing pointing to it, so we can't use it.

Because 'a' now points to the memory pointed to by 'b', free()ing 'a' inherently free()s 'b' as well. Dereferencing either pointer at this point would cause a segmentation fault.

Hope that helps!

NOTE: free() doesn't cause 'a' or 'b' to *actually* point to NULL (0), but conceptually this is pretty accurate. 'a' will still point to a memory location, but dereferencing it would be as bad as dereferencing NULL itself.

---

### Post by stchman on 2011-03-03
Here is how I handle dynamic memory allocation.

[php]
// dynamically allocate an array of doubles with user_input being the number of elements
double *data = malloc( user_input * sizeof( double ) );

// free the memory
free( data );

[/php]

Once you execute the free command the memory is no longer available for future allocations.  Also if you don't execute the free command that memory can be tied up in the OS until something trounces over it.

---

### Post by NovaAesa on 2011-03-03
> **Portmanteaufu said:**
> 
NOTE: free() doesn't cause 'a' or 'b' to *actually* point to NULL (0), but conceptually this is pretty accurate. 'a' will still point to a memory location, but dereferencing it would be as bad as dereferencing NULL itself.

I would like to add that it's not "as bad as dereferencing NULL itself", it's actually worse. When you dereference a NULL pointer, you will ALWAYS get a segfault, however when you dereference a pointer to a free()ed block of memory, you may or may not get a segfault. It might work fine during the whole of development, and then break once deployed to your users.

---

### Post by foxmuldr on 2011-03-03
> **NovaAesa said:**
> I would like to add that it's not "as bad as dereferencing NULL itself", it's actually worse. When you dereference a NULL pointer, you will ALWAYS get a segfault, however when you dereference a pointer to a free()ed block of memory, you may or may not get a segfault. It might work fine during the whole of development, and then break once deployed to your users.

Absolutely, because if that memory area pointed to by the now invalid pointer, is re-allocated by another process, and is then valid to the process, then when you write to it you will not get an error, but it will overwrite other structures, data, class items, etc.

The method I use for undoing a pointer is like this:
```
free(x);
x = NULL;
```

That way it's always set to the invalid value.  Another way to do it is with a macro (or an inline) of this function:
```
void my_free(void* p)
{
    free(p);
    p = NULL;
}
```

And then in your code just call my_free(x) and it frees.

- Rick C. Hodgin

---

### Post by Arndt on 2011-03-04
> **foxmuldr said:**
> 

That way it's always set to the invalid value.  Another way to do it is with a macro (or an inline) of this function:
```
void my_free(void* p)
{
    free(p);
    p = NULL;
}
```

And then in your code just call my_free(x) and it frees.



In the function my_free, 'p' is local to the function, even if inline, so doing my_free(q) will not set q to NULL.

---

### Post by Arndt on 2011-03-04
> **NovaAesa said:**
> I would like to add that it's not "as bad as dereferencing NULL itself", it's actually worse. When you dereference a NULL pointer, you will ALWAYS get a segfault, however when you dereference a pointer to a free()ed block of memory, you may or may not get a segfault. It might work fine during the whole of development, and then break once deployed to your users.

Always, in practice, maybe, on Linux, today. But it has not always been that way, and it would surprise me if the C standard prescribes it. I remember that in some environment (not Linux), there was an option to the linker to make the lowest memory page unmapped, so that dereferencing NULL would fail. The default was not to do so.

This does not lessen the impact of your statement, of course.

---

### Post by trent.josephsen on 2011-03-04
The C standard does not so prescribe.  Dereferencing an uninitialized pointer and dereferencing 0 are both "undefined behavior".

(Standards pedant signing off.)

---

### Post by Portmanteaufu on 2011-03-04
> **NovaAesa said:**
> I would like to add that it's not "as bad as dereferencing NULL itself", it's actually worse. When you dereference a NULL pointer, you will ALWAYS get a segfault, however when you dereference a pointer to a free()ed block of memory, you may or may not get a segfault. It might work fine during the whole of development, and then break once deployed to your users.

Absolutely correct. Poorly worded on my part, good catch!

---

### Post by JupiterV2 on 2011-03-04
Freeing a block of memory without "nullifying" is what's called a dangling pointer. This is a [security issue]("http://en.wikipedia.org/wiki/Dangling_pointer").

While it is good practice to always nullify a pointer, it's not necessary when the pointer will immediately be unreferenced/collected as in the following example:

```

void myfun()
{
  int *i = malloc (sizeof (int));

  free(i); /* only do this if no more code follows */
}
```

This is because the variable has local scope and will be removed from the heap once the function is complete.

---

### Post by foxmuldr on 2011-03-04
> **Arndt said:**
> In the function my_free, 'p' is local to the function, even if inline, so doing my_free(q) will not set q to NULL.

Yes, it should be void **p, and then referenced as free(*p) and *p = NULL. My bad.

- Rick C. Hodgin

---

### Post by NovaAesa on 2011-03-04
> **Arndt said:**
> Always, in practice, maybe, on Linux, today. But it has not always been that way, and it would surprise me if the C standard prescribes it. I remember that in some environment (not Linux), there was an option to the linker to make the lowest memory page unmapped, so that dereferencing NULL would fail. The default was not to do so.

This does not lessen the impact of your statement, of course.

Interesting, you learn something new each day!

---

### Post by foxmuldr on 2011-03-05
> **NovaAesa said:**
> Interesting, you learn something new each day!

Here's something even more interesting I think. Back in the days of MS-DOS and real-mode programming, NULL pointers would dereference without a failure in access, meaning they would point to the location in memory beginning at 0 and any writes there would cause the whole system to become unstable and crash either sooner or later with an errant program (depending on how much data was attempted to write there, it could be immediately).

This was bad, but of course but it only took the OS about 2 seconds to reboot once it started loading from disk again, so during testing this wasn't as big a pain as it could have been.  Still an annoyance.

- Rick C. Hodgin

---

