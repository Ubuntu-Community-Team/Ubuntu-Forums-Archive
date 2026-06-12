---
title: "Problems with C program"
date: 2009-04-11
forum: Programming Talk
---

### Post by SMohr on 2009-04-11
I have to write my own bit functions for a program.  Out of 4 functions I've only written 2 which you'll see below.  When I compile I get an error saying "line 6 variable a not found".  Why is that when I've declared a to be a variable in the function?  Btw, for the first function I'm not allowed to use | which is why I have it written the way I do.

int bitOr(int, int)
int a, b;
{
return ~(~a & ~b);
}

int bitXOr(int, int)
int a, b;
{
return (a | b)&(~a | ~b);
}



int main() {
  int x, y;
  while (1) {
    printf("Enter 2 integers, or ^C to stop\n");
    scanf("%d %d", &x, &y);
    int or = bitOr(x,y);
    int xor = bitXOr(x,y);
    //int not = bitNot(x);
    //int neq = isNotEqual(x,y);

    printf("bitOr(x,y) = %d.  x|y = %d.\n", or, x|y);
    printf("bitXOr(x,y) = %d. x^y = %d.\n", xor, x^y);
    //printf("bitNot(x) = %d.  ~x = %d.\n", not, ~x);
    //printf("isNotEqual(x,y) = %d.  x!=y = %d.\n\n", neq, x!=y);
  }
}

---

### Post by Idefix82 on 2009-04-11
We are not supposed to do your homework for you, but just to help you a bit: you need to go back to your lecture notes or whatever and to understand how to write basic functions. In particular
[LIST]
[*]You need to give your arguments names so that you can refer to them in the function. Something like myfunc(int,int) won't do because you haven't named the argument, you have only specified the types. It should read myfunc(int a, int b)
[*]After the name of the function and the list of arguments comes the opening bracket of the function '{', meaining 'I'm now going to describe what the function does (to the argument)'
[/LIST]

I hope that makes sense. As I said, make sure you understand the basic syntax first.

---

### Post by xtremethegreat1 on 2009-04-11
> **SMohr said:**
> I have to write my own bit functions for a program.  Out of 4 functions I've only written 2 which you'll see below.  When I compile I get an error saying "line 6 variable a not found".  Why is that when I've declared a to be a variable in the function?  Btw, for the first function I'm not allowed to use | which is why I have it written the way I do.

int bitOr(int, int)
int a, b;
{
return ~(~a & ~b);
}

int bitXOr(int, int)
int a, b;
{
return (a | b)&(~a | ~b);
}



int main() {
  int x, y;
  while (1) {
    printf("Enter 2 integers, or ^C to stop\n");
    scanf("%d %d", &x, &y);
    int or = bitOr(x,y);
    int xor = bitXOr(x,y);
    //int not = bitNot(x);
    //int neq = isNotEqual(x,y);

    printf("bitOr(x,y) = %d.  x|y = %d.\n", or, x|y);
    printf("bitXOr(x,y) = %d. x^y = %d.\n", xor, x^y);
    //printf("bitNot(x) = %d.  ~x = %d.\n", not, ~x);
    //printf("isNotEqual(x,y) = %d.  x!=y = %d.\n\n", neq, x!=y);
  }
}

Your way of function argument declaration is outdated. May be that's why gcc isn't able to recognize it. You should use the declaration like:

int bitXOr(int a, int b){
    return (a | b)&(~a | ~b);
}

Do it similarly in the first function. This should work. If it does work, please notify me.

:guitar:

---

### Post by wd5gnr on 2009-04-11
Just for historical accuracy it isn't outdated, its wrong. The outdated form (which gcc should accept would be:

int f(a,b)
int a,b;
{
/* do whatever */
}

The NAMES are in the () not the types. It took me the LONGEST time to quit writing it like that. And then I started doing Verilog which is even stranger.

---

### Post by Idefix82 on 2009-04-11
Funny, this must have been before my time. I have never seen this syntax.

---

### Post by rich1939 on 2009-04-11
Your program would work fine if you changed it as follows:

```

int bitOr(int a, int b)
{
   return ~(~a & ~b);
}

int bitXOr(int a, int b)
{
   return (a | b)&(~a | ~b);
}

int main()
{
   int x, y;
   while (1) 
   {
      printf("Enter 2 integers, or ^C to stop\n");
      scanf("%d %d", &x, &y);
      int or = bitOr(x,y);
      int xor = bitXOr(x,y);
      printf("bitOr(x,y) = %d. x|y = %d.\n", or, x|y);
      printf("bitXOr(x,y) = %d. x^y = %d.\n", xor, x^y);
   }
}       

```

---

### Post by xtremethegreat1 on 2009-04-11
> **wd5gnr said:**
> Just for historical accuracy it isn't outdated, its wrong. The outdated form (which gcc should accept would be:

int f(a,b)
int a,b;
{
/* do whatever */
}

The NAMES are in the () not the types. It took me the LONGEST time to quit writing it like that. And then I started doing Verilog which is even stranger.

Oops!

:KS

---

### Post by SMohr on 2009-04-11
Thanks for all of your help.  I had written a strcat function before this problem and I used a for loop and had to intialize i outside the loop so I'm thinking that's why I wrote it that way.

