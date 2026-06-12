---
title: "Simple question about C"
date: 2008-11-01
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-01
I got this:
```

/* a list to hold information about every plasma missile shot by player */
int player_plasma_missiles[200];
int ind;
for (ind = 0; ind < 200; ind++)
{
    player_plasma_missiles[ind] = NULL;
}

```
But it keeps saying:
> 
gltest.c:37: error: expected identifier or ‘(’ before ‘for’
gltest.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘<’ token
gltest.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘++’ token

If I comment/remove that part then there will be no errors, so the that part obviously makes the errors.

What is wrong with that? I don't get it. I use similar for loop in many other parts of the program but they don't give errors. And they are identical to this one! :confused::confused:

---

### Post by perove on 2008-11-01
i compiled it, and got no errors, but do you have the code inside a method? 
you get those errors you listed if you put it outside

void foo()
{
    //here
}

//not here

int main()
{
    //or here
}

---

### Post by Delever on 2008-11-01
> **crazyfuturamanoob said:**
> gltest.c:37: error: expected identifier or ‘(’ before ‘for’
gltest.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘<’ token
gltest.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘++’ token :

Such error usually means that symbol was not found. Usually out of scope, unreachable in that place. Make sure you know how C scope works.

---

### Post by crazyfuturamanoob on 2008-11-01
What!?? I can only use **for** inside a function? Why?

---

### Post by WW on 2008-11-01
*All* your executable statements must be in functions.  If you want to write a script-like program, put all your code in **main()**.  When you compile and run your program, **main()** is the first thing that is run.

E.g.
```

int main()
{
    /* a list to hold information about every plasma missile shot by player */
    int player_plasma_missiles[200];
    int ind;
    for (ind = 0; ind < 200; ind++)
    {
        player_plasma_missiles[ind] = 0;
    }

    return 0;
}

```
Note that I changed NULL to zero.  You declared the array to be int, but NULL means the null pointer.

If you want, you can make the array a global variable by declaring it outside of main(), like this
```

/* a list to hold information about every plasma missile shot by player */
int player_plasma_missiles[200];

int main()
{

    int ind;
    for (ind = 0; ind < 200; ind++)
    {
        player_plasma_missiles[ind] = 0;
    }

    return 0;
}

```
The for loop must still be in main() (or some other function).

---

### Post by PandaGoat on 2008-11-01
It's all about scope.  Anything not inside a method is placed on the heap (in memory), and the rest is placed in the stack (in memory).  Its called these because the heap is just a heap of variables and symbols that can be accessed at any time, anywhere.  The stack is an ordered stack of variables, control structures, calls to functions, *et cetera*.  It makes no since really using this paradigm for for loops or anything but declaration to be on the heap.  The stuff that controls you program and ran in some order are in the call stack, not the heap.

It's just the way C does things.

---

### Post by nvteighen on 2008-11-01
> **PandaGoat said:**
> It's all about scope.  Anything not inside a method is placed on the heap (in memory), and the rest is placed in the stack (in memory).  Its called these because the heap is just a heap of variables and symbols that can be accessed at any time, anywhere.  The stack is an ordered stack of variables, control structures, calls to functions, *et cetera*.  It makes no since really using this paradigm for for loops or anything but declaration to be on the heap.  The stuff that controls you program and ran in some order are in the call stack, not the heap.

It's just the way C does things.

You're wrong, but you point to the right idea.

Yes: stuff declared in functions is put in the stack... that's not C's way, but rather how memory works in general. IIRC, Assembly does the same, but manually.

Stuff not placed in any function is written into the Data Segment memory. That's the place where constant stuff is stored (in first place, your whole program). If the constant is a value, it's a const variable. If just the initial value is constant, it's a static variable (the reference allows you to change it). If only the memory address, it's a global. But a for-loop is code that is executed in time, by pushing-popping the call stack (just for entering a for-loop, aprox. 4 calls are done... check it with gdb!), so though the code for the loop is in the Data Segment too, the execution (which is variable) is on stack.

The heap is dynamic memory and has nothing to do with these issues. Actually, anything placed in heap has to be managed by a pointer and therefore, you can place that pointer wherever you like as any other variable.

---

### Post by snova on 2008-11-01
Methinks crazyfuturamanoob has been using Python for too long. :)

You could accomplish something similar to this with classes, by defining a class that initializes the data in it's constructor and then creating a global instance of the class. Then the ctor will be run before main().

A little messy, but possible.

---

### Post by LaRoza on 2008-11-01
> **snova said:**
> You could accomplish something similar to this with classes, by defining a class that initializes the data in it's constructor and then creating a global instance of the class. Then the ctor will be run before main().

A little messy, but possible.

Impossible, in C.

---

### Post by nvteighen on 2008-11-02
> **snova said:**
> Methinks crazyfuturamanoob has been using Python for too long. :)

You could accomplish something similar to this with classes, by defining a class that initializes the data in it's constructor and then creating a global instance of the class. Then the ctor will be run before main().

A little messy, but possible.
Nothing can be started before main()...

---

### Post by Zugzwang on 2008-11-02
> **nvteighen said:**
> Nothing can be started before main()...
...except in C++. ;-)

[PHP]
#include <iostream>

class Hello {

public:
  Hello() { std::cout << "Hello "; }
};

Hello hello;

int main() {
  std::cout << "World!\n";
}
[/PHP]

---

### Post by LaRoza on 2008-11-02
> **Zugzwang said:**
> ...except in C++. ;-)


Yes, but C++ is an entirely different language. It is about C, not other languages.

---

### Post by snova on 2008-11-02
Oops. I forgot it was C.

I think there's an __attribute__ you can use with GCC to put a function in a special section so that it will be called before main(), but I'm not sure of it.

---

### Post by sjton on 2009-05-06
Thank you!

This helped me too. I have a C++ project and I was using .c and .h extensions. I'm migrating from a windows compiler that didn't care to gcc which reads such code as C. I couldn't figure out what was wrong.

Again, thank you.
~sj

---

### Post by eye208 on 2009-05-07
> **nvteighen said:**
> Nothing can be started before main()...
Hmmm...

```
#include <stdio.h>
#include <stdlib.h>

int main() {
        printf("inside main()\n");
        return 0;
}

void _start() {
        printf("outside main()\n");
        main();
        exit(EXIT_SUCCESS);
}
```
Compile with **-nostartfiles** option. ;)

---

