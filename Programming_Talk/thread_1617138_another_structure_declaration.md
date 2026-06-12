---
title: "another structure declaration"
date: 2010-11-09
forum: Programming Talk
---

### Post by jamesbon on 2010-11-09
I came across one more declaration of structure which has confused me enough and I re read Kernighan Ritchie but could not find it in the way it was declared in the program
```

static const cli_pulldown_t pulldown_values[] =
{
    [X264_PULLDOWN_22]     = {1,  {TB},                                   1.0},
    [X264_PULLDOWN_32]     = {4,  {TBT, BT, BTB, TB},                     1.25},
    [X264_PULLDOWN_64]     = {2,  {PIC_STRUCT_DOUBLE, PIC_STRUCT_TRIPLE}, 1.0},
    [X264_PULLDOWN_DOUBLE] = {1,  {PIC_STRUCT_DOUBLE},                    2.0},
    [X264_PULLDOWN_TRIPLE] = {1,  {PIC_STRUCT_TRIPLE},                    3.0},
    [X264_PULLDOWN_EURO]   = {24, {TBT, BT, BT, BT, BT, BT, BT, BT, BT, BT, BT, BT,
                                   BTB, TB, TB, TB, TB, TB, TB, TB, TB, TB, TB, TB}, 25.0/24.0}
};

```
[Here]("http://git.videolan.org/?p=x264.git;a=blob;f=x264.c#l139") is where I saw this sort of structure declaration.

---

### Post by worksofcraft on 2010-11-09
> **jamesbon said:**
> I came across one more declaration of structure which has confused me enough and I re read Kernighan Ritchie but could not find it in the way it was declared in the program
```

static const cli_pulldown_t pulldown_values[] =
{
    [X264_PULLDOWN_22]     = {1,  {TB},                                   1.0},
    [X264_PULLDOWN_32]     = {4,  {TBT, BT, BTB, TB},                     1.25},
    [X264_PULLDOWN_64]     = {2,  {PIC_STRUCT_DOUBLE, PIC_STRUCT_TRIPLE}, 1.0},
    [X264_PULLDOWN_DOUBLE] = {1,  {PIC_STRUCT_DOUBLE},                    2.0},
    [X264_PULLDOWN_TRIPLE] = {1,  {PIC_STRUCT_TRIPLE},                    3.0},
    [X264_PULLDOWN_EURO]   = {24, {TBT, BT, BT, BT, BT, BT, BT, BT, BT, BT, BT, BT,
                                   BTB, TB, TB, TB, TB, TB, TB, TB, TB, TB, TB, TB}, 25.0/24.0}
};

```
[Here]("http://git.videolan.org/?p=x264.git;a=blob;f=x264.c#l139") is where I saw this sort of structure declaration.

Hum... well what you have to realize is these are all tables that are being initialized at compile time. SO let's start with the type:
[php]
typedef struct{
     int mod;
     uint8_t pattern[24];
     float fps_factor;
} cli_pulldown_t;
[/php]

... each entry consists of an int, followed by an array of 24 bytes followed by a floating point number. Evidently they don't bother specifying all 24 bytes when only one or two of them are used, but they still represented as an array by putting {} round it. So that should explain everything on the right hand side of the = signs right ?

---

### Post by worksofcraft on 2010-11-09
so it just leaves the bits on the left.
Notice the enum:
[php]
enum pulldown_type_e
{
     X264_PULLDOWN_22 = 1,
     X264_PULLDOWN_32,
     X264_PULLDOWN_64,
     X264_PULLDOWN_DOUBLE,
     X264_PULLDOWN_TRIPLE,
     X264_PULLDOWN_EURO
};
[/php]
so all those are is indexes into the array that is being created and quite pointless because they are in sequential order anyway although TBH I didn't even know you could do that in C oh well ^^

---

### Post by dwhitney67 on 2010-11-09
> **jamesbon said:**
> I came across one more declaration of structure which has confused me enough and I re read Kernighan Ritchie but could not find it in the way it was declared in the program

I've never seen such a construct either, but apparently it is supported by the compiler.

It is equivalent too:
```

static const cli_pulldown_t pulldown_values[] =
{
   {0,  {0}, 0.0},
   {1,  {TB},                                   1.0},
   {4,  {TBT, BT, BTB, TB},                     1.25},
   {2,  {PIC_STRUCT_DOUBLE, PIC_STRUCT_TRIPLE}, 1.0},
   {1,  {PIC_STRUCT_DOUBLE},                    2.0},
   {1,  {PIC_STRUCT_TRIPLE},                    3.0},
   {24, {TBT, BT, BT, BT, BT, BT, BT, BT, BT, BT, BT, BT,
         BTB, TB, TB, TB, TB, TB, TB, TB, TB, TB, TB, TB}, 25.0/24.0}
};

```


P.S.  Next time write yourself a small little program when you encounter an uncertainty.  Asking for help at every little encounter of the unknown reminds me a lot of my 5 year old daughter, as she discovers the world.

```

#include <stdio.h>

struct Other
{
   int val1;
   int val2;
};

struct Foo
{
   int          ival;
   struct Other other;
   float        fval;
};


enum Indexes { ZERO, ONE, TWO, THREE };

static const struct Foo values[] =
{
   [ONE]   = { 1, {2,3}, 4.0 },
   [TWO]   = { 5, {6,7}, 8.0 },
   [THREE] = { 9, {0,1}, 2.0 }
};

int main(void)
{
   for (int i = ZERO; i <= THREE; ++i)
   {
      printf("values[%d] = { %d, {%d,%d}, %2.1f }\n", i,
                                                      values[i].ival,
                                                      values[i].other.val1,
                                                      values[i].other.val2,
                                                      values[i].fval);
   }
   return 0;
}

```

---

### Post by Arndt on 2010-11-09
> **dwhitney67 said:**
> I've never seen such a construct either, but apparently it is supported by the compiler.


Me neither. It seems to have been introduced with C99.

---

### Post by dwhitney67 on 2010-11-09
> **Arndt said:**
> Me neither. It seems to have been introduced with C99.

I just tested that theory; apparently the feature is supported by C89.

---

### Post by vikas.sood on 2010-11-09
Same here. just tested it. One of the new feature with C99.
But for what joy? I will never write my code this way.

---

### Post by Arndt on 2010-11-09
> **dwhitney67 said:**
> I just tested that theory; apparently the feature is supported by C89.

```
$ gcc -pedantic --std=c89 -c arr3.c 
arr3.c:21: warning: ISO C90 forbids specifying subobject to initialize
arr3.c:22: warning: ISO C90 forbids specifying subobject to initialize
arr3.c:23: warning: ISO C90 forbids specifying subobject to initialize
$ gcc -pedantic --std=c99 -c arr3.c 
$ 

```

arr3.c is the program you posted. Without -pedantic, gcc is more lenient.

---

### Post by Arndt on 2010-11-09
> **vikas.sood said:**
> Same here. just tested it. One of the new feature with C99.
But for what joy? I will never write my code this way.

From the C99 Rationale. I think this is the right section (6.7.8):

> A new feature of C99: Designated initializers provide a mechanism for initializing sparse arrays,
a practice common in numerical programming. They add useful functionality that already exists
25 in Fortran so that programmers migrating to C need not suffer the loss of a program-text-saving
notational feature.
This feature also allows initialization of sparse structures, common in systems programming, and
allows initialization of unions via any member, regardless of whether or not it is the first
member.
30 Designated initializers integrate easily into the C grammar and do not impose any additional runtime
overhead on a user’s program. Their initial C implementation appeared in a compiler by
Ken Thompson at AT&T Bell Laboratories.

---

