---
title: "C programming stacks"
date: 2013-03-07
forum: Programming Talk
---

### Post by binaryperson on 2013-03-07
Hello. Can someone please write a C program that has the following characteristics:

1) Uses a LIFO stack to store integers
2) User can enter values(PUSH)
3) User can remove values(POP)
4) Stack is printed to the screen when the program starts and each time PUSH or POP is performed.
5) The top of the stack contains the newest element, the bottom contains the oldest element.

I want the program to actually print out something that looks like a stack. Something like this:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
int stackElement=9;
int i;

for(i=0; i<10; i++)
{
printf("+------------+\n");
printf("|     %d     |\n",stackElement);
printf("|            |\n");
printf("+------------+\n");
stackElement--;
}

return 0;
}

```
Note: The output of my program is nicely aligned to make a rectangle.

This isn't homework. I want to learn stacks on my own and I think a  program like this would help me. Please use as few functions and  pointers as possible.

---

### Post by trent.josephsen on 2013-03-07
> **binaryperson said:**
> Hello. Can someone please write a C program
Yes, someone can. I can, in fact, for a reasonable hourly rate (two hour minimum). But you're not likely to get an uninteresting program like this for free, even if it's not homework.

> This isn't homework. I want to learn stacks on my own and I think a  program like this would help me. Please use as few functions and  pointers as possible.

Wouldn't you learn more by doing it yourself?

---

### Post by binaryperson on 2013-03-07
I was thinking of reverse engineering the program and then trying to write a FIFO stack on my own followed by other abstract data types. I am only familiar with arrays and structures as far as data types go. Everyone needs to be lent a hand, at the beginning, before they get the hang of things. By the way, how much do you charge per hour? Do you offer any help, advice or suggestions without the expectation of monetary return?

---

### Post by slickymaster on 2013-03-07
> **trent.josephsen said:**
> Wouldn't you learn more by doing it yourself?

:)  I wonder what will be the answer you'll get?

Assuming that there's going to be one. :)

---

### Post by binaryperson on 2013-03-07
No I wouldn't learn more if I have no idea where to start. If someone doesn't help me I will just not learn stacks and that will be the end of it. I don't have to learn stacks, I just wanted to.

---

### Post by binaryperson on 2013-03-07
Thanks for absolutely nothing.

---

### Post by BlinkinCat on 2013-03-07
> **binaryperson said:**
> Thanks for absolutely nothing.


Trying to do it yourself is always the best option -

You can always ask for help if you come up with a deadend - :)

---

### Post by steeldriver on 2013-03-07
IIRC Kernighan and Ritchie develop a simple implementation of a stack-based RP calculator in their original 'The C Programming Language' book - maybe that would be a good starting point?

---

### Post by slickymaster on 2013-03-08
> **binaryperson said:**
> Thanks for absolutely nothing.

I think that what [COLOR=#000000]trent.josephsen meant was something [/COLOR][COLOR=#000000]like > “Give a man a fish, and you’ll feed him for a day. Teach a man to fish, and you’ve fed him for a lifetime.”

So as a sort of a fishing rod, you can start here:
[/COLOR][COLOR=#000000][Stack - Array Implementation]("http://www.cs.bu.edu/teaching/c/stack/array/")
[Data Structures: Stacks ( with C Program source code)]("http://www.thelearningpoint.net/computer-science/data-structures-stacks--with-c-program-source-code")[/COLOR]

---

### Post by r-senior on 2013-03-08
Also [https://en.wikipedia.org/wiki/Stack_(abstract_data_type)](https://en.wikipedia.org/wiki/Stack_(abstract_data_type))

---

### Post by Warren Hill on 2013-03-08
Some basic clues.

First you need somewhere to store your data say a simple array and a variable to tell you which element in the array is currently top.

Now write two functions **push()** and **pop()**.

To** push** or **pop** all you need to do is copy data into or out of the array and change the index variable.  Also think about what should happen if you try to** push** too many values or **pop **more than you have pushed.

Not too difficult.  Have a go and if you get stuck show us what you have.  We are happy to help but you wont learn if one of us does it for you.

---

