---
title: "[C] ANSI types and string.h"
date: 2009-12-24
forum: Programming Talk
---

### Post by jonszy on 2009-12-24
I typically do more embedded programming, often using ANSI types in order to explicitly describe variables' size and signedness.

While writing an application for my PC, I ran into a strange warning.  I was hoping someone could explain why this error occurs, and provide some insight on how to use ANSI types correctly with libraries whose arguments and return values are just the built-in types.

**Snippet:**
```

int8_t      my_str[] = "This is a test string."
uint32_t    str_len;

/* This results in an error when compiling with gcc's -Wall flag */
str_len = strlen(  my_str );

```**Warning:**
```
pointer targets in passing argument 1 of 'strlen' differ in signedness
```[I][B]

stdint.h [/B][/I][B]Snippet:
[/B]```
typedef signed char             int8_t;

```Casting my_str to a (char*) obviously clears up the error.  (Although casting it to a signed char* still results in the above warning.)  However, I feel like this casting defeats the point of using ANSI types.  

To bring this all into a single question -- what's the difference between signed char and char, such that the compiler throws a fit?  I was assuming that since char is not unsigned, that it must be the case that signed char == char.   I was planning to look at the language spec when I get a chance, but was hoping someone could save me some time.  Thanks!

---

### Post by MadCow108 on 2009-12-24
a string literal, as you use it, is a pointer to a unsigned char which is unsigned (and usually bigger than 1 byte).
but you assign it to a int8_t which is signed and no pointer!

this should be correct:
char * my_str = "...";

in case this was just a typo, then the problem is related to char itself. the char type can be signed or unsigned. What it is defers from machine to machine
you can change how gcc handles it with the -fsigned-char -funsigned-char flag
in case of your warning char is obviously a unsigned char and int8_t is signed => sign mismatch

also strlen returns size_t, so you should use that instead of uint32_t. size_t is always defined to the right type for the return.

---

### Post by jonszy on 2009-12-24
Thanks MadCow108.  What you've said makes sense -- using the types dictated by the manual page is generally a help ;)

I've been on projects where our "standard" dictates that we only use the ANSI types.  Any idea what's the generally good practice for writing standard-compliant and portable code?

---

### Post by MadCow108 on 2009-12-24
the builtin types are ansi types. the _t things from stdint.h you are using are just additional types added in the C99 standard for better int handling.
The standard library is designed to be portable. If you stick to its types you will not create problems.

also I just tested, gcc 4.4.1 seems to throw spurious warnings if you use (un)signed char* on a string literal.
I don't know why, it should be no error for at least one of the two possiblities.
just stick to char* for literals, this is always correct as they are defined to be char*.

---

### Post by ju2wheels on 2009-12-25
[http://www.trilithium.com/johan/2005/01/char-types/](http://www.trilithium.com/johan/2005/01/char-types/)

In general, the reality is that the system and architecture you use can create differences.

"a string literal, as you use it, is a pointer to a unsigned char which is unsigned (and usually bigger than 1 byte).
but you assign it to a int8_t which is signed and no pointer!"

No, only the signedness is in question here. int8_t var[] is int8_t* var so it is a pointer.

---

### Post by jonszy on 2009-12-25
That's my fault -- I made a typo in posting the example, and forgot to add the []'s -- should have marked the update in the original posting.

I guess what I'm really looking for here is an explanation of why stdint.h exists, and how to use it properly.  I like using these explicit types when working on a micro, because it makes it very clear of how you're working with data (i.e. I don't have to think, "Now what's a signed 16-bit integer value on this architecture?" ). 

Furthermore, I've been operating under the assumption that using these sort of typedef'd types lend to easily portable code -- for example, when moving from a 16-bit micro to a 32-bit micro, it's certainly easier to make a new header file with typedefs than to run through a bunch of source files making changes.

However, it's obviously a problem when libraries aren't using the same typedef'd types. Anyone have any clean tricks/solutions?

---

### Post by MadCow108 on 2009-12-25
stdint does exist to increase portability.
pre C99 C only had guarantees of minimum size, like int was guaranteed to be 32 bit wide, but it could also be 64 bit wide.
in stdint now are typedef's to integers which are guaranteed the right size.

if your code requires 32 bit integers and want to compile and run it also on 64 bit machines you have to use the stdint types (or make your own typedefs)
if you use the plain old int, your code may break because int will be 64 bit wide on most 64 bit machines and 32 bit wide on 32 bit machines whereas uint32_t will always be 32 bit wide also on a 64 bit machine.

if you have a library which code is dependent on the width of types and doe not use the safe typedefs you have a problem.
You'll have to go through the code and fix the problems or use a better library.

---

