---
title: "passing variables || use them as global"
date: 2008-10-13
forum: Programming Talk
---

### Post by kcode on 2008-10-13
When should we make variables global and when to just work around by passing them between functions? 
(sometimes i get really confused about what to choose)

thanks

---

### Post by Canis familiaris on 2008-10-13
IMO It's better to pass variables among functions rather than creating global variables.

---

### Post by Rich78 on 2008-10-13
**

---

### Post by Rich78 on 2008-10-13
Agreed, globals should be used as little as possible.

There are some rare circumstances where globals are useful and make sense, such as with enums or constants.

But generally global variables are better avoided particularly if they're assignable variables.

---

### Post by nvteighen on 2008-10-13
I suppose this is about Python. If not, please tell us.

Think about this: when you refer to an object inside a "scope block" (function, class or module), Python will look at the variables available on that block, if none is found, NameError is thrown.

So, you use "global" when you want to make the interpreter clear that, when referencing that object inside a "scope block", it should rather look for the definition at the module's top-level instead of looking for it at the current chunk of code. If you know C, it works almost the same as the "extern" keyword.

But, the posters above are right: except in some very particular situations, you'd better not use a global variable, as it obscures code. Think about this: when you don't use them at all, you're absolutely sure that only variables declared inside the function and those passed as parameters will affect that function's behaivor; so, you get a very manageable set of variables to look at when analyzing the function (e.g. for debugging). But, if you start relying on global variables, you'll see that any change on that variable may affect the function's behaivor... and as the variable is global, the triggering change could be produced by just any function.

So, are they completely useless? Well, not. C's most famous global variable is errno, a global variable programmers use to keep track of what the last error produced was. Notice that that global variable is meant to be written/read only when something exceptional occurs, so yes, it will affect the program's behaivor, but usually only when something weird else already did. 

If the global variable it's for a very special, exceptional purpose you just can't do by local variables, then it may be clever to use a global variable. But the criterion seems to be that "un-hazardous" global variables are meant to be debugging helps and never meant to be part of the "working code".

---

### Post by kcode on 2008-10-13
Im working on C right now.
Got it.

thanks

---

### Post by monkeyking on 2008-10-13
It depends on so much.
Generally you should avoid using globals,
but it's not because of speed issues, or something like that.
It's simply because, you a more likely to do wrong things.


If you pass variables as arguments, you can use const correctness,
which is quite handy in larger programs.


In some programs,
like pthreaded programs,
you have to use globals.

Also
If you're using one variabel in all your functions,
then it would be stupid not to use one global var.


just use commen sense

---

### Post by dwhitney67 on 2008-10-14
> **kcode said:**
> Im working on C right now.
Got it.

thanks

Since you are learning C, if you require a variable's declaration to lie outside a function, make sure it is accessible only from within a module (a .c file) where the function(s) are implemented.  Provide accessor functions that can be used to obtain or to set the value of this variable.  These functions should be defined in a header file, and implemented in the same file where the variable is defined.

Below is a small example you can play with.  To build it:
```
gcc -Wall -pedantic -std=gnu99 Main.c SignalHandler.h -o sigtest
```

SignalHandler.h:
[PHP]#ifndef SIGNAL_HANDLER_H
#define SIGNAL_HANDLER_H

void setupInterruptHandler();

int  interruptReceived();      // 1 = yes, 0 = no

#endif[/PHP]

SignalHandler.c:
[PHP]#include "SignalHandler.h"
#include "signal.h"


// Static variable accessible only within this module.
// From the viewpoint of this module, the variable is GLOBAL.
static int intRcvd = 0;

// Not defined in SignalHandler.h because we don't want anyone calling it.
static void sigHandler(int);


void setupInterruptHandler()
{
  signal(SIGINT, sigHandler);
}

int  interruptReceived()
{
  return intRcvd;
}

void sigHandler(int signum)
{
  intRcvd = 1;
}[/PHP]

Main.c:
[PHP]#include "SignalHandler.h"
#include <unistd.h>
#include <stdio.h>


// Possible. But try to access and you will not be able to.
extern int intRcvd;


int main()
{
  setupInterruptHandler();

  // Not possible; compiler has no idea what 'sigHandler' is.
  //sigHandler(1);

  while ( !interruptReceived() )
  {
    printf( "idling, waiting for operator to enter ctrl-c.\n" );
    sleep(1);

    // Not possible; linker has no idea what 'intRcvd' is.
    //intRcvd = 1;
  }
  return 0;
}[/PHP]

---

