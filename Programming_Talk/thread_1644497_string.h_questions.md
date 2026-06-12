---
title: "string.h questions"
date: 2010-12-13
forum: Programming Talk
---

### Post by nolag on 2010-12-13
I noticed that in many functions of string.h they take an int and interpert it as an unsigned char.  I am wondering why they don't just take an unsigned char?
 
For the call 
 
```
 
char str[] = "almost every programmer should know memset!";
memset (str,'-',6);


```
 
they use a char there, so it is fine, but if they had used 
 
```
 
char str[] = "almost every programmer should know memset!";
int c = 'a'<< 24 | 'b'; //a is now in the 1st 8 bits and b in the last 8 0's in between.
memset (str,c,6);

```
 
what would the result be?  It just seems odd that they would use an int and interpert it as an unsigned char, wond the 'b' part just be ignored, even though the integer has a legit meaning?

---

### Post by worksofcraft on 2010-12-13
> **nolag said:**
> I noticed that in many functions of string.h they take an int and interpert it as an unsigned char.  I am wondering why they don't just take an unsigned char?
 
For the call 
 
```
 
char str[] = "almost every programmer should know memset!";
memset (str,'-',6);


```
 
they use a char there, so it is fine, but if they had used 
 
```
 
char str[] = "almost every programmer should know memset!";
int c = 'a'<< 24 | 'b'; //a is now in the 1st 8 bits and b in the last 8 0's in between.
memset (str,c,6);

```
 
what would the result be?  It just seems odd that they would use an int and interpert it as an unsigned char, wond the 'b' part just be ignored, even though the integer has a legit meaning?

According to the documentation it should just discard the most significant bits, so it is the b that gets used and the a that is not.

I also agree that it is very bad practice to not declare things of the appropriate type.

---

### Post by nolag on 2010-12-13
> **worksofcraft said:**
> According to the documentation it should just discard the most significant bits, so it is the b that gets used and the a that is not.
 
I also agree that it is very bad practice to not declare things of the appropriate type.
 
Wait where did you read that?  From what I read it says "converted to unsighed char", so I would assume it would do:
 
```
 
function(void* something, int c, size_t n){
  int i = 0;
  for (;i < n;i++){
    something[x] = (unsighned char) c;
  }
}

```
 
Won't that just take it like the address of c interperted as an unsigned char?  If so then it only takes the most significant.
 
Also I am glad you agree it is bad practice, I wonder why it is done this way...

---

### Post by trent.josephsen on 2010-12-13
Look up "default argument promotions".

In pre-ANSI C, function prototypes did not exist, so to make sure function arguments were placed on the stack predictably, certain promotions were performed on every function argument.  E.g., when you wrote
```
func(3, 'a');
```
both the 3 and the 'a' would be promoted to int, and func would probably be defined something like
```
func(arg0, arg1)
int arg0;
int arg1;
{ ... }
```
IIRC you might declare arg1 as char if you so desired, but that would only mean that the number, after being converted to an int for passing in, would be converted back to a char in the function.  (But I could be wrong.)

Anyway, when C89 introduced function prototypes, it became possible to tell the compiler ahead of time what arguments a function would expect; among other things, this can limit the amount of wasted space on the stack when passing a char or a short (which would otherwise take up the same amount of space as an int).

But C89's job was primarily to document existing practice, not to change it.  So the old rules were left in there, and most of them are still there.  The old promotions still apply to calls to variadic functions like printf, because they can't know what size variables to expect.  Moreover, functions like memset, which existed before the Standard, were still using the old conventions, expecting char arguments to be passed in ints.  Sending a char-sized object to a function expecting an int-sized one could result in disaster, so rather than break all the existing C libraries, it was decided that those old functions would take int arguments and convert them according to the regular rules.

