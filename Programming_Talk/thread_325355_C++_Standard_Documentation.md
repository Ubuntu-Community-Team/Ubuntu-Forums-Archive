---
title: "C++ Standard Documentation"
date: 2006-12-25
forum: Programming Talk
---

### Post by HokeyFry on 2006-12-25
is there a web site that has the c++ standard documentation, kind of like the java api documentation?

---

### Post by chippy99 on 2006-12-25
Google C++ documentation returns lots of valid results.

Heres one [http://www.cppreference.com/](http://www.cppreference.com/)

---

### Post by Patrick-Ruff on 2006-12-25
here's a good one (also found in google) 

[http://cplus.about.com/](http://cplus.about.com/)

---

### Post by Zdravko on 2006-12-26
> **HokeyFry said:**
> is there a web site that has the c++ standard documentation, kind of like the java api documentation?
Yes, there is! It is located here: [http://www.sgi.com/tech/stl/](http://www.sgi.com/tech/stl/)

SGI has currently the best STL implementation. MS' one sux.

---

### Post by Verminox on 2006-12-26
> **Patrick-Ruff said:**
> here's a good one (also found in google) 

[http://cplus.about.com/](http://cplus.about.com/)


Somehow I never find my way around about.com.... I don't like commercial websites with loads of ads and unformatted code snippets for programming... </opinion>

I'd really rather go for a more plainer website that gives documentation to the point... and as the OP likes the Java API docs, something like [cppreference.com]("http://www.cppreference.com") would be more suitable.

---

### Post by Halcy0n on 2006-12-26
If you want a website, then cppreference.com is probably the best way to go.  My opinion on a great STL reference (not a website) would be: The C++ Standard Library: A Tutorial and Reference by Nicolai M. Josuttis.  I love this book and keep it nearby my desk since I'm forgetful of simple APIs :)

---

### Post by nszabolcs on 2006-12-26
unfortunately the above links has nothing to do with the C++ standard

if you want _the_ C++ language specification then you should look around on [http://www.open-std.org/](http://www.open-std.org/)

direct link to the latest working draft: [http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n2009.pdf](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n2009.pdf)
(imho this is what you want)

---

### Post by amo-ej1 on 2006-12-28
I'm rather fond of the libstdc++ API documentation: [http://gcc.gnu.org/onlinedocs/libstdc++/documentation.html](http://gcc.gnu.org/onlinedocs/libstdc++/documentation.html)  but it takes some time to get used to it.

---

### Post by FyreBrand on 2006-12-28
> **Zdravko said:**
> Yes, there is! It is located here: [http://www.sgi.com/tech/stl/](http://www.sgi.com/tech/stl/)

SGI has currently the best STL implementation. MS' one sux.

SGI has the best C++ API documentation.  It's so easy to read through and find your way around.  I like how it describes forms and also provides links to associated concepts.  It's pretty thorough.

The cppreference.com site is pretty nice too.

---

### Post by nfm on 2006-12-30
Hello,

I'm also looking for standard library documentation but for C language, not C++ since I haven't got that far... Two best links that I found are:

[http://www-ccs.ucsd.edu/c/index.html](http://www-ccs.ucsd.edu/c/index.html)
[http://www.acm.uiuc.edu/webmonkeys/book/c_guide/](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/)

According to the standards, there are **18** headers available in C library, the first link describes all 18 of them, second only 15. Other sites cover only 4, but in very good detail with straightforward examples. I would be very grateful if anybody could tell about any reference, book or anything that covers those all 18 in great detail :-| 

I have "**The C Programming Language, 2nd edition**" but it doesn't cover them all, or maybe I just will google each individual header/class to learn more about it.

Also another question, I have Visual Studio 2005, is Standard Template Library (STL) based on the STL published by SGI? I am so confused on those STLs. I want to learn C++ after I finish with C, I got past pointers and I'm finishing up :) 

Can anybody tell me why linux kernel, drivers and most of the apps are still programmed in C but not in C++? Does it have to do with objects creating garbage and memory leaks?

---

### Post by Mirrorball on 2006-12-30
The one I like: [http://www.cplusplus.com/](http://www.cplusplus.com/)
It has everything, as far as I can tell.

---

### Post by Zdravko on 2006-12-30
> **nfm said:**
> 
Also another question, I have Visual Studio 2005, is Standard Template Library (STL) based on the STL published by SGI? I am so confused on those STLs. I want to learn C++ after I finish with C, I got past pointers and I'm finishing up :) 

Can anybody tell me why linux kernel, drivers and most of the apps are still programmed in C but not in C++? Does it have to do with objects creating garbage and memory leaks?

STL is just a design pattern - it is described as a collection of libraries, functions and classes. Complexity, signatures and algorithms are also specified by STL. No matter whether you use Windows or Linux, STL looks one and the same - that is your code is 100% portable. But its implementation differs significantly! How a C++ function's body looks like, depends on the programmer that coded it for that machine ;) I don't like MS' one, because it has some quite weird details (invisible to you and most beginners ;)) and slow in comparison to the SGI's one ;)

The kernel and most apps are coded in C, because of speed performance, backward compatibility, flexible manipulation of the hardware etc.

---

### Post by Faolan84 on 2006-12-30
Hm... standard documentation for what library? GTKmm, std, QT? Or do you just want to learn the basics?

Truthfully if the basics are all you want to know you can easliy find info on the web but if you're like me the you'd probably like a book to go along with that too. I'd really recommend "C++ Programming: In Easy Steps" by Mike McGrath it's short, simple, and concise. Plus it has pictures and exaple code and is written in plain english. It set me back about $11 but it was worth it.

Also don't use IDEs , they slow you down and dumb things down. Just use a text editor with syntax highlighting and such. Some editors even have plugins or features that are useful like invoking "make" and such. I would recommend Vim there but if that isn't your bag Gedit is good and so is KATE.

And lastly, GTKmm (the C++ incarnation of GTK+) can be almost nightmarish... just like the character in your pic, Gaara. GTK+ is a much more well formed and thought out library and many times more mature. Get ready to exprience a world of frustration with having to make tree models just to populate a combo box. On the otherhand, at least in theory, C++ is supposed to use less code.

Oh, and good luck. BTW: I still think Rock Lee could've kicked Gaara's ***! That was just a fluke :P

---

