---
title: "link list implementation in linux kernel easy question syntax not clear"
date: 2010-10-09
forum: Programming Talk
---

### Post by jamesbon on 2010-10-09
Hi,in [Linux Kernel]("http://lxr.linux.no/#linux+v2.6.18/include/linux/list.h")
following section of code
there is a structure which is defined as
```

struct list_head {
        struct list_head *next, *prev;
};

```It is used in another file as 
```

#define LIST_HEAD_INIT(name) { &(name), &(name) }

#define LIST_HEAD(name) \
        struct list_head name = LIST_HEAD_INIT(name)

static inline void INIT_LIST_HEAD(struct list_head *list)
{
        list->next = list;
        list->prev = list;
}


```I came across a book where the code is given as follows in an example
```

include/linux/list.h
struct list_head {
struct list_head *next,*prev;
};
#define LIST_HEAD_INIT(name) {&(name),&(name)}

#define LIST_HEAD(name) struct list_head name = LIST_HEAD_INIT(name)
#define INIT_LIST_HEAD(ptr) do {\
(ptr)->next = (ptr);(ptr)->prev= (ptr);\
}while(0)

```I was not able to understand above code segment.
I am aware of what a #define is but still I could not understand above thing.
Can some one help in understanding with some example?

---

### Post by worksofcraft on 2010-10-09
hum... well I'm no good at making those nice ascii diagrams that someone else is renowned for so I'll just explain it with words:
```

struct list_head {
     struct list_head *next,*prev;
};

```
This is the head of each and every element in a bi-directionally linked list: Has pointer to next element and to the previous element, but here in it's most primitive form there is no attached data. Presumably they derive classes of actual doubly linked items from this base class, probably just by type casting.

Now personally I like to signal end of list by having the pointer to next be NULL and ditto the pointer to previous element at the other end. That way you would have no choice but to stop iterating when you get to the end of your list.

However in both these cases you are initializing the element to point to itself. Such is usually how one starts a circularly linked list... that is one that is like daisy chain necklace, just going round and round on itself with no actual start or end:
```

// this macro sets both prev and next pointers to the address of the
// same identifier (whatever you supply for the "name" parameter.
#define LIST_HEAD_INIT(name) {&(name),&(name)}

// this macro defines a list_head struct identified with "name" and
// sets both prev and next to point to itself.
#define LIST_HEAD(name) struct list_head name = LIST_HEAD_INIT(name)

// and this one initializes a list_head struct in same way given
// a pointer to it.
// Note: they use dummy do {} while construct so that it can be used
// syntactically as a single statement.
#define INIT_LIST_HEAD(ptr) do {\
     (ptr)->next = (ptr);(ptr)->prev= (ptr);\
}while(0)

```

now as an exercise to see if you understand it try writing a bit of code to insert a struct list_head into a list given another struct list head that is part of the actual list you wish to insert to. Youcan even try making that into a macro and if you really get stuck I'll do one for you ;)

---

### Post by jamesbon on 2010-10-15
I was going through this post of yours again but I could not understand why is  there a need to declare LIST_HEAD_INIT and INIT_LIST_HEAD they both seem to do the same thing.

---

### Post by worksofcraft on 2010-10-16
> **jamesbon said:**
> I was going through this post of yours again but I could not understand why is  there a need to declare LIST_HEAD_INIT and INIT_LIST_HEAD they both seem to do the same thing.

That's a very good question there, our 007 dude ;)

LIST_HEAD_INIT initializes one of these list head structure thingamajigs at compile time and so it doesn't actually generate any code, but stores constant values in a structure of which the address is known and fixed.

OTOH INIT_LIST_HEAD takes a pointer and so it could be a structure that is dynamically allocated, e.g. with "malloc" or one that is passed in to your function... and then it does it's stuff at run time.

The compile time version is indeed superfluous and it doesn't really save a lot of processing but perhaps it does make sense to people who are writing OS kernels :shock:

---

### Post by nvteighen on 2010-10-16
> **worksofcraft said:**
> 
The compile time version is indeed superfluous and it doesn't really save a lot of processing but perhaps it does make sense to people who are writing OS kernels :shock:

I think it's more about abstracting the struct initialization in the most efficient way. I mean: in normal conditions, if I had to initialize this struct that way, I'd just have done:

```

struct list_head
{
    struct list_head *prev, *next;
};

struct list_head list_head_init(struct list_head *name)
{
    struct list_head tmp = {name, name};

    return tmp;
    /* C99 allows: 
     * return (struct list_head){name, name}; 
     */
}

void init_list_head(struct list_head *list)
{
    list->prev = list;
    list->next = list;
}

```

That'd be a nice abstraction to initialize a struct whose members have the same value when initialized. But, we are wasting a function call for that, even creating a temporary structure that we then return for the caller code to set as the value of a variable. for the Nice abstraction, but not efficient. The same goes for init_list_head: even by using a pointer as argument, you have to copy the original list's memory address to the local pointer...

Using a macro or a static inline function avoids that by copying the code where it is used. Ok, you may think the time wasted on function calls is negligible in this case, but it seems the kernel developers have evidence that this is a necessary move... Maybe they're constructing huge linked lists using recursion in some place or whatever. Also think the kernel does not only run on PCs, but also on embedded devices, where this may be of importance. And you can't hope the compiler will optimize this in the best possible way (even though the kernel is compiled with optimization set up): in low-level programming, the more control you have, the better.

---

### Post by saulgoode on 2010-10-16
> **worksofcraft said:**
> The compile time version is indeed superfluous and it doesn't really save a lot of processing but perhaps it does make sense to people who are writing OS kernels :shock:
The function version will not work within the LIST_HEAD macro.

---

### Post by dwhitney67 on 2010-10-16
IMHO, defining macros, such as the ones presented above, are a waste of time.  It saves very little in terms of coding time, and merely adds to end-time necessary for others to understand and maintain the code.

Amateurish code, if you ask me.

---

### Post by johnl on 2010-10-16
You can see these macros in user-space by including <sys/queue.h>.

Suppose you are writing a C program and you need a linked list containing a widget_t, another linked list containing a foobar_t, a double-ly linked list containing a baz_t, etc.

How do you implement these?  Do you write something 'generic' using a void pointer?  Do you write a bunch of different list implementations for each type?  Remember, this is C.  There are no templates, no inheritances. 

The purpose of this header is to allow you to easily create lists without having to re-code the wheel.  It provides all sorts of different structures that are easy to use once you understand how. 

Check [this blog post](http://unixjunkie.blogspot.com/2006/12/lists-and-queues.html) or **man queue**for a good explanation of how the macros expand and what they do.

---

