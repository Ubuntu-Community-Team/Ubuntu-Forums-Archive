---
title: "C++ Programming"
date: 2015-03-04
forum: Programming Talk
---

### Post by Tristan_Williams on 2015-03-04
Ubuntu Studio 14.10

I want to start programming in C++. I already use C, Java, and Bash.

I absolutely hate IDEs, so please don't suggest them. I want to write code in a text editor like Gedit, and compile through command line tools.

What do I need to install?



Edit:

I installed g++, but when I go to compile any program, I get errors like "&#8216;cout&#8217; was not declared in this scope"

---

### Post by ubudog on 2015-03-04
I'd start by installing the build-essential metapackage, which will install gcc and g++ for compiling C and C++ code, respectively.

I personally recommend vim as a text editor, but that's just me.  Gedit is also available, as well as plenty of other text editors that you can try out and find one that suits your needs.

Edit: Your error "'cout' was not declared in this scope" is an error in your code, most likely not including the iostream library.

---

### Post by QIII on 2015-03-04
Moved to Programming Talk.

As a professional software developer, I couldn't do what I do and meet deadlines without an IDE.  Just sayin'.

---

### Post by flaymond on 2015-03-09
Before go any further, can you answer these simple questions?

1. How long have you been programming in C, Java or scripting Bash?

2. Do you make any useful programs or involved in any project in development (in this case - programming)

3. Which type programmer you are? Casual programmer, hobbyist programmer, professional programmer?

cout error is probably because of -

1. You don't include header library - iostream (for input/output stream)

2. You don't declare the use of the method/class in iostream - using namespace std / std::cout

If you wanna compile a simple example, here it is

```

/* hello.cpp -- This print "Hello, World!" string. */

#include <iostream> // This include input/output stream header library, if you programming in C, it's just a bit same with <stdio.h>
using namespace std; // This declare of using standard method in <iostream>, you will understand better in OO's lesson.

int main()                // Program start here
{
    cout << "Hello, World!" << endl;    // cout mean print and endl mean 'endline', endl is same with '\n' in C.
    return 0;                                     // This terminate the program and return 0 to OS
}                                                   // This end the block of int main


```

compile this with this command

```
 make hello.cpp 
```

I'm using vim as my text editor, it's very easy to use and fun.

---

### Post by ofnuts on 2015-03-09
> **QIII said:**
> Moved to Programming Talk.

As a professional software developer, I couldn't do what I do and meet deadlines without an IDE.  Just sayin'.

So do I. And IDE isn't just something that compiles the code for you. It's also something that keeps track of everything. You click a method usage and it shows you where this method comes from in your hierarchy. It can suggest valid completions because it knows what makes sense where you are. When something is badly named you can rename it and it will fix the rest of the code to match. If you work with several other people there are parts of the code you barely know,  but the IDE will know them. Pre-Y2K IDEs where an impairment to the good programmers, but they have come a long way...

---

