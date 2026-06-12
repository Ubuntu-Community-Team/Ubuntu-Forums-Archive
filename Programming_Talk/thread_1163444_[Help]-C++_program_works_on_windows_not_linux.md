---
title: "[Help]-C++ program works on windows not linux"
date: 2009-05-18
forum: Programming Talk
---

### Post by xnerdx on 2009-05-18
I have been progressively working with C and C++ over the last year or so and I have happily begun to become a better programmer, despite my relevant novice ability as of now. I got bored while in a waiting room and decided to throw together a calculator type program in C++ (Which is what I have started studying recently). I wrote out a little program for adding, subtracting, dividing, and multiplying 2 or 3 numbers using an abundance of switch cases and i/o commands in C++. I used CPP, GPP, GCC to compile this program and each come up with their own fancy way of not wanting to run the program :). I copied the file over to my winbox and compiled it in VC09 (Visual Studios 2008 Professional), and it had no problem compiling and the code runs fine.

I don't want to sound like a novice in linux because I have been using it for a couple of years now and understand completely the differences between Windows and Linux. But I am asking if someone could look at this code and tell me why Linux won't compile the script where as Windows will, I understand there are two different compilers but I am just wondering if anyone can explain why? The file is attached to this post, please do not flame me because I know I don't know much of anything about programming compared to most. Thank you! I look forward to the replies!

---

### Post by dwhitney67 on 2009-05-18
Your code compiles/links/runs fine using the following statements:
```

g++ -Wall -pedantic -ansi calc.cpp
./a.out

```
I was able to run the app, but the user-interface needs serious work;  it's very amateurish, and does not handle erroneous user input very gracefully.  I only tested the 'addition' to two numbers.

---

### Post by xnerdx on 2009-05-18
Of course I am aware that the code is very simple and novice-like. I am still in the middle of learning, I just didn't know why it wouldn't compile on linux correctly the way I was running it which was: 
```

gcc (directory and source file) -o (directory of source file, file named calc)

```

As well I ran it with gpp and cpp with the same aug's but okay I thank you for helping me!

---

### Post by dwhitney67 on 2009-05-18
> **xnerdx said:**
>  
```

gcc (directory and source file) -o (directory of source file, file named calc)

```


'gcc' will compile, but not link, C++ applications unless you specify -lstdc++ (the standard C++ library).  Of course, it is easier to use/type 'g++', and hence that's what 99.44% of developers use for building their C++ apps.  ;)

---

### Post by xnerdx on 2009-05-18
Haha I did forget about g++. I just feel it is a little out of control to have cpp, c++, gcc, gpp, g++ it is can be difficult to determine which one is the best, why, etc.

---

