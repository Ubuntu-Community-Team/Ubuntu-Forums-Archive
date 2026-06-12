---
title: "I made a resizeable array in C, it works, but with warning. How to quiet the warning?"
date: 2008-11-21
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-21
I wrote a small program in C to see, if resizeable arrays are possible to make (not linked lists):
```

#include <stdio.h>

int *testarray;

void set_array_size( int size )
{
    int new_array[size];
    testarray = &new_array;
    printf("Array size: %i\n", size);
}

int main( )
{
    set_array_size(23);
    printf("Test slot #9: %i\n", testarray[9]);
    testarray[9] = 2;
    printf("Test slot #9: %i\n", testarray[9]);
    set_array_size(5);
    printf("Test slot #3: %i\n", testarray[3]);
    set_array_size(16);
    
    return 0;
}

```
It works just as it should work. (it shouldn't keep previous values after resize)

But gcc gives me a warning:
> 
arho@ohra-laptop:~/Työpöytä/C/teststuff/arrays$ gcc array_test__2.c -o test2
array_test__2.c: In function ‘set_array_size’:
array_test__2.c:8: warning: assignment from incompatible pointer type
arho@ohra-laptop:~/Työpöytä/C/teststuff/arrays$ 

So what does that warning mean and how can I fix it?

---

### Post by rbprogrammer on 2008-11-21
Your code might be slightly flawed, thats why you are getting that warning.  Basically you are declaring a variable on the stack within the function (ie. the array).  Then when you leave the function that data is not in scope.

A better solution to the problem would be:
```


#include <stdio.h>

int *testarray;

void set_array_size( int size )
{
    int * new_array = (int*) malloc(size*sizeof(int));
    testarray = &new_array;
    printf("Array size: %i\n", size);
}

int main( )
{
    set_array_size(23);
    printf("Test slot #9: %i\n", testarray[9]);
    testarray[9] = 2;
    printf("Test slot #9: %i\n", testarray[9]);
    set_array_size(5);
    printf("Test slot #3: %i\n", testarray[3]);
    set_array_size(16);
    
    return 0;
}

```

In this case, the data will be on the heap instead of the stack.  As far as your code working, I would have to say that would be a false positive.  There is no gaurantee that your code will be with a more elaborate program.

---

### Post by rbprogrammer on 2008-11-21
Give me a few more minutes, and I will be able to refine my code, it seems that my code also give a slightly different warning.

---

### Post by rbprogrammer on 2008-11-21
Haha, silly me... I forgot to include the right header for malloc

```

#include <stdio.h>
#include <stdlib.h>

int *testarray = NULL;

void set_array_size( int size )
{
    int * new_array = (int*) malloc(size*sizeof(int));
    if( testarray != NULL )
        free( testarray );
    testarray = new_array;
    printf("Array size: %i\n", size);
}

int main( )
{
    set_array_size(23);
    printf("Test slot #9: %i\n", testarray[9]);
    testarray[9] = 2;
    printf("Test slot #9: %i\n", testarray[9]);
    set_array_size(5);
    printf("Test slot #3: %i\n", testarray[3]);
    set_array_size(16);
    
    return 0;
}

```

There, that works.  but keep in mind that global variables are mostly considered bad practice and should be avoided whenever possible.

---

### Post by raf_kig on 2008-11-21
> **crazyfuturamanoob said:**
> I wrote a small program in C to see, if resizeable arrays are possible to make (not linked lists):
It works just as it should work.

No it doesn't.
It leaks memory, uses wrong types and i does more or less random stuff. You should read up on malloc/free and pointers.
Below is a version that should be working (my c is pretty rusty...)

```

#include <stdio.h>
#include <stdlib.h>

int *testarray = NULL;

void set_array_size( size_t size )
{
    if (testarray != NULL)
        free(testarray);
    testarray = (int *) malloc(size*sizeof(int));
    if(testarray == NULL)
        printf("unable to allocate memory"); //do some error handling here
}

int main( )
{
    set_array_size(23);
    printf("Test slot #9: %i\n", testarray[9]);
    testarray[9] = 2;
    printf("Test slot #9: %i\n", testarray[9]);
    set_array_size(5);
    printf("Test slot #3: %i\n", testarray[3]);
    set_array_size(16);
    return 0;
}

```

Regards

raf

/edit hi rbprogrammer ;-)
didnt see your version clicking reply :-)

