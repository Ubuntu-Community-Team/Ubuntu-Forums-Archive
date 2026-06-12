---
title: "[C] Memory operations with chars"
date: 2011-02-23
forum: Programming Talk
---

### Post by cguy on 2011-02-23
[php]#include <stdio.h>
#include <string.h>

int main()
{
	char my_string[] = "hello world!";
	
	printf("%s %lu\n", my_string, strlen(my_string));
	*(my_string + 4) = '\0';
	printf("%s %lu\n", my_string, strlen(my_string));
	
	return 0;
}
[/php]

I reduced my_string's length from 12 down to 4 by inserting a NULL character in the 5th position.
The memory that the removed characters (in the 5th, 6th...12th) occupied is now considered to be free, right?


Then I wanted to make my_string bigger, so I replaced the ending NULL with another character and 'moved' NULL one byte further from my_string[0].
But alas, it produces errors at runtime! Is this the kernel at work protecting against buffer overflows?




And third:
this declaration ```
char my_string[] = "hello world!";
``` allows this operation: ```
*(my_string + 3) = 'a';
```but this declaration ```
char *my_string = "hello world!";
``` does not. Why?

---

### Post by MadCow108 on 2011-02-23
> **cguy said:**
> [php]

I reduced my_string's length from 12 down to 4 by inserting a NULL character in the 5th position.
The memory that the removed characters (in the 5th, 6th...12th) occupied is now considered to be free, right?

no
in fact this memory is on the so called stack so it will only be freed when it goes out of scope (the return 0; in this case), it cannot be grown or increased at any other time.

for more flexible memory you must use the heap with malloc
(google stack, heap for more information and see the man page of malloc)

> 
Then I wanted to make my_string bigger, so I replaced the ending NULL with another character and 'moved' NULL one byte further from my_string[0].
But alas, it produces errors at runtime! Is this the kernel at work protecting against buffer overflows?

yes you then have a buffer overflow.
C is very low level, you need to tell the computer almost everything you want it to do.
To grow memory you must reallocate it with realloc (but that only works with heap memory allocated with malloc, and **not** in your example)

example for using the heap
```

#include <stdio.h> 
#include <stdlib.h>
#include <string.h> 

int main() 
{ 
    // allocate 50 bytes of memory, save pointer to it
    char *my_string = malloc(sizeof(char)*50);

    // check if allocation succeded
    if (my_string == NULL)
      return 1;

    // copy string into the memory
    strcpy(my_string, "hello world");

    printf("%s %zu\n", my_string, strlen(my_string)); 
    *(my_string + 4) = '\0'; 
    printf("%s %zu\n", my_string, strlen(my_string));

    // shrink memory to 30 byte
    my_string = realloc(my_string, 30);

    // check if reallocation succeded
    if (my_string == NULL)
      return 1;

    // content is still the same when it fits into the 30 bytes, else its truncated
    printf("%s %zu\n", my_string, strlen(my_string)); 

    // free the memory
    free(my_string)
    return 0; 
} 

```

> 
And third:
this declaration ```
char my_string[] = "hello world!";
``` allows this operation: ```
*(my_string + 3) = 'a';
```but this declaration ```
char *my_string = "hello world!";
``` does not. Why?

the last should be const char *my_string. The compiler tells you this when you compile with -Wall
And you can't modify a constant string.
this string is actually allocated at process startup in a read only memory section, any attempt to modify it results in a segmentation fault.
It only gets deleted when the process ends. You have no further control over it.

the first case is again stack memory which can be modified.

minor note:
strlen returns a size_t type which can have different sizes depending on the system. to print it you use %zu not %lu

---

### Post by nvteighen on 2011-02-23
C doesn't allow you to resize anything declared in the stack, because those elements are fixed and their size is known at compile-time. For creating dynamic elements, you need malloc()... these can be resized, but you have to deal with manual memory management. Take a look on this: [http://www.crasseux.com/books/ctutorial/Memory-allocation.html](http://www.crasseux.com/books/ctutorial/Memory-allocation.html)

Then, there's a difference between using pointer- or array-notation when declaring C strings. If you use pointer-notation, what you're saying is that you want a constant string created somewhere and that you want a pointer to it... so, trying to modify the strings fires a segfault up. Using array-notation, instead, creates what you want: an array of characters that's interpreted as a NULL-terminated string.

---

### Post by foxmuldr on 2011-02-24
> **cguy said:**
> [php]#include <stdio.h>
#include <string.h>

int main()
{
	char my_string[] = "hello world!";
	
	printf("%s %lu\n", my_string, strlen(my_string));
	*(my_string + 4) = '\0';
	printf("%s %lu\n", my_string, strlen(my_string));
	
	return 0;
}
[/php]

