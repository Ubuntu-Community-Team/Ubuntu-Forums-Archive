---
title: "Day 1 of C++ proves too much for me"
date: 2007-02-23
forum: Programming Talk
---

### Post by barney_1 on 2007-02-23
So I decided I wanted to learn some C++.  I've had experience with other languages so I figured, no problem.  I'm using the "Teach yourself C++" from the second post of this thread:
[http://www.ubuntuforums.org/showthread.php?t=333867](http://www.ubuntuforums.org/showthread.php?t=333867)

Unfortunately, I'm getting a compile error with the code in one of the exercises from the first day.  How embarassing!  Can anyone point out my problem:

```
#include <iostream.h>
int main()
{
  int x = 5;
  int y = 7;
  cout "\n";
  cout << x + y << " " << x * y;
  cout "\n";
	return 0;
}

```
Compiling output:
```
mike@krusty:~/C++$ g++ exercise1.cpp
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from exercise1.cpp:1:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
exercise1.cpp: In function ‘int main()’:
exercise1.cpp:6: error: expected `;' before string constant
exercise1.cpp:8: error: expected `;' before string constant

```

---

### Post by WiseElben on 2007-02-23
The lines **cout "\n";** should be **cout << "\n";** or **cout << endl;**. "<<" is the operator that "feeds" into the cout (which means "console out," if you were wondering), and "endl" represents "end line", which does the same thing as "\n".

---

### Post by barney_1 on 2007-02-23
Thanks for the quick reply.  That makes perfect sense to me now.

---

### Post by lnostdal on 2007-02-23
if that book uses #include <iostream.h> you need to stay away from it as it is too old to teach you C++ as it is now (after 1998 )

try instead [http://mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html)

the correct name of the header to include is iostream .. so you should do

```
#include <iostream>
```

---

### Post by Engnome on 2007-02-23
> **lnostdal said:**
> if that book uses #include <iostream.h> you need to stay away from it as it is too old to teach you C++ as it is now (after 1998 )

try instead [http://mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html)

the correct name of the header to include is iostream .. so you should do

```
#include <iostream>
```

Hmm that's the book I read and I like it. I think I read somewhere that it used iostream.h for people using older compilers and that you could just replace it with iostream to be ansi compliant.

It says [_here_]("http://newdata.box.sk/bx/c/htm/ch01.htm#Heading10") that:

> For most students of C++, the ANSI standard will be invisible. The standard has been stable for a while, and all the major manufacturers support the ANSI standard. We have endeavored to ensure that all the code in this edition of this book is ANSI compliant.

---

### Post by Wybiral on 2007-02-23
You also need to...

```

using namespace std;

```

After "#include <iostream>"

Because it is in the "std" namespace, otherwise you will have to use "std::cout" and "std::endl" instead of the normal "cout" and "endl"

---

### Post by barney_1 on 2007-02-23
Thanks for all of that.  I've got it going now.  I'd like to continue on with the "Teach yourself C++ in 21 day" because it seems well written.  I took a look at the book that Inostdal suggested and it's written more like a text-book than a self learning book.  I'm doing a bit of a primer at this site right now:

[http://www.cprogramming.com/tutorial.html#c++tutorial](http://www.cprogramming.com/tutorial.html#c++tutorial)

---

### Post by jmillikin on 2007-02-23
Depending on how old the book is, you won't get much out of it. Modern C++ makes heavy use of the Standard Template Library - vectors, strings, iostreams, etc. If the book you're using covers those topics poorly or not at all, consider a different book.

---

### Post by Wybiral on 2007-02-23
I learned C++ from the internet... Example code/tutorials. After I had a rough idea, I purchased a couple of books and learned about its real power.

For C++ you need to learn two things.

First. The language itself. How it works, how to use it...

Second. The STL. The standard libraries that come with C++. Unfortunately it seems like most people learn basic C++ and maybe iostream but stop there... The STL is VERY VERY important if you really want to have a good understanding of C++.

It will save you tons of work (because a lot of the things that you think you need to write yourself end up being part of the STL to begin with... safe dynamic containers, various standard algorithms like sort/swap, stream manipulators... all kinds of cool stuff)

So, my personal advice (while it is simply my opinion) don't just learn the language... Do yourself a huge favor and learn as much of the standard library as possible. It will pay off a lot!

---

### Post by barney_1 on 2007-02-24
Thanks for the great advice.  I take it to heart that I need to learn as much about the Standard Library as I can.  

I picked up a book from the public library today, I think it's just what I needed.  It is called "Teach Yourself C++ (3rd edition)" by Herbert Schildt.  Right on the cover it says "Covers the Standard Template Library (STL)".  I've gone through the first chapter and I'm very happy with it thus far.

---

### Post by Enselic on 2007-02-24
> **Wybiral said:**
> You also need to...

```

using namespace std;

```

After "#include <iostream>"

Because it is in the "std" namespace, otherwise you will have to use "std::cout" and "std::endl" instead of the normal "cout" and "endl"

It is generally adviced **not** to open up the whole std; namespace (especially, but not limited, opening std in header files).

Please refer to: [http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5]("http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5")

For temporary programs it doesn't matter, but one can just as well adopt good habits right away, and use std::cout << "sausage" << std::endl;

---

