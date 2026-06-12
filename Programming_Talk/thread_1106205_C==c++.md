---
title: "C==c++"
date: 2009-03-25
forum: Programming Talk
---

### Post by Sockerdrickan on 2009-03-25
[php]#include <iostream>

int main() {
    {
        int C (42);

        if(C==C++)
            std::cout<<"C==C++"<<std::endl;
    }

    {
        int C (42);

        if(C++==C)
            std::cout<<"C++==C"<<std::endl;
    }
}[/php]

---

### Post by simeon87 on 2009-03-25
C++ means the update happens afterwards, so it's comparing C to C and then incrementing C by one. In contrast, ++C means the increment occurs first.

---

### Post by Sockerdrickan on 2009-03-25
Yes.

---

### Post by jimi_hendrix on 2009-03-25
that code isnt even valid, is it

---

### Post by Can+~ on 2009-03-25
> **Tux0r said:**
> Yes.

Indeed.

---

### Post by Nemooo on 2009-03-25
Do the brackets inside main serve any purpose? I've never seen them used like that before.

---

### Post by kjohansen on 2009-03-25
you can declare blocks like that.  think of it like the inside of a loop or if statement in that it has its own scope.

really you can probably code all your life and never find an absolute need for them...

---

### Post by simeon87 on 2009-03-25
> **kjohansen said:**
> you can declare blocks like that.  think of it like the inside of a loop or if statement in that it has its own scope.

really you can probably code all your life and never find an absolute need for them...

They can be useful for delimiting operations in OpenGL, for example between the glBegin and glEnd instructions.

---

### Post by Can+~ on 2009-03-25
Funny thing, I never discovered about that {} generated scopes, I always thought that only function definitions created scopes. Imagine my surprise when I first declared a variable inside an switch-case. Although, it wasn't very pretty, I had to rewrite a major part of code due to that discovery.

I had built a whole system which accepted a void* and then it was casted into the proper type depending on a character, for example, [FONT="Courier New"]insert(pointer, 'c');[/FONT] (where 'c' was client). Then I started making the switch-case for it and banged my head on the keyboard moments after. Never again.

---

### Post by stroyan on 2009-03-25
That "C==C++" expression is actually undefined by the ANSI C standard.
The "==" operator does not force a sequence for the evaluation of its two operands.  The side-effect of "C++" is ambiguous because "C" is referenced again in the same expression.
See [http://www.lysator.liu.se/c/c-faq/c-4.html](http://www.lysator.liu.se/c/c-faq/c-4.html)
and [http://www.lysator.liu.se/c/rat/c3.html](http://www.lysator.liu.se/c/rat/c3.html)
for more information on the topic.

---

### Post by jimi_hendrix on 2009-03-25
> **Can+~ said:**
> Funny thing, I never discovered about that {} generated scopes

i have seen it in tutorials, but just thought the author was saying it doesnt matter if its a function or if statement or what

---

### Post by Sockerdrickan on 2009-03-25
It's local scoping I used it so that I could declare the variable C again in the same way to be more explicit.

In C++09 you can init anything with { }
[php]#include <iostream>

int main() {
    {
        int C {42};

        if(C==C++)
            std::cout<<"C==C++"<<std::endl;
    }

    {
        int C {42};

        if(C++==C)
            std::cout<<"C++==C"<<std::endl;
    }
}[/php]
[apt://gcc-snapshot](apt://gcc-snapshot)

---

### Post by tyfius on 2009-03-26
> **Nemooo said:**
> Do the brackets inside main serve any purpose? I've never seen them used like that before.This is not used much in C++ but more in C where you have to declare variables at the beginning of your function.

```
void foo() {
  int a = 0;
  a = doSomethingWithA(a);

  int b = 0;
  a = doSomethingWithB(b);
}
```When compiling strict or C89 this will result in an error. You have to declare your variables at the beginning of the function. Of course, when you have a lot of variables which are merely used somewhere at the bottom of the function this clutters the first lines of the function. The {} can create a local scope thus making your function more readable.```
void foo() {
  int a = 0;
  a = doSomethingWithA(a);

  {
    int b = 0;
    a = doSomethingWithB(b);
  }
}
```

---

