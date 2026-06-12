---
title: "C; my attempts to free memory fail."
date: 2010-01-12
forum: Programming Talk
---

### Post by Senesence on 2010-01-12
I program predominantly in Python, so forgive my ignorance if this is something that should be immediately obvious to a C programmer.

I have the following files:

**vector.h**
[PHP]
#ifndef VECTOR_H_GUARD
#define VECTOR_H_GUARD

typedef struct vector_t *vector;
vector vector_new(float x, float y);
void vector_delete(vector this);

#endif
[/PHP]

**vector.c**
[PHP]
#include <stdlib.h>
#include "vector.h"

struct vector_t
{
    float x,y;
};

vector vector_new(float x, float y)
{
    vector new_vector = (vector)malloc(sizeof(struct vector_t));
    new_vector->x = x;
    new_vector->y = y;

    return new_vector;
}

void vector_delete(vector this)
{
    free(this);
}
[/PHP]

**main.c**
[PHP]
#include <stdio.h>
#include <stdlib.h>
#include "vector.h"

main()
{
    int elements = 10000000;
    vector *container = (vector*)malloc(sizeof(vector)*elements);
    printf("Allocated\n");
    getchar();

    int i;
    for (i = 0; i < elements; i++)
    {
        container[i] = vector_new(64,64);
    }
    printf("Memory initialized\n");
    getchar();

    for(i = 0; i < elements; i++)
    {
        vector_delete(container[i]);
    }
    free(container);
    printf("Freed (supposed to be)\n");
    getchar();
}
[/PHP]

When memory initializes, I observe the expected spike in memory usage, so I assume that the allocation/initialization was indeed successful.

The de-allocation loop that uses "vector_delete(container[i])" doesn't seem to free memory, though. I know this, because memory usage remains unchanged; if it was released properly, memory usage should return to its original (lower) levels.

I receive neither compile-time, or run-time errors.

So, what am I missing here?

---

### Post by SledgeHammer_999 on 2010-01-12
The C runtime(?) doesn't **immediately** free all the space that was allocated to you. It holds some of it in case you need to allocate more memory in the future. This happens for speed reasons. I think there's an environment variable you can set that makes the runtime release the memory immediately. Sorry, I don't remember details. (and I didn't check the validity of your code).

---

### Post by nvteighen on 2010-01-12
Several issues. Compiling with the -Wall flag raises warnings you should take care of.

1) **Never** write "main()". The only two correct ways of declaring main() are: 1) **int main(void)** 2) **int main(int, char **)** (for getting the command line arguments. Of course, you see that both require main to return an integer, 0 when no error occurs and something else when it does.

2) **vector new_vector = (vector)malloc(sizeof(vector_t));** is wrong. When referring to a struct type, you always have to write the "struct" keyword too: **vector new_vector = (vector)malloc(sizeof(struct vector_t));**

3) In main.c you fail to free the memory of container. You know "1 free per 1 malloc"... The malloc() if vector_new() is correspondent to the free() in vector_delete()... but the malloc() in main.c has no counterpart.

4) You honestly don't need such a high number of elements to prove anything. Learn how to use valgrind, a powerful memory checker (in order to use it, it's best to compile your code with debugging symbols by using the -g flag).

---

### Post by MadCow108 on 2010-01-12
you can use the typedef in the sizeof to save the struct keyword if you like

but if you typedef pointers give them a name which includes pointer somehow, like vector_ptr
otherwise you really confuse the readers

---

### Post by Senesence on 2010-01-12
> **SledgeHammer_999 said:**
> The C runtime(?) doesn't **immediately** free all the space that was allocated to you. It holds some of it in case you need to allocate more memory in the future. This happens for speed reasons. I think there's an environment variable you can set that makes the runtime release the memory immediately. Sorry, I don't remember details. (and I didn't check the validity of your code).

I suspected that was the case, but then I ran the following test:

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

main()
{
	printf("Press enter to allocate space.");
	getchar();
	
	char *storage = (char*)malloc(sizeof(char)*100000000);
	memset(storage, 0, sizeof(char)*100000000);

	printf("Press enter to deallocate space.");
	getchar();

	free(storage);

	printf("Press enter to end program");
	getchar();
}
[/PHP]

