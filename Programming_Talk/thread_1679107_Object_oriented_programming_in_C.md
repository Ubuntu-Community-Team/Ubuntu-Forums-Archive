---
title: "Object oriented programming in C"
date: 2011-01-31
forum: Programming Talk
---

### Post by Barrucadu on 2011-01-31
I and a friend, new to programming, were discussing writing games for the Nintendo DS. He was initially thinking about using C++ for the object oriented capabilities. Of course, I pointed out that you can do OOP perfectly well in C, so he did a bit of googling and linked me to the typical horrible example of a struct with a load of function pointers in, representing a class.

First off, why do people put function pointers in a struct? Is it just so you can get roughly similar syntax when calling methods to other languages? That's clearly a bad reason. And so, I set about producing some example code using OOP with constructors, destructors, and inheritance in C.

The most basic class I am using for demonstration is a "box":
```

typedef struct
{
  coords_t *coords; /**< Coordinates of the box. */
  int width;        /**< Width of the box. */
  int height;       /**< Height of the box. */
} box_t;
```

And now, inheritance, in a "superbox":
```
typedef struct
{
  box_t super;      /**< Inherited class */
  box_t *superp;    /**< Pointer returned by malloc */

  colour_t *fill;   /**< Fill colour */
  colour_t *border; /**< Border colour. */
} superbox_t;
```

Magic. You can use all of the box functions with a superbox, just by typecasting. Of course, helper functions / macros could be made to hide the typecasting from the programmer if you so desired.

I shall demonstrate how the inheritance works with the demonstration for a superbox, makes a new superbox, sets some values via the constructor, and then calls superbox_print_info, and box_print_info:

```
/* Run the superbox example */
void
superbox_example ()
{
  superbox_t *superbox;
  colour_t *fill, *border;
  coords_t *coords;

  /* Make the colours and coordinates we'll need for the superbox constructor */
  fill   = colour_new (0xFF, 0xFF, 0xFF);
  border = colour_new (0x00, 0x00, 0x00);
  coords = coords_new (25, 7);

  /* Construct our superbox */
  superbox = superbox_new (coords, 10, 10, fill, border);

  /* Print info */
  superbox_print_info (superbox);
  printf ("\nLook at me, I can be typecast as a box!\n\n");
  box_print_info ((box_t*) superbox);

  /* Free the superbox */
  superbox_free (superbox);
}
```

Admittedly, this example is missing polymorphism, as it's not possible (in the traditional sense) with the method I'm using. Functions are not stored in the "class", so there's nothing to override, if you want a child class to have a different way of doing a certain function, you just write a different function - but the old one can still be used - if you call it and remember to typecast.

Full (short) code: [http://misc.barrucadu.co.uk/oop-c/](http://misc.barrucadu.co.uk/oop-c/)

So, I was wondering, do any of you know of any OOP 'tricks' for C I've missed? How (if you have) have you used OOP with C in your own code?

And, finally, what advantages do the OOP features of C++ offer over C, if you're willing to sacrifice the syntactic sugar?

---

### Post by Vaphell on 2011-01-31
> First off, why do people put function pointers in a struct? Is it just so you can get roughly similar syntax when calling methods to other languages? That's clearly a bad reason.

No, that's not the reason. If it's not a part of the object, it's not a method but a completely unrelated random function.
Object should carry all the toys needed to interact with it and pointers to functions provide sorta-like-method mechanism, which makes the interaction with the object data foolproof (at least in theory).
Without function pointers you rely on external functions to manipulate object data and it's up to you to use a proper function in a given context, which becomes more and more difficult to keep track of as the project grows in size.

---

### Post by worksofcraft on 2011-01-31
> **Barrucadu said:**
> ...
So, I was wondering, do any of you know of any OOP 'tricks' for C I've missed? How (if you have) have you used OOP with C in your own code?

And, finally, what advantages do the OOP features of C++ offer over C, if you're willing to sacrifice the syntactic sugar?

While I do agree that coding this kind of thing "manually" shows an excellent understanding of OOP concepts I also feel you are making an awful lot of unnecessary work for yourself here:

You are losing not just "syntactic sugar" but all the compile time type checking stuff and the implicit use of constructors and destructors, and the transparent use of v-tables for polymorphism and exception handling and templates, and so on ...

IMO you are in danger of ending up with source code that is infested with macros and unsafe type casts and it will likely become unmaintainable and unintelligible. Why would you want to do such a thing? :shock:

---

### Post by MadCow108 on 2011-01-31
when you want to do real object orientation in C have a look at gobject which implements it in C (in a different way than C++ does).

If you want just C with oop syntax have a look at objective C
(or vala which is basically syntactic sugar for gobject)

as mentioned doing it with all oop features (inheritance, virtual methods, polymorphism etc) in plain C is a quite frustrating to say the least

---

