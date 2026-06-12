---
title: "C and Reverse Engineering ?"
date: 2011-03-02
forum: Programming Talk
---

### Post by cap10Ibraim on 2011-03-02
I finished a C course - with data structures - last year 
I would like to learn more about C , can you suggest some books that cover advanced topics in C

---

### Post by foxmuldr on 2011-03-02
> **cap10Ibraim said:**
> I finished a C course - with data structures - last year 
I would like to learn more about C , can you suggest some books that cover advanced topics in C

Such as? What advanced topics?

---

### Post by rnerwein on 2011-03-03
> **cap10Ibraim said:**
> I finished a C course - with data structures - last year 
I would like to learn more about C , can you suggest some books that cover advanced topics in C
hello
for you it must look very antique but i learned C with:
The C Programming Language by Prentice-Hall, Inc. 1977
Programming in C by Kernighan - Ritchie

i know it's very very old. but i think it's still the bible for starting to learn C.
C is like a rasor - but without a grip :-)
ciao

---

### Post by trent.josephsen on 2011-03-03
> **rnerwein said:**
> hello
for you it must look very antique but i learned C with:
The C Programming Language by Prentice-Hall, Inc. 1977
Programming in C by Kernighan - Ritchie

i know it's very very old. but i think it's still the bible for starting to learn C.
C is like a rasor - but without a grip :-)
ciao
OP said he finished a C-based Data Structures course already; he's probably not looking for an introduction to C.

@OP: What kind of advanced topics?  If you're looking at (say) OS or compiler design, you should look into books that address those things directly.  "Advanced topics" are language-agnostic.

Knuth is always a good option.

---

### Post by rnerwein on 2011-03-04
> **trent.josephsen said:**
> OP said he finished a C-based Data Structures course already; he's probably not looking for an introduction to C.

@OP: What kind of advanced topics?  If you're looking at (say) OS or compiler design, you should look into books that address those things directly.  "Advanced topics" are language-agnostic.

Knuth is always a good option.
hello
that's right.
but when that guy want to go deep in to the C language i think - before read:
OPERATING SYSTEMS
Desing and implementation
- Prentice-Hall Internal Editions
Andrew S. Tanenbaum

why ? most parts ( excludeded some drivers .. ) are written in C.
just a question ( i bet you never heard about it ) what is:

void foobar_init1(void) __attribute__ ((constructor));
void foobar_fini1(void) __attribute__ ((destructor));

ciao :-))

---

### Post by trent.josephsen on 2011-03-04
FYI, that __attribute__ stuff is a GNU extension, not standard C.  If OP wants to learn about GNU C, that's fine too, but I have both the books you mentioned, and neither is an appropriate resource for that.

Perhaps someone else can recommend a good learning resource for GNU extensions to standard C?

---

