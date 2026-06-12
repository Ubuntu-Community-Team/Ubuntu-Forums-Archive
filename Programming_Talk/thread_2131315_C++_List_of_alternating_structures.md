---
title: "C++ List of alternating structures"
date: 2013-04-01
forum: Programming Talk
---

### Post by Dirich on 2013-04-01
In a certain .hpp of mine, I would like to define a list of two alternating kind of structures:

```

struct A
{
    /* TONS of stuff */
    B* Next;
    B* Previous;
};

struct B
{
    /* very few stuff */
    A* Next;
    A* Previous;
};

```

The problem, the way I wrote this code, is that the compiler has no idea of what B is when it finds it while reading the definition of struct A. With functions the problem is solved by pre-declaring them at the beginning of the file or by declaring the header.

How do I do it (without putting everything in a single structure so that the problem is avoided altogheter)?

---

### Post by r-senior on 2013-04-01
I'm not a C++ expert but I happened to be reading about this the other day. It should work if you declare it like this:

```
struct A {
    struct B *next;
    struct B *prev;
};

struct B {
    struct A *next;
    struct A *prev;
};

```

Gory details here ...

[http://stackoverflow.com/questions/612328/difference-between-struct-and-typedef-struct-in-c](http://stackoverflow.com/questions/612328/difference-between-struct-and-typedef-struct-in-c)

Someone who knows the ins and outs of this better than I do will fill in the details.

---

### Post by Dirich on 2013-04-01
> **r-senior said:**
> I'm not a C++ expert but I happened to be reading about this the other day. It should work if you declare it like this:

```
struct A {
    struct B *next;
    struct B *prev;
};

struct B {
    struct A *next;
    struct A *prev;
};

```

Gory details here ...

[http://stackoverflow.com/questions/612328/difference-between-struct-and-typedef-struct-in-c](http://stackoverflow.com/questions/612328/difference-between-struct-and-typedef-struct-in-c)

Someone who knows the ins and outs of this better than I do will fill in the details.


Thank you. That link is very useful. I did not know that of the tag and typedef namespace.
The solution is the same as in the case I want struct A to contain a pointer to struct A!

---

### Post by TheKrieg on 2013-04-01
If you are using C++, some of this can be avoided by using Classes. and namespaces.

---

### Post by SledgeHammer_999 on 2013-04-01
> **Dirich said:**
> In a certain .hpp of mine, I would like to define a list of two alternating kind of structures:

```

struct A
{
    /* TONS of stuff */
    B* Next;
    B* Previous;
};

struct B
{
    /* very few stuff */
    A* Next;
    A* Previous;
};

```

The problem, the way I wrote this code, is that the compiler has no idea of what B is when it finds it while reading the definition of struct A. With functions the problem is solved by pre-declaring them at the beginning of the file or by declaring the header.

How do I do it (without putting everything in a single structure so that the problem is avoided altogheter)?

I think another way of solving this is with "forward declaration" of the struct/class. Warning I didn't actually try to compile the following code:
```

struct B; //forward declare the struct

struct A
{
    /* TONS of stuff */
    B* Next;
    B* Previous;
};

struct B
{
    /* very few stuff */
    A* Next;
    A* Previous;
};

```

---

### Post by Dirich on 2013-04-02
Namespaces is what the solution suggested in the link by the 1st one to answer is about: tag namespace vs typedef namespace. The typedef namespace allows the forward declaration of the struct. So, maybe you last 2 have in mind different things, or maybe everybody got the same idea! :)

---

### Post by akvino on 2013-04-03
Bravo. I couldn't believe this went through 5 comments without someone suggesting forward declaration. In essence this is a very common problem to have, and until you get familiar with forward declaration it becomes PITA to dance around it.

---

### Post by SledgeHammer_999 on 2013-04-04
**@akvino** read it again. I already mentioned forward declaration.

---

