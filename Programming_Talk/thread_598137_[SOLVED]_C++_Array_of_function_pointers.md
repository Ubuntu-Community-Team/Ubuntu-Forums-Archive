---
title: "[SOLVED] C++ Array of function pointers"
date: 2007-10-31
forum: Programming Talk
---

### Post by paukku92 on 2007-10-31
I am trying to make a class that calls GUI elements draw functions. It gets a function pointer throught an Add-function, and it should keep an dynamic array of the function pointers. I have tried to make a array of functon pointers without success. How do you make a array of function pointers with *alloc?

---

### Post by dumbsnake on 2007-10-31
To make an array of C++ function pointers:
```

#include <vector>

std::vector<void (*)(const Drawable &)> functions;

```If your function signature was "void draw(const Drawable &)"


You really shouldn't use malloc with C++.  If you don't like the standard containers use:

```

// pointer to pointer to function that returns void and takes a const Drawable &
void (**draw_functions)(const Drawable &);

// allocate 10 objects
draw_functions = new void (*)(const Drawable &)[10];

...

// delete an array (don't use strait delete although it is probably fine here)
delete[] draw_functions;

```


If you are a C programmer and don't understand that you should never use malloc... you *could* use the following:

```

#include <malloc.h>

void (**draw_functions)(const Drawable &);

// allocate 10 items
draw_functions = static_cast<void (**)(const Drawable &)>(malloc(sizeof(void (*)(const Drawable &)) * 10));

...

free(draw_functions);

```

Trust me though, the first is the best.  The C++ STL is really fast and good.  Usually faster than handcoded stuff unless you really spend some time on it and really know what you are doing.  And then it is still only a maybe.  As far as development time and readability it is way better.  Abandon malloc.

hope that helps....

---

### Post by Wybiral on 2007-10-31
As dumbsnake said, you shouldn't use malloc in C++. You shouldn't even use new/delete, you should use a vector.

If you meant C:
```

#include <stdio.h>
#include <stdlib.h>

typedef void (*function_ptr)(int);

void testa(int x)
{
    printf("a: %i\n", x);
}

void testb(int x)
{
    printf("b: %i\n", x);
}

int main(int argc, char *argv[])
{
    function_ptr *arr = (function_ptr*)malloc(sizeof(function_ptr) * 5);

    arr[0] = testa;
    arr[1] = testb;
    arr[2] = testa;
    arr[3] = testb;
    arr[4] = testa;

    for(int i = 0; i < 5; ++i) arr[i](i);

    free(arr);

    return 0;
}

```

dumbsnake: I've never seen static_cast and malloc together before... I'm scared, lol.

---

### Post by paukku92 on 2007-10-31
I'm doing the gui for a OpenGL game, and there are classes for buttons and images etc. and they have draw function ALWAYS like this: 
```
void Draw();
```
Why shouldn't i use malloc?

---

### Post by Wybiral on 2007-10-31
> **paukku92 said:**
> Why shouldn't i use malloc?

Because it's C, not C++ and it isn't safe to use with C++.

---

### Post by dumbsnake on 2007-10-31
> **Wybiral said:**
> Because it's C, not C++ and it isn't safe to use with C++.

To expand a little, you can use malloc if you want to, but there is a better way in C++.  If you use malloc though, you must free that memory with free() instead of deleting it.  It is more more complicated to use malloc anyway and has no advantages.

It would be like using qsort() from C when the STL sort() is way faster and cleaner.

---

### Post by runningwithscissors on 2007-10-31
> **paukku92 said:**
> I'm doing the gui for a OpenGL game, and there are classes for buttons and images etc. and they have draw function ALWAYS like this: 
```
void Draw();
```
Why shouldn't i use malloc?I don't use C++ much, but instead of maintaining an array of function pointers, you can simply create an abstract base class for game elements with an overridable draw(). That would be much saner and cleaner.

---

### Post by paukku92 on 2007-10-31
I have already a component class from where all the visible elements inherit from. They have the common propeties like Left, Top, Visible etc. But the can also have some component spesific propeties like a graphics container, or a font class. They also have the Draw() function which draws the component to the surface.

But it's not very handy to call every Draw-function separately, this is where this function pointer class comes in. When a component is created its registered to GRegistry class, and with a single call to the registry draws every component.

That vector thing seems quite interesting, i'll try it when I get home.

P.S. it's all made myself and its structure reminds quite a lot the VCL-library in Borland c++ Builder which I was using before.

---

### Post by paukku92 on 2007-10-31
It works! 

Thank you all for help!

---

