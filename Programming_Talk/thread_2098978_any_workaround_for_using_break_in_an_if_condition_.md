---
title: "any workaround for using break in an if condition without a loop"
date: 2012-12-28
forum: Programming Talk
---

### Post by IAMTubby on 2012-12-28
Hey,
Is there any workaround for using 'break' in an if condition even if the if condition doesn't come inside a loop.

For example
```

#include <stdio.h>

int main(void)
{
 int a = 4;
 int b = 7;

 **if(a<10)**
 {
  if(a<5)
  {
   workaround_of_break;
   //break out of top a<10 condition and go directly to the check for b
  }
  printf("\nI don't want this to be printed if the value of a is less than 5 because it would have break'ed out before reaching here");
 }

 **if(b<10)**
 {
  if(b<5)
  {
   break;
   //I want to break out here of top b<10 condition
  }
  printf("\nI don't want this to be printed if the value of b is less than 5 because it has already break'ed out");
 }

 return 0;
}

```

**I understand this condition can very well be written as if((a>5) && (a<10))**, but I was just demo'ing my requirement. 
Please advise.
Thanks.

---

### Post by fdrake on 2012-12-28
ops.... never mind! :P

---

### Post by The Cog on 2012-12-28
Break can only break loops.
How about:
```
#include <stdio.h>

int main(void)
{
 int a = 4;
 int b = 7;

 if(a<10)
 {
  if(a>=5)
  {
   printf("\nI don't want this to be printed if the value of a is less than 5 because it would have break'ed out before reaching here");
  }
 }

 if(b<10)
 {
  if(b>=5)
  {
   printf("\nI don't want this to be printed if the value of b is less than 5 because it has already break'ed out");
  }
 }

 return 0;
}
```

---

### Post by IAMTubby on 2012-12-28
> **fdrake said:**
> ops.... never mind! :P
hey fdrake, didn't get that .

---

### Post by IAMTubby on 2012-12-28
> **The Cog said:**
> Break can only break loops.

The Cog, thanks for the reply. I understand that since this is a fairly simple example, there are quite a few ways of getting it working. But it is only meant to demo my requirement and not part of something I'm working on.

I am mainly interested in knowing if there is a way to break out of the if block.

Thanks.

---

### Post by The Cog on 2012-12-28
All I can think of is to use if statements. If you want to break out of a bunch of nested if statements, you need to set a flag and check that everywhere. 

It might be easier to put all the nested ifs in a function and just return from the function at the point where you want to break.

Or you could summon the dark forces of goto, but this is generally not approved of and could make you go blind.

---

### Post by IAMTubby on 2012-12-28
> **The Cog said:**
> 
dark forces of goto
:) thanks for the reply

---

### Post by r-senior on 2012-12-28
Extracting a function and using return seems to fit. This effectively breaks you out of the if block.

```
#include <stdio.h>

void validate(int n);

int main(void)
{
    int a = 4;
    int b = 7;

    validate(a);
    validate(b);

    return 0;
}

void validate(int n)
{
    if (n < 10) {
        if (n < 5) {
            return;
        }
        printf("%d is in range\n", n);
    }
}

```

---

### Post by dwhitney67 on 2012-12-28
Use the if-else construct, or try to expand your conditional statements

Example:
```

if (a >= 5 && a < 10)
{
    printf("...");
}

if (b >= 5 && b < 10)
{
    printf("...");
}

```

