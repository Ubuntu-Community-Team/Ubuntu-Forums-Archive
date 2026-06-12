---
title: "C/C++ Lets talk about growing stack in Linux and Windows"
date: 2012-12-18
forum: Programming Talk
---

### Post by akvino on 2012-12-18
[http://www.kernel.org/doc/man-pages/online/pages/man3/alloca.3.html](http://www.kernel.org/doc/man-pages/online/pages/man3/alloca.3.html)

How does one know if you allocated too much memory on the stack?
What are the best practices to protect yourself from it?
How does stack allocation work in Linux? and if someone knows Windows?

I came onto memory management solution which relies heavy on 'alloca'. I was wondering if someone else had similar problems, and if you can share few pointers...

---

### Post by trent.josephsen on 2012-12-18
> **akvino said:**
> How does one know if you allocated too much memory on the stack?
I wasn't 100% sure, so I tried it.

```
% cat st_overflow.c 
#include <stdio.h>

void blow_up(void);

int main(void)
{
    puts("Let's overflow the stack!");
    blow_up();
    return 0;
}

void blow_up(void)
{
    static size_t size = 0;
    char v[1000] = {0};
    size++;
    printf("%zu kB\n", size);
    blow_up();
}
% make st_overflow
cc -std=c99 -pedantic -Wall -Wextra -Wwrite-strings    st_overflow.c   -o st_overflow
st_overflow.c: In function 'blow_up':
st_overflow.c:15:10: warning: unused variable 'v' [-Wunused-variable]
% ./st_overflow
... many lines skipped ...
8176 kB
8177 kB
8178 kB
8179 kB
8180 kB
8181 kB
8182 kB
8183 kB
zsh: segmentation fault (core dumped)  ./st_overflow

```

This program deliberately overflows the stack by calling an infinitely recursive function that reserves space for a large automatic variable every time it's called. By the output it looks like the stack has a size of 8192 kilobytes (8 megs) with a few extra k of overhead. That varies depending on platform and compilation options... I think. But at the end of the day I tried to call it one too many times. I ran out of stack space and my program segfaulted.

> What are the best practices to protect yourself from it?
(1) Don't hold large amounts of data in memory at once. (2) If you do, malloc() it, so you can recover from a failed allocation. (3) If you must use the stack, for performance or other reasons, **make sure the stack is large enough** -- there's really nothing else you can do. For better or worse there's no way to recover from overflowing the stack. The stack is, basically, the entire state of your program -- when it runs out, your program cannot proceed.

> How does stack allocation work in Linux? and if someone knows Windows?

I'm not sure what you mean by "how does [it] work", beyond what the manpage you linked describes. [Wikipedia on the call stack](http://en.wikipedia.org/wiki/Call_stack), if that's more like what you're looking for. Windows and Linux are going to be essentially the same in that respect.

> I came onto memory management solution which relies heavy on 'alloca'. I was wondering if someone else had similar problems, and if you can share few pointers...

[Obligatory](http://xkcd.com/138/), and more appropriate than usual.

There's no way to make alloca() safe. It would be quite reckless to use it in a way that doesn't allow you to predict the growth of the stack. In addition, since such memory is implicitly freed when the calling function returns, you can't pass it back up the call stack.

That's not to say that the code you're looking at is bad, or that you should change it. It's just that general rules of thumb or tips probably wouldn't be very helpful without a more complete picture of *why* the original author chose to use alloca() over malloc()/free() or ordinary automatic memory.

Sorry for not being very helpful :-/

---

### Post by rnerwein on 2012-12-19
> **trent.josephsen said:**
> I wasn't 100% sure, so I tried it.

```
% cat st_overflow.c 
#include <stdio.h>

void blow_up(void);

int main(void)
{
    puts("Let's overflow the stack!");
    blow_up();
    return 0;
}

void blow_up(void)
{
    static size_t size = 0;
    char v[1000] = {0};
    size++;
    printf("%zu kB\n", size);
    blow_up();
}
% make st_overflow
cc -std=c99 -pedantic -Wall -Wextra -Wwrite-strings    st_overflow.c   -o st_overflow
st_overflow.c: In function 'blow_up':
st_overflow.c:15:10: warning: unused variable 'v' [-Wunused-variable]
% ./st_overflow
... many lines skipped ...
8176 kB
8177 kB
8178 kB
8179 kB
8180 kB
8181 kB
8182 kB
8183 kB
zsh: segmentation fault (core dumped)  ./st_overflow

```This program deliberately overflows the stack by calling an infinitely recursive function that reserves space for a large automatic variable every time it's called. By the output it looks like the stack has a size of 8192 kilobytes (8 megs) with a few extra k of overhead. That varies depending on platform and compilation options... I think. But at the end of the day I tried to call it one too many times. I ran out of stack space and my program segfaulted.


(1) Don't hold large amounts of data in memory at once. (2) If you do, malloc() it, so you can recover from a failed allocation. (3) If you must use the stack, for performance or other reasons, **make sure the stack is large enough** -- there's really nothing else you can do. For better or worse there's no way to recover from overflowing the stack. The stack is, basically, the entire state of your program -- when it runs out, your program cannot proceed.



I'm not sure what you mean by "how does [it] work", beyond what the manpage you linked describes. [Wikipedia on the call stack]("http://en.wikipedia.org/wiki/Call_stack"), if that's more like what you're looking for. Windows and Linux are going to be essentially the same in that respect.



[Obligatory]("http://xkcd.com/138/"), and more appropriate than usual.

There's no way to make alloca() safe. It would be quite reckless to use it in a way that doesn't allow you to predict the growth of the stack. In addition, since such memory is implicitly freed when the calling function returns, you can't pass it back up the call stack.

That's not to say that the code you're looking at is bad, or that you should change it. It's just that general rules of thumb or tips probably wouldn't be very helpful without a more complete picture of *why* the original author chose to use alloca() over malloc()/free() or ordinary automatic memory.

Sorry for not being very helpful :-/
hi
have a look at following man pages: sigstack, setrlimit, getrlimit, sigaction, siglongjmp, sigsetjmp and signal ( notice with the normal signal handler you can't manage a stack overflow because that hander needs what isn't no more available --> the stack :-)
have fun

---

### Post by dwhitney67 on 2012-12-19
> **akvino said:**
> 
How does one know if you allocated too much memory on the stack?

You can't.

> **akvino said:**
> 
What are the best practices to protect yourself from it?

That's easy... write good code.

> **akvino said:**
> 
How does stack allocation work in Linux? and if someone knows Windows?

I take the good programming practices that I have learned over the years programming in Linux/Unix, and hope that they work in Windoze.  If they don't, then I curse at Microsoft and wish that the corporation would die.

> **akvino said:**
> 
I came onto memory management solution which relies heavy on 'alloca'. I was wondering if someone else had similar problems, and if you can share few pointers...
Whoa... alloca() is not POSIX compliant.  Why bother discussing it for multi-OS development.

---

### Post by MadCow108 on 2012-12-19
> **akvino said:**
> [url]
I came onto memory management solution which relies heavy on 'alloca'. I was wondering if someone else had similar problems, and if you can share few pointers...

never ever use alloca. It can only cause problems, e.g. functions using alloca cannot be inlined or unrolled (or will just blow up if the compiler is bad and tries it)

c99 variable sized arrays have mostly made it obsolete.
for the few remaining use cases there are stack-like memory pools like glibc's obstacks

---

### Post by trent.josephsen on 2012-12-19
> **MadCow108 said:**
> c99 variable sized arrays have mostly made it obsolete.
for the few remaining use cases there are stack-like memory pools like glibc's obstacks
Hmm... which is worse, the disease or the cure?

---

### Post by akvino on 2012-12-19
WoW I get the thread trend (thrend) :-)...

I know, I know, those were my first thoughts as well. Yet this bastard code works. It allocates the memory on the stack, puts the one size fits all chuncks in linked list, and then it reuses linked list when memory chuncks become available for the reuse. 


I like the dwhitney67 quote:
> 
I take the good programming practices that I have learned over the years programming in Linux/Unix, and hope that they work in Windoze. If they don't, then I curse at Microsoft and wish that the corporation would die.

Thanks all for help and thanks trent.josephsen for not so helpful but yet helpful post.

---

### Post by trent.josephsen on 2012-12-19
> **akvino said:**
> I know, I know, those were my first thoughts as well. Yet this bastard code works. It allocates the memory on the stack, puts the one size fits all chuncks in linked list, and then it reuses linked list when memory chuncks become available for the reuse. 

Interesting. Sounds like a disaster waiting to happen to be honest. Obviously this can only "work" if used carefully, and the consequences for not being careful may be much more severe than the consequences for forgetting to free() something.

The only plausible advantage I can see is not having to call free() when you're done -- just return from the function. But you save what, a handful of cycles? In exchange for a kludgy and unportable way to handle memory? Better have a really good reason for wanting to save those cycles...

---

### Post by akvino on 2013-01-14
> **trent.josephsen said:**
> Interesting. Sounds like a disaster waiting to happen to be honest. Obviously this can only "work" if used carefully, and the consequences for not being careful may be much more severe than the consequences for forgetting to free() something.

The only plausible advantage I can see is not having to call free() when you're done -- just return from the function. But you save what, a handful of cycles? In exchange for a kludgy and unportable way to handle memory? Better have a really good reason for wanting to save those cycles...

Actually it is faster since it doesn't have to call malloc.

---

### Post by trent.josephsen on 2013-01-14
> **akvino said:**
> Actually it is faster since it doesn't have to call malloc.

> **akvino said:**
> It allocates the memory on the stack, puts the one size fits all chuncks in linked list, and then it reuses linked list when memory chuncks become available for the reuse.

How does malloc() work?

---

### Post by akvino on 2013-01-14
> **trent.josephsen said:**
> How does malloc() work?

You're missing the point, or maybe I wasn't clear enough. 
It allocates bunch of same size chunks of memory which otherwise would have to be malloc-ed, meaning saves on memory manager allocating the memory on the heap and returning the pointer (which is what malloc is), since it's already done on the stack. Stack is also much faster.

---

### Post by ofnuts on 2013-01-15
> **akvino said:**
> You're missing the point, or maybe I wasn't clear enough. 
It allocates bunch of same size chunks of memory which otherwise would have to be malloc-ed, meaning saves on memory manager allocating the memory on the heap and returning the pointer (which is what malloc is), since it's already done on the stack. Stack is also much faster.
When you want to do this, you use malloc() to allocate a large chunk, and then sub-allocate it with algorithms that can be as as simple as bumping the "last used" pointer. When your chunck is exhausted, allocate another one.

And why do you think that the stack should be any faster than any other part of memory given the size of the cache in modern CPUs?

---

