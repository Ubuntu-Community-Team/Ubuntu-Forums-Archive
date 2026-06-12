---
title: "what is a library?"
date: 2010-09-08
forum: Programming Talk
---

### Post by cybo on 2010-09-08
i did some coding before and kept hearing people telling me that i need use this library and that library, but i really never knew and no one (not even a professor in college) explained to me what a library is. can someone tell me what is it? where is it stored and what can i do with it?

any help is appreciated

---

### Post by stee1rat on 2010-09-08
[http://en.wikipedia.org/wiki/Library](http://en.wikipedia.org/wiki/Library) :)

---

### Post by Zugzwang on 2010-09-08
> **stee1rat said:**
> [http://en.wikipedia.org/wiki/Library](http://en.wikipedia.org/wiki/Library) :)

Not quite. It's rather: [http://en.wikipedia.org/wiki/Library_%28computing%29](http://en.wikipedia.org/wiki/Library_%28computing%29)

---

### Post by cybo on 2010-09-08
> **stee1rat said:**
> [http://en.wikipedia.org/wiki/Library](http://en.wikipedia.org/wiki/Library) :)

i don't want to be rude but i posted a question because i couldn't understand what wikipedia meant. wiki says > "library is a collection of useful material for common use." i'd like to know what is meant by it in perspective of coding? what common resources are we talking about? can anyone give examples of libraries and what is stored in them?

help is appreciated

---

### Post by schauerlich on 2010-09-08
Basically, it's a bunch of code usually centered around a certain task (text processing, file I/O, graphics, regular expressions, etc) that is self-contained and can be used in a bunch of different projects. It prevents someone coding a program from having to reinvent the wheel if their program needs to solve a problem that's been solved many times before.

---

### Post by KdotJ on 2010-09-08
Say I'm writing a program that needs to read data from a file, I need some sort of file I/O (input/output). So to save me having to create a bunch of code to implement this, I can just use code from a library that's already been created by someone else

So for example, making said program in java, I would import the I/O library...

```
import java.io.*;
```

Now after I have used this import I can use all classes, methods etc that are in the java I/O library

---

### Post by nvteighen on 2010-09-08
A library is a collection of code that's reusable. I'm sure that as soon you've got some programming experience, you may have noticed that sometimes you code the same stuff more than once in different programs. Well, what libraries do is to allow you to not recode stuff everytime you need them.

Now, usually when people talk about libraries, they refer to "third-party libraries", i.e. libraries that are written by other people that allow you to use it in your code (as opposed to libraries you code for your own personal use and don't necessarily make them public). 

The ways of using libraries vary from language to language, so I won't get into this. Also sometimes languages name libraries as "modules", "packages" or other ways, but the concept is rather the same.

---

### Post by dwhitney67 on 2010-09-08
> **stee1rat said:**
> [http://en.wikipedia.org/wiki/Library](http://en.wikipedia.org/wiki/Library) :)

Good answer!  I may use your reply myself based on some of the off-wall questions posed on this forum.

---

### Post by hakermania on 2010-09-08
Libraries is like HEADER files. They declare functions. So, including these libraries into your main program you can use the functions declared there. E.g. iostream library has a function named std::cout, and you can use this function in your main program if you include the library iostream

---

### Post by nvteighen on 2010-09-09
> **hakermania said:**
> Libraries is like HEADER files. They declare functions. So, including these libraries into your main program you can use the functions declared there. E.g. iostream library has a function named std::cout, and you can use this function in your main program if you include the library iostream

No! The header file system is a C, C++ and Objective-C specific technique. Header files are needed to tell the compiler to know the signature of a function that isn't written in your code (because it is in the library). The library is, in the case of C, C++ and Objective-C (and others, I guess), the .so or .a file the linker links with your executable.

---

### Post by Zugzwang on 2010-09-09
> **cybo said:**
> i don't want to be rude but i posted a question because i couldn't understand what wikipedia meant.

Fair enough. But then why didn't you wrote in your first post that you already looked it up? It's just that the question you asked basically asks for an answer that would be extremely similar to what is written in wikipedia anyway, so people's natural reaction is to just post the link here.

---

### Post by cybo on 2010-09-09
thanks everyone for helping. i think i get the idea now.

---