I reduced my_string's length from 12 down to 4 by inserting a NULL character in the 5th position.
The memory that the removed characters (in the 5th, 6th...12th) occupied is now considered to be free, right?


Yes, it is free, but only up to the originally allocated size, which in this case is 12 letters plus the NULL.

That memory there can be used for any purpose. The memory is allocated on the local stack within that function, and will be accessible for any purpose. You could use the data there at the 5th through 12th position for anything else.


> **cguy said:**
> Then I wanted to make my_string bigger, so I replaced the ending NULL with another character and 'moved' NULL one byte further from my_string[0].
But alas, it produces errors at runtime! Is this the kernel at work protecting against buffer overflows?

Your string CANNOT be bigger than was originally declared. It can only be up to that initial size.

The compiler in debug mode inserts lots of runtime checks to look for this condition, which is called a stack overrun, meaning some data access took place outside of the defined variable's space.

Hope this helps.

---

### Post by trent.josephsen on 2011-02-24
> **foxmuldr said:**
> Yes, it is free, but only up to the originally allocated size, which in this case is 12 letters plus the NULL.
This doesn't match any conventional definition of "free".

---

### Post by foxmuldr on 2011-02-25
> **trent.josephsen said:**
> This doesn't match any conventional definition of "free".

Not sure how you conclude that. When the NULL is there in a character string, the originally allocated characters beyond that NULL are unused, and will remain unused until the NULL is moved.  Those bytes are exactly that: free.

---

### Post by Arndt on 2011-02-25
> **foxmuldr said:**
> Not sure how you conclude that. When the NULL is there in a character string, the originally allocated characters beyond that NULL are unused, and will remain unused until the NULL is moved.  Those bytes are exactly that: free.

Yes, they are free to use for other purposes, as long as you keep track of whether that memory is available to your process.

But,

free memory usually means memory which is not allocated by the program. The 'free' function, for example, frees earlier allocated memory in that sense: gives it back to the runtime system, so it is no longer available but can be made available again if requested.

As long as you (and everyone else involved) are aware of the two separate distinctions: free vs. used, and free vs. allocated, there won't be trouble.

---

### Post by foxmuldr on 2011-02-25
> **Arndt said:**
> free memory usually means memory which is not allocated by the program. The 'free' function, for example, frees earlier allocated memory in that sense: gives it back to the runtime system, so it is no longer available but can be made available again if requested.

As long as you (and everyone else involved) are aware of the two separate distinctions: free vs. used, and free vs. allocated, there won't be trouble.

You're talking about C-level semantics. The memory is free by any definition, except those related to the malloc() family / free() function call sets.

This is the difference between having a toolset understanding of something, and understanding the underlying philosophy of what makes something work, how it works, why it works, and when you can do whatever you need to with it.

In any event, it's certainly not free by the free() standard.  But by the ability to use it ... it's wholly free.

- Rick C. Hodgin

---

### Post by nvteighen on 2011-02-26
> **foxmuldr said:**
> You're talking about C-level semantics. The memory is free by any definition, except those related to the malloc() family / free() function call sets.

This is the difference between having a toolset understanding of something, and understanding the underlying philosophy of what makes something work, how it works, why it works, and when you can do whatever you need to with it.

In any event, it's certainly not free by the free() standard.  But by the ability to use it ... it's wholly free.

- Rick C. Hodgin

Free memory just means memory that isn't allocated by the OS and therefore, any program that grabs it first can use it. This is only really applicable to dynamic memory, though, because the stack is always preallocated to a predefined size (ulimit -s).

---

### Post by Arndt on 2011-02-26
> **foxmuldr said:**
> You're talking about C-level semantics. The memory is free by any definition, except those related to the malloc() family / free() function call sets.

This is the difference between having a toolset understanding of something, and understanding the underlying philosophy of what makes something work, how it works, why it works, and when you can do whatever you need to with it.



C-level semantics is what the whole thread is about.

Are we to understand that you are the one who has this wonderful grasp of the world, and the rest of us have no idea of what really happens inside the computer?

Your little rambling, quite beautiful in itself, may be appropriate in some time and space, but this was not the right situation for it.

---

### Post by trent.josephsen on 2011-02-26
@Arndt

I neglected to thank you for your previous post.  Please allow me to thank you twice this time.

---

### Post by foxmuldr on 2011-03-01
> **Arndt said:**
> C-level semantics is what the whole thread is about.

Are we to understand that you are the one who has this wonderful grasp of the world, and the rest of us have no idea of what really happens inside the computer?

Your little rambling, quite beautiful in itself, may be appropriate in some time and space, but this was not the right situation for it.

As I read it, the OP indicated was trying to access that memory, so the context went beyond C-level semantics. Perhaps I was wrong in that.

- Rick C. Hodgin

---

