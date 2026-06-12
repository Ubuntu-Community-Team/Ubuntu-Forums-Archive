---
title: "Whoa...headers? Implementation files..uh?"
date: 2008-05-17
forum: Programming Talk
---

### Post by UltraSonicSite on 2008-05-17
I'm currently on my C++ learning voyage with my trusty and sometimes confusing (for me) book: SAMS Teach Yourself C++ in 10 minutes(Per lesson lol), by Jesse Liberty.

It's introducing headers and er implementation files and now I'm completely lost. This is what I have, and I am using g++

hello.C
```
#include <iostream>
#include "displaywelcome.h"

using namespace std;

main()
{
	displaytxt();
	return 0;
}
```


displaywelcome.h
```
#ifndef displaywelcomeH
#define displaywelcomeH

void displaytxt(void);

#endif
```


displaywelcome.C
```
#include <iostream>
#include "displaywelcome.h"

using namespace std;

void displaytxt(void)
{
	cout << "display txt!!!!" << endl;
}
```



Console:
```
ultrasonicsite@ubuntu:~/Learn CPP$ g++ hello.C -o first
/tmp/ccZl0O8B.o: In function `main':
hello.C:(.text+0x18e): undefined reference to `displaytxt()'
collect2: ld returned 1 exit status

```

---

### Post by UltraSonicSite on 2008-05-17
Silly me, I had to do:

```
ultrasonicsite@ubuntu:~/Learn CPP$ g++ hello.C displaywelcome.h displaywelcome.C -o first

```

that is, include all the files in the console.

I still don't know what a header is for, I'll have to check into that.

---

### Post by UltraSonicSite on 2008-05-17
Wait what am I doing?! You see I'm a very visual person and I'm having a hard time visualizing how all this fits together, why in the world is the "displaywelcomeH" thing needed in the **displaywelcome.h** file?

Why do I need header files and implementation files? I had this idea that header files were a list of special commands like **iostream** that has commands such as *cout* and *cin*.

Oh great now the book is talking about namespaces! Noooooo!!!

---

### Post by LaRoza on 2008-05-17
> **UltraSonicSite said:**
> Wait what am I doing?! You see I'm a very visual person and I'm having a hard time visualizing how all this fits together, why in the world is the "displaywelcomeH" thing needed in the **displaywelcome.h** file?

Why do I need header files and implementation files? I had this idea that header files were a list of special commands like **iostream** that has commands such as *cout* and *cin*.

Oh great now the book is talking about namespaces! Noooooo!!!

You don't need to specify the header on the command line, it is included by the preprocessor.

Header files allow the compiler to allocate space and know what is going on. I don't think you are getting C++ from this book (for what is worth, that book was the exact same one I first used to learn programming, I didn't succeed with C++ with it)

I can't draw diagrams here, but K&R had the best chapter on such concepts (headers and implementation). If you want more resources for learning, see my wiki.

---

### Post by UltraSonicSite on 2008-05-17
A lot of people seem to advocate learning Python first, should I take this route before learning C++? I mean will it ease my journey =P

---

### Post by LaRoza on 2008-05-17
> **UltraSonicSite said:**
> A lot of people seem to advocate learning Python first, should I take this route before learning C++? I mean will it ease my journey =P

Yes, I would recommend it. Even though I started with C++, I didn't get it until after I learned another language.

My wiki should have all you need.

---

### Post by snova on 2008-05-17
Perhaps I can help. Since I don't know what you do and do not understand, I'll have to explain some things that may be redundant to you.

First, some terminology.

A "header" usually ends in .h, and contains declarations of functions and variables, constants, classes, and so on.

The word "source" usually refers to .cpp files, though you seem to use .C instead. (I would discourage this, because on Windows, it would be mistaken for a .c file instead- and C is a different (however related) language. But to each his own.) I say usually because in the plural, "sources" refer to both .cpp and .h files.

Source files contain the actual function code.

The point of this arrangement is to split programs into multiple sources. This becomes necessary as projects get large. For example, the Linux kernel (only a very small piece of the overall operating system) comprises *several million* lines of code. Sorting code into different files is necessary when you get this much code.

In short, headers contain "declarations", which tell the compiler that a certain function exists somewhere. Sources contain the actual code.

Let us dissect your error line by line:

```
/tmp/ccZl0O8B.o: In function `main':
```

This is the prelude. G++ is telling you the next message it gives you was found in the function called 'main'.

```
hello.C:(.text+0x18e): undefined reference to `displaytxt()'
```

Here we have the meat of the error. Essentially, this means that your main refers to something called displaytxt (the compiler doesn't know at this point in the process whether it's a variable or a function- but it does know it's needed), and it can't find it.

It can't be found because you put it in another file! Somehow you have to command the compiler to combine the two sources you have into one executable.

```
collect2: ld returned 1 exit status
```

This last bit simply informs you that the linker (ld) failed.

Now for an explanation of *why*.

I have noticed that in all of your command lines, you give the compiler sources and it outputs executables. I infer from this that you need an explanation of what object code is, and how to use it.

Object code is an intermediary between source code and programs. It's binary gibberish (have you ever opened a program in a text editor?) at this point, but it needs more binary gibberish before it can work.

The linker's job is to combine several dozen object files into a single program. When it discovers that some function is needed but not present, it complains, hence the error, and quits.

GCC is only a compiler- a converter from source to object code. It has a few extra features, though, in that it will link automatically for you if you want.

What you need is to prevent this extra step, and make GCC stop after it finishes compiling. To achieve this, simply append the string '-c' to your command line. It's output will be object code.

So you must compile each source separately, producing an object file (BTW, these usually end in .o) for each. Then link them all together into your program, using the same command as you started with- but with object files as arguments instead of sources. It will autodetect what they are, and take the appropriate action. In this case, it is what we want, linking.

To wrap it up:
```
g++ -c hello.C -o hello.o
g++ -c displaywelcome.C -o displaywelcome.o
g++ hello.o displaywelcome.o -o myprogram
```

I hope this helped.

PS. Python is a beautiful language. Maybe you *should* try it. The Python documentation includes a tutorial I suggest you read.

---

### Post by UltraSonicSite on 2008-05-17
Tell you what, I'll bookmark your wiki and go from there. Hey thanks!

Thanks snova!

---

### Post by jpkotta on 2008-05-18
> **UltraSonicSite said:**
>  why in the world is the "displaywelcomeH" thing needed in the **displaywelcome.h** file?


That makes the header file *idempotent*, which means that including it more than once is the same as including it only once.  The compiler doesn't like it if something (like a function) is declared more than once, so you should always use that trick if you are programming C/C++.  I don't think python is as strict.

[http://en.wikipedia.org/wiki/Idempotent](http://en.wikipedia.org/wiki/Idempotent)
[http://c-faq.com/cpp/nestincl.html](http://c-faq.com/cpp/nestincl.html)

---