You can still find C libraries that don't prototype their functions, and they depend on this behavior to work.  You can even use them without including the header files;
```
int memset();
```
will suppress the warning if you neglect to #include <stdlib.h>, and you are perfectly OK with using printf with such a declaration, but since it's not prototyped, the compiler can't warn you about passing the wrong parameters.

(There's another reason for char to be int in some functions, e.g. getchar, which has to be able to return EOF in addition to all the possible values of char.)

---

### Post by trent.josephsen on 2010-12-13
BTW, worksofcraft is right, only the least-significant byte will be used.  Conversion is not the same as reinterpreting a pointer.

(If it had worked as you expected, then on a system where sizeof(int) == 4, the value used would always be 0 -- because the high byte of (int)c is always 0.  There's not much use for a memset that always interprets its middle argument the same way.)

---

### Post by nolag on 2010-12-13
> **trent.josephsen said:**
> BTW, worksofcraft is right, only the least-significant byte will be used. Conversion is not the same as reinterpreting a pointer.
 
(If it had worked as you expected, then on a system where sizeof(int) == 4, the value used would always be 0 -- because the high byte of (int)c is always 0. There's not much use for a memset that always interprets its middle argument the same way.)
 
Wait, why would the high byte of int(c) be 0 if sizeof(int) == 4? 
 
[--------] -------- -------- --------
 
why is the hight byte (in []) always 0? 
 
c = FF000000 would make
 
[11111111] 00000000 00000000 00000000
 
If I had the byte b = FF = 11111111 and interpert as an int the way I said it would see the address of b and would see (in hex) 
 
FF xx xx xx where x is unknown (whatever just so happens to be there).

---

### Post by dwhitney67 on 2010-12-13
> **nolag said:**
> Wait, why would the high byte of int(c) be 0 if sizeof(int) == 4? 
 
[--------] -------- -------- --------
 
why is the hight byte (in []) always 0? 
 
c = FF000000 would make
 
[11111111] 00000000 00000000 00000000
 
If I had the byte b = FF = 11111111 and interpert as an int the way I said it would see the address of b and would see (in hex) 
 
FF xx xx xx where x is unknown (whatever just so happens to be there).

I have no idea what you are attempting to state, or ask, above.

Try this little nugget to help you understand what part of an int is extracted when it is converted to an unsigned char.
```

#include <stdio.h>

int main(void)
{
   int val = 0xCAFEBABE;

   printf("val = %x\n", val);

   printf("val as unsigned char = %x\n", (unsigned char) val);

   return 0;
}

```

---

### Post by nolag on 2010-12-13
> **dwhitney67 said:**
> I have no idea what you are attempting to state, or ask, above.
 
Try this little nugget to help you understand what part of an int is extracted when it is converted to an unsigned char.
```

#include <stdio.h>
 
int main(void)
{
   int val = 0xCAFEBABE;
 
   printf("val = %x\n", val);
 
   printf("val as unsigned char = %x\n", (unsigned char) val);
 
   return 0;
}

```
 
 
Good idea, I was going to when I get home!  I am guessing CAFE, but from the sounds of what is being said it sounds like it's BABE :(.  I thought of it in terms of a pointer so
 
-> [CAFEBABE] if it is an int but -> [CAFE]BABE if it was char (unsigned or not does not matter).  Unless the endianness of x86 makes me wrong [CAFEBABE] <- (for int) and CAFE[BABE] <- (for char), but then how would C not vary by platform?

---

### Post by worksofcraft on 2010-12-13
> **nolag said:**
> Good idea, I was going to when I get home!  I am guessing CAFE, but from the sounds of what is being said it sounds like it's BABE :(.  I thought of it in terms of a pointer so
 
-> [CAFEBABE] if it is an int but -> [CAFE]BABE if it was char (unsigned or not does not matter).  Unless the endianness of x86 makes me wrong [CAFEBABE] <- (for int) and CAFE[BABE] <- (for char), but then how would C not vary by platform?

You might want to read about the terms ["littleendian" and "bigendian"]("http://en.wikipedia.org/wiki/Endianness") which causes no end of incompatibilities will poorly designed code.

In a nutshell, there are different processor architectures that produce different (swapped) byte orders in memory.

So called littleendian processors like Intel x86 store the little (least significant) byte at the beginning (lower memory address) while bigendian processors such as Motorola 68k store it at the  end (higher address) and have the big (most significant) byte at the beginning... and yes it does seem they got those names round the wrong way sometimes :D

---

### Post by trent.josephsen on 2010-12-13
Good point.

Notably, since C doesn't "know" what kind of platform it's on, code that depends on endianness has undefined behavior.

```
char c = 'a';
void *p = &c;
int i = *(((int *)p);
```

(unless I have overlooked something) might come up with i == 'a' on a little-endian system, might come up with i == 0 on a big-endian system, but it's also likely to do nothing useful at all, at least in theory.  Undefined behavior can do anything.

However, that has absolutely no bearing on the original topic.

---

### Post by dwhitney67 on 2010-12-14
> **trent.josephsen said:**
> 
However, that has absolutely no bearing on the original topic.
Of course it is on topic; consider this:
```

#include <stdio.h>

int main(void)
{
   int x = 1;

   printf("You are using a %s endian system.\n", ((unsigned char) x == 1 ? "little" : "big"));
   return 0;
}

```

Btw, I haven't tested the code above with a big endian system to verify if it is correct or not.  Code I've seen in the past utilized something like this instead:

```

#include <stdio.h>

int main(void)
{
   union
   {
      unsigned int  ui;
      unsigned char uc[4];
   } x;

   x.ui = 1;

   printf("You are using a %s endian system.\n", (x.uc[3] == 1 ? "big" : "little"));

   return 0;
}

```

---

### Post by nolag on 2010-12-14
Yeah, I knew the difference, I thought that casting worked like pointers.  I then relized that it can't or it would cause problems with simple things like we discussed (and I know that casting must be platform independant?).  I forgot to try that code yesterday :P.  I will tonight.  I am making my own string.h (I want to make my own small OS for learning and because I will be making one for coldfire for school soon), that was why I asked :D (also I still think it is weird and wrong).

---

### Post by trent.josephsen on 2010-12-14
@dwhitney:  Explicit conversions like (unsigned char)x have well-defined behavior; your example will always print "little".  You would need to do *((unsigned char *)&x) to determine endianness.

Edit:  also, IIRC, == will promote both its arguments to int for comparison, so you're not even comparing a char to a char.

@nolag:  Weird, sure.  Wrong, well, the worst it can do is waste a few bytes on the stack, and it allows you to call functions without a proper prototype in scope -- which isn't a good idea for user code, but for somebody who's writing a toolchain, might indeed come in handy.

---

### Post by worksofcraft on 2010-12-16
I just came up with this related problem:

I'm testing if characters are ascii digits using
[php]
int isdigit(int c)
[php]

... but the character I'm using is a full Unicode value (so up 21 bits can be occupied). Evidently I don't want to classify codes that have higher bytes set as digits just because the low byte is one... and to make matters worse there are locale dependent versions of isdigit that recognize digits from other languages...

So now IDK what the standard is, but luckily it is such a simple function that writing my own shouldn't have too many bugs :D

---

### Post by dwhitney67 on 2010-12-16
> **worksofcraft said:**
> I just came up with this related problem:

I'm testing if characters are ascii digits using
[php]
int isdigit(int c)
[php]

... but the character I'm using is a full Unicode value (so up 21 bits can be occupied). Evidently I don't want to classify codes that have higher bytes set as digits just because the low byte is one... and to make matters worse there are locale dependent versions of isdigit that recognize digits from other languages...

So now IDK what the standard is, but luckily it is such a simple function that writing my own shouldn't have too many bugs :D

I don't know if it will buy you anything, but try using iswdigit() for wide-characters.  Include <wctype.h>.

---

