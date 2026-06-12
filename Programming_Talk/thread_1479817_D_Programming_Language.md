---
title: "D Programming Language"
date: 2010-05-11
forum: Programming Talk
---

### Post by dodle on 2010-05-11
I was wondering if some others had opinions about the D programming language.  I had seen it around every once in a while, and yesterday I spent a little time on Wikipedia reading about it.  It sounded pretty interesting so I downloaded the Digital Mars Compiler.  Ubuntu has the GNU D compiler in one of its repositories, but Digital Mars offers their compiler in a deb labeled for Ubuntu.  So I went ahead and tried it out.  

From what I understand, it claims to be a language as powerful as C++ with benefits of other languages as well, like Java and Python.  

I want to know what others think about it.  It's sounds interesting, but I want to become proficient in programming languages that are going to be around for a while and widely used.  I am currently trying to learn C++ and have done some Python scripting.  D is not standardized and I'm guessing that there is not a lot of support yet from other projects, like wx, Qt and Gtk.  But I could be wrong.

[http://digitalmars.com/d/index.html](http://digitalmars.com/d/index.html)
[http://en.wikipedia.org/wiki/D_%28programming_language%29](http://en.wikipedia.org/wiki/D_%28programming_language%29)

---

### Post by soltanis on 2010-05-11
It's another language trying to claim successor to the C line after C++ did such a great job messing that up. It follows along the paradigms of object orientation and the code looks pretty clean, otherwise nothing to get too excited about. Unfortunately, it hasn't been snapped up by the community I think is a wayside language.

If you want to check out other C-like successors take a look at Limbo (evolved from a C descendant used in Plan 9 development) and Go, which is the most recent iteration of that line of languages (from Google, oddly enough -- is it just me or does Google seem to just pop out of nowhere and give everyone goodies?).

---

### Post by he_the_great on 2010-05-17
Many people won't use D because it has a small community and there isn't a large company backing it. Those that use the language enjoy it and wish to see the language to reach the masses, but they know that won't happen unless people start using the language. The development team behind its development have quite impressive backgrounds especially in C++. 

I would suggest D over Go since the language is more mature and Go does not really provide anything over D, but does lack many things. There is also no reason you should choose a single language to be proficient in. But if you learn D you won't want to develop in C++.

---

### Post by dodle on 2010-05-18
I think I'll tinker with it while I learn C++.  It has a few more libraries available than I thought it did.  The C++ wxWidgets library can be used with it through wxD.  The only thing that doesn't appear very appealing is how it creates large executables, much larger than C++.

---

### Post by he_the_great on 2010-05-18
> **dodle said:**
> The only thing that doesn't appear very appealing is how it creates large executables, much larger than C++.

The size has been attributed a few things, on of which is that shared libraries aren't being used. Other have been related to templates. The large size is really only an issue when trying to work under 1MB. If you're looking at the size from using wxD then its larger because shared libraries aren't being used.

---

### Post by dodle on 2010-05-18
I wasn't referring directly to wxD.  If you take a simple "Hello World" program:

C++ (compiled with g++):
```
// Hello World! in C++

#include <iostream>
using namespace std;

int main()
{
  cout << "Hello World!" << endl;
  return 0;
}
```
D (compiled with dmd):
```
// Hello World! in D

import std.stdio;

void main()
{
   writefln("Hello World!");
}
```

The C++ executable is 6.6kb, the D executable is 124kb.  Of course I don't know if the difference is relative, or if D executables will always only be 100kb more than C++.  I'd have to compile some bigger programs to check it.

---

### Post by he_the_great on 2010-05-18
There hasn't been extensive testing, but when under 1MB it is expected to be larger than C++ because of the overhead of having a Gargbage Collector and probably some other things.

D may always produce larger executables than C++ but there are a lot of variables that make it diffacult to provide a fair comparison.

---

