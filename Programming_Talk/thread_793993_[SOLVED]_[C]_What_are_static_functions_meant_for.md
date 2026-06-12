---
title: "[SOLVED] [C] What are static functions meant for?"
date: 2008-05-14
forum: Programming Talk
---

### Post by nvteighen on 2008-05-14
Hi!
No matter how much I read on this, I don't get the point on which are static functions should be used in C for... I just don't get the concept behind them. If you're planning to call a certain function more than once, why would you want to keep a whole function stack stored statically? Won't you be always overwritting data again? Or is it related to code optimization and speed?

Can someone please enlighten me or point me to some good reading on this?

Thanks!

---

### Post by JupiterV2 on 2008-05-14
A static variable has local scope but global lifetime. In other words, its memory isn't deallocated automatically when the function that contains it exits. When you use a statically declared variable, the function itself must also be declared static.

[php]
#include <stdio.h>

static int static_fun()
{
	static int count = 5;
	
	printf("%d...\n", count--);
	
	if( !count ) 
	{
		printf("BOOM!\n");
		return 0;
	}
	
	return 1;
}

int main()
{
	int x;
	
	while( x ) x = static_fun();
	
	return 0;
}[/php]

It's useful to avoid declaring global variables or when you don't want to pass a variable to the function. I believe, but I could be mistaken here, that extensive use of static variables and functions will cause your program to have a larger memory footprint.

I'm not sure if you're looking for more in-depth explanation that this or not...

---

### Post by andrew_kirkham on 2008-05-14
My understanding was that declaring a function as static in C simply means that the function scope is limited to that .c file, thus it simply helps avoid namespace pollution.

---

### Post by jespdj on 2008-05-14
> **JupiterV2 said:**
> A static variable has local scope but global lifetime. In other words, its memory isn't deallocated automatically when the function that contains it exits. **When you use a statically declared variable, the function itself must also be declared static.**
I can't test it right now, but I doubt that this is true.

**static** in C has to do with linkage: static functions have internal linkage, which means they are only visible to other functions inside the same compilation unit.

See: [C - Static functions](http://www.space.unibe.ch/comp_doc/c_manual/C/SYNTAX/static.htm)

Note that in C++, static has a different meaning for member functions.

---

### Post by WW on 2008-05-14
> **jespdj said:**
> I can't test it right now, but I doubt that this is true.

jespdj is correct--a function does not have to be declared static to use a static variable.  This function simply counts how many times it has been called; the *function* is not declared static, but it uses a static *variable*:
```

int counter()
    {
    static int count = 0;

    ++count;
    return count;
    }

```

---

### Post by mike_g on 2008-05-14
A static variable in C is the same as a global, but with limited scope.
I had thought that static function is similar in that it dosent need to allocate a new stack each time it is called.

I noticed that by using static types you can get reallyy big speed gains. The downside to it is that it can cause problems if the compiler wants to inline it for optimisation. So, whether or not it may actually turn out to be faster    depends.

---

### Post by dwhitney67 on 2008-05-14
The 'static' keyword can be used to limit the scope of a variable or a function to a module.  It can also be used, as previously posted, to define a static local variable within a function that retains state even after the function call has completed.

It is possible to emulate certain aspects of Object Oriented Programming when programming C; namely, the encapsulation principles.

Thus it is possible to define a local variable within a module, and manipulator functions, that can only be accessed from within the module.  Other modules will not have access to these, however can have access to 'public' functions.

Here's a simple example demonstrating these concepts...

Silly.h:
[PHP]#ifndef SILLY_H
#define SILLY_H

// Declare only public function(s) here
//
void set( unsigned int );
unsigned int get();

#endif[/PHP]

Silly.c:
[PHP]#include "Silly.h"


// Private data
//
static unsigned int value = 0;


// Private functions
//
static unsigned int multiplyByTwo( unsigned int v )
{
  return v << 1;
}


// Public functions
//
void set( unsigned int v )
{
  value = multiplyByTwo( v );
}

unsigned int get()
{
  return value;
}[/PHP]

Main.c:
[PHP]#include "Silly.h"
#include <stdio.h>


int main()
{
  printf( "Calling set() with value of 10\n\n" );
  set( 10 );

  printf( "Calling get(), the value = %d\n", get() );

  //multiplyByTwo( 10 );     // cannot call... private/static method only accessible in Silly.c

  return 0;
}[/PHP]

---

### Post by nvteighen on 2008-05-14
Thank you all!

I think I've got it now... 

1) Static functions = scope inside the file it belongs to. I've seen this can be used for implementing a certain function needed inside a shared library for internal purposes.

2) Static variables = scope inside block but with global lifetime.

Thanks again! (marking as solved)

---

### Post by rbprogrammer on 2008-05-14
> **andrew_kirkham said:**
> My understanding was that declaring a function as static in C simply means that the function scope is limited to that .c file, thus it simply helps avoid namespace pollution.

i second you andrew.  i learned about the static keyword for C this last semester for my systems programming class.

and with the many header files that we needed for each project, the static keyword came in handy a few times for that very reason.

---

