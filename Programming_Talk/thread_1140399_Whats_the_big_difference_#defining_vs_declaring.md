---
title: "Whats the big difference #defining vs declaring"
date: 2009-04-27
forum: Programming Talk
---

### Post by darius2002 on 2009-04-27
Ok, I have another question ^^

I've decided to stop learning new stuff, and really solidify what I've learned about C++ in the last few weeks before I move on to arrays/pointers. And one question I have is about the preprocessor #define

To my understanding, you can write something like #define circle 360 and then on, circle is now = too 360. 
However, you can also just declair something like that, like ;
double circle = 360;

and it's doing the same job, right? I don't get why I should use one over the other :confused: and my book only tells me how to use them.

Anyone have a good layman's answer for me? :D

Thanks

---

### Post by Namtabmai on 2009-04-27
#define is what they call a preprocessor command. Basically this means that the compiler will go through your code replacing all circles with 360 **before** it even compiles your code.

double circle = 360;
on the other hand is actual code.

defines can be handy, but you lose all compiler features that come with using variable and generally you are better off using the second method.

---

### Post by lisati on 2009-04-27
ALthough you can sometimes do things with both and achieve similar results, #define'ing something and declaring something have different uses. 

Declaring a variable (e.g. float circle=2.0) sets aside a memory location that can be used in your program. 

#define is more like a shorthand that is used more to help program readability or to give the compiler special instructions (e.g. in conjunction with #if and #endif): it is more for the benefit of the programmer and the compiler than the actual finished result.

I'm sure someone else will be able to jump in and give a more concise and more accurate definition of the difference.

EDIT: I like namtabmai's explanation.

---

### Post by Simian Man on 2009-04-27
Namtabmai is correct.  A #define is basically a find/replace of the left hand side with the right hand side.  Back in the days when compilers were not very smart, there were cases when a #define would be more efficient than a regular variable.  Those days are gone, however, so you should really avoid using macros.

One not, however, is that the code without a macro would really be
```
**const** double circle = 360;
```

Always use const for values that won't change; it helps prevent mistakes.

---

### Post by Namtabmai on 2009-04-27
> **Simian Man said:**
> One not, however, is that the code without a macro would really be
```
**const** double circle = 360;
```

Always use const for values that won't change; it helps prevent mistakes.

Ah const correctness, a very important topic for C and C++ programmers, many of which discover far to late on when learning.

---

### Post by darius2002 on 2009-04-27
Awsome, that cleared it up nicely for me :D 
Thanks again guys! And Namtabmai for the second time giving me great input ;)

---

### Post by ZuLuuuuuu on 2009-04-27
Preprocessor directives are for **pre**compiling stage. This means they only effect your source code not the program itself (at least directly). In other words, **the preprocessor is just a text processor** which applies some stuff to your source code files.

When you write:

#define circle 360

this will change all the appearances of the word "circle" in your source with the word "360". On the other hand, when you write:

double circle = 360;

the compiler will allocate necessary memory and put the number 360 in it also it will handle the variable throughout the program. In this case the preprocessor directive might be more effective because in the second case your program wastes time on allocating memory and handling the variable all over the program.

Of course, the above statements are pretty much wrong for this example, or exaggerated. Because most compilers today have a lot of optimizations which eliminates the overhead of declaring such small variables. Also defining a small variable will not effect the speed of most of your programs at all if they are not dealing with algorithms which acts on thousands of values. But this does not mean preprocessor directives are useless. Actually there are some other usages then just defining a word replacement (like macros or conditional compiling) and they are used a lot in actual programming. You can see different usages by exploring some source code of other software.

---

### Post by Simian Man on 2009-04-27
> **Namtabmai said:**
> Ah const correctness, a very important topic for C and C++ programmers, many of which discover far to late on when learning.

Agreed!  When I teach C++, I take off points when students neglect to make something const that could be :).

---

### Post by darius2002 on 2009-04-27
I'll be sure to do just that. I have already out of curiosity started grabbing up source code from other peoples programs, to see if I can recognize elements in their construction, kind of to test or verify my own ability, and see the different ways people write there code. 

Actually I was quite surprised, as I learned very early, there are many many ways to write the same program in a single language, I'm really starting to see how important sticking to a standard writing style, or trying to keep your code clean and clear will be crucial.

---

### Post by lisati on 2009-04-27
Another $0.02: the smart use of things like '#define' and 'const' can simplify program maintenance if the program specs change (e.g. the need for different array size, or different versions of a routine for different data types). The idea is to define/declare the thing that might change in one place that you can find quickly - when the time comes to change your program, you only need to change one or two lines instead of what could be hundreds of lines.

---

### Post by Namtabmai on 2009-04-27
> **Simian Man said:**
> Agreed!  When I teach C++, I take off points when students neglect to make something const that could be :).

Please tell me you once failed a student for using Hungarian notation.

darius2002, it's probably a little early in learning the language but once you feel more comfortable with it I recommend picking up this book for topics like this.

[http://www.amazon.com/Effective-Specific-Addison-Wesley-Professional-Computing/dp/0321334876/ref=sr_1_2?ie=UTF8&s=books&qid=1240868968&sr=8-2](http://www.amazon.com/Effective-Specific-Addison-Wesley-Professional-Computing/dp/0321334876/ref=sr_1_2?ie=UTF8&s=books&qid=1240868968&sr=8-2)

It won't teach you C++ but it will explain a lot of good practises.

---

### Post by slavik on 2009-04-27
as pointed out:

directives beginning with # (except for #pragma I believe) are processed before the compiler gets to the code.

make something const that could be? everything could be a const ... but should it? could and should: big difference.

---

