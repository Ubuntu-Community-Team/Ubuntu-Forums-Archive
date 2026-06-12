---
title: "[SOLVED] Boolean variables in C"
date: 2009-01-10
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-10
I want a boolean variable, which needs only 1 bit memory, 
and can have either 1 or 0 as value, of course.

But C doesn't have a boolean variable by default, so how to make one?

---

### Post by jimi_hendrix on 2009-01-10
a)

```

#import <boolean.h>

```

b)

```

enum bool = {false, true};

```

c)

```

#define bool int
#define true 1
#define false 0

```

should all work

---

### Post by SledgeHammer_999 on 2009-01-10
Of course C has built-in boolean variables
```
bool var;
var = false;
var = true;
```

In this example var is 1 byte in size.

---

### Post by jimi_hendrix on 2009-01-10
not ANSI C iirc...what C are you useing?!?!

---

### Post by Bachstelze on 2009-01-10
> **SledgeHammer_999 said:**
> Of course C has built-in boolean variables
```
bool var;
var = false;
var = true;
```

In this example var is 1 byte in size.

No it doesn't.

```
firas@itsuki ~ % cat bool.c
int main(void)
{
        bool var;
        var = true;
        return 0;
}

firas@itsuki ~ % cc -o bool bool.c
bool.c: In function 'main':
bool.c:3: error: 'bool' undeclared (first use in this function)
bool.c:3: error: (Each undeclared identifier is reported only once
bool.c:3: error: for each function it appears in.)
bool.c:3: error: expected ';' before 'var'
bool.c:4: error: 'var' undeclared (first use in this function)
bool.c:4: error: 'true' undeclared (first use in this function)

```

---

### Post by mali2297 on 2009-01-10
> **jimi_hendrix said:**
> a)

```

#import <boolean.h>

```


Rather...
```

#include <stdbool.h>

bool b = false;

```

---

### Post by jimi_hendrix on 2009-01-10
havnt had a need to use the lib in a while...thanks

---

### Post by dwhitney67 on 2009-01-10
> **jimi_hendrix said:**
> havnt had a need to use the lib in a while...thanks
:confused:   What lib are you referring to?

---

### Post by jimi_hendrix on 2009-01-10
*fails at vocab*
the header

---

### Post by monkeyking on 2009-01-10
> **crazyfuturamanoob said:**
> I want a boolean variable, which needs only 1 bit memory, 
and can have either 1 or 0 as value, of course.

But C doesn't have a boolean variable by default, so how to make one?

It's quite impossible to have 1bit variables as primitive types in c/c++.

The smallest amount of memory you can access directly is a byte,
this is defined as the size of a char by CHAR_BIT.

If you still want this lowmemory variable you can still implement it by extracting and shifting bitpatterns.

If you use c++
then you can use vector<bool> which will try to pack it and spaceoptimize.

The vector<bool> type is very different from the other vector<T> types. [http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=98](http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=98)

good luck

---

### Post by Cracauer on 2009-01-10
You can't have one variable that only occupies one bit.


You can have a bunch of variables each occupying one bit two ways:

structs with bit width field

```

struct {
  int blah: 1;
  int fasel: 1;
  int blubb: 1;
};

```

Or you can manually pack them into a bit-vector of your choice (usually operates on a long int).

---

### Post by SledgeHammer_999 on 2009-01-10
> **HymnToLife said:**
> No it doesn't.

```
firas@itsuki ~ % cat bool.c
int main(void)
{
        bool var;
        var = true;
        return 0;
}

firas@itsuki ~ % cc -o bool bool.c
bool.c: In function 'main':
bool.c:3: error: 'bool' undeclared (first use in this function)
bool.c:3: error: (Each undeclared identifier is reported only once
bool.c:3: error: for each function it appears in.)
bool.c:3: error: expected ';' before 'var'
bool.c:4: error: 'var' undeclared (first use in this function)
bool.c:4: error: 'true' undeclared (first use in this function)

```

I FAIL! hahahaha
I was under the impression that it has "bool". I have been using till today C++ and I thought that this fundamental type was available in C too... I guess I was totally wrong.

---

### Post by jimi_hendrix on 2009-01-10
hehe...for loops are different too...cant declare a new var in the for () part...only assign a value

---

