---
title: "Completely deleting a variable in C?"
date: 2008-11-09
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-09
I want to delete a variable in C. I already declared it and gave it a value, but I want to now delete it. Like when I try to use it after deletion I'd get notfound error.

How to do that? Is it even possible?

---

### Post by SledgeHammer_999 on 2008-11-09
I don't think that's possible. 
Just a suggestion: After you used it give it the value of NULL(eg int a = NULL;) And then when trying to use it do this -> 
[php]if (a != NULL) a = 155;[/php]

---

### Post by Thesuperchang on 2008-11-09
I think you're confusing dynamic variable behavior with static variable behavior. For a dynamic variable;
[PHP]
#include <stdlib.h>

int main(void) {
    char *cptr;

    cptr = (char *)calloc(1, sizeof(char)); // Allocate space in heap
    if(cptr == NULL) {
         // Error handler!
    }

    *cptr = 0; // Initialise dynamic variable

    // Insert programming code
    // Insert programming code
    // Insert programming code    

    free(cptr); // Release allocated space!

    return 0;
}
[/PHP]

On the other hand there are static variables.
[PHP]
int main(void) {
    char cbyte;

    cbyte = 0; // Initialise static variable

    // Insert programming code
    // Insert programming code
    // Insert programming code

    return 0;
}
[/PHP]

As you can see, static variables cannot be released form memory unless the scope in which they exist is destroyed. (ie. The function in which they where created in returns.) On the contrary, dynamic variables are only ever destroyed when the free() function is invoked.

---

### Post by Tony Flury on 2008-11-09
Essentially in C there is no concept of deleting variables, like there is for instance in Python (and probably other languages aswell).

All that happens in C is that a variable is declared in a particular scope, and it only exists within that scope.

---

### Post by dwhitney67 on 2008-11-09
> **Thesuperchang said:**
> I think you're confusing dynamic variable behavior with static variable behavior. ...
On the other hand there are static variables.
[PHP]
int main(void) {
    char cbyte;

    cbyte = 0; // Initialise static variable

    // Insert programming code
    // Insert programming code
    // Insert programming code

    return 0;
}
[/PHP]

As you can see, static variables cannot be released form memory unless the scope in which they exist is destroyed. (ie. The function in which they where created in returns.) On the contrary, dynamic variables are only ever destroyed when the free() function is invoked.

Conceptually you are correct, however the use of the word "static" to describe variables that are created on the stack is inappropriate.  The term "static" refers to something completely different.

Variables that are declared as static will remain on the stack.
[php]
int main()
{
  for (int i = 0; i < 5; ++i)
  {
    static char ch = 'a';
    printf("ch = %c\n", ch);
    ++ch;
  }

  ...
  return 0;
}
[/php]

---

### Post by winch on 2008-11-09
> **dwhitney67 said:**
> Variables that are declared as static will remain on the stack.

A static variable is just a global variable that is limited in scope. So they end up in the .data section of the executable along with other globals.

Variables created on the stack when a function is entered are refered to as automatically allocated.

---

### Post by nvteighen on 2008-11-09
Well, **very basically put** all variables get destroyed after the function is exited.

But, what's the point of this? If you just want to "delete" a variable, just don't use it anymore in the same function!

---

### Post by crazyfuturamanoob on 2008-11-09
> **nvteighen said:**
> Well, **very basically put** all variables get destroyed after the function is exited.

But, what's the point of this? If you just want to "delete" a variable, just don't use it anymore in the same function!

But the point is I want to delete a global variable. :D

---

### Post by dwhitney67 on 2008-11-09
> **crazyfuturamanoob said:**
> But the point is I want to delete a global variable. :D

There isn't a way to do that (unless you exit the program).

Why are you using global variables in the first place?  It can lead to or indicate a poor design.

If you have a variable that must be referenced by other modules, rather than expose that variable, create functions that these other modules can call.


Header.h:
[php]
#ifndef HEADER_H
#define HEADER_H

int getValue();
void setValue(int value);

#endif
[/php]


Header.c:
[php]
#include "Header.h"

static int gvalue = 0;

int getValue()
{
  return gvalue;
}

void setValue(int value)
{
  gvalue = value;
}
[/php]


OtherModule.c:
[php]
#include "Header.h"

void myFunction()
{
  int value = getValue();
  ...
  return 0;
}
[/php]

---

### Post by crazyfuturamanoob on 2008-11-09
I was just wanting to do a dynamically extendable list the easy way. A list like in python.

