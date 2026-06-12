---
title: "Started learning C, problems with gcc and whatnot :("
date: 2007-11-04
forum: Programming Talk
---

### Post by Pekkalainen on 2007-11-04
Hi!

I have always wanted to learn how to program and finally found a good book about C that just works the way I want to learn.

The problem I am having is that at the second exercise in the book where Im supposed to make a program that gives me a conversion table between celsius and fahrenheit degrees the program complies just fine but when I try to run it it spits out a bunch of errors.

Heres what the program looks like (copied to the letter from the book):

```

#include <stdio.h>
/* print Fahrenheit-Celsius table
    for fahr = 0, 20, ..., 300 */
main()
{
  int fahr, celsius;
  int lower, upper, step;
  lower = 0;       /* lower limit of temperature scale */
  upper = 300;     /* upper limit */
  step = 20;       /* step size */
  fahr = lower;
  while (fahr <= upper) {
       celsius = 5 * (fahr-32) / 9;
       printf("%d\t%d\n", fahr, celsius);
       fahr = fahr + step;
  }
}

```

and this is the error I get when I try to run it:
```

pekka@svartburken:~/Programmering$ ./celsius.c
./celsius.c: line 2: /bin: is a directory
./celsius.c: line 3: syntax error near unexpected token `='
./celsius.c: line 3: `    for fahr = 0, 20, ..., 300 */'

```

What have gone wrong? :(

I have build-essential installed

---

### Post by rzrgenesys187 on 2007-11-04
Well i copied your program and saved it as celsius.c.  It seems to me you just forgot to compile it

if you run this in the terminal

```
 gcc -o celsius celsius.c 
```

this will compile the file and save it to a script called celsius

```
 ./celsius 
```

will then run the file.

Hope that helps.  I just started c last week myself

---

### Post by Pekkalainen on 2007-11-04
Ah!
I just used: 

```

gcc celsius.c

```
to compile and it worked for the initial "hello world" program apparently but not for this "advanced" piece of program :)

Thanks for teaching me how to compile properly :D

Thread may be closed and hopefully forgotten :oops:

---

### Post by rzrgenesys187 on 2007-11-04
that code should've worked but it would've named the script 
```
a.out
``` 
i think.  You would've had to run 
```
./a.out
```

---

### Post by Pekkalainen on 2007-11-04
Doh #-o

I see now, it is merely a case of "problem between the chair and the keyboard" :D

---