And after free(storage) memory usage returns to it's original levels.

So, how do you explain that?

> **nvteighen]Several issues. Compiling with the -Wall flag raises warnings you should take care of.

1) Never write "main()". The only two correct ways of declaring main() are: 1) int main(void) 2) int main(int, char **) (for getting the command line arguments. Of course, you see that both require main to return an integer, 0 when no error occurs and something else when it does.[/quote]

Actually, I compiled with the -Werror flag, and I was alerted about the value that main should return.

The reason I've written main as I did is simply because that's how I've seen it written in K&R (C Book), and I thought that looked "cooler" than the current standard. In either case, it compiles fine, and I don't think it causes any unforeseen side-effects (return type defaults to ‘int’ said:**
> 2) vector new_vector = (vector)malloc(sizeof(vector_t)); is wrong. When referring to a struct type, you always have to write the "struct" keyword too: vector new_vector = (vector)malloc(sizeof(struct vector_t));

Ahh, yea. I should have just copy-pasted my code (where the struct was included), but for some reason I had to re-type it all. :)

* fixed

> 3) In main.c you fail to free the memory of container. You know "1 free per 1 malloc"... The malloc() if vector_new() is correspondent to the free() in vector_delete()... but the malloc() in main.c has no counterpart.

Yea, but doing: **free(container)**, right after the vector_delete(container[i]) loop doesn't change the situation. Memory usage is still in spiked state.

> 4) You honestly don't need such a high number of elements to prove anything. Learn how to use valgrind, a powerful memory checker (in order to use it, it's best to compile your code with debugging symbols by using the -g flag).

Thanks, I'll look into it.

Although, for now, my current method is effective enough.

---

