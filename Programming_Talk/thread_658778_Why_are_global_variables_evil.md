---
title: "Why are global variables evil?"
date: 2008-01-05
forum: Programming Talk
---

### Post by xelapond on 2008-01-05
Hi Everyone, 

I'm writing a program in C where a function generates some data that a rest of the program will need.  This data is in an array.  So, I have two options, because I cannot return an array I can either make it a global variable or use a pointer and return it.  Because all sorts of stuff within main has to access it why not just make it a global variable?

Pretty much my question is, why are global variables evil.  They would seem really efficient to me:^)

---

### Post by Wybiral on 2008-01-05
The need for globals (especially in large applications) is typically a sign that the overall design needs rethinking. In a small application where it's easy to manage, it probably wont make a difference (though it's usually still frowned upon). When you have situations as it sounds like you have, IMO a cleaner pattern IS to pass the pointer around. And if you have multiple "objects" (not in the OO sense) that you need to pass around, you obviously don't want to pass each one to each function, so it's best to wrap them in a structure/class/array and pass that around.

What's wrong with passing a pointer around?

---

### Post by popch on 2008-01-05
Global variables are not evil. 

It is a sound design decision to keep each and every variable available exactly as long as it can possibly be used. 

Hence, variables which are only needed to - say - locate and open a database should disappear when the database is open.

On the other hand, data which is first collected, then enhanced and lastly used for the whole time the program is running are very likely candidates for global variables.

Another sound design decision consists of implementing each part of the program in a way which makes it independent of as many decisions as possible.

Therefore, the individual parts of the program should not be coded in a way that makes it dificult to transform global variables into something else. Hence, the different parts of the program should not access the global variables by themselves if it is at all possible.

Conclusion: a plausible design could be as follows.

Keep your data array in a global variable but build and process that data only in local 'branches' of your application, and have those branches access your global variable through pointers, and through pointers only.

You will be grateful to yourself when the first change to the program is to be done, which is about ten days before the program is put to any use.

---

### Post by wolfbone on 2008-01-05
> **xelapond said:**
> 
Pretty much my question is, why are global variables evil.  They would seem really efficient to me:^)

Global variables are (potentially) evil because they are accessible from every function in every file. They can be shadowed by local variables and, in the worst case, modified by multiple different functions. This increases complexity, the potential for bugs, and reduces ease of code maintenance.

It doesn't mean you should never use them but you should try to avoid introducing and using them.

---

### Post by evymetal on 2008-01-05
I agree with just about all of what popch and wybiral have said.

If you know your code will never be used by anyone else in a different context then go ahead and use globals, but it's asking for conflicts if you're writing a module for someone else.

Personally I would declare it on the heap and pass a pointer back from the function (or declare it in the outer scope as a pointer, pass that to the function, and modify the value in the function - it's far from functional programming but I like that method). It just gives you more control for modifying your code later.

---

### Post by Lster on 2008-01-05
I wouldn't call them evil, but do use caution with them. Many applications I write use them and I pride myself on stability and performance.

---

### Post by LaRoza on 2008-01-05
Global variables cause nasty bugs that are difficult to track down. I wouldn't call them evil, I just don't think they are worth using unless you are really sure you can manage it.

---

### Post by Quikee on 2008-01-05
What's the point in having functions then, if for the same input data you get different output, depending on the global variable. 

Example:

```

int delta = 0;

int calculate(int a, int b, int c) {
  delta += 1;
  return (a * b * c) + delta;
}
```

Now you let's say you don't have the implementation and just want to use the function calculate (pretend that calculate, a, b and c have meaningful names). 

The only thing you see is:
```
int calculate(int a, int b, int c);
```

It is better to avoid global variables altogether if you have the choice.

---

### Post by xelapond on 2008-01-05
so would a better way be to return it in the form of a pointer, then turn that pointer into an array in main?

Sorry if im completely wrong, I have never used pointers before:^)

Thanks, 

Alex

---

### Post by evymetal on 2008-01-05
You've never used pointers?

Read up on them, then read some more. You can't understand C properly until you understand pointers. (and IMHO you can't understand other languages properly until you understand C pointers)


**Quick overview (really, really quick, read up on it...):**

imagine memory as a load of numbered boxes 0,1,2,.....n (e.g n=1023 for 1Kb RAM).

