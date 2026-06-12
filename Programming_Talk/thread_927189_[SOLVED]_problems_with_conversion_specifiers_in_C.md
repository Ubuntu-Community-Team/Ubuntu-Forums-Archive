---
title: "[SOLVED] problems with conversion specifiers in C"
date: 2008-09-22
forum: Programming Talk
---

### Post by Xnyper on 2008-09-22
I have a homework assignment due next friday.  The basic premise of this assignment is passing parameters by reference.  Before I pass said parameters, I need to collect some input from the user; this input collection is hardly the point of the program--but it is the point of this post.

before even worrying about the passing of parameters, I wanted to verify that my data collection was going according to planned so I set up a printf to tell me the values of the variables.  Much to my dismay, they were all wrong.

for example, if my input is:

1
2
3

then the output of the last printf is:

one: 2.000000 
two: -0.000000 
three: 32.000001

I went through my code, and replaced all of the %f (for float) with %d (for integer).  And suddenly it was working just fine.  As far as I can find (in the book and in the notes) there shouldn't be any additional requirements for changing the conversion specifiers, a simple find and replace should effectively change the variable type in question.  

I have attached my source, assignment1.c is the working one, with integers.  assignment1a.c is the broken one, with floats.

If anyone can tell me why the variable aren't getting stored properly (or possibly why they arent printing properly) in assignment1a.c I would really appreciate it.  

Thanks!

---

### Post by Peter Frank on 2008-09-22
Change the line
*int one = 0,two = 0, three = 0;*
to
*float one = 0,two = 0, three = 0;*

And it will work. C allows you to mess up variable types and won't give you a compiler error.

---

### Post by Can+~ on 2008-09-22
An integer is just a piece of memory, usually of the size of 4 bytes (or 32 bits (you can check it with sizeof(int))). And on the other hand, [floats](http://en.wikipedia.org/wiki/IEEE_754) are a whole different thing, which hold a certain area for the sign, exponent and the fraction.

When you do scanf "%f" it expects a float to fill in, and it will do it accordingly, but if you handle an integer, it will still try to write as a float, causing this weird results.

The error lies that you ask for floats and insert them on integers:

[PHP]int one = 0,two = 0, three = 0;
scanf("%f" , &one );
printf("Number two:");[/PHP]

When you should ask for integers or use the float variable type:

[PHP]float one = 0,two = 0, three = 0;
scanf("%f" , &one );
printf("Number two:");[/PHP]

---

### Post by Xnyper on 2008-09-22
wow, I'm special.  thanks guys!

---

### Post by dwhitney67 on 2008-09-22
> **Peter Frank said:**
> ...
C allows you to mess up variable types and won't give you a compiler error.
Not necessarily.  If one uses the -Wall option, the discrepancies as described in the OP would have been caught.

For example:
[PHP]#include <stdio.h>
int main()
{
  int value = 10;
  printf( "%f\n", value );
  return 0;
}[/PHP]

Compile this with the -Wall option to see the warning that is produced concerning the usage of %f, when an int value is given.

---

### Post by nvteighen on 2008-09-23
Why the gcc devs just don't set -Wall as default behaivor? (I guess there might be a reason, but anyway... it would just save a lot of people)

---

### Post by dwhitney67 on 2008-09-23
Probably because it would "break" a lot of existing code where the s/w developers were sloppy in their development efforts.

Personally, I find it convenient to define 'gcc' and 'g++' as aliases in my ~/.bashrc file.

```
alias gcc='/usr/bin/gcc -Wall -pedantic -D_GNU_SOURCE -std=gnu99'
alias g++='/usr/bin/g++ -Wall -pedantic'
```

P.S.  I don't think the /usr/bin path is necessary, but doesn't hurt.

---

### Post by nvteighen on 2008-09-23
> **dwhitney67 said:**
> Probably because it would "break" a lot of existing code where the s/w developers were sloppy in their development efforts.


In other words, it would show us who's who.

---

