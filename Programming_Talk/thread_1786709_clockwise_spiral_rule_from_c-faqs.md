---
title: "clockwise spiral rule from c-faqs"
date: 2011-06-20
forum: Programming Talk
---

### Post by jamesbon on 2011-06-20
On this link a Spiral Rule is given,
[http://c-faq.com/decl/spiral.anderson.html](http://c-faq.com/decl/spiral.anderson.html)
and an example is given in Section 3 Ultimate

```
void (*signal(int, void (*fp)(int)))(int);
```
even with the explanation given I was not able to understand what it means.Can some one help to understand as to what will above code snippet get evaluated to and how can it be used.Any example some where which has this kind of statement will be nice for me to understand.

---

### Post by schauerlich on 2011-06-20
The reason it's called "The Ultimate" is because it's much more complicated that anything you're likely to encounter (indeed, more complicated than any sane programmer would use). The author simply wanted to demonstrate his rule still worked on horribly complicated examples. It declares exactly what the article says it does:

> signal is a function passing an int and a pointer to a function passing an int returning nothing (void) returning a pointer to a function passing an int returning nothing (void)

That is, "signal" is a function that takes two arguments: The first is an integer, and the second is a function pointer named "fp". This function pointer points to a function whose return type is void, and whose only argument is an integer. "signal" then returns a function pointer of the same type.

Here's an example:

```
#include <stdio.h>

void foo(int a) {
  printf("a=%d\n", a);
}

void bar(int b) {
  printf("b=%d\n", b);
}

void (*signal(int i, void (*fp)(int)))(int) {
  printf("i=%d\n", i);

  fp(42);

  return bar;
}

int main(int argc, char **argv) {
  void (*fptr)(int) = signal(101, foo);

  fptr(6667);

  return 0;
}

```

Signal takes an integer (101) and a pointer to a function (foo), prints the integer it gets, runs the function it gets with the argument 42, and then returns a function pointer (bar). Then, in main, we store that function pointer, and run the function it refers to with the argument 6667.

---

### Post by Arndt on 2011-06-20
> **schauerlich said:**
> The reason it's called "The Ultimate" is because it's much more complicated that anything you're likely to encounter (indeed, more complicated than any sane programmer would use). The author simply wanted to demonstrate his rule still worked on horribly complicated examples.

And to see what a saner way to declare 'signal' looks like, do "man signal".

Another C library function taking a function as an argument is 'qsort'.

---

### Post by jamesbon on 2011-06-20
> **schauerlich said:**
> 
Thanks for your code I understood the explanation with respect to original question I had asked.
```

  void (*fptr)(int) = signal(101, foo);


```
Only this statement is what I am not able to understand in your code.

---

### Post by schauerlich on 2011-06-20
> **jamesbon said:**
> Thanks for your code I understood the explanation with respect to original question I had asked.
```

  void (*fptr)(int) = signal(101, foo);


```
Only this statement is what I am not able to understand in your code.

Do you know how function pointers work? They're a sort of rudimentary first-class function type. Basically, you can pass around references to functions, and then call whatever function it refers to. Since C is statically typed, any function pointer that you use must also give you information about the return type and argument type(s) of the function that the pointer refers to. In my example, "fptr" is a pointer to a function that takes an int and has a return type of void. That is also the type of foo, and the type of the second argument of signal. So, I pass in "foo" to signal, and it returns a function pointer of return type void that accepts one argument of type int. I store this function pointer in "fptr", and then call it later.

---

### Post by jamesbon on 2011-06-21
Ok if I have understood this correctly then signal is returning a pointer which is a function pointer and that is what fptr is pointing to.

---

### Post by schauerlich on 2011-06-21
> **jamesbon said:**
> Ok if I have understood this correctly then signal is returning a pointer which is a function pointer and that is what fptr is pointing to.

Yup.

---

### Post by jamesbon on 2011-06-21
Great dhwitney67s old post [here]("http://ubuntuforums.org/showthread.php?t=1610737") also helped me to understand the same.
Mentioning here so that if some one comes here can read it.
Thanks to you too schauerlich.

---