The pointer is the number for the beginning of the variable you are looking up.

so, I could put a massive variable at #23. When I pass this variable to another function I can either pass the entire massive variable (and copy it to somewhere else in RAM to do that, taking time), or I can just send "23" to the function (and what type of variable it is).

A pointer wraps up the position and the type of variable in a nice (to C programmers anyway) way, and lets you work with large variables without copying them each time you make a function call.

Because of the way that arrays are held in memory you can do all kinds of other "pointer magic" with arrays, I'd recommend reading up on arrays and pointers because it can make your array functions much faster.


Out of interest, you can also do it another way with pointers. You can pass the pointer to the function as a parameter when you call it, and then any changes you make within the function will actually be changing the original data.


Good luck, it's a bit hard to get to grips with at first, but when you do you'll never look back.

---

### Post by dwhitney67 on 2008-01-05
> **xelapond said:**
> so would a better way be to return it in the form of a pointer, then turn that pointer into an array in main?

Sorry if im completely wrong, I have never used pointers before:^)

Thanks, 

Alex
Below is a silly example.  To compile:

```
gcc -std=c99 silly.c
```

[PHP]#include <stdio.h>     // for printf() and sprintf()


struct Foo
{
  int   value;
  char str[20];
};


void displayArray( const struct Foo *array, const size_t numElements )
{
  for ( int i = 0; i < numElements; ++i )
  {
    printf( "array[%d].value = %d\tarray[%d].str = %s\n",
            i, array[i].value,
            i, array[i].str );
  }
}


int main()
{
  const size_t SIZE = 10;

  // declare array
  struct Foo array[ SIZE ];

  // setup array (probably would be better to do this in a function)
  for ( int i = 0; i < SIZE; ++i )
  {
    array[i].value = i * 5;
    sprintf( array[i].str, "track_%d", i + 1 );
  }

  // call function, passing the array and its size
  displayArray( array, SIZE );

  return 0;
}[/PHP]

---

### Post by stroyan on 2008-01-05
Global variables lead to surprises when they are used in place of function parameters.  Writing and maintaining code is a constant struggle against misunderstandings and false assumptions.  It is very important to make code clearly understandable.  That is best accomplished by simplicity.  Making functions affect only data passed as parameters helps to keep their effects more clear.

In many circumstances the size of data is not known in advance.  Allocating a fixed buffer for variable sized data will lead to buffer overflows or wasted memory.  Variable size data is handled by dynamically allocating memory for data.  That requires the use of pointers in C.  The malloc, free, and realloc functions are at the heart of C data management.  And they are a rich source of defects.  You need to use them very carefully to avoid mistakes that can cause mysterious and difficult to find bugs.  You would do well to study the conventions for allocating and freeing dynamic memory.  And you should get comfortable with a debugging tool such as valgrind that can help you to find and fix the mistakes that every beginning C programmer does make.

---

### Post by xelapond on 2008-01-05
In relatively new to C if I haven't already made that apparent:)

Im reading up on them right now.  Thanks for the help!

Also, I should probably mention I am not programming on a conventional x86-64 based computer running Linux.  I am programming on an Atmel ATmega16 with 16 Kilobytes of flash program memory and 1 Kb of SRAM.

But for future programs should I completely avoid them or just use them sparingly?

Thanks, 

Alex

---

### Post by DMills on 2008-01-05
On an embedded core like the one you are using, you often find that space efficiency is everything and that making things like status flags global will save you a few bytes (which can matter, bitfields are your friend).

On bigger things you often find a few things that it makes sense to make global, but it often makes sense to create accessors for them so the variable itself is not really global:

global.h:
int * status();
struct foo * myfoo();

Global.cpp 
int st = 0;
struct foo f = 0;

status()
{

---

### Post by pmasiar on 2008-01-05
There is another danger when using lots of globals.
Chances are, you will need to change how your globals behave. If you wrapped globals in a "world" singleton object, you can use same methods, even if internal representation changed. If you used data directly, you may have to change every use of the global variable. Not a big deal in small program, major pain in large project with many developers, possibly maintaining multiple versions of the software. Especially if you have to maintain the same database structure...

And yet another issue is using globals in shared libraries. WTF website has "interesting" examples what went wrong. Up to irreversible corrupting of a huge bank database, not fun.

---

