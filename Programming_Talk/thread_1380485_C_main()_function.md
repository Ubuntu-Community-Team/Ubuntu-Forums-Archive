---
title: "C main() function"
date: 2010-01-13
forum: Programming Talk
---

### Post by nmccrina on 2010-01-13
Hi all,

In another thread, nvteighen said the main() function should **always** be

```
int main(void)
```
or
```
int main(int argc, char *argv[])
```,
never
```
int main()
```

What is the reasoning behind this? Is it really such a big deal? I've always used int main() with no problems, since I started with C++ and the habit just sort of continued.

---

### Post by lisati on 2010-01-13
Your first example lets your program return an "exit value" (MS-DOS/Windows: "Errorlevel"), but doesn't use the command-line arguments. Your second example adds in the use of the command-line arguments. 

"int main()" is a little bit "out there", neither saying that you're using command-line arguments, nor saying that you're *not* using them. The first two examples are "more standard".

---

### Post by nmccrina on 2010-01-13
Ah. From now on I will try to remember to put the 'void' in there, I would hate to confuse my computer! :D

Thanks!

---

### Post by MadCow108 on 2010-01-13
the reason main() is worse than main(void) has to do with portability
some compilers need(ed?) the void if a function (and not only main) had no arguments
I think it had to to with K&R C but I can't remember the exact reasoning anymore

there's even a special warning for that in gcc: -Wold-style-definition

---

### Post by SunSpyda on 2010-01-13
In the most popular variant of C, C89, 'int main()' is completely allowed, and is the most used. This also applies to K&R C and C++. In fact, in C89 and K&R C, you can even leave out the 'int' part, as it is implied.

But this is where it changes... 'int main()' in C99 shouldn't be used, instead it should be 'int main(void)'. I think Obj-C is using C99 (It was last time I compiled some Obj-C files), since it is a strict-subset, thus that requires 'int main(void)' as well.

If you wish to be complacent with the latest C standard, use 'int main(void)'. If you wish it to be a subset of C++, the 'void' part is redundant.

---

### Post by saulgoode on 2010-01-13
It is helpful to recognize the distinction between declaring a function with "foo(void)" versus with "foo()". The former explicitly forbids any arguments from being passed to the function; the latter merely indicates that nothing is known about the arguments. A call with arguments would not necessarily fail, and is typically permitted by the compiler (though warnings may be generated).

'main' is unique in the C language in that it can have either no or two arguments and still be compliant with the standard (ANSI). Some compilers allow more than two arguments (MS C has three, and others permit variable-length lists of arguments), but these are non-compliant. Leaving out 'void' is not equivalent to having either zero or two arguments, so it is likewise non-compliant.

If your program is intended to be maximally portable, it should comply with the ANSI standard. This means using 'void' when no arguments are expected.

---

### Post by Joeb454 on 2010-01-13
Whenever I write any C applications now, I tend to use ```
int main(int argc, char *argv[])
```

Just in case I want to take any command line arguments :)

---

### Post by era86 on 2010-01-14
Now I know in C, the arguments to a function are stored on the stack right after the function call, correct?  So by declaring argc and argv, you are making space on the stack for them.

Now I know void == nothing, but is there a difference in the way the stack is managed with using void versus not using it?

Kinda out there, but curious if anyone knows off the top of their head :)

---

### Post by Habbit on 2010-01-14
> **era86 said:**
> Now I know void == nothing, but is there a difference in the way the stack is managed with using void versus not using it?

In old C, functions were not always prototyped. Declaring a function as "T f();" tells the compiler that any arguments are acceptable (including no arguments at all). Acceptable calls would be f(), f(5), f("a", &var), etc. On the other hand, declaring it  as "T f(void);" specifies that it takes no arguments, so any call other than f() is a compiler error. C99 (and common sense) advises to always declare a function that takes no arguments as "T f(void);"

In C++, both declarations mean exactly the same, since the name manling required by its function overload feature makes it necessary for the compiler to know the full prototype of any function before calling it.

WRT to your stack question, in the usual C/C++ calling convention, the caller is tasked with cleaning up the passed arguments from its stack after a function call returns. Thus, even if you declare a function with "T f();" and call it like f(5), that 5 will rest in the stack, unused by the function, and be removed by the caller when f returns. So no damage done, other than possible optimization opportinities lost by the compiler.

---

### Post by rabidbadger on 2010-01-14
Although your original Q has been answered, you might find [this link to the *comp.lang.c* FAQ]("http://www.c-faq.com/index.html") useful for future reference (see answer *11.12a* -- and links -- for discussion about your original question).

---

### Post by nmccrina on 2010-01-14
> **rabidbadger said:**
> Although your original Q has been answered, you might find [this link to the *comp.lang.c* FAQ]("http://www.c-faq.com/index.html") useful for future reference (see answer *11.12a* -- and links -- for discussion about your original question).

Thanks, that was helpful!

---

### Post by nvteighen on 2010-01-14
And here's nvteighen :P

The thing is that in C, () in a function declaration means "indefinite number of arguments". That notation is used when you want a pointer-to-function allowed to point to functions with any kind of argument list. So, writing "int main()" means to tell the compiler that main will accept an indefinite amount of arguments.

Of course, writing "int main()" is much less harmful than writing "int foo()": it has no visible effect because you won't call main in your code  But in the case of a function you are calling, telling the compiler that function hasn't a definite argument list will make the compiler not be able to tell you if you're calling it right or wrong... because it actually won't be wrong as the argument list was left indefinite!

---

### Post by era86 on 2010-01-16
> **Habbit said:**
> In old C, functions were not always prototyped. Declaring a function as "T f();" tells the compiler that any arguments are acceptable (including no arguments at all). Acceptable calls would be f(), f(5), f("a", &var), etc. On the other hand, declaring it  as "T f(void);" specifies that it takes no arguments, so any call other than f() is a compiler error. C99 (and common sense) advises to always declare a function that takes no arguments as "T f(void);"

In C++, both declarations mean exactly the same, since the name manling required by its function overload feature makes it necessary for the compiler to know the full prototype of any function before calling it.

WRT to your stack question, in the usual C/C++ calling convention, the caller is tasked with cleaning up the passed arguments from its stack after a function call returns. Thus, even if you declare a function with "T f();" and call it like f(5), that 5 will rest in the stack, unused by the function, and be removed by the caller when f returns. So no damage done, other than possible optimization opportinities lost by the compiler.



This is what I had in mind... thank you!

---

