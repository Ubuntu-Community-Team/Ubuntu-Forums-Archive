---
title: "g++/ cout"
date: 2011-02-17
forum: Programming Talk
---

### Post by bovisrex on 2011-02-17
I have a very basic question that I feel I should be able to answer. I'm using g++ on Ubuntu 10.10/ Gnome 2.32.0... finally formally learning c++ after years of other languages. And: I can't get 'cout' to work, or at least, it won't output anything.

This is the code I'm using:

// operating with variables

#include <iostream>
using namespace std;

int main ()
{
  // declaring variables:
  int a, b;
  int result;

  // process:
  a = 5;
  b = 2;
  a = a + 1;
  result = a - b;

  // print out the result:
  cout << result;

  // terminate the program:
  return 0;
}

Also, it results in a file with a .o extension; that file is nothing but
gobbledegook and null characters.

Please help! Pretty sure it's something silly that I'm overlooking.

---

### Post by Zugzwang on 2011-02-17
You code works quite well. It outputs "4" on my machine.

However, if you are using an IDE and run your program from there, it might be that your IDE swallows the output as you don't write a newline-character after the number. Executing your program on this computer yields:

```

me@my-computer:/tmp$ g++ test.cpp
me@my-computer:/tmp$ ./a.out 
4me@my-computer:/tmp$ 

```

Change your output line to "cout << result << endl;" to fix this.

---

### Post by schauerlich on 2011-02-17
What's the command you're using to compile? If it's producing a .o file, you probably have '-c' in there somewhere. Try it without.

```
g++ foo.cpp -o foo.out
```

will compile foo.cpp and make an executable named "foo.out".

A .o file is a special kind of object file. A normal object file is an executable - you can run it directly through a shell just by typing its name (ie, ./foo.out). However, a .o file is a sort of "incomplete" executable. It contains all of the compiled code that you wrote, but it hasn't been linked with the other code that it needs to be able to run on its own. You typically produce a .o file for a small portion of your program (ie, one physical source file), and then link them all together into one big executable, which can then be run on its own.

---

### Post by forrestcupp on 2011-02-17
Also, if you're using an IDE, it may just be opening a console and closing it so fast you're not seeing the result. I usually try to put an input at the end to allow me to see what's going on until I input something. You could put something like this right before the return.

```
int x;
cin >> x;
```

---