### Post by snova on 2009-01-10
There is a _Bool type.

---

### Post by jimi_hendrix on 2009-01-10
since when?

---

### Post by dwhitney67 on 2009-01-10
> **SledgeHammer_999 said:**
> I FAIL! hahahaha
I was under the impression that it has "bool". I have been using till today C++ and I thought that this fundamental type was available in C too... I guess I was totally wrong.

This was what I thought too, but I was proven wrong.

If you want the 'bool' type in a C program, **#include <stdbool.h>**.

---

### Post by dwhitney67 on 2009-01-10
> **jimi_hendrix said:**
> hehe...for loops are different too...cant declare a new var in the for () part...only assign a value

That is because you are probably using the ISO C standard adopted in the stone-ages.  Use a more current version (e.g. 1999 standards), then you can declare variables in C at the closest point where needed.

---

### Post by snova on 2009-01-10
> **jimi_hendrix said:**
> since when?

Since I tried it, at the least. :P

test.c:

[PHP]int main()
{
    _Bool b;
    return 0;
}[/PHP]

```
gcc -o test test.c
```

No problems here...

---

### Post by jespdj on 2009-01-10
I don't know where that _Bool type comes from, but it is certainly not standard C.

C has [bit fields](http://en.wikipedia.org/wiki/Bit_field), that's the closest you can come to a boolean that takes only 1 bit of memory space.

---

### Post by samjh on 2009-01-10
_Bool is part of the C99 standard, contained in stdbool.h.

---

### Post by jimi_hendrix on 2009-01-10
> **dwhitney67 said:**
> That is because you are probably using the ISO C standard adopted in the stone-ages.  Use a more current version (e.g. 1999 standards), then you can declare variables in C at the closest point where needed.

i just use what gcc says...how do i use C99 (i thought it wasnt ansi)

---

### Post by wmcbrine on 2009-01-10
Bit fields are unreliable (their representation may vary), and yes, the bool type is only in C99 (C89 is still the de facto standard), and wouldn't do what you want anyway.

The normal way to handle this in C is to use the bitwise operators to arrange multiple boolean flags into a char, int or long. For example:

```

#define MASK_FOO 1
#define MASK_BAR 2  /* next would be 4, 8, etc. */

unsigned char flags = 3;

if (flags & MASK_BAR)
    printf("Bar is set!\n");

flags &= ~(MASK_FOO);  /* unset foo */

```

Etc.

---

### Post by jpkotta on 2009-01-11
In C, any value that isn't equal to 0 is true.  This goes for pointers, numeric types, enums, floats, etc.  structs can't be compared so they don't count.  

To alias a value to 0 or 1, you can apply logical not twice:
```

int bool = !!(bitvector & MASK); /* bool is 0 or 1 */

```

---

### Post by PmDematagoda on 2009-01-11
> **samjh said:**
> _Bool is part of the C99 standard, contained in stdbool.h.

_Bool is part of C99, but it is not contained in stdbool.h, stdbool.h contains the bool type. stdio.h has _Bool, and _Bool can have either 0 or 1.

---

### Post by PmDematagoda on 2009-01-11
> **jimi_hendrix said:**
> i just use what gcc says...how do i use C99 (i thought it wasnt ansi)

GCC can use _Bool, I've used it plenty of times with only the stdio.h header. And you don't need to tell it to use a specific type of standard either. And, correct me if I'm wrong, but isn't C99 the new ANSI/ISO standard for C?

---

### Post by mdurham on 2009-01-11
> **jpkotta said:**
> To alias a value to 0 or 1, you can apply logical not twice:
```

int bool = !!(bitvector & MASK); /* bool is 0 or 1 */

```
V Clever

---

### Post by Npl on 2009-01-11
> **PmDematagoda said:**
> GCC can use _Bool, I've used it plenty of times with only the stdio.h header. And you don't need to tell it to use a specific type of standard either. And, correct me if I'm wrong, but isn't C99 the new ANSI/ISO standard for C?
Well, theres no reason to use _Bool. just include stdbool.h which will work transparently with all C Versions.

AFAIK all recent C Versions are ISO-Standards, very very long ago it was an ANSI standard. ANSI-C denotes the stone-old Version at any rate, and theres little reason to use it.

---

### Post by Npl on 2009-01-11
> **jpkotta said:**
> In C, any value that isn't equal to 0 is true.  This goes for pointers, numeric types, enums, floats, etc.  structs can't be compared so they don't count.  

To alias a value to 0 or 1, you can apply logical not twice:
```

int bool = !!(bitvector & MASK); /* bool is 0 or 1 */

```
Its more efficient to compare against 0:
```
int bool = (bitvector & MASK) != 0;
```

---

### Post by PmDematagoda on 2009-01-11
> **Npl said:**
> Well, theres no reason to use _Bool. just include stdbool.h which will work transparently with all C Versions.

AFAIK all recent C Versions are ISO-Standards, very very long ago it was an ANSI standard. ANSI-C denotes the stone-old Version at any rate, and theres little reason to use it.

Even though there may not be much of a reason to use _Bool, you can use it, that's just it:).

---

### Post by crazyfuturamanoob on 2009-01-11
Looks like it's just easier to use integers for this. :S

---

### Post by samjh on 2009-01-11
> **crazyfuturamanoob said:**
> Looks like it's just easier to use integers for this. :S

You are correct. :)