Anyways, I need more help.  In the code below the only thing I've written is the bit functions, the main was provided by my professor.  Maybe its the way I've written the functions thats causing the error but at least half of my professors class examples don't end up working so it could also be the main.  Anyway the error I get is:

line 20: Parse Error, expecting `'}''
'int'

line 20 would be the line that reads:

int or = bitOr(x,y);

Anyways, I'm not sure where to go from here.  Any help would be greatly appreciated.

#include <stdio.h>

 int bitOr(int a, int b)
  {
  return ~(~a & ~b);
  }

 int bitXOr(int a, int b)
  {
  return (a | b)&(~a | ~b);
  }

int main() {
  int x = 5, y = 4;
  
  printf(x, y);
  while (1) {
    printf("Enter 2 integers, or ^C to stop\n");
    scanf("%d %d", &x, &y);
    int or = bitOr(x,y);
    int xor = bitXOr(x,y);
    //int not = bitNot(x);
    //int neq = isNotEqual(x,y);

    printf("bitOr(x,y) = %d.  x|y = %d.\n", or, x|y);
    printf("bitXOr(x,y) = %d. x^y = %d.\n", xor, x^y);
    //printf("bitNot(x) = %d.  ~x = %d.\n", not, ~x);
    //printf("isNotEqual(x,y) = %d.  x!=y = %d.\n\n", neq, x!=y);
  }
 

}

---

### Post by Arndt on 2009-04-11
> **SMohr said:**
> Thanks for all of your help.  I had written a strcat function before this problem and I used a for loop and had to intialize i outside the loop so I'm thinking that's why I wrote it that way.

Anyways, I need more help.  In the code below the only thing I've written is the bit functions, the main was provided by my professor.  Maybe its the way I've written the functions thats causing the error but at least half of my professors class examples don't end up working so it could also be the main.  Anyway the error I get is:

line 20: Parse Error, expecting `'}''
'int'

line 20 would be the line that reads:

int or = bitOr(x,y);

Anyways, I'm not sure where to go from here.  Any help would be greatly appreciated.

#include <stdio.h>

 int bitOr(int a, int b)
  {
  return ~(~a & ~b);
  }

 int bitXOr(int a, int b)
  {
  return (a | b)&(~a | ~b);
  }

int main() {
  int x = 5, y = 4;
  
  printf(x, y);
  while (1) {
    printf("Enter 2 integers, or ^C to stop\n");
    scanf("%d %d", &x, &y);
    int or = bitOr(x,y);
    int xor = bitXOr(x,y);
    //int not = bitNot(x);
    //int neq = isNotEqual(x,y);

    printf("bitOr(x,y) = %d.  x|y = %d.\n", or, x|y);
    printf("bitXOr(x,y) = %d. x^y = %d.\n", xor, x^y);
    //printf("bitNot(x) = %d.  ~x = %d.\n", not, ~x);
    //printf("isNotEqual(x,y) = %d.  x!=y = %d.\n\n", neq, x!=y);
  }
 

}

Your program compiles for me. With loud warnings for the printf(x,y) thing, but there is no syntax error.

What you should do next is make sure that what you have pasted here is what you are compiling. Then, remove things from the program until you have a minimal program that exhibits the errors. At that point, it should be easy to see what's wrong.

---

### Post by SMohr on 2009-04-11
> **Arndt said:**
> Your program compiles for me. With loud warnings for the printf(x,y) thing, but there is no syntax error.

What you should do next is make sure that what you have pasted here is what you are compiling. Then, remove things from the program until you have a minimal program that exhibits the errors. At that point, it should be easy to see what's wrong.

So I simplified my program (thanks) and it seems to be working properly now, but I've still got two more functions to write so stay tuned!

#include <stdio.h>


 int bitOr(int a, int b)
  {
    return ~(~a & ~b);  
  }

 int bitXOr(int a, int b)
  {
  return (a | b)&(~a | ~b);
  }
  
  int isNotEqual(int, int)
  {
  }
  


int main() {
  int x, y;
  while (1) {
    printf("Enter 2 integers, or ^C to stop\n");
    scanf("%d %d", &x, &y);
    
    printf("%d\n", bitXOr(x, y));
   
  }
}

---

### Post by soltanis on 2009-04-11
I'm assuming you're not allowed to use the | or ^ operators? Construction of bitwise operators from other bitwise operators?

---

### Post by rplantz on 2009-04-11
I would also suggest talking to your professor in his/her office hours. Most of us go into teaching because we like helping students, especially those who show an interest in learning. We sure as hell don't go into teaching for the money. :-)

---

### Post by Arndt on 2009-04-12
> **SMohr said:**
> So I simplified my program (thanks) and it seems to be working properly now, but I've still got two more functions to write so stay tuned!

#include <stdio.h>


 int bitOr(int a, int b)
  {
    return ~(~a & ~b);  
  }


I suggest you use the CODE or PHP tags to wrap your code in. That way, it will stand out better, and more importantly, will keep its indentation, so it's easier to read. CODE is the #-like symbol in the second row of symbols in the editing window, and PHP is the last one in the same row.

Like this:

```
int bitOr(int a, int b)
  {
    return ~(~a & ~b);  
  }
```

---