---

### Post by JohnFH on 2008-11-21
> **crazyfuturamanoob said:**
> I wrote a small program in C to see, if resizeable arrays are possible to make (not linked lists):

But gcc gives me a warning:

So what does that warning mean and how can I fix it?

To answer your question ...
The warning basically means that the assignment in the line:
```
testarray = &new_array;
```
is incorrect.  The compiler is saying that &new_array is not an int pointer.  &new_array is the address of the address of the array, so you want to specify either &new_array[0] or just new_array to get the address of the array.  Fixing this line will fix your warning, but as others have said, your code still needs fixed after that.

Have a look at using realloc to re-allocate memory of the array.

---

### Post by rbprogrammer on 2008-11-21
Just for the record, crazyfuturamanoob do you know that arrays and pointers are the same thing, only in different notation.  Using pointers does not imply that you are using linked lists.  However, the opposite does not apply.  Meaning, linked lists are made from pointers, but pointers do not always make linked lists.

---

### Post by rbprogrammer on 2008-11-21
> **raf_kig said:**
> 
/edit hi rbprogrammer ;-)
didnt see your version clicking reply :-)

back at ya ;-)

Yeah, after my first reply I decided to test my code that I wrote and found that i forgot to include the stdlib.h header.  I guess I got "reply" greedy.. :lolflag:

---

### Post by crazyfuturamanoob on 2008-11-21
> **rbprogrammer said:**
> 
There, that works.  but keep in mind that global variables are mostly considered bad practice and should be avoided whenever possible.

Huh??? :confused: What's wrong with global variables? Almost every possible program uses global variables as I know???

---

### Post by tom66 on 2008-11-21
From what I understand, you could be wasting memory, and, if you have a global variable it doesn't override a local variable so this could cause problems and confuse you writing code, e.g:

```


int i = 5;

void somefunc()
{
   i = 4; // not the same as int i = 4
}


```

would not create a new i variable, but would set the global variable. It's just confusing. There's nothing actually preventing you from using global variables, though. 

Compare:

```


int i = 5;

void somefunc()
{
   int i = 4; 
}


```

Now we have two i variables in different scopes. Want to access the original i variable? Out of luck, you can't.

---

### Post by crazyfuturamanoob on 2008-11-21
> **tom66 said:**
> From what I understand, you could be wasting memory, and, if you have a global variable it doesn't override a local variable so this could cause problems and confuse you writing code, e.g:

```


int i = 5;

void somefunc()
{
   i = 4; // not the same as int i = 4
}


```

would not create a new i variable, but would set the global variable. It's just confusing. There's nothing actually preventing you from using global variables, though. 

Compare:

```


int i = 5;

void somefunc()
{
   int i = 4; 
}


```

Now we have two i variables in different scopes. Want to access the original i variable? Out of luck, you can't.

But why the hell would I want two variables with exactly same name? That would be even more confusing.

I don't see a point why should I avoid using global variables. Some things are even impossible to do without them.

---

### Post by Tony Flury on 2008-11-21
What can't you do without using globala ? just curious. 

I can't envisage anything that would be impossible with globals - tougher to do in some cases - but not impossible. I only have 20 + years of writing application critical code, so of course i could be wrong :-)

---

### Post by crazyfuturamanoob on 2008-11-21
> **Tony Flury said:**
> What can't you do without using globala ? just curious. 

I can't envisage anything that would be impossible with globals - tougher to do in some cases - but not impossible. I only have 20 + years of writing application critical code, so of course i could be wrong :-)

I have a game engine chunk I have been writing.

Now I'm making load/save routines for maps.