### Post by MadCow108 on 2010-01-12
[http://www.gnu.org/s/libc/manual/html_node/Freeing-after-Malloc.html#Freeing-after-Malloc](http://www.gnu.org/s/libc/manual/html_node/Freeing-after-Malloc.html#Freeing-after-Malloc)

> 
Occasionally, free can actually return memory to the operating system and make the process smaller. Usually, all it can do is allow a later call to malloc to reuse the space. In the meantime, the space remains in your program as part of a free-list used internally by malloc.


this sounds that if you really want to free the memory immediately you'll have to use a different allocator

---

### Post by Senesence on 2010-01-12
> **MadCow108 said:**
> this sounds that if you really want to free the memory immediately you'll have to use a different allocator

The example in my previous post uses free(), just like the example in my original post, but the results are different (in one example the memory lingers, while in the other it's released immediately).

So, that doesn't seem to be true (at least generally).

---

### Post by Habbit on 2010-01-12
Note that free() _can_ return memory to the system, but doesn't have to. It's very possible that the implementation of malloc/free in glibc only returns memory to the system if you free a particularly large chunk. This difference could be the culprit, as you are allocating 1E7 vectors, which, at a presumable size of 8 bytes each (2x32 bit floats), makes 80M (_decimal_ M). OTOH, you allocate 1E8 chars, for a total of 100M. Maybe that difference crosses the free() threshold.

However, as MadCow said, you'd need to use another (non ANSI C standard) allocator if you wish to _guarantee_ the immediate return of memory to the system. I don't know if POSIX/SUS offers such facilities, or you'd have to use Linux-specific calls directly.

---

### Post by Senesence on 2010-01-12
> **Habbit said:**
> Note that free() _can_ return memory to the system, but doesn't have to. It's very possible that the implementation of malloc/free in glibc only returns memory to the system if you free a particularly large chunk. This difference could be the culprit, as you are allocating 1E7 vectors, which, at a presumable size of 8 bytes each (2x32 bit floats), makes 80M (_decimal_ M). OTOH, you allocate 1E8 chars, for a total of 100M. Maybe that difference crosses the free() threshold.

I ran a test with 40 million elements, as opposed to 10, so, 40 million, times 8, gives 320 million, which is well over a 100.

The result was virtually unchanged, so apparently it's not a "threshold" issue.

> However, as MadCow said, you'd need to use another (non ANSI C standard) allocator if you wish to _guarantee_ the immediate return of memory to the system. I don't know if POSIX/SUS offers such facilities, or you'd have to use Linux-specific calls directly.

Ok, I'll look into that, too.

But, just to confirm: Is the code in my original post (the parts that allocate, initialize, and free memory) correct?

---

### Post by nvteighen on 2010-01-13
> **Senesence said:**
> 
But, just to confirm: Is the code in my original post (the parts that allocate, initialize, and free memory) correct?

No. You still have the main() wrongly written, which means undefined behaivor on the program's exit. Ok, yes... GCC will handle it for you... or maybe kernel will... The thing is that you're assuming the system will fix it for you instead of fixing it yourself. Actually, GCC's behaivor here comes from a what the C++ standard asks to a C++ compiler...

And similarly, you are also assuming the system will have enough memory. You always should compare the pointer returned from malloc() against NULL; NULL will be returned when something is going wrong... and will protect you against several issues.

Both of these can be summarized into: If someone defined an interface, use it completely as designed.

---

### Post by cliddell on 2010-01-13
There are two ways that the glibc will allocate memory in non-threadsafe code. The first is used for "small" blocks of memory and uses the traditional brk()/sbrk() functions (see [http://opengroup.org/onlinepubs/007908775/xsh/brk.html](http://opengroup.org/onlinepubs/007908775/xsh/brk.html)). The second is used for "large" blocks and is mmap().

All memory allocated to the process through brk()/sbrk() is allocated in a contiguous block from the "bottom" of the process memory address space upwards. Because it is (and must be) contiguous, memory can only be freed back to the OS if it is at the top of the contiguous area (in other words, the contiguous address space can grow and shrink, but never fragment).

Thus if you allocated a number of small blocks of memory then immediately free them, there's a good chance it will be released back to the OS, and the process memory will shrink. On the other hand, if you allocate a large number of small blocks of memory, and then do something which might also allocate small blocks of memory (for example, getchar(), printf() etc etc), then release your small blocks, they may or may not be freed back to the OS - depending on how the intervening activities have affected memory use.

In particular, printf() and getchar() are buffered IO calls, thus calling them can affect the memory used in the IO buffers, which I would expect to be "small" blocks.

Larger blocks are allocated through mmap() which, on Linux, at least, allocates memory from the top of the process address space downwards, and is not required to be contiguous. Thus munmap() can return memory to the OS immediately, without worrying about leaving the top part of the process address space with "holes" in it.


I believe this would the difference in behaviour you see.

IIRC, compiling with gcc's -pthread option causes all, or almost all, memory allocations to be done via mmap()/munmap(), so that may produce the behaviour you expect - but that's from memory, as it were! This is because brk()/sbrk() predate threads by a *long* way, and are far from being thread safe.

HTH,

Chris

---

### Post by JSeymour on 2010-01-13
> **Senesence said:**
> The reason I've written main as I did is simply because that's how I've seen it written in K&R (C Book), ...
**Which** "K&R?"  The 1st Edition is obsolete and has *been* obsolete since ANSI C was ratified in 1989.  I can't lay my hands on a 2nd Ed., right now, but since it's ANSI C, I can't imagine K&R actually suggested one declare main() like that.

> **Senesence said:**
> ...and I thought that looked "cooler" than the current standard.
Oh yeah, "looks cooler" is a *great* reason to purposefully write bad code :rolleyes:

Sorry for the sarcasm, but "looks cooler" most definitely has no place in software design and coding.

> **Senesence said:**
> In either case, it compiles fine, ...
You know what the neat thing about C is?  It'll give you all the rope you ask for.  Just don't blame the language when you hang yourself.

Other than main() being improperly defined...

You're not checking the return from malloc().  Bad habit.  Can't count the number of times I've had to fix code for talented (or so they believed themselves) software designers and programmers that habitually coded like that.

Style nit: It is unclear that "vector" is actually "pointer to type struct vector_t."  Furthermore the struct definition belongs in vector.h.  Better to do it this way, IMO:
```

vector.h

[COLOR=#000000][COLOR=#0000bb]typedef struct vector_t
[/COLOR][COLOR=#007700]{
    [/COLOR][COLOR=#0000bb]float x[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]y[/COLOR][COLOR=#007700];
} vector;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]
[/COLOR][COLOR=#0000bb]vector *vector_new[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]float x[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]float y[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]void vector_delete[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]vector **this[/COLOR][COLOR=#007700]);
[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700]

That way it's lucidly clear throughout exactly what you have everywhere.

The reason you pass a pointer-to-a-pointer to vector_delete() is so you
can set the pointer to NULL after the free(), so there's no doubt
elsewhere  in the code that it's no longer an invalid pointer.

As for the apparently memory loss/leak: I don't see anything right off to explain it.

[/COLOR][/COLOR]

---

### Post by cliddell on 2010-01-13
I'm not defending poor programming style, or lack of error checking, but I'm pretty sure the OP didn't ask for a code critique. I'm pretty sure the OP asked a perfectly valid technical question, with simple code to illustrate the query.

It's common for such examples to exclude code not directly required to illustrate the example/query/problem, and exclude error checking for brevity/clarity.

Perhaps we could take it as read that the OP is now aware that there are problems with the example code if it were applied in the "real world", and stick to the topic at hand which is the behaviour of glibc's memory management code?

Chris

---

### Post by Senesence on 2010-01-13
**About main()**:

I think cliddell explains my position perfectly (thanks for understanding, cliddell).

Guys, rest assured that I will not rely on the compiler when the code I'm writing is to go somewhere else, and someone has to actually depend on it.

I understand that it should be "int main(void)" and that I should return 0 (when everything goes right). 

I'm so sorry that I posted "main()" and caused all this trouble.

Forgive me.

[quote=JSeymour]Oh yeah, "looks cooler" is a great reason to purposefully write bad code

Sorry for the sarcasm, but "looks cooler" most definitely has no place in software design and coding.[/quote]

Never said it was a good reason, I just tried to illustrate the root of my decision when I perceived the difference between "main()" and "int main(void)" to be a matter of style, rather than function. Now I know better.

And no need to be sorry; I understand what you're trying to say.


**About error checking code:**

Yea, you're right (just like with main); I should check the return value of malloc for NULL (I knew that, but since I can see the memory usage levels, I thought it was a reasonable assumption in this particular case).


**About the memory issues - the "main" topic of this thread.**

I used valgrind, and apparently everything is released just fine, and there is no possibility for a leak.

So, I guess that settles it, and the difference I observed between two tests is in relation to small blocks/big blocks and how the memory manager handles them, as cliddell said.

I now consider the issue resolved, and thank everyone who participated.

---

### Post by nvteighen on 2010-01-13
> **JSeymour said:**
> [
Style nit: It is unclear that "vector" is actually "pointer to type struct vector_t."  Furthermore the struct definition belongs in vector.h.  Better to do it this way, IMO:
```

vector.h

[COLOR=#000000][COLOR=#0000bb]typedef struct vector_t
[/COLOR][COLOR=#007700]{
    [/COLOR][COLOR=#0000bb]float x[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]y[/COLOR][COLOR=#007700];
} vector;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]
[/COLOR][COLOR=#0000bb]vector *vector_new[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]float x[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]float y[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]void vector_delete[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]vector **this[/COLOR][COLOR=#007700]);
[/COLOR][/COLOR]
```

Hmm... not necessarily, though I believe I understand why you say that. If you include the struct's definition in the header, you lose modularization because everything becomes automatically public. Using a forward declaration allows you to have better compile-time control over access of the struct's members. But, in the other hand, using this "opaque pointer technique" also makes it impossible to just allocate the structure in stack and benefit from automatic memory management.

I guess you are thinking in how C++ classes are written, by usually writing the whole definition into the public header. Well... that's because in C++ you've got the access keywords and because it actually turns out to be better to do it that way.

---

