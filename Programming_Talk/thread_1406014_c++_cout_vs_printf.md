---
title: "c++ cout vs printf"
date: 2010-02-13
forum: Programming Talk
---

### Post by zwaldowski on 2010-02-13
I've been learning c++ for a while now, and i've been using the cout function to display text on screen, but I often come across programs using printf for the same purpose. Is there any difference, besides the syntax?

---

### Post by Enrui on 2010-02-13
It seems to me that cout and printf are two different things almost entirely. 

cout is very inflexible, but easy and can't be formatted. 

printf is very flexible, yet a little harder and somewhat strict, but it can be formatted. 

[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)
[http://www.cplusplus.com/reference/iostream/cout/](http://www.cplusplus.com/reference/iostream/cout/)

of course they're also part of different library's.

edit

There's a lot more to it than that upon reading through the links. I'll be sticking to cout (as a beginner)

---

### Post by MadCow108 on 2010-02-13
printf is C
cout is C++

the both serve the same purpose, just cout (or generally C+ streams) as a C++ object is typesafe and more flexible.
What enrui says is completly wrong. cout is the more flexible one and it can easily be formated (see iomanip)
printf is limited to what it can do in C. Whereas cout can handle all the power of C++, most important overloading of stream operators (<< >>) and you can redirect the stream to where ever you like (as long as its derived from ostream).

In general stick with C++ streams in C++ programs.

What is used when the power of streams is not needed (e.g. debugging) is mainly preference of programmer (and strongly influenced if the programmer started with C or C++)
Some thing are also just quicker with printf. Like formating of output.
e.g. setting precision with printf:
"%.5f", d
with cout:
cout << setprecision(5) << d
more verbose but the advantage is the code is easier to read
other things are quicker with streams:
class { loads of members, but with overloaded << operator} object;
cout << object;

---

### Post by tbastian on 2010-02-13
I think that people who use printf tend to be C programmers who are used to programming in C and take advantage of C++'s backwards compatibility with C. One other possible reason is that output formatting is a little simpler with printf.

---

### Post by Lux Perpetua on 2010-02-14
> **zwaldowski said:**
> I've been learning c++ for a while now, and i've been using the cout function to display text on screen, but I often come across programs using printf for the same purpose. Is there any difference, besides the syntax?The only reason C++ has printf is for compatibility with C. C++ iostreams should be thought of as replacing the C stdio library. 

In theory, printf is more flexible than cout in that it lets you specify an arbitrary format string. However, I can't think of any non-contrived use of printf that can't be ported straightforwardly to iostream/iomanip. (If such exists, I'd like to see it.) 

As a rule, in C++, you should always use iostreams unless you have a good reason to fall back to the C library (like performance).

---

### Post by nvteighen on 2010-02-14
> **Lux Perpetua said:**
> 
As a rule, in C++, you should always use iostreams unless you have a good reason to fall back to the C library (like performance).

As a rule, use the native features of a language no matter how backwards compatible it is with another one.

Otherwise, you'll be mixing "meaning layers"... The way C expresses code is totally different to the way real C++ (not that "C compiled with a C++ compiler" thing) does it. There's a reason why they are called different languages... The same reason why people look at you awkwardly if you happen to use English vocabulary with German syntax is valid here to not mix C and C++ just because the C++ compiler allows you.

---

### Post by Vox754 on 2010-02-14
> **nvteighen said:**
> As a rule, use the native features of a language no matter how backwards compatible it is with another one.

Otherwise, you'll be mixing "meaning layers"... The way C expresses code is totally different to the way real C++ ... does it. ...

In summary:
[LIST]
[*]**printf()** is a **C** function
[*]**std::cout** is a **C++** function (actually a **stream object**)
[*]C and C++ are different languages (believe it or not!)
[*]C++ is to some extent backwards compatible with C, so it allows **printf()** and other standard functions
[*]Mixing C functions with C++ code is not recommended
[/LIST]

Also, consult the reference.
For the C Standard Input-Output Library, including **printf()**
[http://www.cplusplus.com/reference/clibrary/cstdio/](http://www.cplusplus.com/reference/clibrary/cstdio/)
```

sudo apt-get install manpages-dev
man 3 printf

```

For C++ streams, including **std:cout**
[http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

---

### Post by dribeas on 2010-02-14
Besides what has already been said about ostreams and printf, there are other small things to consider. Printf is limited in different ways, it cannot process user defined types, but only primitive types (try to pass a std::string instead of a const char* and you will get a nice crash). The compiler will not be able to check that the number or type of arguments is right.

---

### Post by MadCow108 on 2010-02-14
the latter is provided by gcc as extension.
activate it with -Wformat

---

### Post by TheBuzzSaw on 2010-02-14
The benefits of C++ and iostream become very apparent once you start using the stringstream object (or any other bidirectional stream object).

---

### Post by nrs on 2010-02-14
I use printf a lot in my C++ programs, at least my private ones. I'm not going to pretend this is good practice, but printf is just easier to work with when writing .. informative .. debug messages. cout is obviously a lot safer.

printf("X1: %d X2: %d X3: %d X4: %d Whatever: %s", x1, x2, x3, x4, whatever); 
vs
cout << "X1: " << x1 << " X2: " << x2 << " X3: " << x3 << " X4: " << x4 <<  " Whatever: " << whatever

---

