---
title: "Does the main C program need a header?"
date: 2009-01-14
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-14
I got plenty of .c files, and .h files, and then one main.c without header, which contains main() function.

So does main.c need a header? Do you use headers with main program file?

---

### Post by Arylon on 2009-01-14
No, main.c does not require a header file. When you have a .c and .h pair, the .h file is to declare the existence of functions that are defined in the .c files so that these functions can be called in other files. Since functions in main.c do not usually need to be called in other files, no main.h file is needed.

---

### Post by eye208 on 2009-01-14
"main.c" needs the headers of the other modules (to access their data types and functions) but usually doesn't have a header file itself.

---

### Post by days_of_ruin on 2009-01-14
> **crazyfuturamanoob said:**
> I got plenty of .c files, and .h files, and then one main.c without header, which contains main() function.

So does main.c need a header? Do you use headers with main program file?

If anything is going to include main.c then you need one.
Otherwise you don't.

---

### Post by wmcbrine on 2009-01-14
Don't do cargo cult programming. Go back to the beginning here, and understand exactly how a header file works, and what it's for. Then a question like this won't arise.

Start with the "include" pre-processor directive:

```

#include "myheader.h"

```

So, what does this do? Just what it says -- it *includes* the contents of myheader.h into the pre-processor output. Say you have two files --

myheader.h:
```

int myfunc(int, int);

```

myjunk.c:
```

#include "myheader.h"

int main()
{
    myfunc(1, 2);
}

```

Now, run myjunk.c through the pre-processor. (This step is part of every compilation, but you don't normally see it, since the pre-processed output is just passed on to the next stage.)

```

$ gcc -E myjunk.c

```

and you'll get this:

```

int myfunc(int, int);

int main()
{
    myfunc(1, 2);
}

```

That's it -- that's all a header file does. It's not used by anything other than "include" directives*, so if you're not actively including something, then you don't need it.

So, when *would* you want to use a header file? In the above example, the header file contains a function prototype. This, data structures, and macros are mostly what you'll find in header files. But in principle, any code that can be in a .c file could also be in a .h file, and vice versa. The distinction is in how it's used: A header file might be included in many different modules, while a .c file should be compiled only once. So header files generally contain declarations only, and not definitions.

* There are exceptions, but they're outside the scope of C proper. Let's not go into that right now.

---

### Post by nvteighen on 2009-01-15
Strictly, header files are not needed unless you decide to use them ;)

---

### Post by jpkotta on 2009-01-15
> **wmcbrine said:**
> 
So, when *would* you want to use a header file? 
...
The distinction is in how it's used: A header file might be included in many different modules, while a .c file should be compiled only once. So header files generally contain declarations only, and not definitions.


Good explanation.  

I like to think of headers as the API.  Is there a function that could be used in several programs or several places with in a large program?  Then that function should go in some collection of similar functions, and be exposed to everything else with a prototype in a header.  Other parts of the program that use the function don't care where it is or how it works, they just know the interface from the header.  If a program is small or the functionality isn't reused, it probably isn't worth exposing things through a header.

---

### Post by eye208 on 2009-01-15
I like to think of headers as class declarations. Typically a header file is a means to implement encapsulation in C. Here's an example:

string.h
```
#ifndef __string_h__
#define __string_h__

typedef struct _string *string;

string string_create(const char* init);
string string_copy(const string other);
void string_delete(string this);
const char* string_charptr(string this);
void string_append(string this, const string other);

#endif
```

main.c
```
#include "string.h"

int main()
{
        string str1 = string_create("Hello ");
        string str2 = string_create("World!");
        string_append(str1, str2);
        printf("%s\n", string_charptr(str1));
        string_delete(str1);
        string_delete(str2);
        return 0;
}
```
Note that all the implementation details of the string class, including its data members, remain hidden in string.c. This is a way to implement basic OOP in C.

---

### Post by crazyfuturamanoob on 2009-01-15
But if some functions in the main program use each others, don't it then need a header?

If I place the function prototypes in main program then it looks messy. :lolflag:

---

### Post by wmcbrine on 2009-01-15
> **crazyfuturamanoob said:**
> But if some functions in the main program use each others, don't it then need a header?If both caller and callee are within the same module, you only need prototypes for functions that are defined after the caller. Otherwise, the definition can also serve as the declaration. So:

```

int foo(int a, int b)
{
    return a + b;
}

int bar()
{
    return foo(1, 2);
}

```

is sufficient; but if bar must come before foo, then you need a prototype of foo first:

```

int foo(int, int);

int bar()
{
    return foo(1, 2);
}

int foo(int a, int b)
{
    return a + b;
}

```

In practice, it's rare to have the kind of circular dependencies that actually make prototypes *necessary*; however, you may sometimes want to arrange functions a certain way just for clarity, or some such; or you may want to have prototypes just as documentation for the module.

> *If I place the function prototypes in main program then it looks messy.*I think superfluous files look a lot messier. But, whatever.

---

### Post by nvteighen on 2009-01-15
> **crazyfuturamanoob said:**
> But if some functions in the main program use each others, don't it then need a header?

If I place the function prototypes in main program then it looks messy. :lolflag:

That may be revealing bad design. The "main" module should be the entry point of a program, so it's what we can call the "uppermost interface". This interface may be a user-interface (usually) or something another program is going to use (though in that case a library may be more suited).

Anyway, if your main module needs to be called it means that some part of the inner implementation is depending on it. That's really bad, as it makes debugging your code much harder (think of it: resolving a circular reference is much difficult than resolving a linear one, isn't it?).

---