Even stdbool's booleans are just typedefs and macros.  Nothing special.  IMHO, it's of no use except to enhance readability.

---

### Post by wmcbrine on 2009-01-11
> **Npl said:**
> ANSI-C denotes the stone-old Version at any rate, and theres little reason to use it.ANSI C is old, but it's nowhere near as old as "K & R" C (so named because it's defined by the first edition of the K & R book, rather than by a standards committee). *That's* the "old version".

ANSI C, aka C89, is the most widely-implemented version of the language, and it's still the standard that gcc defaults to. You have to give gcc an option to tell it to use C99 -- and in fact, C99 is not quite fully supported even now. So yes, there's good reason to use ANSI C.

But there's no longer much reason to use K & R C, which is the one where functions look like this:

```

foo(a, b)
int a;
int b;
{
...

```

instead of:

```

int foo(int a, int b)
{
...

```

---

### Post by Cracauer on 2009-01-11
The original poster explicitly said he wants one that takes up one bit (presumably when combined with other bools).

So C99's bool is out.

In C++ they decided to kick out explicit bit-vectors in favor of telling the user to hope that vector<bool> will be specialized to a bit-fiddling facility. Sometimes I don't get these people...

---

### Post by jpkotta on 2009-01-11
> **Npl said:**
> Its more efficient to compare against 0:
```
int bool = (bitvector & MASK) != 0;
```

Not always.  I'm not sure if this is ever the case.  They compile to the same thing for me (I only tested on one machine, with and without -O2), and this is exactly what I would expect for any decent compiler.

```
#include <stdint.h>
#define MASK (1<<10)

int double_negative(uint32_t bv)
{
    return !!(bv & MASK);
}

int cmp_zero(uint32_t bv)
{
    return (bv & MASK) != 0;
}
```

```
gcc bool.c -c
objdump -d bool.o
```

```
00000000 <double_negative>:
   0:	55                   	push   %ebp
   1:	89 e5                	mov    %esp,%ebp
   3:	8b 45 08             	mov    0x8(%ebp),%eax
   6:	25 00 04 00 00       	and    $0x400,%eax
   b:	85 c0                	test   %eax,%eax
   d:	0f 95 c0             	setne  %al
  10:	0f b6 c0             	movzbl %al,%eax
  13:	5d                   	pop    %ebp
  14:	c3                   	ret    

00000015 <cmp_zero>:
  15:	55                   	push   %ebp
  16:	89 e5                	mov    %esp,%ebp
  18:	8b 45 08             	mov    0x8(%ebp),%eax
  1b:	25 00 04 00 00       	and    $0x400,%eax
  20:	85 c0                	test   %eax,%eax
  22:	0f 95 c0             	setne  %al
  25:	0f b6 c0             	movzbl %al,%eax
  28:	5d                   	pop    %ebp
  29:	c3                   	ret   
```

So it all comes down to which is more readable.  Personally, I think mine is, but I'm biased.  Obviously it doesn't really matter, because you could make a macro that implements either one.
```

#define BOOLIFY1(x) (!!(x))
#define BOOLIFY2(x) ((x) != 0)
```

---

