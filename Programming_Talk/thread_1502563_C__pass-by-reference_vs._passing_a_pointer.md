---
title: "C:  pass-by-reference vs. passing a pointer"
date: 2010-06-05
forum: Programming Talk
---

### Post by MichaelBurns on 2010-06-05
I am working my way through a C tutorial ([http://www.crasseux.com/books/ctutorial](http://www.crasseux.com/books/ctutorial), which I think was suggested in one of the sticky threads here).

I encountered a problem when I tried to pass an integer pointer to **fscanf()** in order to get an integer value from the terminal.  (Never mind that **fscanf()** is not "the best" way to do this; I am experimenting.)  Here is the problem code:
```

#include<stdio.h>
int main(void){
  int *my_int_pntr;
  fscanf(stdin,"%i",my_int_pntr);
  return 0;
}

```
The above code compiles successfully (I'm using Geany, and I press **F9** to compile).  However, when I run it (**F5**) and enter an integer (say, **3\n**) from the keyboard, I get a segfault.

Here is the change that I made, more in line with the examples, that worked:
```

#include<stdio.h>
int main(void){
  int my_int_pntr;
  fscanf(stdin,"%i",&my_int_pntr);
  return 0;
}

```
To save you the tedium of trying to figure out what is the difference: I changed the third line to declare a "normal" int variable instead of a pointer, and the fourth line passes the variable by reference instead of passing a pointer directly.  It compiles (**F9**) successfully, and I can run it (**F5**) and enter an integer (say, **3\n**) without producing a segfault.

If I understand the concept of pointers, these two codes should give to the compiler exactly the same instructions: reserve an integer-sized place in memory and then give the **fscanf()** function access to that memory location.  The only issue that I can think of is that, since the pointer (in the first example) is uninitialized, it contains a garbage address that happens to be disallowed.  Is that the case?  If so, why does the compiler choose a bad memory location in the first example (i.e. when **fscanf()** finally uses it) but a good memory location in the second example (i.e. when it is declared)?  Does C provide the tools to assign a value to a pointer directly?  (Note: I did try to initialize the pointer by assigning a value to the location that is "pointed to" in the third line, but that didn't work.)

What is the utility of defining a pointer if I can just as well use the **&** operator?  If I define a pointer, must I also define a superfluous variable that the pointer can "point to" in order to initialize it, thus taking up extra memory that I don't really need?  Explicit pointers seem superfluous.

---

### Post by Bachstelze on 2010-06-05
> **MichaelBurns said:**
> The only issue that I can think of is that, since the pointer (in the first example) is uninitialized, it contains a garbage address that happens to be disallowed.  Is that the case?

Yes. Never ever do anything with un uninitialised pointer (minus initialising it of course).

> **MichaelBurns said:**
> If so, why does the compiler choose a bad memory location in the first example (i.e. when **fscanf()** finally uses it) but a good memory location in the second example (i.e. when it is declared)?

Because when you declare a variable, the program only creates one object of the appropriate type, nothing more. When you declare an int, the program creates an int. That is, it will "claim" from the kernel the memory required to accomodate an object of type int, and "bind" the declared name to that memory area. Likewise, when you declare an int*, it will allocate the memory for an int* and bind the declared name to the allocated memory area.

In neither case is the actual memory in the allocated area modified in any way: it will still contain the same data it did before the declaration. This is why when you declare a pointer variable, it can point to absolutely anywhere, since the address pointed to is defined by the data of the pointer. In your first example, the program does not choose anything: until the pointer is initialised, it will just use whatever data was there before.

> **MichaelBurns said:**
> Does C provide the tools to assign a value to a pointer directly?

Sure, there are plenty of ways to do that. In your particular case, you could use malloc():

```
int *p = malloc(sieof(int));
```

> **MichaelBurns said:**
> What is the utility of defining a pointer if I can just as well use the **&** operator?  If I define a pointer, must I also define a superfluous variable that the pointer can "point to" in order to initialize it, thus taking up extra memory that I don't really need?  Explicit pointers seem superfluous.

Of course, it seems superflouos to create a pointer for something as small as an int. For large arrays, however, it's another story. If you're working on buffers that are several megabytes long, you don't really have another way.

---

### Post by Some Penguin on 2010-06-05
> **Bachstelze said:**
> 
Of course, it seems superflouos to create a pointer for something as small as an int. For large arrays, however, it's another story. If you're working on buffers that are several megabytes long, you don't really have another way.

And more generally (not really applicable for main-method-only toys)

There's also the issue that space allocated on the stack really shouldn't be reused for anything else once the stack is popped off.  You can get and return the address of a local variable (including a function parameter), but it'll be not too useful because the next function call might easily overwrite that location on the stack.   C isn't going to decide to keep the data inviolate just because somebody's gotten an address of it.

Heap space, on the other hand, is allocated upon request and retained until specifically deallocated or when the process is terminated.

---

### Post by lisati on 2010-06-05
Sometimes the declaration and initialization of variables can be a bit baffling when you're new to programming or to a particular language.

To add to what Some Penguin said, the stack is commonly used for stuff that is transient in nature, small in size, and which isn't needed for long, e.g. return addresses when calling up functions/subroutines/etc.

The heap is more useful for stuff that you might need to have available for a bit longer, and can be useful when you don't know exactly how much memory you'll need until you run the program.

---

### Post by soltanis on 2010-06-05
Short answer to your immediate question: it segfaults because your trying to write to an address that either isn't in your memory space or you aren't allowed to write to.

Longer answer: since you never initialized the pointer, it just takes on the value of whatever was in that memory spot before it was allocated (the pointer, not the actual space for data). If you are on a 32-bit system, visualize it like this:

```

+----------+-------------------
+0xDEADBEEF| other variables, random data...
+----------+-------------------
  ^-- your pointer, pointing to some random value

```

Complete answer: you'll learn later why explicit pointers are useful, but in this particular case, if you want to manipulate data using that pointer, you need to make it point to a *valid* space in memory for it to store information in.

How you do this can actually happen two ways (actually more, but two ways that you should be using):
1. You declared another "stack" or "automatic" variable like this:

```

int main(int argc, char **argv)
{
    int i, *pi;
    /* and then assigned it to the memory space of i like this: */
    pi = &i;

```

The reason that is valid is because when main executes, space is automatically allocated for the variable i (which stores an integer). By assigning to pi the address of i, writing data to *pi (the dereference of the pointer) will cause it to be written into the address space of i, i.e., it will change i's value.

2. The other way is to allocate memory dynamically using **malloc**(3).

```

int main(int argc, char **argv)
{
    int *pi;
    pi = malloc(sizeof(int));

```

malloc is quite a beast and I suggest that at this stage, you acknowledge its existence and move on, but what it does is it requests at runtime that the system set aside some amount of memory. The argument to the function is actually how much memory you want to set aside, in this case, the amount of memory an int takes up, which is on some systems 4 bytes (but it varies so use sizeof).

Before you use pi, you actually have to check if it refers to a valid address (which you can do by checking that it is not NULL; if it is, that means malloc couldn't allocate memory for you, which probably means you're out of memory). But, when you dereference it now (*pi), you're writing data into that space.

Note that since you can set the argument to malloc to anything, including something determined at runtime (compare to the size of an array, which must be defined at compile time) you can create dynamically sized arrays with this function.

---

### Post by BoneKracker on 2010-06-06
Nice explanation, soltanis.

---

### Post by MichaelBurns on 2010-06-06
Thanks, y'all.  I believe that **malloc()** is the concept at the root of my confusion.  I will try to take soltanis' advice and "move on" for now, at least until I get through the tutorial (although I get increasingly bogged down by these kinds of issues as I go).  But, I want to take one more crack at resolving my confusion.

I was considering the following declarations to be exactly the same thing, just written in different ways:
```

int my_var1;
int *my_ptr2;

```
i.e., both have a location and size in memory (and the particular bytes that consume that memory are initially undetermined).  I was trying to think of the "int" in the declaration as the type, and then the "*" as part of the variable name in the "pointer" declaration.  This is how I explained to myself that a pointer needs a datatype.  The only reason that I can see for a pointer to have a datatype is to determine the amount of memory to be allocated.  But, what does it mean to allocate sizeof(int) bytes if those bytes don't even exist?  Do integers get different kinds of memory than floats?  (I know that they have different numerical interpretations in terms of the bits, but do they have different dedicated areas of memory?)  Why not just declare all pointers as "void" and then give them a size explicitly?  (That looks basically like what **malloc()** is supposed to do.)

I guess I can refine my question slightly:

Is there some purpose for making invalid memory appear to be available for storing a variable when in fact it is not available?

---

### Post by Bachstelze on 2010-06-06
> **MichaelBurns said:**
> 
I guess I can refine my question slightly:

Is there some purpose for making invalid memory appear to be available for storing a variable when in fact it is not available?

Once again, when you declare a variable, its contents are simply what was in that memory area before, until you initialize it with a correct value. It's like when you buy a used hard drive on ebay and the previous owner didn't wipe it clean: you will get whatever was in there, which may be total garbage to you, until you replace it with the stuff you want.

---

### Post by Some Penguin on 2010-06-06
> **MichaelBurns said:**
> The only reason that I can see for a pointer to have a datatype is to determine the amount of memory to be allocated.

Compile-time type safety.  It's really for *you* -- you *could* do treat all pointers as (void*) and cast appropriately, but then the compiler will have greater difficulty telling you that you're making mistakes.  Memory addresses are the same size no matter what is being pointed to.

---

### Post by rplantz on 2010-06-06
> **MichaelBurns said:**
> 
I was considering the following declarations to be exactly the same thing, just written in different ways:
```

int my_var1;
int *my_ptr2;

```
i.e., both have a location and size in memory (and the particular bytes that consume that memory are initially undetermined).  I was trying to think of the "int" in the declaration as the type, and then the "*" as part of the variable name in the "pointer" declaration.  This is how I explained to myself that a pointer needs a datatype.  The only reason that I can see for a pointer to have a datatype is to determine the amount of memory to be allocated.
The data type part of a pointer declaration also tells the compiler what instructions to generate for some operations on the pointer variable. For example, in
```

   int x;
   int *xPtr;
   char y;
   char *yPtr;

   xPtr = &x;
   yPtr = &y;

   x++;
   y++;

```
the "++" operator adds 4 to the value (an address) stored in xPtr, but it adds 1 to the value (an address) stored in yPtr. (Assuming an environment where an int is 4 bytes in size.) 

> 
But, what does it mean to allocate sizeof(int) bytes if those bytes don't even exist?  Do integers get different kinds of memory than floats?  (I know that they have different numerical interpretations in terms of the bits, but do they have different dedicated areas of memory?) 

Basically, no.

---

### Post by schauerlich on 2010-06-06
Think of
```
int i;
```
as a box, and
```
int *int_ptr;
```
as an arrow. 

When you declare i, you're saying "here's a box. it can store an integer." When you declare int_ptr, you're saying "here's an arrow. it should point to a box that can store an integer." But, be careful: you didn't MAKE a box, you just made an arrow [which can *point* to a box. When you pass i in by reference to fscanf, you're saying "here's an arrow pointing to my box, where you can store an integer." However, if you tried to pass in int_ptr, you'd be giving it an arrow that is pointing to some random box, which probably isn't yours. When this happens, the OS steps in and kills your program (segfaults) because you tried to put your integer in someone else's box.

---

### Post by BoneKracker on 2010-06-07
... and it's not cool to point your integer at someone else's box.

---

### Post by schauerlich on 2010-06-07
> **BoneKracker said:**
> ... and it's not cool to point your integer at someone else's box.

Party foul?

---

### Post by Compyx on 2010-06-07
Here's a little video explaining pointers: [http://www.youtube.com/watch?v=mnXkiAKbUPg]("http://www.youtube.com/watch?v=mnXkiAKbUPg") ;)

---

### Post by nvteighen on 2010-06-07
> **Compyx said:**
> Here's a little video explaining pointers: [http://www.youtube.com/watch?v=mnXkiAKbUPg]("http://www.youtube.com/watch?v=mnXkiAKbUPg") ;)

The conclusion you have to draw from that video is that, after all, pointers aren't that difficult. I love it!

---

### Post by BoneKracker on 2010-06-07
> **Compyx said:**
> Here's a little video explaining pointers: [http://www.youtube.com/watch?v=mnXkiAKbUPg]("http://www.youtube.com/watch?v=mnXkiAKbUPg") ;)

Ack!  That's great!

I love it how he dereferences an un-intialized pointer and his head gets cut off.

It's like, "Ooooh Nooooh!  Mr. Bill!", in the old Saturday Night Live. :lol:

I'm not sure this actually makes it any easier to understand, but it is entertaining.

---

### Post by MichaelBurns on 2010-06-08
Thanks, rplantz and shauerlich, but I'm getting confused again.  I suspect that y'all just made typos, but I want to make sure that I'm not overlooking some subtle issue.

> **rplantz said:**
> 
```

   int x;
   int *xPtr;
   char y;
   char *yPtr;

   xPtr = &x;
   yPtr = &y;

   x++;
   y++;

```
the "++" operator adds 4 to the value (an address) stored in xPtr, but it adds 1 to the value (an address) stored in yPtr. (Assuming an environment where an int is 4 bytes in size.) I didn't think that incrementing a value in memory should change the location where the value is stored, but that's what I understand from your post.
In your last two lines, did you mean to type
```

xPtr++;
yPtr++;

```
?  I think the point that you were trying to make is that, whereas the *value of a pointer* is just an address, which is the same for any datatype, the *behavior* of that value according to some operation *does, in fact,* depend on what is being addressed, and the compiler automatically adjusts the behavior according to the datatype.  Then, by extension
```

void *ptr=malloc(ptr_size);
ptr++;

```
would increase the numerical value of the pointer by ptr_size.  Did I get your point?  That would indeed make sense to me and would help me to better understand the pointer datatype, even without dereferencing.

> **schauerlich said:**
> Think of
```
int i;
```
as a box, and
```
int int_ptr;
```
as an arrow. 

When you declare i, you're saying "here's a box. it can store an integer." When you declare int_ptr, you're saying "here's an arrow. it should point to a box that can store an integer."Did you simply forget the "*" prefix in the pointer declaration?  Or, is there something more subtle going on?

---

### Post by schauerlich on 2010-06-08
> **MichaelBurns said:**
> Did you simply forget the "*" prefix in the pointer declaration?  Or, is there something more subtle going on?

Yes I did, sorry. Fixed.

---

### Post by Bachstelze on 2010-06-09
> **MichaelBurns said:**
> Then, by extension
```

void *ptr=malloc(ptr_size);
ptr++;

```
would increase the numerical value of the pointer by ptr_size.  Did I get your point?

No. Protip: instead of waiting for someone to tell you whether your guess is right, just try it for yourself. ;) In the case of a void*:

```
firas@tsukino ~ % cat foo.c 
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    void *p;
    p = malloc(256);
    printf("Before: %p\n", p);
    p++;
    printf("After:  %p\n", p);
    return 0;
}

firas@tsukino ~ % cc -o foo foo.c
firas@tsukino ~ % ./foo          
Before: 0xfe8010
After:  0xfe8011

```

The address is incremented by one. In the case of an int*, it would be incremented by sizeof(int), which is generally 4:

```
firas@tsukino ~ % cat foo.c 
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int *p;
    p = malloc(256);
    printf("An int is %lu bytes long.\n", sizeof(int));
    printf("Before: %p\n", p);
    p++;
    printf("After:  %p\n", p);
    return 0;
}

firas@tsukino ~ % cc -o foo foo.c
firas@tsukino ~ % ./foo          
An int is 4 bytes long.
Before: 0xf04010
After:  0xf04014
```

When you increment a pointer, you say "point to the next element", so if an element takes n bytes, the address will be incremented by n, so that it does indeed point to the "start" of the next element, like this (assuming p is an int*):

```

-+---+---+---+---+---+---+---+---+-
 | int (4 bytes) |   other int   |
-+---+---+---+---+---+---+---+---+-
 ^    <->        ^               ^
 p    one       p+1             p+2
      byte
```

That's another reason why typed pointers are useful: so that the system knows by how much to increment the actual address when a pointer is incremented by one.

---

### Post by trent.josephsen on 2010-06-09
> **Bachstelze said:**
> No. Protip: instead of waiting for someone to tell you whether your guess is right, just try it for yourself. ;) In the case of a void*:
<code snipped>
The address is incremented by one.
It might be, but unfortunately you can't do that (TM).  No operation except conversion to another pointer type, assignment, and comparison to 0 (or NULL) is defined for a pointer to void.  Pointer arithmetic has undefined behavior.

---

### Post by Bachstelze on 2010-06-09
> **trent.josephsen said:**
> It might be, but unfortunately you can't do that (TM).

As Cartman says: "Oh yeah? I'm pretty sure I just did." It might not be standard, but some compilers, not only gcc, allow it, and I answered a specific question.

---

### Post by jim_24601 on 2010-06-09
Protip: "It works on my compiler" is a very bad argument in a C language discussion. Particularly when the compiler in question is gcc, which by default compiles a language that, although it resembles C quite closely, is not actually C.

---

### Post by Bachstelze on 2010-06-09
> **jim_24601 said:**
> Protip: "It works on my compiler" is a very bad argument in a C language discussion. Particularly when the compiler in question is gcc, which by default compiles a language that, although it resembles C quite closely, is not actually C.

Define "C"? I said that it is non-standard, what more do you want? Also lol @ "my compiler". I don't recall ever participating in gcc's development, you're fighting a straw man here.

---

### Post by BoneKracker on 2010-06-09
<deleted after deciding not to participate in counterproductive pissing contest>

Takeaways:

a) A pointer's increment and decrement operators alter the pointer address by sizeof(type) bytes. (As nicely demonstrated by Bachstelze)

b) Pointer arithmetic on type 'void' has undefined behavior (in one or more primary C standards) and should therefore be eschewed. (As astutely pointed out by jim_24601)

---

### Post by jim_24601 on 2010-06-09
> **Bachstelze said:**
> Define "C"? I said that it is non-standard, what more do you want?

I apologise for the snarkiness of my reply. I meant to point out that it is not good practice to rely on a given compiler to tell you what is valid C. The standard leaves enough things undefined that even a perfectly compliant compiler can throw up nasty surprises once you stray into the realm of undefined behaviour.

> Also lol @ "my compiler". I don't recall ever participating in gcc's development, you're fighting a straw man here.

I meant "my compiler" as in "the compiler I'm using", rather than "the compiler I developed".

---

### Post by MichaelBurns on 2010-06-09
I am enjoying the developing discussion.  Delicious!  Thank you, everyone.

@Bachstelze:
Thank you for that very valuable and thorough demonstration; it helps me to understand (in spite of the ensuing, and also valuable, "pissing contest" LOL).  Of course, I *do* try things myself, but my attempt to re-understand C at a "deep" level (deeper than my first attempt, anyway) has alerted me to the same basic problem that others have mentioned:  Beware of the leniancy provided by the C standard.  So, even if I try for myself (as I certainly agree that I should), I must do so on a specific compiler.  Therefore, I find it very beneficial to solicit the opinions of experienced programmers (such as yourself), and I greatly appreciate the time that you have taken to oblige.

Thanks, again, everyone.  I continue to watch this discussion with great interest (and amusement).

Here's a followup question:
Is sizeof(void)==1?  Again, I know that I can code this up, but in the meantime, and with respect to the "pissing contest", I also would like to hear what y'all have to say.

---

### Post by BoneKracker on 2010-06-09
GCC has flags you can use to restrict its behavior to be fully compliant with various dialects of C:

[http://gcc.gnu.org/onlinedocs/gcc/C-Dialect-Options.html](http://gcc.gnu.org/onlinedocs/gcc/C-Dialect-Options.html)

---

### Post by Bachstelze on 2010-06-09
> **MichaelBurns said:**
> 
Is sizeof(void)==1?  Again, I know that I can code this up, but in the meantime, and with respect to the "pissing contest", I also would like to hear what y'all have to say.

No, void does not have a size (this is why arithmetic on void pointers is not defined). gcc treats void as having size 1, but other compilers may think otherwise (or even give a completely random value based on the day of the week, phase of the moon or shape of the clouds, if they wish). So, yes, I answered your question about void pointer arithmetic, but I should really have mentioned that it is non-standard and shouldn't be relied upon.

If you want something that is guaranteed to have size 1 and can contain any value, use [font=monospace]unsigned char[/font].

---

### Post by trent.josephsen on 2010-06-09
> **MichaelBurns said:**
> Here's a followup question:
Is sizeof(void)==1?  Again, I know that I can code this up, but in the meantime, and with respect to the "pissing contest", I also would like to hear what y'all have to say.

Let's see what the [C Standard](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1256.pdf) has to say.

6.5.3.4p1 states that "the **sizeof** operator shall not be applied to an expression that has [...] an incomplete type [or] to the parenthesized name of such a type", and 6.2.5p19 makes it clear that **void** is an incomplete type (in fact, **void** is special in that it can never be made complete).

So, any code that tries to take sizeof(void) is in violation of the constraint 6.5.3.4p1.  Constraint violations require diagnostics, and GCC will give one if you use the -pedantic switch.  However, if you choose to ignore the diagnostic, your program invokes undefined behavior.  In practice this will most often mean that sizeof(void) gets replaced by 1.  But it might be different elsewhere.  Consider
```
int ary[10];
void *p = ary;
printf("%zu\n", sizeof *p);
```

It's possible for a theoretical C implementation to recognize that p points to an array of ints and assume that you want sizeof(int) in that last line.  And, since the behavior is undefined, the C implementation would be perfectly within its rights to replace sizeof *p with whatever the sizeof an int is (after generating the required diagnostic).  This is an instance where undefined behavior could be exploited to do fancy stuff.  In practice, you're much more likely to encounter the behavior that GCC exhibits.  However, [nasal demons](http://www.catb.org/jargon/html/N/nasal-demons.html) are also a possibility.

---

### Post by Compyx on 2010-06-09
> **Bachstelze said:**
> If you want something that is guaranteed to have size 1 and can contain any value, use [font=monospace]unsigned char[/font].

I assume you mean [font=monospace]unsigned char *[/font], which is close to the generic pointer type pre-ANSI, which was [font=monospace]char *[/font].

---

### Post by BoneKracker on 2010-06-09
Does gcc still treating void as having size 1 for pointer arithmetic purposes if the -ansi flag is invoked?

---

### Post by Bachstelze on 2010-06-09
> **BoneKracker said:**
> Does gcc still treating void as having size 1 for pointer arithmetic purposes if the -ansi flag is invoked?

Yes. The standard does not say that sizeof(void) must be a specific value, nor that it must throw an error, so a compiler is free to define it as anything it wants without violating the standard (and really, it *has to*, what else could it do?).

*EDIT: As trent.josephsen said, it will however throw a warning when called with the [font=monospace]-pedantic[/font] flag.*

---

### Post by BoneKracker on 2010-06-09
> **Bachstelze said:**
> Yes. The standard does not say that sizeof(void) must be a specific value, nor that it must throw an error, so a compiler is free to define it as anything it wants without violating the standard (and really, it *has to*, what else could it do?).

Throw an error?

---

### Post by jim_24601 on 2010-06-09
> **trent.josephsen said:**
> Let's see what the [C Standard](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1256.pdf) has to say.

OK, as the first person to cite the C standard, you officially win the pissing contest :)

Bearing in mind my own warning about taking compiler behaviour as gospel, I checked what is returned by sizeof(void) on a couple of compilers. gcc with command-line defaults silently accepts the code and returns 1. Microsoft's compiler (from VS.NET 2003) gives a warning, but compiles the code nevertheless and returns 0. (And I don't think it's very polite of gcc to effectively accuse us of pedantry for asking it to follow the standard.)

So yeah. sizeof(void) is undefined, and the compiler, although it should warn you, is at liberty to return whatever it likes. 0, 1, 69 ...

---

### Post by Bachstelze on 2010-06-09
> **BoneKracker said:**
> Throw an error?

That could be another possibility (someone correct me if I'm wrong: is it okay to throw an error when the standard does not explicitly say one must be thrown?), but the standard does not say it has to, so it's okay if it does not. Of course, it could do anything, my point in asking "what else could it do?" was that any option would be equally valid in terms of standard compliance, since the standard precisely does not say anything about what to do.

---

### Post by Compyx on 2010-06-09
[QUOTE="ISO/IEC 9899:1999"]
6.5.3.4 The sizeof operator

Constraints

1. The sizeof operator shall not be applied to an expression that has function type or an incomplete type, to the parenthesized name of such a type, or to an expression that designates a bit-field member.
[/QUOTE]

Since void is an incomplete type, applying the sizeof operator to void is a constraint violation, which requires a diagnostic. At least that's what I make of it, though I'm not that well versed in standardese.

Then again, Mark Adler (author of zlib), used arithmetic on void* in the zlib code, until someone in comp.lang.c mentioned that that was not strictly allowed by the standard. The zlib code has always worked properly on a wide variety of systems, so the Standard and real-life code can co-exist peacefully, it seems.

Another thing the standard forbids is converting between void* and function pointers, although that is exactly what POSIX requires with the dlsym() call. In such a case I decide to ignore the C standard and go with the POSIX specification.
So although I think it's a good thing to have a standard, it is by no means sacred in my book.

---

