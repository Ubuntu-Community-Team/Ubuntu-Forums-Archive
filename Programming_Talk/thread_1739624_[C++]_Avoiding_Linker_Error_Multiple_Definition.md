---
title: "[C++] Avoiding Linker Error: Multiple Definition"
date: 2011-04-26
forum: Programming Talk
---

### Post by dodle on 2011-04-26
[php]#ifndef _TEST_H_
    #define _TEST_H_

#include <iostream>
using namespace std;

void PrintHello()
{
    cout << "Hello World\n";
}

#endif /* _TEST_H_ */[/php]

To avoid multiple defintions of PrintHello when linking, is the only solution to separate the declaration and definition into source/header files?

[php]#ifndef _TEST_H_
    #define _TEST_H_

#include <iostream>
using namespace std;

void PrintHello();

#endif /* _TEST_H_ */[/php]

[php]#include "test.h"

void PrintHello()
{
    cout << "Hello World!\n";
}[/php]

---

### Post by dwhitney67 on 2011-04-26
First, you should avoid placing a "using namespace" directive in a header file.  Any module that includes the header file would then have it's space unnecessary filled with the particular namespace defined in the header file.

As for good programming style, typically one declares functions and classes within a header file, and then implements the functions and class methods within a .cpp file.

If however, you want to be different, you could declare/implement your function in the header file -- but you must preface it with the "static" or "inline" keyword.  I'm not sure why the latter works, but it just does.  :-)

---

### Post by Arndt on 2011-04-26
> **dwhitney67 said:**
> First, you should avoid placing a "using namespace" directive in a header file.  Any module that includes the header file would then have it's space unnecessary filled with the particular namespace defined in the header file.

As for good programming style, typically one declares functions and classes within a header file, and then implements the functions and class methods within a .cpp file.

If however, you want to be different, you could declare/implement your function in the header file -- but you must preface it with the "static" or "inline" keyword.  I'm not sure why the latter works, but it just does.  :-)

Is it certain that 'inline' must be obeyed by the compiler? For C, I think it's the case that the compiler is allowed to choose whether to inline or not.

When it is inlined, and not accessed using by having its address taken and passed around, it never needs to appear under its own name in an object file. At least that seems to be a good reason why it doesn't result in multiple definition clashes during linking.

---

### Post by nvteighen on 2011-04-26
But, do you understand what causes a multiple definition, right?

What you have to avoid is any situation where the linker could find more than one definition for the same function. Remember that in C++, due to function overloading, two functions A and B are defined multiple times (and therefore failing) iff A's and B's signatures are exactly the same and that a function signature is formed by the name, namespace (or class, if it's a method), return type and argument list.

So, what you want is to get rid of any multiple definition before the linker does it job. Inlining would do it, because it works on the compilation stage, but it would hide the function for any usage external to the specific module in which the function has been inlined (@Arndt, @dwhithney67: IMO, this should be true regardless of whether the code is effectively inlined or not, as any inlined function is implicitly a static function... at least from an interfacing POV...). Declaring as static would definitely work, as static functions are local to the module in which they have been defined and declared (actually, you can't declare them in a header file... it'd defeat their purpose).

But I'd rather go for a normal approach: just don't define the same function twice or two functions with the exact same signature; if needed, use overloading or namespaces, as you're in C++ and not in C.

---

### Post by dodle on 2011-04-26
**@dhwhitney & nvteighen:** Thanks again, I probably couldn't count how many times you have responded to my questions.

Okay, so from what you have told me and what I have read since ([http://www.cprogramming.com/tutorial/statickeyword.html](http://www.cprogramming.com/tutorial/statickeyword.html)), these seem like the best solutions: Either declare functions in a header file and define them in a source:

[php]#ifndef _TEST_H_
    #define _TEST_H_

void Initialize();

#endif[/php]
[php]#include "test.h"

bool initialized = false;

void Initialize()
{
    if (!initialized) initialized = true;
}[/php]

or declare them as static and define them in a single header:

[php]#ifndef _TEST_H_
    #define _TEST_H_

static void Initialize()
{
    static bool initialized = false;
    if (!initialized) initialized = true;
}[/php]

Is there a reason for avoiding one or the other? Declaring and defining in the header makes less typing in the command line.

---

### Post by flyingAnt on 2011-04-27
:confused: In study, difficult to understand

---

### Post by Arndt on 2011-04-27
> **dodle said:**
> **@dhwhitney & nvteighen:** Thanks again, I probably couldn't count how many times you have responded to my questions.

Okay, so from what you have told me and what I have read since ([http://www.cprogramming.com/tutorial/statickeyword.html](http://www.cprogramming.com/tutorial/statickeyword.html)), these seem like the best solutions: Either declare functions in a header file and define them in a source:

[php]#ifndef _TEST_H_
    #define _TEST_H_

void Initialize();

#endif[/php]
[php]#include "test.h"

bool initialized = false;

void Initialize()
{
    if (!initialized) initialized = true;
}[/php]

or declare them as static and define them in a single header:

[php]#ifndef _TEST_H_
    #define _TEST_H_

static void Initialize()
{
    static bool initialized = false;
    if (!initialized) initialized = true;
}[/php]

Is there a reason for avoiding one or the other? Declaring and defining in the header makes less typing in the command line.

I'm not sure what you mean with less typing on the command line. In any case, if the length of the compilation and linking commands feel prohibitive, it's time to write a Makefile. For larger projects, they (or some equivalent framework) are indispensible.

---

