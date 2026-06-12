---
title: "Re-learning C++"
date: 2010-07-11
forum: Programming Talk
---

### Post by lsutiger on 2010-07-11
I am wanting to relearn C++ after not programming in that language in over 15 years.

I decided to go to this link ["Teach Yourself C++"]("http://newdata.box.sk/bx/c/htm/ch01.htm"), which I went to from the sticky in this forum.

I have build-essential installed.

I can not even compile a simple hello-world program. 
```
hello-world.cpp:6:22: error: iostream.h: No such file or directory
hello-world.cpp: In function ‘int main()’:
hello-world.cpp:9: error: ‘cout’ was not declared in this scope

```
The program is simple enough:```
#include <iostream.h>
   int main()
   {
           cout << "Hello World \n";
           return 0;
   }
```
So I looked around on google and found that I had include the namespace std and remove the h from the iostream.h include file.


Can someone elaborate on this for me? It just seems it could be a problem in the learning stage to have to figure out something so nuanced...

Thank you

---

### Post by Tony Flury on 2010-07-11
try

```

std::cout

```

You have to specific the namespace that you are using.

you can also use the "using" directive to make std the default 

```

using namespace std;

```
I think

---

### Post by MadCow108 on 2010-07-11
That book seems seriously outdated.
c++ standard headers **all** do not have a .h extension (including the standard C headers!) and everything is in the std:: namespace.

A quite good tutorial (for the basics) can be found here:
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Also the reference on same page is very good, with many working examples.

---

### Post by Yarui on 2010-07-11
The correct way to include iostream is defnitely
```
#include <iostream>
```
iostream.h might work as well, but this is the standard way of doing it.  The reason for including the line
```
using namespace std;
```
is to let the program know to look in the std library by default.  The std library contains the code for standard operations like cin and cout.  If you didn't include the using namespace std line you would have to do the following every time you wanted to use cout
```
std::cout << "Hello World!";
```
This is obviously less convenient, so we let the program know to always look in std if a library is not specified with the using namespace std line.

---

### Post by TheStroj on 2010-07-11
This should work.
Using namespace will take care of 'cout' not being recognized.

```

#include <iostream>
using namespace std;
int main()
{
    cout << "Hello world \n";

    return 0;

}
```

---

### Post by lsutiger on 2010-07-11
Thanx for all of the replies!

---

### Post by trent.josephsen on 2010-07-11
> **MadCow108 said:**
> That book seems seriously outdated.
c++ standard headers **all** do not have a .h extension (**including the standard C headers!**) and everything is in the std:: namespace.
Can you provide a source for that?  C++ introduces some new headers that are meant to replace the C headers, some of which go by the same names.  But #include <stdio> doesn't work (obviously, it should be <cstdio>).

@OP:  int main(void) is better style than int main(), unless you prototype it elsewhere.

---

### Post by Queue29 on 2010-07-11
> **trent.josephsen said:**
> Can you provide a source for that?  C++ introduces some new headers that are meant to replace the C headers, some of which go by the same names.  But #include <stdio> doesn't work (obviously, it should be <cstdio>).

@OP:  int main(void) is better style than int main(), unless you prototype it elsewhere.

