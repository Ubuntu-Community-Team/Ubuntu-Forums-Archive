---
title: "C++ (gnu) Reference to Pointer"
date: 2013-02-21
forum: Programming Talk
---

### Post by Dirich on 2013-02-21
I would like to pass a pointer by reference to a function.
The reason is that in the function I may need to resize a dynamic array, which recquries me to actually create a different one, so if I do not have the pointer passed by reference I am going to lose the newly allocated dynamical array:

```

void func (int & * pointer,)
{
       bool array_needs_resize;
/* code that does stuff */

     if (array_needs_resize)
     {
         delete[] pointer;
         pointer = new int  [100];
     }

/* whatever else */
}

int main ()
{
     int * pointer;
     pointer = new int [5];
     func(pointer);
// now pointer has 100 elements, if a resize was needed
}

```I hope I gave you the idea. Looking on the internet I found references that talk about this kind of thing (reference to a pointer), I even found an entry on some microsoft official programming pages.

The problem is that my g++  shouts out an error:

error: cannot declare pointer to 'int&'

Beside the fact that "int & * " is what everybody was calling a reference to a pointer, while the compiler calls it a pointer to a reference, why does it not compile?

Is a reference to pointer something that is implemented only by some compilers? I found no note about that...


P.S.
Alternatives may be welcome: the problem I am trying to solve is that I have 4 different arrays of 4 different types, on which I do a ton of operations, thus I wrote a template function since I do the same operations on all the arrays, it's just the type that changes. This is why I pass the pointer on which I create the dynamical array.

---

### Post by spjackson on 2013-02-21
```

int & * pointer

```
is pointer to reference to int.
```

int * & pointer

```
is reference to pointer to int.

But seriously, don't do this. Use std::vector or other appropriate container.

---

### Post by Dirich on 2013-02-21
> **spjackson said:**
> ```

int & * pointer

```is pointer to reference to int.
```

int * & pointer

```is reference to pointer to int.

But seriously, don't do this. Use std::vector or other appropriate container.

Well, both those codes do not compile under gnu. I guess it's the compiler as I thought.

Thank you.

---

### Post by GeneralZod on 2013-02-21
spjackson's suggestion compiles fine, here. Is the code in the OP copy-and-pasted? If so, you have a rogue "," before the closing bracket.

---

### Post by dwhitney67 on 2013-02-21
> **Dirich said:**
> Well, both those codes do not compile under gnu.
Sure it does...
```

void func(int*& pointer)
{
}

int main()
{
    int* ptr = 0;
    func(ptr);
}

```

---

### Post by Dirich on 2013-02-21
Your code actually does compile. I also tried again my code and now it does compile... I have no idea what did I do to make it not work when I was at work...

Thanks!


P.S.
No, the code in the first post was an example... I was probably too tired to think that I could have posted the test code I was using at the moment... hard day of work is my excuse, I guess.

---

