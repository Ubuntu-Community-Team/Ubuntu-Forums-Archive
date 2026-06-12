---
title: "Recommended language for making [games] + Gnome apps"
date: 2008-02-12
forum: Programming Talk
---

### Post by maximilion on 2008-02-12
Hello. :)

I thought I'd make myself useful in the Linux world as well. I've coded a DirectX game, a simulator+a bunch of other utilities, and misc. stuff in SDL on Windoze using Delphi. I'm a fan of Niklaus Wirth's languages. :KS

Before that I've coded mostly Z80, 68k and ARM assembler. Before that, BASIC for umpteen home computers.


I thought I'd ask you guys for advice on how to get started:

There are a bunch of aspects I'm considering (most important first)

1. Number of distros that can run it, i.e.: should I code for Gnome? GTK? SDL? GLX? As you see I really have no real overview of misc "GUI engines" that are available in [Ubuntu] Linux. Heck, I just installed in 4 days ago :P

2. Easy interface to graphics/sound/file/WIMP APIs, as well as the possibility to at least get some form of direct control of graphics and sound. Give me a frame/window buffer and pan/mix/stop controls over sound channels please! :)

3. A nice IDE where I can set breakpoints and look at variables, for those functions that cannot be debugged until it's loaded something. Like the productive Delphi IDE, if possible. 

4. A reasonably non-cryptic language. Python, Ruby look nice, Pascal and Javascript are no problem. I also know html, css, a bit of php. 


Basically, if I can setup an "app template" that opens a window, gives me the frame buffer, and allows me to occasionally pop up a [file]dialog, I'm usually a happy camper :D


I'd like to not program in C (and dialects). They're ugly in my eyes. If you prefer it, then you should of course use it. No flame wars please! :)

---

### Post by LaRoza on 2008-02-12
You might want to check out Python and PyGame. There are also game engines available for Python, but I don't do such programming.

The good thing about Python and PyGame is that the games will work on most operating systems without changes.

For graphics, you can use SDL, OpenGL and probably others. 

For GUI's, you have a lot of options, wxWidgets, QT, GTK+ and TK are usable in many languages and on many platforms. GNOME uses GTK+.

See my wiki and the sticky for more.

---

### Post by pmasiar on 2008-02-12
Python has bonus that it is also main language for OLPC and Ubuntu.

Wiki in my sig has all python links you need. "Dive into Python" is exactly for people like you - experienced prgrammers, who need dive into Python and start hacking. Have fun!

---

### Post by maximilion on 2008-02-12
Heh, didn't expect replies so soon. :)

Sounds good. Glad you mentioned documentation as it's glaringly missing from my initial post. A code hinter, rich help system, community with "what can I do with this then?"-demo sources all help in making programming enjoyable.

I'd go Kylix, but it looks like WIndows on Linux, and I'm afraid I've been a little spoiled playing with themes and such in Ubuntu :D Maybe I should say 'Gray Borland apps'. I mean, .BMP? Move ON! I'm more of an .MNG/layer opacity type person I guess :P

Not that I'm about to make YAVP (Yet Another Video Player, I've no idea if there's perhaps already a Linux app called this ;)) or Adobe Premiere type app, but if there is an as enjoyable IDE that is .PNG, .MP3/.OGG, maybe even .XGL-concious, I would take a good look :)

---

### Post by shawnhcorey on 2008-02-12
You may want to look at the [Glade Interface Designer]("http://glade.gnome.org/").  It is designed for GUI Apps but you might find it useful.

You can load it via Applications->Add/Remove...

---

### Post by RIchard James13 on 2008-02-13
NOTE: SDL is not a GUI library, you can get other libraries to go with SDL that will get you widgets or you can program your own widgets. Think of SDL as more like a DirectDraw Canvas + Sound + Input. SDL is excellent for games but not so good for writing GUI's

---

### Post by maximilion on 2008-02-18
Yeah, I've used SDL before.

Python looks good, are there speed comparisons of script languages vs compiled ones? Or am I overly skeptical/missing something and speed will not be a major issue?

Reason I'm asking is one of the things I'd like tot toy with are real time 2D filters, could I expect to write a VLC filter in Python?

---

### Post by LaRoza on 2008-02-18
> **maximilion said:**
> 
Python looks good, are there speed comparisons of script languages vs compiled ones? Or am I overly skeptical/missing something and speed will not be a major issue?

