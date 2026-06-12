---
title: "Various Linux API documentation"
date: 2011-09-30
forum: Programming Talk
---

### Post by StephanG on 2011-09-30
Okay, I've been playing around, writing small little programs.  My largest program was only 576 KB after compilation.  

But, now I've been toying with the idea of writing a larger program and then open-sourcing it and putting it on my website (which is admittedly still under development).

It is ambitious, especially for someone as inexperienced as I am, but the idea is mostly to gain some experience in writing software.  Even though my program is pretty small, quality is important to me, so I want to do it the "right" way.  By which I mean, make use of existing infrastructure instead of creating my own libraries.

So, I wanted to know if there's a place that documents all the relevant API's that I might want to make use of?

Something else:  Up until now, my apps have pretty much been as I envisioned them.  But now that I'm contemplating sharing my app, I want to know if there are any standards that I need to know about.

---

### Post by karlson on 2011-09-30
> **StephanG said:**
> So, I wanted to know if there's a place that documents all the relevant API's that I might want to make use of?


You need to be a little more specific.  The documentation for APIs is provided normally by their developers.  You can certainly start with [http://tldp.org/](http://tldp.org/)

Beyond that you will need to get specific.

> 
Something else:  Up until now, my apps have pretty much been as I envisioned them.  But now that I'm contemplating sharing my app, I want to know if there are any standards that I need to know about.

1.  Know your competition
2.  Read the code of some of the open source projects.
3.  Make your code readable.  (Functions about 1 page, descriptive variable names, etc. for my personal preference)
4.  Again as a personal preference no "Hungarian Notation"

---

### Post by regala on 2011-09-30
> **StephanG said:**
> So, I wanted to know if there's a place that documents all the relevant API's that I might want to make use of?

On Ubuntu, install manpages-dev package, and in section 2 on man pages infrastructure, you should have all the documentation for POSIX apis.
Example code:
```
man 2 write
```
will display then the complete documentation for write() syscall use.

You can also go there: [http://pubs.opengroup.org/onlinepubs/9699919799/](http://pubs.opengroup.org/onlinepubs/9699919799/)
which is the reference for any POSIX or related specification.

oh I forgot, there's a Bible: [http://nostarch.com/tlpi](http://nostarch.com/tlpi)
Michael Kerrisk is the Linux man pages maintainer, and his book is the most straightforward and comprehensive manual on POSIX interfaces programming, which is a must, and on Linux-specific APIs (like epoll()) which is a shiny "plus". Enjoy !

---

### Post by StephanG on 2011-09-30
> You can certainly start with [http://tldp.org/](http://tldp.org/) 

Thanks for the link, I'll give it a look through.

> You need to be a little more specific. The documentation for APIs is provided normally by their developers.

Oh.  I was under the impression that every DE used a standard set of APIs so that programs would work well between different Desktop Environments.  So that each DE would open with it's own "Open File" dialogue, etc.

But, I just found developer.ubuntu.com, which seems to be more or less what I'm looking for.  So I'll give that a look first.

---

### Post by karlson on 2011-09-30
> **StephanG said:**
> Oh.  I was under the impression that every DE used a standard set of APIs so that programs would work well between different Desktop Environments.  So that each DE would open with it's own "Open File" dialogue, etc.

But, I just found developer.ubuntu.com, which seems to be more or less what I'm looking for.  So I'll give that a look first.

They do provide a standard set of APIs but GNOME's is different from KDE and probably different from Xfce(don't know never used it).  And if you are talking doing doing something other then Desktop (which btw wasn't in your original post) you might want to look at other things...

---

### Post by StephanG on 2011-09-30
No, it wasn't in my original post... Sorry.

I've learned some C++, Java, C# and C.  But, every program I've written, I've mostly had to do everything myself.  So, I actually have no idea what other information might be important.

---

### Post by karlson on 2011-09-30
> **StephanG said:**
> I've learned some C++, Java, C# and C.

Nice Mix...
> 
But, every program I've written, I've mostly had to do everything myself.  So, I actually have no idea what other information might be important.

What do you mean about having to do everything yourself?  Somehow I don't believe you were writing low level rendering of the file dialog window....

---

### Post by StephanG on 2011-09-30
> What do you mean about having to do everything yourself? Somehow I don't believe you were writing low level rendering of the file dialog window.... 

No, I haven't.  But my programs up to this point have actually been VERY simple.  Mostly, I just used a iostream to read to and from *.txt files.  And even then it was pretty basic.

For example, what I wrote a little command line app that would store all of South Africa's area codes into an array, and then search for a code that the user entered, and tell him what area the code is from.  Another example is a little random code generator that would produce integers between two numbers specified by the user.  I mostly used it to produce those *.txt files, so I could use them to test my other programs.

But, I've never actually written a program with a GUI before, so maybe I'm being a little ambitious...

---

### Post by karlson on 2011-09-30
> **StephanG said:**
> But, I've never actually written a program with a GUI before, so maybe I'm being a little ambitious...

No you're fine as long as you take a reasonable approach to it.  The biggest problem in the GUI is not the interface but actually the back end.  If your data structures and methods for accessing them are flawed you may have the best GUI look and feel in the world and your program would still suck...

I would suggest if you want to learn about GUI's to get some example programs like the ones coming with QT and I am sure that GTK+ has some too, get a GUI designer (QtDesigner or Glade or something else) and try your hand at something simple like "Hello World!" with a Quit button.

Then go through some data structures and algorithms and then start on your software.

Data Structures, Algorithms, and Design Patterns are hard.  Once you get a hang of those you can easily apply them to any API and any programming language for that matter...

---

### Post by nvteighen on 2011-10-01
Hm... I think most of us have passed through a similar stage in our programming life.

Ok, there are some APIs you should know (at least, its very basics), mostly because it's very likely you'll use them at some point in time. This is a non-exhaustive list in no particular order:

0. ncurses
1. GTK+ (GLib)
2. Qt
3. BSD sockets
4. POSIX

But mostly, you'll be learning APIs when you need them. Of course, before implementing anything that's not directly related to your main goal, be sure if there's not already a library that might do that.

About GUIs in general: it's a good exercise to work on them in a bottom-up style, i.e. first creating the backend, test it by using a text-based interface and only when that works, create the GUI. When you're writing an interface 8or any kind), you shouldn't need to manipulate the backend structures... if you have or your current design makes everything really hard, it means something has been badly designed "back there".

---

