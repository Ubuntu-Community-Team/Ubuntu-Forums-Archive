---
title: "why is gcc telling me my for loop is wrong"
date: 2008-11-09
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-09
heres my for loop```
for(int i = 2; i < x; i++)
{
     //code here
}
```

heres the error

```
 error: ‘for’ loop initial declaration used outside C99 mode
```

---

### Post by Phenax on 2008-11-09
Don't declare the variable in the loop, declare it before the loop.

---

### Post by Sinkingships7 on 2008-11-09
You can't declare variables within the parenthesis following the for statement by C90 standards. I think C99 allows this. Rewriting it like this will work:
[php]
int x;
for (x = 0; x < y; x++){
    // code here
}
[/php]

---

### Post by jimi_hendrix on 2008-11-09
> **Sinkingships7 said:**
> You can't declare variables within the parenthesis following the for statement by C90 standards. I think C99 allows this. Rewriting it like this will work:


why doesnt gcc use the newest version of C?

---

### Post by jimi_hendrix on 2008-11-09
and why am i getting floating point exceptions in here?

[php]
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

bool isPrime( int x );


int main()
{
    int x;
    printf("enter a number: \n", x);
    scanf("%d", &x);
    if (isPrime(x) == true) printf("is prime \n");    
    if (isPrime(x) == false) printf("is not primeprime \n");
    return 0;
}

bool isPrime(int x)
{
    int i;
    if (x < 2)
    {
        return false;    
    }

    else
    {
        for(i = 0; i < x; i++)
        {
            if (x % i == 0)
            {
                return false;
            }
        }

        return true;
    }
}
[/php]

while were here...does vim have auto indenting?

---

### Post by WW on 2008-11-09
> **jimi_hendrix said:**
> and why am i getting floating point exceptions in here?

[php]
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

bool isPrime( int x );


int main()
{
    int x;
    printf("enter a number: \n", x);
    scanf("%d", &x);
    if (isPrime(x) == true) printf("is prime \n");    
    if (isPrime(x) == false) printf("is not primeprime \n");
    return 0;
}

bool isPrime(int x)
{
    int i;
    if (x < 2)
    {
        return false;    
    }

    else
    {
        for(i = 0; i < x; i++)
        {
            if (x % i == 0)
            {
                return false;
            }
        }

        return true;
    }
}
[/php]

You are computing x % 0 when i is 0, which is not allowed--it is like dividing by 0.  Change the starting value of i in the loop to be 2. Not 1, because x % 1 is always 0.

There are faster ways to determine if a number is prime, but that should fix your immediate problem.

---

### Post by Phenax on 2008-11-09
> **jimi_hendrix said:**
> and why am i getting floating point exceptions in here?

[php]...
[/php]

while were here...does vim have auto indenting?

First of all, you're getting a floating point exception at
[php]
if (x % i == 0)
[/php]
You can use the GNU DeBugger (GDB) to easily find the lines that are making your program crash, along with **tons** of other valuable information.
You get it because it performs the operation (int) % 0. Your for loop should start with 2. 0 will raise floating point exceptions and 1 will return everything as composite.

[php]
    if (x < 2)
    {
        return false;    
    }
[/php]
There are an infinite number of primes below the number two. That code makes your program return incorrect solutions. Perhaps you mean **return true;**. All numbers below two are prime, not composite.

[php]
    printf("enter a number: \n", x);
    scanf("%d", &x);
[/php]
... This is a fairly obvious mistake

You should also look into the Sieve of Eratosthenes, it's not very complex, but even when you get your algorithm to work it will be very slow. It's easy to optimize it using elements of some well-established sieves and algorithms.

And yes, vim has autoindenting. It's an option you can set in your ~/.vimrc or enable realtime.

---

### Post by jimi_hendrix on 2008-11-09
now about that indenting thing...is there auto indenting in vim or are there lightweight editors with it?

---

### Post by jimi_hendrix on 2008-11-09
thanks...i have to stop coding past 9 pm...

---

### Post by LaRoza on 2008-11-09
> **jimi_hendrix said:**
> now about that indenting thing...is there auto indenting in vim or are there lightweight editors with it?

Yes, there is.

> **jimi_hendrix said:**
> why doesnt gcc use the newest version of C?

It does, but by default, it uses the most common version. You will have to specific the standard to use.

```

man gcc | grep "c99"

```

---

### Post by LaRoza on 2008-11-09
> **jimi_hendrix said:**
> thanks...i have to stop coding past 9 pm...

Only 9 pm? Why, I've stayed up all night, into sunrise coding. This is usually a bad idea though, only code when you are fully awake and fueled by things other than adrenaline and mountain dew.

---

### Post by geirha on 2008-11-10
> **jimi_hendrix said:**
> now about that indenting thing...is there auto indenting in vim or are there lightweight editors with it?

The vim installed by default is a minimal version, without syntax highlighting and indenting. Install [apt://vim-full](apt://vim-full) to get the full featured vim. Then, edit /etc/vim/vimrc, it has comments explaining what options will give you auto indenting.

---

### Post by LaRoza on 2008-11-10
> **geirha said:**
> The vim installed by default is a minimal version, without syntax highlighting and indenting. Install [apt://vim-full](apt://vim-full) to get the full featured vim. Then, edit /etc/vim/vimrc, it has comments explaining what options will give you auto indenting.

Or just **vim**. vim-full has silly stuff.

---

### Post by cl333r on 2008-11-10
> **LaRoza said:**
> Yes, there is.

It does, but by default, it uses the most common version. You will have to specific the standard to use.

```

man gcc | grep "c99"

```

Also because c99 isn't fully supported yet. IMHO it makes sense making them default only after all specifications from c99 get implemented, and looks like the gcc devs think the same way. It will be default anyway, it's just a matter of time.

---

### Post by achelis on 2008-11-10
> **Phenax said:**
> 
There are an infinite number of primes below the number two. That code makes your program return incorrect solutions. Perhaps you mean **return true;**. All numbers below two are prime, not composite.


There is no primes less than 2.

Quoting wikipedia:
> 
In mathematics, a prime number (or a prime) is a natural number which has exactly two distinct natural number divisors: 1 and itself.


---

### Post by nvteighen on 2008-11-10
> **jimi_hendrix said:**
> why doesnt gcc use the newest version of C?
As other have said, gcc supports C99, but you have to use the --std=c99 flag for that.

But this is not just gcc, IIRC almost all compilers do this, just because C99 is not a widespread standard. The ANSI and the ISO bodies can declare standards on their will, but can't make people adopt them...

The same occurs with the W3 Consortium... yeah, there's the HTML 4.01 standard and XHTML 1.1... but how many webpages follow them? Worse, how many browsers comply with them?

---

### Post by LaRoza on 2008-11-10
> **nvteighen said:**
> The ANSI and the ISO bodies can declare standards on their will, but can't make people adopt them...


Au contraire, Microsoft can make ISO declare standards, and make people adopt them (but, the adoption is different from the standard...)

---

### Post by jimi_hendrix on 2008-11-10
> **LaRoza said:**
> Only 9 pm? Why, I've stayed up all night, into sunrise coding. This is usually a bad idea though, only code when you are fully awake and fueled by things other than adrenaline and mountain dew.

ya but the quality of my questions drops serverly after 9:00

---

### Post by LaRoza on 2008-11-10
> **jimi_hendrix said:**
> ya but the quality of my questions drops serverly after 9:00

The quality of my code drops...

(Time varies, as my obligations change, so "late" is quite relative)

---