Avoid the 'goto', and avoid any silly code.  Learn how to write conditional statements that employ the technique of short-circuiting.  Read more here: [http://en.wikipedia.org/wiki/Short-circuit_evaluation](http://en.wikipedia.org/wiki/Short-circuit_evaluation)

---

### Post by trent.josephsen on 2012-12-28
I'm going to play devil's advocate for a moment and state that there's no practical reason to completely eschew **goto**, in a language that provides it. Breaking out of a loop prematurely, or returning from a function prematurely, is no different in terms of program flow -- you don't see people get in arms about that kind of thing only because it doesn't use the letters G-O-T-O.

Everyone loves Dijkstra, but his 1968 letter to the editor was clearly addressing the *over*use of go to, i.e. using it where conditionals (if-else) or "repetition clauses" (do, while, for) can express the same idea. This was the 60s; structured programming was *new* -- and it wasn't universally understood that "spaghetti code" (a pejorative term invented later to (successfully) discourage unmaintainable programming) was something to be avoided. One unconditional jump doesn't make spaghetti code.

Like the switch statement, goto is a construct almost obsoleted by newer features in more "modern" languages. But C doesn't have anonymous subroutines or message passing, and every once in a while you find an algorithm that works best (readably and efficiently) with goto.

Is that the case with IAMTubby's code? I don't know, likely not. But "avoid goto" is not appropriate advice for every situation.

---

### Post by Bachstelze on 2012-12-28
[http://c2.com/cgi/wiki?GoTo](http://c2.com/cgi/wiki?GoTo)

Even short-circuit evaluation is not appropriate all the time (I am not saying it would not be appropriate here).

---

### Post by rnerwein on 2012-12-28
> **trent.josephsen said:**
> I'm going to play devil's advocate for a moment and state that there's no practical reason to completely eschew **goto**, in a language that provides it. Breaking out of a loop prematurely, or returning from a function prematurely, is no different in terms of program flow -- you don't see people get in arms about that kind of thing only because it doesn't use the letters G-O-T-O.

Everyone loves Dijkstra, but his 1968 letter to the editor was clearly addressing the *over*use of go to, i.e. using it where conditionals (if-else) or "repetition clauses" (do, while, for) can express the same idea. This was the 60s; structured programming was *new* -- and it wasn't universally understood that "spaghetti code" (a pejorative term invented later to (successfully) discourage unmaintainable programming) was something to be avoided. One unconditional jump doesn't make spaghetti code.

Like the switch statement, goto is a construct almost obsoleted by newer features in more "modern" languages. But C doesn't have anonymous subroutines or message passing, and every once in a while you find an algorithm that works best (readably and efficiently) with goto.

Is that the case with IAMTubby's code? I don't know, likely not. But "avoid goto" is not appropriate advice for every situation.
hi
that's a +1 from me
some times it's just easier to read the code than you have a labyrint nested if conditions
cheers

---

### Post by GeneralZod on 2012-12-28
> **trent.josephsen said:**
> snip

Another +1 from me.  Also:

```

$ grep -niR goto linux-3.2.0/ | wc -l
96580

```

---

### Post by Elmer Fudd on 2012-12-28
IAMT,

Any chance that you could be a little more specific without giving away any secrets?  Easier then to propose a workaround rather than the obvious solutions that don't suit your need.

---

### Post by slickymaster on 2012-12-28
> **trent.josephsen said:**
> I'm going to play devil's advocate for a moment and state that there's no practical reason to completely eschew **goto**, in a language that provides it. Breaking out of a loop prematurely, or returning from a function prematurely, is no different in terms of program flow -- you don't see people get in arms about that kind of thing only because it doesn't use the letters G-O-T-O.

Everyone loves Dijkstra, but his 1968 letter to the editor was clearly addressing the *over*use of go to, i.e. using it where conditionals (if-else) or "repetition clauses" (do, while, for) can express the same idea. This was the 60s; structured programming was *new* -- and it wasn't universally understood that "spaghetti code" (a pejorative term invented later to (successfully) discourage unmaintainable programming) was something to be avoided. One unconditional jump doesn't make spaghetti code.

Like the switch statement, goto is a construct almost obsoleted by newer features in more "modern" languages. But C doesn't have anonymous subroutines or message passing, and every once in a while you find an algorithm that works best (readably and efficiently) with goto.

Is that the case with IAMTubby's code? I don't know, likely not. But "avoid goto" is not appropriate advice for every situation.

+1
I agree. Even though overall usage of gotos has been declining, there are still situations in some languages where a goto provides the shortest and most straightforward way to express program's logic and can be a useful language feature, improving program speed, size and code clearness.

---