There is one global variable, which holds the map data.

How could it be if not global? Multiple functions need to access it.

It must be global. No other way around, and if there is, then it's so
hard there's no point using it.

---

### Post by Tuna-Fish on 2008-11-21
> **crazyfuturamanoob said:**
> 
There is one global variable, which holds the map data.

How could it be if not global? Multiple functions need to access it.

Use dynamic memory?

There is no situation where you cannot survive without globals. But, "do not use globals" does not mean "NEVER USE GLOBALS", it means avoiding their use when possible. Mainly this is because if you are writing any program that gets bigger than a tiny afternoon project, if your code is full of globals it can be very hard to reason about it.

---

### Post by mssever on 2008-11-21
The only time I can think of where globals are helpful is a program-wide configuration object. Aside from that, just pass your data around. The misuse of globals can lead to hard-to-find bugs and maintenance problems.

---

### Post by Tony Flury on 2008-11-21
Accessible by everything does not mean that it is a globally declared variable - there are other methods of ensuring that something is globally available.

For instance - declare and instatiate the variable and the memory in the main() function - and then pass a pointer to it around the rest of the functions. The data is still available - just not a globally named variable.

If you have a massive chunk of data - instantiate the data in one function, and use a mmap to make sure that other code has access to the same data.

---

### Post by Cracauer on 2008-11-21
> **crazyfuturamanoob said:**
> I wrote a small program in C to see, if resizeable arrays are possible to make (not linked lists):
```

#include <stdio.h>

int *testarray;

void set_array_size( int size )
{
    int new_array[size];
    testarray = &new_array;
    printf("Array size: %i\n", size);
}

```


No can do.

new_array is stack allocated.

It seems to work because you happen to not use the stack for anything else in this test program but it's not working. The moment you call another function the array will be overwritten with the other function's local variables and return address.

