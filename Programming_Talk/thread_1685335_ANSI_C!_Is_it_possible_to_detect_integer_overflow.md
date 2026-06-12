---
title: "ANSI C! Is it possible to detect integer overflow?"
date: 2011-02-10
forum: Programming Talk
---

### Post by mimiteto on 2011-02-10
I have a homework (c course in the college), and one of my the problems is to detect integer overflow, but I can't find standard method of doing it. I found some posts over the net, but none of them seemed to work every time or to be platform AND compiler independent. Thank you in advance for the help, guys :D

---

### Post by lisati on 2011-02-10
/me smiles and thinks of an answer which might *sometimes* work if you were using assembler instead of C.

This is a very good question to which I don't have an answer specific to C. 

Here's my $0.02: Satisfactorily dealing with situations where the data processed by a program tests the program's ability to produce a useful result is something that you'll need to give some thought to at some point, regardless of programming language. My advice is to think about what integer overflow is, and how you might recognize when it happens within your program.

---

### Post by trent.josephsen on 2011-02-10
Detecting integer overflow is theoretically easy.  Assuming signed two's-complement addition, integer overflow occurs when
1) adding a positive number to a positive number results in a negative number
2) adding a negative number to a negative number results in a positive number

So you can determine whether overflow occurred by checking the sign of the result and comparing it to the signs of the operands.  Multiplication requires more checks (and can wrap around multiple times), but it's still possible to test for in similar fashion.

But you said ANSI C.  I don't have a copy of the Standard, but I'm certain that integer overflow causes either implementation-defined or undefined behavior (I think the first).  Checking the signs of the operands and result therefore isn't guaranteed to work *by ANSI*, although it is very likely to work on most ANSI-conforming implementations.  Sign-and-magnitude and saturation arithmetic are likely to foil this approach on systems that use them.

The only ANSI standard way to detect overflow is before it happens.  Check out [http://c-faq.com/misc/intovf.html](http://c-faq.com/misc/intovf.html).

---

### Post by mimiteto on 2011-02-11
Thank you for the answers :)
Actually, when I posted this thread, I already had the idea about obvious overflow (that thing with INT_MAX - a < b), but it's not working most of the time (ex. 999999999999999999 + 203). Thats driving me crazy :mad: If teacher gave us such task, it must be extremely easy. (ANSI C class is far from our main subject). Thank you again guys.

---

### Post by Vaphell on 2011-02-11
let's say you have 2digit unsigned decimal system (0-99)
1. compare
```
50+30=80    50 _ 80 and 30 _ 80 - fill with one of following: < > = >= <=
```
with
```
99+30=29    99 _ 29 and 30 _ 29 - fill with one of following: < > = >= <=
```
now find the difference

2. compare
```
90-50=40   90 _ 40
```
with
```
5-90=15    5 _ 15
```
again, find the difference

---

### Post by worksofcraft on 2011-02-11
> **mimiteto said:**
> Thank you for the answers :)
Actually, when I posted this thread, I already had the idea about obvious overflow (that thing with INT_MAX - a < b), but it's not working most of the time (ex. 999999999999999999 + 203). Thats driving me crazy :mad: If teacher gave us such task, it must be extremely easy. (ANSI C class is far from our main subject). Thank you again guys.

Most processors simply have a status flag that gets set when there is integer overflow, but many C compilers do have an option to create the instructions necessary to test that flag at run time.

However the constant express 99999999999999999999 + 203 is evaluated at compile time so the only time you can detect the overflow is when you compile the program:
[php]
/* gcc overflow.c */
#include <stdio.h>

int main() {
	int X = 99999999999999999999 + 203;
	return !printf("X=%d\n", X);
}
[/php]

```

$ gcc overflow.c
overflow.c:5:10: warning: integer constant is too large for its type
overflow.c: In function ‘main’:
overflow.c:5: warning: overflow in implicit constant conversion

```

Instructions to do the actual addition do not actually ever get created in the executable program unless you assign the things to different variables first.

---

