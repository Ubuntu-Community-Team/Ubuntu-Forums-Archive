---
title: "Segmentation fault  - gcc"
date: 2008-11-22
forum: Programming Talk
---

### Post by david sousa on 2008-11-22
I'm learning how to program c at university and so I'm using gcc with ubuntu(intrepid ibex). But after compiling a program i allways get that "segmentation fault" error. I allready done a lot of search but didn't found a solution.

It's really iimportant for me to solve this problem because I have to complete my project...

thanks for your attention

---

### Post by cmnorton on 2008-11-22
Can you bring the executable up in gdm? You'll need to build the modules with -g (I think).

Offhand, this sounds like you've either built the executable incorrectly or your program is built properly and it is doing something illegal like touching non-existent memory.

I would become very knowledgeable very quickly with gdb.

Another thing to try to make sure this is not an install issue. Write a hello world program in one module; build it; run it; and if that works your project is probably doing something it shouldn't and you'll need to debug the project.

---

### Post by david sousa on 2008-11-22
Well, in fact I didn't start my project yet but i'm testing some codes. "printf" works just fine. But when i write "scanf" i get that error. Anyway i think it's not a a code problem... And i don't know what to do right now because i'm not really a linux master...

---

### Post by dexter on 2008-11-22
Maybe you should post some of your code so we can have a look at it...

---

### Post by david sousa on 2008-11-22
as i said, i have only done some tests like 6-7 lines of code, and sometimes I get this error. so it's not a code problem. I allready have some knowledge about C and I made other programs in another computer.

So i must solve this segmentation program with my ubuntu

---

### Post by Joeb454 on 2008-11-22
My guess is that you're using incorrect syntax for scanf, so look that up on google. I believe [this page]("http://forum.codecall.net/c-tutorials/3516-how-use-scanf-c.html") may help.

Edit:

After re-reading the thread, I believe the OP isn't requesting that the entire project be written for him/her, but requesting help regarding syntax in C, therefore I re-opened the thread.

Thanks :)

---

### Post by david sousa on 2008-11-22
Hey! Thanks for that link! I really forgot to put  this "&" before the varialbe at scanf code. Simple as that...

Sometimes distraction beats the knowledge...

---

### Post by cmay on 2008-11-22
> **david sousa said:**
> Hey! Thanks for that link! I really forgot to put  this "&" before the varialbe at scanf code. Simple as that...

Sometimes distraction beats the knowledge...
you are not the first to have forgotten that. and you are also not likely to be the last to forget that. scanf is good to know but its even better to use fgets. simply becouse its safer to use. 
good luck to you.

---

### Post by slavik on 2008-11-22
can you post the code that gives you a segfault and also how you run it in a terminal? would make it easier for everyone to see what is going on.

---

### Post by scourge on 2008-11-23
> **david sousa said:**
> Hey! Thanks for that link! I really forgot to put  this "&" before the varialbe at scanf code. Simple as that...

Sometimes distraction beats the knowledge...

GCC will warn you when you forget the "&", with something like this:
"warning: format ‘%d’ expects type ‘int *’, but argument 2 has type ‘int’"

You should also push compiler warnings to the max and compile with -Wall and maybe -pedantic.

---

### Post by samgonsalvis on 2011-08-20
```

/*Power a^b*/

#include <stdio.h>
double power(double,float);

/*Definition of power function*/

double power(double a, float b)
{
    if (b=0)
        return 1;
    else if (b<0)
        return ( a*power(a,b+1));
    else
        return (a*power(a,b-1));
}


void main()
{
    double m;
    float e;
    printf("Enter mantissa.\n");
    scanf("%lf",&m);
    printf("Enter exponent\n");
    scanf("%f",&e);
    if(e<0)
    printf("\nAnswer is %lf",1/power(m,e));
    else
    printf("\nAnswer is %lf",power(m,e));
}

```



inspite of using & i am getting segmentation error! Any solutions???

---

### Post by Arndt on 2011-08-20
> **samgonsalvis said:**
> ```

/*Power a^b*/

#include <stdio.h>
double power(double,float);

/*Definition of power function*/

double power(double a, float b)
{
    if (b=0)
        return 1;
    else if (b<0)
        return ( a*power(a,b+1));
    else
        return (a*power(a,b-1));
}


void main()
{
    double m;
    float e;
    printf("Enter mantissa.\n");
    scanf("%lf",&m);
    printf("Enter exponent\n");
    scanf("%f",&e);
    if(e<0)
    printf("\nAnswer is %lf",1/power(m,e));
    else
    printf("\nAnswer is %lf",power(m,e));
}

```



inspite of using & i am getting segmentation error! Any solutions???

You shouldn't attach your question to a three year old thread just because the subject seems to fit. Start a new thread instead.

The reason for the error is the test (b=0). It assigns 0 to b, it doesn't test whether b is zero. You want (b==0).

There are some other problems with the code. For example, what will it do if you enter 2.5 as the exponent?

It is also good to end the output lines with \n.

---

### Post by GeneralZod on 2011-08-20
It's also very unlikely that b will always end up comparing exactly to 0 (b is a float, not an int!), in which case you'll probably get a stack overflow.

---

