---
title: "Programming with Linux"
date: 2008-07-29
forum: Programming Talk
---

### Post by randipoling on 2008-07-29
I am new to all this programmingof software.  I have started out with it in Visual Studio on windows.  But I am wanting to expand to Linux aswell.  Anyone know where I can find a tutorial or something to help guide me when it comes to programming and writing software in linux?

thanks for reading.

---

### Post by knightcoder on 2008-07-29
If you're working on C++ on VS, the language doesn't change much on Linux, the only difference is the interface and the way you compile and build.

I personally am very comfortable with vim editor and gcc, makefiles. Its the bread and butter of programming in C/C++ on Linux.

All the above is command line based. If you love GUI, you may have to do some search and find something that closely emulates VS.

Good luck !

---

### Post by ibuclaw on 2008-07-29
Nothing beats CLI programming in Linux, it is the way to go!!!

But, if you are serious about your IDEs, then check out and install [Code::Blocks 8.0]("http://www.codeblocks.org/")

It is quite possibly the best Dedicated C/C++ IDE out there...

If you used VB.NET, there is [Gambas 2]("apt://gambas2"), although it is a branch of BASIC, not a copy of MS' VB.

And lastly, C#, there is [Mono Develop]("apt://monodevelop").

Regards
Iain

[EDIT]
Fixed broken apt:// links...

---

### Post by randipoling on 2008-07-29
Ive been messing around with C# just to start out and to get the feel of things.  Which I am not sure is the best way to go? I;m going to college fro programming,b ut I dont start actually doing the code and progrraming itself til this fall.  So I probably should take a look at C++, and so on, right?  I just want to learn on my own aand take that with me to class, because I plan on making a career out of this, and my life is being planned as we speak, and yeah, aside from my life, all the suggestions that can be made would be great! =D

thanks to everyone that has already posted!

--------------------------------------------------
I'm also not too worried about a GUI btw.

---

### Post by knightcoder on 2008-07-29
I'd say that C# would be great once you start you career in programming. I strongly suggest you first learn C/C++ and then move on to C#.

It will help you build a solid foundation for your career.

---

### Post by ibuclaw on 2008-07-29
From my point of view, Learning C/C++ is a strong choice if you wish to program for more than just the Windows platform.

Although Perl is another great language too. Especially so for people from a C/C+ background, it also helps give you an inside feel for the two greatest text-processing languages too (also worth an attempt at learning), Awk and Sed.

Although, if money is all you care about... Then C# is the career for you :(

Regards
Iain

---

### Post by eximius1 on 2008-07-29
Sorry to kind of hijack the thread slightly but how would you compile java in linux? Anything important I need to know about writing java in linux? 

Thanks.

---

### Post by knightcoder on 2008-07-29
You should try eclipse. Its an IDE for Java. I'm not a Java guy but I hear its real good.

I believe they were trying to include C++ in there too. Don't know how far its come.

---

### Post by ashgromnies on 2008-07-30
> **eximius1 said:**
> Sorry to kind of hijack the thread slightly but how would you compile java in linux? Anything important I need to know about writing java in linux? 

Thanks.

```
javac somefile.java
```

It's pretty easy to do on the command line. Eclipse is a nice Java IDE, though.

---

### Post by fd9_ on 2008-07-30
> **knightcoder said:**
> If you're working on C++ on VS, the language doesn't change much on Linux, the only difference is the interface and the way you compile and build.


...and debug. Most people seem to forget that one. I have yet to find an integrated debugger that's as powerful as VS.

---

### Post by dexter.deepak on 2008-07-30
> **eximius1 said:**
> Sorry to kind of hijack the thread slightly but how would you compile java in linux? Anything important I need to know about writing java in linux? 

Thanks.

its very similar to windows.

to compile :
javac <code.java>
to run :
java <code>

you also have a faster (but platform-independent) medthod of using gcj :
to compile :
gcj <code.java>
to run :
./code

---

### Post by ibuclaw on 2008-07-30
> **fd9_ said:**
> ...and debug. Most people seem to forget that one. I have yet to find an integrated debugger that's as powerful as VS.

Have you tried out Codeblocks?
You can find the Hardy debs from their main site, but it has now been merged with Ubuntu's testing repository for their next release (8.10), if you prefer to pin install it instead...

Regards
Iain

---

### Post by knightcoder on 2008-07-30
For guys who love to work on CLI, use gdb. Its a very powerful debugger. I use it all the time.(Sadly, you have to compile your code with the debug option. But hey, you have choice)
I forgot to mention that in my previous post. Thanks for bringing that up fd9_.

---

### Post by fd9_ on 2008-07-30
One of the major features lacking in gdb is the ability to properly debug STL code. And yes, I have tried the debugger in code::blocks, but I believe it's just a frontend to gdb?

---

### Post by eximius1 on 2008-07-30
Thanks for the help guys. I'm only starting out with java but it's going well so far, I even got a book :lolflag:

---

### Post by ceclauson on 2008-07-31
Based on some of the previous posts, I thought I'd mention NetBeans, a Java IDE that can run on Linux.  Like Visual Studio, NetBeans lets you create guis with drag and drop.

Although I wholeheartedly agree with the earlier advice about the importance of studying C++ if you're interested in computers in the long run, if your background is C# on Visual Studio, and you're looking for something similar on Ubuntu to mess with, Java with NetBeans may be worth looking in to.

---

### Post by Zugzwang on 2008-07-31
> **fd9_ said:**
> ...and debug. Most people seem to forget that one. I have yet to find an integrated debugger that's as powerful as VS.

There is none. In the last VC++ version I used the program could be changed while it is running (provided that I didn't introduce new variables and so on). Never seen similar tools here.

Also the (GNU) Linker ist somewhat bad - Ordering of libraries in the list of libraries to links against is actually important, no incremental linking and unused functions are still included in the executable file. Maybe that's why everyone on Linux prefers shared libraries. ;-)

---

### Post by pmasiar on 2008-07-31
Ridiculous. OP is asking FAQ, and from 16 answers none suggests reading sticky FAQ (which has much better answers than random suggestions as posted). I wonder how many people answering this read FAQ themselves?

---

### Post by mssever on 2008-07-31
> **pmasiar said:**
> OP is asking FAQ, and from 16 answers none suggests reading sticky FAQ (which has much better answers than random suggestions as posted).
pmasiar could also have mentioned his signature, which links to his wiki and has info about programming in Python.

---

### Post by nvteighen on 2008-07-31
> **pmasiar said:**
> Ridiculous. OP is asking FAQ, and from 16 answers none suggests reading sticky FAQ (which has much better answers than random suggestions as posted). I wonder how many people answering this read FAQ themselves?
Good question.

---

### Post by LaRoza on 2008-07-31
> **fd9_ said:**
> One of the major features lacking in gdb is the ability to properly debug STL code. And yes, I have tried the debugger in code::blocks, but I believe it's just a frontend to gdb?

A major feature lacking in C++ is sane code ;)

Debugging Templates isn't that easy (neither is debugging C++...)

[http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)

For all the other questions, the sticky should answer everything. For whoever asked about Java, the sticky also addresses that.

---

