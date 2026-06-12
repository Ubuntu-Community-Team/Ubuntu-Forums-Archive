---
title: "putting an int into a char array using C?"
date: 2010-11-18
forum: Programming Talk
---

### Post by smdawson on 2010-11-18
I cannot remember if there is another way to put an integer into a character string in C, without using itoa(). I don't know if itoa() is a part of the C library or C++ library but my reference to it is coming up "undefined" when I try to compile my program. Can anyone tell me if there is a way to solve this or if itoa() is the common solution?

---

### Post by worksofcraft on 2010-11-18
> **smdawson said:**
> I cannot remember if there is another way to put an integer into a character string in C, without using itoa(). I don't know if itoa() is a part of the C library or C++ library but my reference to it is coming up "undefined" when I try to compile my program. Can anyone tell me if there is a way to solve this or if itoa() is the common solution?

my understanding is that a char is just an 8 bit int, so all you have to do is cast your int to a char and it will bung the ls 8 bits of your int into the char value and lose the rest.

OTOH if you want to write it's value as a decimal ascii string you could try [snprintf()]("http://www.cplusplus.com/reference/clibrary/cstdio/sprintf/") because [itoa]("http://www.cplusplus.com/reference/clibrary/cstdlib/itoa/") is not a standard function.

---

### Post by saulgoode on 2010-11-18
The standard way to do this is with 'sprintf()'.

---

### Post by smdawson on 2010-11-19
I looked up sprintf() but it looks like that is just for output. I need to put variable integers into a character array. Are there any other solutions out there?

---

### Post by Arndt on 2010-11-19
> **smdawson said:**
> I looked up sprintf() but it looks like that is just for output. I need to put variable integers into a character array. Are there any other solutions out there?

The printf family is indeed described as "formatted output conversion", but did you read beyond the first sentence of the description section in the manual page?

"sprintf(),  snprintf(),
       vsprintf() and vsnprintf() write to the character string str"

---

### Post by nvteighen on 2010-11-19
Hm... "putting an int into a char array" can mean several things.

1) A contradiction: if you want to put an integer, why did you declare a char *?
2) You want to decompose the integer into several characters, such that 123 becomes {'1', '2', '3'}
3) You want to convert the integer into a string (a char *), so that 123 becomes "123\0".

1) is obviously impossible... either you get a third-party library that provides heterogenous lists for C or you better switch to another language that supports them from start, as C doesn't.

And if you look at it carefully, 2) and 3) are actually the same thing (the only difference being the NULL character)... And that's done using snprintf() by outputting into a string.

---

### Post by lisati on 2010-11-19
> **nvteighen said:**
> Hm... "putting an int into a char array" can mean several things.


Agreed. Another meaning that comes to mind is where you have a character string and you want to append a character for which you have the numeric code, e.g. 0x20 for a space. A simple copy/assignment, with castings as required, might suffice.

---

### Post by trent.josephsen on 2010-11-19
My first thought was that the OP actually wanted to use an int to initialize memory belonging to a character array, like so:
```
char ary[4];
*(int *)ary = 0x6b656547;
```

Needless to say, don't do that.

---