I am noob to C and dynamic memory mallocation is too hard, I don't understand it. But I still need to do that thing.


So first create an array. 
Then, when adding into it, 
copy the array into another with 1 slots more, 
and replace the original array with new one.

Didn't work, because the arrays were different size.
That's why deleting the original array before replacing
it with new one is needed.

---

### Post by Luggy on 2008-11-09
In C and C++ you cannot delete a variable, but you can unallocate or free the memory used by the variable or you can change the scope so that the variable name can be used in other parts of the code.

Scope Example:
```

{
   int y = 5;
   {
      // because y was declared before this current scope, Y is known here
      int x = y;
   }
   // x is no longer known because we got out of the scope
   // you can thus, re-declare x. If this was not true, the previous line
   // would cause an error.
   // When the scope is changed all the memory allocated to the variables
   // is freed.
   int x = 6;
}

```

Deallocation example:
```

{
   int *foo;
   foo = (int*)malloc(sizeof(int));
   // memory is allocated!

   free(foo);
   // deallocates the memory occupied by foo!
}

```

---

### Post by Luggy on 2008-11-09
> **crazyfuturamanoob said:**
> 
So first create an array. 
Then, when adding into it, 
copy the array into another with 1 slots more, 
and replace the original array with new one.


I don't think you can do what you want to do without dynamic allocation... Well, not without making it sloppy... and not without getting into C++ as opposed to C.

If you can get into C++ and don't want to play with dynamic allocation ( which is easier in C++ then in C ) you can use Vectors from STL (The Standard Template Library). Vectors are just what you want, an expandable, adjustable array.

---

### Post by dwhitney67 on 2008-11-09
Say you have allocated an array, populated it, and then want to add more but you are limited in space.  The solution is to reallocate a new chunk of memory for that array.

Here's how:
[php]
#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int main()
{
  char* buf = malloc(6);      // initially allocate 6 bytes

  strcpy(buf, "hello");       // copy a 5-character string into the buffer;
                              // this leave a space for the null-termination
                              // character

  buf = realloc(buf, 12);     // let's make the buffer bigger (12 bytes)

  strcat(buf, " world");      // append to the buffer 6 more characters;

  printf("buf = %s\n", buf);  // voila!  You have a buffer with 11 printable
                              // characters, and one null-termination char

  ...

  free(buf);                  // free the memory


  return 0;
}
[/php]

---

### Post by jimi_hendrix on 2008-11-09
@whitney

thanks for that example...i actually (for no specific purpose) wanted to figure out how to resize an array in C

---

### Post by nvteighen on 2008-11-09
> **crazyfuturamanoob said:**
> I was just wanting to do a dynamically extendable list the easy way. A list like in python.

Now you see what's a low-level language about... 

> I am noob to C and dynamic memory mallocation is too hard, I don't understand it. But I still need to do that thing.


No matter how hard it is (actually it's not that hard if you know how to work with pointers... which in turn also aren't that hard as they seem at first glance), you can't do anything interesting in C without knowing how to use malloc(). It's a fundamental piece of the Std. Lib. (like many others, of course).

Have you installed the manpages-dev package? That will give you documentation accessable from the 'man 3' command (the 3 is for restricting search to the programming section, otherwise you can get a failure on ambiguous cases like printf).

---

### Post by LaRoza on 2008-11-09
> **crazyfuturamanoob said:**
> I was just wanting to do a dynamically extendable list the easy way. A list like in python.

There is no easy way, you have to understand what you are trying to do (it isn't that hard, but if you don't understand it, it is impossible).

> 
I am noob to C and dynamic memory mallocation is too hard, I don't understand it. But I still need to do that thing.

No, it isn't too hard. It is simple. Read up on it. Basically, when you dynamically allocate memory, that memory is spoken for until you release it. If you allocate memory in a function, and you don't free it, that memory is unusable while the program is running (if you do this a lot of times, that can crash a system). That is called a memory leak. Local variables go out of scope when the function returns. 

> 
So first create an array. 
Then, when adding into it, 
copy the array into another with 1 slots more, 
and replace the original array with new one.

Didn't work, because the arrays were different size.
That's why deleting the original array before replacing
it with new one is needed.
You are doing it wrong, or at least, a weird way ;)

---

### Post by SledgeHammer_999 on 2008-11-09
Well why not use "linked lists"? If you use gtk take a look at GList-->[http://library.gnome.org/devel/glib/stable/glib-Doubly-Linked-Lists.html](http://library.gnome.org/devel/glib/stable/glib-Doubly-Linked-Lists.html)

---

