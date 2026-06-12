---
title: "New (to me) C++ Standards"
date: 2006-10-22
forum: Programming Talk
---

### Post by indigoshift on 2006-10-22
So, I found the source code to an old C++ program I wrote, and decided to move it over to my Ubuntu box and tweak it a little.

Cleaned up the code a bit, and tried to compile, and got a ton of weird errors.  Did some research, and noticed that the standards have changed since the last time I did any serious coding (which was around 2000).

Whereas before, I could just:

```
cout << "blah blah blah"  << endl;
```

Now, I have to put in a:

```
using namespace std;
```

before it, unless I'd rather be typing out a ton of "std::cout"...and when did this whole "leave the .h off of your #include <blah.h>" stuff start?

Well, now I feel old.  ;)

Are there any other gotchas for someone who hasn't coded since the turn of the century?  Any good websites?  So far, I'm relearning via cplusplus.com's tutorial pages, but any other links would be more than welcome.

Thanks!  And get off my lawn!  :D

---

### Post by alek66 on 2006-10-22
Just add this:

#includ <iostream>
using namespace std;

and everything will work
or
#include <iostream>
using std::cout;
using std::endl;

---

### Post by po0f on 2006-10-22
indigoshift,

C++'s standardization was finalized in Nov '98, and released sometime Jan '99 I believe.  Compiler verndors closely following the process could have implemented features that were shoe-ins for the standard, but I can see how a compiler from circa 2000 still would not have implemented the whole standard.

All of C++'s libraries are in what's called the **std** namespace.  Namespaces were created so that the global namespace would not be so polluted.  As you stated, you can just write in a **using** directive to let the compiler know to allow the whole std namespace into the global namespace, so you can use the functions unqualified.

The standard also states that the C++ libraries do not have to point to actual files.  I don't know how this is actually implemented, /usr/include/c++/4.1.2/iostream looks like a file to me.  ;)

As far as reading material goes, I like to recommend Bruce Eckel's [Thinking in C++](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html) series.  They are very good books, and are free to download!  (I actual own volume 1 in print, would like to get volume 2 in print as well.)

Hope this helps.

---

### Post by indigoshift on 2006-10-22
Helps a lot, actually.  Thanks!

I <3 free books. :)

---