Reason I'm asking is one of the things I'd like tot toy with are real time 2D filters, could I expect to write a VLC filter in Python?

There are two types of time when programming, computer time and programmer time.

There is significant gains when using a dynamic language like Python over a lower level language. There is a great article on it, that uses Tcl as the example. I will try to find it...

Python and most of its modules are written in C, and will be very fast.

---

### Post by sryth on 2008-02-18
Might not be popular but I recommend downloading DrScheme (it's in the ubuntu repos) And taking a look at scheme.  The Dr Scheme IDE is very nice for the language and you can go the procedural route or use the Swindle dialect for a nice object system, and there is nothing you can't do with it really.  [http://www.plt-scheme.org/](http://www.plt-scheme.org/)  Is a great website for tutorials and such.

---

### Post by Choad on 2008-02-18
python-ogre is worth taking a look at. it's relatively new but the build scripts do finally work now, and it is very nicely documented and to me seems like the most elegant "all-in-one" solution to making a game (can code your game in c++ too if you feel like it)

---

### Post by slavik on 2008-02-18
since the Python people had their say, I will say this:

You are familiar with SDL, no reason to go to read about pygame (sorry pmasiar) since Python has SDL and OpenGL bindings. So do Perl and Ruby.

For a game, if you are serious about writing one that performs well, I will have to say C.

PS: Don't know about others, but in Perl there is no glVertex2d and such, just glVertex, since perl does all the type conversion/checking. ;)

---

### Post by Fbot1 on 2008-02-18
> **maximilion said:**
> Hello. :)

I thought I'd make myself useful in the Linux world as well. I've coded a DirectX game, a simulator+a bunch of other utilities, and misc. stuff in SDL on Windoze using Delphi. I'm a fan of Niklaus Wirth's languages. :KS
...

I've heard that Lazarus is a really good for using Pascal. I like the compiler (...it's a nice compiler...) but I'm not a big fan of the language so take my suggestion critically.

---

### Post by happysmileman on 2008-02-18
> **maximilion said:**
> Python looks good, are there speed comparisons of script languages vs compiled ones? Or am I overly skeptical/missing something and speed will not be a major issue?

Python is an interpreted language and therefore would be slower than a compiled one, compiling Python would be faster, but still not as fast as C/C++ or something like that.

However for small games the performance of them usually is negligible, since it's usually not that complex, and for large games rendering graphics and stuff are usually the bottleneck rather than the actual computation, and since you'd just be using Bindings to the OpenGL/SDL libraries, which are written in C/C++, you're effectively using C/C++ to do the rendering anyway.

I'm not an expert, but I think most of that's right.

(tl;dr: Do it in Python, if that's slow try compiling the Python, if it's still slow and you're sure you can't speed it up, then you'll need to use C/C++ or some other lower level language)

---

### Post by maximilion on 2008-02-18
> **LaRoza said:**
> There are two types of time when programming, computer time and programmer time.

Python and most of its modules are written in C, and will be very fast.
Yes, and I was asking about computer time. ;)

Actually found a benchmark site :) Here is Python vs Ruby - [http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=python&lang2=ruby](http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=python&lang2=ruby)

(btw, It was strange that c was tested a bit faster than Pascal - it used to be the other way round. Perhaps c compilers have been optimized over the years?)

Python definitely seemed the fastest of the scripting languages, although I don't know the attributes of all the languages on that page - and it was fared pretty well vs c#.

Can finished Python functions be compiled into libraries, like Python's own modules? Would it be at all feasible to write Photoshop/VLC type filters in Python?

Anyway, just started looking at SPE, will try some simple things...


I will start another thread regarding 'game engine' and any killer games made with it.

(Which of course doesn't mean this thread is dead by any means ;)) Especially any thoughts on speeding up certain functions when finalized would be appreciated :)

---

### Post by pmasiar on 2008-02-18
> **slavik said:**
> since the Python people had their say, I will say this:

You are familiar with SDL, no reason to go to read about pygame (sorry pmasiar) since Python has SDL and OpenGL bindings. So do Perl and Ruby.


I am not sure why you say that. Anyone can say what s/he thinks, and if substantiated with facts and experience, we will consider that. Do you feel differently?

LaRoza was the person who mentioned pygame in this thread. I agree it is fine advice, but this is first time **I** mentioned pygame in this thread. 

Why you fell sorry? And why not to read about pygame to find if it fits the requirements or not?

---

