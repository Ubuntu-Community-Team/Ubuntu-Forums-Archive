---
title: "Change default C in GCC?"
date: 2015-09-21
forum: Programming Talk
---

### Post by jonathan90 on 2015-09-21
Hi, I've been using gcc and g++ to compile my C/C++ programs, but the default C version is something like c89, and in order to use c99 I have to type "c99 -o file file.c". How do I set it so gcc uses c99 as the default? Also, should I use the c99 command or the gcc command to compile? Thanks!

---

### Post by mystics on 2015-09-21
It would be something like this:

```
gcc -std=c99 hello_world.c -o hello_world
```

Basically, both gcc and g++ use

```
-std=<standard>
```

to set the standard.

Edit: And just for clarity, if you're using C++, then you have to add the ++ to it. So if you had hello_world.cpp, then it would be:

```
g++ -std=c++11 hello_world.cpp -o hello_world
```

---

### Post by jonathan90 on 2015-09-21
Okay, I've set an alias to use gcc for C99 and g++ for C++11 on my computer. I was also wondering, should I put the output from g++ into outputfile.exe or just outputfile like you did in your code?

---

### Post by mystics on 2015-09-21
Given the .exe, I'm guessing you're doing this on Windows? Sorry, but I'm not that familiar with naming conventions on Windows. I don't believe the .exe extension is necessary, but it might be common naming convention on Windows. 

If you're doing this on Mac or Linux, don't bother with the .exe. That's used to signify Windows executables.

---

### Post by jonathan90 on 2015-09-22
I'm on Ubuntu but I just found the .exe naming thing from some Google searches. When I did my C compiling, I left it without the .exe extension and figured it should be the same for C++. And so if I compile a C and a C++ with the same in the same folder, will it conflict? Also, which is the latest, stable version of C and C++ working for GCC/G++? Sorry for asking so many questions! Thanks!

---

### Post by mystics on 2015-09-24
> **jonathan90 said:**
> I'm on Ubuntu but I just found the .exe naming thing from some Google searches. When I did my C compiling, I left it without the .exe extension and figured it should be the same for C++.

OK then, the EXE file extension shouldn't be used. The whole .exe thing is an entirely Windows thing.

And for future reference, be careful when reading online tutorials, as many of them are written for Windows. Early on, it won't mean much (so don't completely disregard tutorials written more for Windows), but once you start getting deeper into C and C++, it will make a huge difference.

> And so if I compile a C and a C++ with the same in the same folder, will it conflict?

You can compile C and C++ code that is in the same folder. However, be sure to keep the compilation of C files separate from C++ files, and use gcc and g++ for them respectively. 

> Also, which is the latest, stable version of C and C++ working for GCC/G++? Sorry for asking so many questions! Thanks!

I think they're on version 5.2 right now. If you want to check your own version against that, use:

```
gcc --version
```

I'm not sure how necessary it would be to have the most up-to-date version, though. I'm personally running 4.8.4 and haven't been running into problems.

---

### Post by jonathan90 on 2015-09-24
Alright, I'll be sure to look into that. And I made a typo: I meant to ask will there be a file conflict if I compile a C program and C++ program under the same name.  Also, I meant to ask what's the latest stable version of C/C++ I can use with GCC/G++, since C++14 came out but I'm using C++11.

---

### Post by Alain_Menard on 2015-09-24
> **mystics said:**
> OK then, the EXE file extension shouldn't be used. The whole .exe thing is an entirely Windows thing.

And for future reference, be careful when reading online tutorials, as many of them are written for Windows. Early on, it won't mean much (so don't completely disregard tutorials written more for Windows), but once you start getting deeper into C and C++, it will make a huge difference.



You can compile C and C++ code that is in the same folder. However, be sure to keep the compilation of C files separate from C++ files, and use gcc and g++ for them respectively. 



I think they're on version 5.2 right now. If you want to check your own version against that, use:

```
gcc --version
```

I'm not sure how necessary it would be to have the most up-to-date version, though. I'm personally running 4.8.4 and haven't been running into problems.

Since 4.8.4 also implement all of the C11 feature beside "[COLOR=#000000][FONT=Times New Roman]Minimal support for garbage collection and reachability-based leak detection" you'll be ok using it for a while still.

[/FONT][/COLOR]

---

### Post by Alain_Menard on 2015-09-24
> **jonathan90 said:**
> Alright, I'll be sure to look into that. And I made a typo: I meant to ask will there be a file conflict if I compile a C program and C++ program under the same name.  Also, I meant to ask what's the latest stable version of C/C++ I can use with GCC/G++, since C++14 came out but I'm using C++11.

C14 support is still experimental for the most part. Not enough time to implement and test all of it yet.

---

### Post by mystics on 2015-09-24
> **jonathan90 said:**
> I meant to ask will there be a file conflict if I compile a C program and C++ program under the same name.

Do you mean compile them separately but just give them the same executable name? Yes, you can do that. The currently existing executable will just be replaced with the newly created one. As a result, you'll have to recompile if you want the executable to behave like it previously did. 

Or are you asking about being able to compile both C and C++ code into a single executable so that the executable is derived from both languages? I'm not 100% sure that that is possible. I know you can't compile the two together in a single gcc statement. However, it might be possible (or at least I've read that it's possible) to compile the C source code and C++ source code into separate object files and then create a single executable by using g++ to compile from the object files. But I'm not entirely sure that writing source code for part of a program in C and another part in C++ would ever be the best way of going about things.

---

### Post by jonathan90 on 2015-10-02
Okay, thanks! One more thing, so C11 is supported in gcc 4.8.4 right?

---

### Post by mystics on 2015-10-02
Yes, it is. That's actually what I always use.

---