You can only use new_array in functions that are below set_array_size in the call tree (and then you don't need a global).

---

### Post by pmasiar on 2008-11-22
> **mssever said:**
> The only time I can think of where globals are helpful is a program-wide configuration object.

... and that is still better handled as [http://en.wikipedia.org/wiki/Singleton_pattern](http://en.wikipedia.org/wiki/Singleton_pattern) - so there are multiple ways to instantiate it, but always only once.

OP: when compiler complains, you better try to understand why, not silence the warning. Worst errors (hardest to discover and fix) are the silent ones!

---

### Post by scourge on 2008-11-22
> **crazyfuturamanoob said:**
> I have a game engine chunk I have been writing.

Now I'm making load/save routines for maps.

There is one global variable, which holds the map data.

How could it be if not global? Multiple functions need to access it.

It must be global. No other way around, and if there is, then it's so
hard there's no point using it.

It sounds like you've started some impressively complex projects before learning even the basics of C. That can be a good way to learn, but it can also lead to frustration, and it will most definitely lead to many rewrites as you get better and realize that your old code sucks. C is a small language, so there's no excuse for not taking a few hours to read about dynamic memory allocation, pointers, structs, etc.

---

### Post by crazyfuturamanoob on 2008-11-22
> **scourge said:**
> It sounds like you've started some impressively complex projects before learning even the basics of C. That can be a good way to learn, but it can also lead to frustration, and it will most definitely lead to many rewrites as you get better and realize that your old code sucks. C is a small language, so there's no excuse for not taking a few hours to read about dynamic memory allocation, pointers, structs, etc.

That's exactly how I learned Python.

And yeah, I got frustrated a couple times.

But I learned it.

So if I do the same with C I'll probably learn it.

---

### Post by geirha on 2008-11-22
All of the suggestions leek memory as the last malloc is never freed... 
Also, why not use realloc? it will keep the values that are possible to keep.

```

#include <stdio.h>
#include <stdlib.h>

int *ta= NULL;

void set_array_size( int size )
{
    ta= realloc(ta, size * sizeof(int));
    if (ta == NULL)
        printf("fail...\n");
}

int main()
{
    set_array_size(2);
    ta[0]=1; ta[1]=2;
    set_array_size(4);
    ta[2]=3; ta[3]=4;
    printf("%d,%d,%d,%d\n", ta[0], ta[1], ta[2], ta[3]);
    set_array_size(2);
    printf("%d,%d\n", ta[0], ta[1]);

    free(ta);
    return 0;
}

```

---

### Post by nvteighen on 2008-11-22
> **crazyfuturamanoob said:**
> 
There is one global variable, which holds the map data.

How could it be if not global? Multiple functions need to access it.

It must be global. No other way around, and if there is, then it's so
hard there's no point using it.

The history of programming has devised the concept of modularity for a reason... To reduce the factors affecting a certain procedure's result to the least amount of data external to the procedure. In other words, yes sometimes it's easier to write stuff using globals, but it's always much easier to debug stuff without globals as you automatically reduce the amount of significant factors to the variables locally declared (this includes the parameter list).

Globals have their use when you want to track the **program's** state of execution... The most classic example is C's errno from errno.h, a global variable used to save the last error code detected. Other usage is Perl's "default variables", which actually act as "constant locations" (e.g. when iterating a list, you know the element accessed is always stored at $_. This is extremely useful in some contexts like regexp matching).

Ok, now to the resizable arrays:
If you read about "malloc() & friends", you'll know there's a function that resizes dynamically stored data.

---

### Post by pmasiar on 2008-11-22
> **crazyfuturamanoob said:**
> That's exactly how I learned Python.
...
So if I do the same with C I'll probably learn it.

Possibly, but Python is **substantially** more forgiving language. Orders of magnitude more forgiving.

Python was designed to be used also by non-CompSci majors to solve simple everyday tasks. C was designed to be used by experts who know exactly what they was to accomplish: to write as effective code as they can for operating system.

---

### Post by u-slayer on 2008-11-24
umm, silly question...but why don't you just use vectors?

They are like arrays but you can change their size easily.

[http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/)

---

### Post by sambarusty on 2008-11-24
> **crazyfuturamanoob said:**
> Huh??? :confused: What's wrong with global variables? Almost every possible program uses global variables as I know???
In a small program, probably nothing, when you are doing development, global variables are a bad practice, it makes things easy sometimes, but you loose control over the flow of the code. It is kid of a free for all.  When you access everything from everywhere, it isn't good.

---

### Post by Geekkit on 2008-11-24
> **u-slayer said:**
> umm, silly question...but why don't you just use vectors?

They are like arrays but you can change their size easily.

[http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/)

Because he's not using C++, he's using C - although for learning purposes he could create similar types of data structures (via structs) and duplicate the behaviors (via functions) ... minus the encapsulation of course.

EDIT: to parrot what several others have said, look up malloc, calloc, realloc, free, and pointers, your program does not work.

---

### Post by nvteighen on 2008-11-24
> **Geekkit said:**
> Because he's not using C++, he's using C - although for learning purposes he could create similar types of data structures (via structs) and duplicate the behaviors (via functions) ... minus the encapsulation of course.


If he splits this into its own module and makes use of the opaque pointer technique, he'll get a very nice and full-fledged encapsulation in C.

---

### Post by Geekkit on 2008-11-24
> **nvteighen said:**
> If he splits this into its own module and makes use of the opaque pointer technique, he'll get a very nice and full-fledged encapsulation in C.

True, although considering he's not quite aware of malloc/calloc/realloc/free yet I'd save that for an advanced lesson. I like GTK's handling of OO-ness with C, quite easy on the eyes.

Don't know if you've read this or not:

[http://www.cs.rit.edu/~ats/books/ooc.pdf](http://www.cs.rit.edu/~ats/books/ooc.pdf)

I found it helped me to be more modular and keep thinking in terms of objects - something I had always enjoyed since C++ and Java.

---

### Post by nvteighen on 2008-11-24
I didn't know about that article... I kinda learned this by observation (GTK+ was a major help to see how OOP in C is like) and advice from people here :p

Thanks!

---