All Standard C++ libraries have .h-less header files. 
[http://msdn.microsoft.com/en-us/library/a7tkse1h(VS.80).aspx](http://msdn.microsoft.com/en-us/library/a7tkse1h(VS.80).aspx)

However, to make anything useful, we usually have to refer to legacy C libraries or C++ libraries for a given OS which end in .h . At the learning level however, the rule of thumb is to avoid all header files ending .h, because there's probably a standards compliant replacement for it. Ex: <ctime> instead of <time.h>

---

### Post by dwhitney67 on 2010-07-11
> **lsutiger said:**
> 
I decided to go to this link ["Teach Yourself C++"]("http://newdata.box.sk/bx/c/htm/ch01.htm"), which I went to from the sticky in this forum.
...

Thank you

If the "bum" link is the cause of your grief, then it is clearly a case of the mods "falling asleep" at the wheel. They need to be more proactive/knowledgeable as to when to pull obsolete links (from the stickies).

---

### Post by krazyd on 2010-07-11
> **trent.josephsen said:**
> Can you provide a source for that?  C++ introduces some new headers that are meant to replace the C headers, some of which go by the same names.  But #include <stdio> doesn't work (obviously, it should be <cstdio>).

There seems to be some confusion here. The answer is: it's all about namespaces.

[http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.4](http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.4)
[http://www.parashift.com/c++-faq-lite/mixing-c-and-cpp.html](http://www.parashift.com/c++-faq-lite/mixing-c-and-cpp.html)

---

### Post by Yarui on 2010-07-12
> **dwhitney67 said:**
> If the "bum" link is the cause of your grief, then it is clearly a case of the mods "falling asleep" at the wheel. They need to be more proactive/knowledgeable as to when to pull obsolete links (from the stickies).
I don't know that it's really the mods' responsibility to be constantly watching the links in the stickies.  If any links are no good they should be reported by the users so that the mods can make the necessary changes.

That being said, the teach yourself C++ link was posted in 2007.  At that time the syntax for a hello world program was identical to the current hello world syntax, so on this example that link is no more out of date now than it was when it was originally posted.  I'm sure it still has plenty of good information in it, it just shouldn't necessarily be your sole source of information.  This is true of almost any source, though.  It's good to learn from more than one source.

---

### Post by nvteighen on 2010-07-12
IIRC, if your knowledge of C++ predates the C++98 ISO standard, then you should also take a look at the whole STL and C++ templates (well... it's kinda the same). I'm not very informed on C++'s history, but I can guess those are two topics you're very likely to never have heard about.

---

### Post by crazyfuturamanoob on 2010-07-12
> **trent.josephsen said:**
> ...
@OP:  int main(void) is better style than int main(), unless you prototype it elsewhere.

Why is that? I prefer less typing.

---

### Post by trent.josephsen on 2010-07-12
> **krazyd said:**
> There seems to be some confusion here. The answer is: it's all about namespaces.
My issue was with the wording, "c++ standard headers **all** do not have a .h extension (including the standard C headers!)" which is not, strictly speaking, true.  #include <stdio.h> is guaranteed to work, for backwards compatibility -- I'd call that a standard C header with a .h extension.  <cstdio> is not a standard C header; it's a C++ interface to the same library.  MadCow's original statement could cause a newbie to think that C headers wouldn't work with C++, because they end in .h.  This makes a difference when, say, porting code from C to C++, because the behavior of #include <cstdio> and #include <stdio.h> are indeed different (and #include <stdio> isn't likely to work at all).

---

### Post by nvteighen on 2010-07-12
> **crazyfuturamanoob said:**
> Why is that? I prefer less typing.

This has been explained several times by several different people, including myself, in these forums... ok, here it is again.

Technically both mean different things. In prototypes, **type function()** means function can take any kind and number of parameters, while **type function(void)** means it takes none. This has some interesting effects, e.g. using **()** will make the compiler never check arguments for that function.

The reason is that in function pointers, you may need a pointer that points to different functions returning the same type but not necessarily having the same argument list. That's declared as **type (*function_pointer)();**. A function pointer declared as **type (*function_pointer)(void);** will definitely not work if assigned to the address of a function of signature **type name(int, char);**.

So I guess the mechanism to interpret prototypes and function pointers is pretty much the same... of course writing **int main()** doesn't cause any harm, but it may be stated in the standard as having undefined behaivor.

---

### Post by GeneralZod on 2010-07-12
> **nvteighen said:**
> 
Technically both mean different things. In prototypes, **type function()** means function can take any kind and number of parameters, while **type function(void)** means it takes none. This has some interesting effects, e.g. using **()** will make the compiler never check arguments for that function.


Side note: this applies only to C, not C++:

> **ISO C++, Appendix C]
8.3.5

Change: In C++, a function declared with an empty parameter list takes no arguments.
In C, an empty parameter list means that the number and type of the function arguments are unknown"
Example:
     int f() said:**
> 

Edit:

[QUOTE=nvteighen;9580258]... of course writing **int main()** doesn't cause any harm, but it may be stated in the standard as having undefined behaivor.

In C++, both forms are actually acceptable:

[quote=ISO C++, Chapter 3]
3.6.1 Main function

An implementation shall not predefine the main function. This function shall not be overloaded. It shall
have a return type of type int, but otherwise its type is implementation-defined. All implementations
shall allow both of the following definitions of main:

      int main() { /* ... */ }


and
                 int main(int argc, char* argv[]) { /* ... */ }
[/quote]

---

### Post by nvteighen on 2010-07-12
> **GeneralZod said:**
> Side note: this applies only to C, not C++:


Oh, I didn't know this was changed explicitely in the C++ Standard... :)

---

### Post by GeneralZod on 2010-07-12
> **nvteighen said:**
> Oh, I didn't know this was changed explicitely in the C++ Standard... :)

It's a pretty obscure point, tucked all the way at the back in the Appendices ;)

---

### Post by ibuclaw on 2010-07-12
> **dwhitney67 said:**
> If the "bum" link is the cause of your grief, then it is clearly a case of the mods "falling asleep" at the wheel. They need to be more proactive/knowledgeable as to when to pull obsolete links (from the stickies).

Unfortunately, we can't be everywhere at once, so could you use the report button and point out which links need replacing? And what to replace them with, if any. :)

---

### Post by trent.josephsen on 2010-07-12
@GeneralZod:  I didn't know that either, thanks for the info.  Noted.

---

