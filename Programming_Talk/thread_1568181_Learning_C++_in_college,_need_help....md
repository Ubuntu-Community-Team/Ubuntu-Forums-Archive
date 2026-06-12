---
title: "Learning C++ in college, need help..."
date: 2010-09-04
forum: Programming Talk
---

### Post by JAYCEE1 on 2010-09-04
Hi,

I'm taking my first programming class and it's one for absolute beginners. I've never programmed anything.

In the class, we use Dev-C++ for Windows. I'm trying like a mad dog to avoid going to walmart to buy a windows machine just for this one class. (Teacher knows less than nada about Linux.)

I installed Geany and I can type in my code, save, and compile. When I try to "Execute," I get the error "failed to execute terminal program."

I uploaded my sourcecode (Hello World!) to the grading website and it is 100% correct. 

I guess my problem is permissions related.

Does anyone know how to get my printf output to pop up in a little window when I hit execute?

Thanks!!!

---

### Post by schauerlich on 2010-09-04
This should help:

[http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by dwhitney67 on 2010-09-04
Don't use Geany.  Use the command line (ie. a gnome-terminal).

And don't use printf() for C++; use cout.

HelloWorld.cpp
```

#include <iostream>

int main()
{
   std::cout << "Hello World" << std::endl;
   return 0;  // superfluous, but shown for completeness.
}

```
To compile:
```

g++ -Wall HelloWorld.cpp -o hw

```
To run the program:
```

./hw

```

Once you have mastered these basic (kindergarten) steps, then you can entertain yourself with Makefiles for more involved projects.  Only after then, should you immerse yourself into an IDE that strips you of all of this knowledge and makes you walk around like a IQ-10 project.

---

### Post by JAYCEE1 on 2010-09-04
OK. That helps.

I cannot execute from the GUI, but when I go to the source code directory I can test it and run it from there. Then it runs in the terminal.

Better than nothing.

Thank you!

---

