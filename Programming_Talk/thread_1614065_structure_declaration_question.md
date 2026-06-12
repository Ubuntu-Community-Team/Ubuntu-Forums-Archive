---
title: "structure declaration question"
date: 2010-11-05
forum: Programming Talk
---

### Post by jamesbon on 2010-11-05
```
static const struct {
        const char *name;
        u32 hw_flags;
 } board_info[] __devinitdata = {
         { "RealTek RTL8139", RTL8139_CAPS },
         { "RealTek RTL8129", RTL8129_CAPS },
 };
```
I am not clear with above type of structure declaration.
Can any one help to understand.
Here is where it is given
[http://lxr.linux.no/linux+v2.6.36/drivers/net/8139too.c#L227](http://lxr.linux.no/linux+v2.6.36/drivers/net/8139too.c#L227)

---

### Post by DanielWaterworth on 2010-11-05
the first thing to understand is that structs are just types so you can create a variable like this:

[PHP]
struct {
    int a;
} some_var;
[/PHP]

although structs are usually typedef'ed before variable declarations. The other part is just an assignment. board_info is an array of 2 structs filled with data.

---

### Post by pconroy on 2010-11-05
> **jamesbon said:**
> ```
static const struct {
        const char *name;
        u32 hw_flags;
 } board_info[] __devinitdata = {
         { "RealTek RTL8139", RTL8139_CAPS },
         { "RealTek RTL8129", RTL8129_CAPS },
 };
```I am not clear with above type of structure declaration.
Can any one help to understand.
Here is where it is given
[http://lxr.linux.no/linux+v2.6.36/drivers/net/8139too.c#L227](http://lxr.linux.no/linux+v2.6.36/drivers/net/8139too.c#L227)

He's defining and initializing the structure at the same time.

"board_info" is of type struct 
"board_info[]" is an array of board_info structs

board_info[ 0 ].name is initialized to "RealTek RTL8139".
board_info[ 0 ].hw_flags is initialized to RTL8139_CAPS.

board_info[ 1 ].name is initialized to "RealTek RTL8129".
etc.


Make sense?

---

### Post by trent.josephsen on 2010-11-05
> **DanielWaterworth said:**
> structs are usually typedef'ed before variable declarations
I'd like to note that although this is somewhat common, it's an annoying obfuscation, like
```
typedef int *intp;
```
When reading code, the asterisks and "struct"s give you valuable clues about how to expect the code to work.  typedefs are one feature of the language I think are used way too much.

---

### Post by DanielWaterworth on 2010-11-05
Yes, I agree, typedef'ing ptrs is annoying (and should be an error in my opinion), but typedefs in general can be very useful when used right.

---

### Post by johnl on 2010-11-05
> **trent.josephsen said:**
> I'd like to note that although this is somewhat common, it's an annoying obfuscation, like
```
typedef int *intp;
```
When reading code, the asterisks and "struct"s give you valuable clues about how to expect the code to work.  typedefs are one feature of the language I think are used way too much.

I hate when basic types are typedef'd for no apparent reason.  I also personally dislike any typedef that hides a pointer, like:

```

typedef struct foobar* foobar_t;

```

That said I have no problem with using a typedef for a structure.

---

### Post by worksofcraft on 2010-11-05
> **johnl said:**
> I hate when basic types are typedef'd for no apparent reason.  I also personally dislike any typedef that hides a pointer, like:

```

typedef struct foobar* foobar_t;

```

That said I have no problem with using a typedef for a structure.

+1
Yes, I so totally agree with your view here :)

---

### Post by jamesbon on 2010-11-08
Actually every thing you people said makes sense
but why is 
__devinit used and what is this doing?
This is what confused me.

---

### Post by worksofcraft on 2010-11-08
> **jamesbon said:**
> Actually every thing you people said makes sense
but why is 
__devinit used and what is this doing?
This is what confused me.

That's a very good good question.
It is not something I came across in C myself, however I suspect it is some kind of "memory qualifier":

When programming in assembler I used to have to divide the memory up into into different "sections" e.g. to discriminate between stuff that is allocated in read-only memory chips from what goes in read-write memory. So I suspect this is just telling the compiler to place your device initialization parameters in a particular memory section. Like perhaps somewhere that interrupt routines can have access to it or something like that.

---

### Post by jamesbon on 2010-11-08
Ok thanks for the answer I just checked after your message
[http://mail.nl.linux.org/kernelnewbies/2002-05/msg00216.html](http://mail.nl.linux.org/kernelnewbies/2002-05/msg00216.html)
Seems the above link is correct __devinit is used to initialize the things is what I understand from above link.

---

