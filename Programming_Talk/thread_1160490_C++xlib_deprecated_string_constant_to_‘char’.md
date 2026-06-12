---
title: "C++/xlib deprecated string constant to ‘char*’"
date: 2009-05-15
forum: Programming Talk
---

### Post by kahootbot on 2009-05-15
I was compiling this example xlib program

[http://www.paulgriffiths.net/program/c/srcs/helloxsrc.html](http://www.paulgriffiths.net/program/c/srcs/helloxsrc.html)

I realize that's a .c file. I also realise there are signifigent differences between C/C++ compiling that are incompatible. However, I would like to use xlib with C++ and I can't see any reason this cannot be accomplished.


I pass the compiler the following string
g++ helloX.cpp -o prog -L/usr/X11/lib -lX11

> 
original.c: In function ‘int main(int, char**)’:
original.c:40: warning: deprecated conversion from string constant to ‘char*’
original.c:41: warning: deprecated conversion from string constant to ‘char*’
original.c:125: warning: deprecated conversion from string constant to ‘char*’
original.c:161: warning: deprecated conversion from string constant to ‘char*’

The only thing that I have done to the link above is taken out the very first and very last lines after ctrl-a and copy/pasting in a file, since there are no // or /* to make those lines comments. I mention this so you know the corresponding line numbers in these compiler errors

Now, the wierd thing some of the Xlib functions themselves take char* as perimeters. 

One example is XStringListToTextProperty. I tried creating a character buffer the size of my text string to allow it to be dynamically changed, only to no avail because it results in type casting char* to char. 

Since the perimeter char* is built in xlib function(s) any idea how to make them C++ compatible without any deprecated usage?

Thanks. :)

---

### Post by dwhitney67 on 2009-05-15
The gcc compiler is stricter nowadays; the string declarations should be something like:
```

const char* window_name = "Hello, X Window System!";

```
Concerning your post, what's this?

```

g++ helloX.cpp -o prog -L/usr/X11/lib -lX11

original.c: In function ‘int main(int, char**)’:
original.c:40: warning: deprecated conversion from string constant to ‘char*’

```
You are compiling helloX.cpp, yet the warnings are originating from original.c.  Please get your compiler warnings/errors straight.

---

### Post by kahootbot on 2009-05-15
Seems I posted wrong from a terminal I had open at the same time which I had the file renamed, my apologies. The same errors apply, just different line numbers per my instructions of removing the to comments at the begining and end of the file linked to in post one..
> 
helloX.cpp: In function ‘int main(int, char**)’:
helloX.cpp:41: warning: deprecated conversion from string constant to ‘char*’
helloX.cpp:42: warning: deprecated conversion from string constant to ‘char*’
helloX.cpp:126: warning: deprecated conversion from string constant to ‘char*’
helloX.cpp:162: warning: deprecated conversion from string constant to ‘char*’


regarding what you said
> 
const char* window_name = "Hello, X Window System!";

Concerning your post, what's this?

I tried the same thing, unfortunately XStringListToTextProperty takes a char* perimeter. 

after some research, I think const_cast <char**>( &window_name) is the only way to handle it in C++. It's almost a bit risky, because const_cast doesn't make a const type writeable, but the man page doesn't show any dynamic memory changes to the string in XStringListToTextProperty. It's the only way to make that function take char* that I know of with C++..

The main warning to deal with now is changing  int argc, char * argv[] inside main(). I would think this would be a common problem though since it is used for command-line arguments..

---

