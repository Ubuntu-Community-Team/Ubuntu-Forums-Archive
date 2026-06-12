---
title: "Programming under ubuntu"
date: 2011-08-27
forum: Programming Talk
---

### Post by mandza on 2011-08-27
hi everyone,
i am writing applications and interactive programs with php. Now i want to do the same work with some other programming language, like c++, delphi or something else. But i want my programs to run under linux/ubuntu and if it is posible under windows; what kind of programming language i need to select for this kind of job???

---

### Post by Idefix82 on 2011-08-27
You can choose almost any programming language, but if it is a compiled language (e.g. C++), then you will need to compile the programs separately under Windows and under Linux. If the programs use a graphical interface, then you likely have to write separate programs for Windows and for Linux (and possibly even separate ones for KDE and gnome). 

One way to avoid that is to use some high level interpreted language like Python or Java.

---

### Post by sanderd17 on 2011-08-27
Using Java would be the best thing in your case.

Java isn't completely interpreted (it's compiled to Java bytecode) so it's faster than interpreted languages, but because it's not native machine code, it's still slower than languages like C(++).

One of the main disadvantages of Java is that it doesn't follow the desktop theme settings.

---

### Post by mandza on 2011-08-27
for beginning i thinking to make a very small program that will display something like "hello world" on screen. but it will listenin port something like 3723 and it will be posible to send data to explorer with this program.

For Example: when i write in explorer 192.168.1.18:3723 it will display "Hello world"

How can i do this?

in the next stage i want to make two separate program one of them will be transmitter and another receiver, and receiver will have interface but transmitter not.

Thank you a lot for your replays Idefix82 and sanderd1. it was helpfull.

Edit: transmitter program will work on ubuntu only. so i just need help for linux now.

---

### Post by OlyPerson on 2011-08-27
I've been doing some work with C++ coupled with [Qt]("http://qt.nokia.com/products/") which sounds a lot like what you want.  Qt is a cross-platform application and UI framework (works in Windows/Linux/Mac/etc).

Qt has a good example of a [server]("http://doc.qt.nokia.com/4.7-snapshot/network-fortuneserver.html")/[client]("http://doc.qt.nokia.com/latest/network-fortuneclient.html") pair on there website.

---

### Post by mandza on 2011-08-27
is Qt easy to learn?

---

### Post by cgroza on 2011-08-27
> **mandza said:**
> is Qt easy to learn?
I tried learning Qt. It depends if you already have experience with GUI building.
I already know wxWidgets when I gave it a go and it did not seem difficult to grasp.

---

### Post by mandza on 2011-08-27
i don't know gui. all i know is php and mysql. and now i had learn python.

---

### Post by OlyPerson on 2011-08-27
Qt is my first attempt at making GUIs and I think it's pretty simple.  Great documentation and lots of [examples]("http://doc.qt.nokia.com/latest/all-examples.html") on their website.

---

### Post by mandza on 2011-08-27
> **OlyPerson said:**
> Qt is my first attempt at making GUIs and I think it's pretty simple.  Great documentation and lots of [examples]("http://doc.qt.nokia.com/latest/all-examples.html") on their website.

Then you a lot i will try it.

---

### Post by hakermania on 2011-08-27
> **OlyPerson said:**
> Qt is my first attempt at making GUIs and I think it's pretty simple.  Great documentation and lots of [examples]("http://doc.qt.nokia.com/latest/all-examples.html") on their website.
+1

And documentation is more than excellent

---

### Post by nvteighen on 2011-08-28
I'd favor Java rather than C++ for this. Ok, it's true that Qt is cross-platform and that you can recompile your C++ source on Windows... when you don't rely on OS-specific APIs! For example, what if you used BSD/POSIX sockets? In such cases, you'd have to fill your code with conditional compilation or rewrite the whole thing.

---

### Post by GeneralZod on 2011-08-28
> **nvteighen said:**
> I'd favor Java rather than C++ for this. Ok, it's true that Qt is cross-platform and that you can recompile your C++ source on Windows... when you don't rely on OS-specific APIs! For example, what if you used BSD/POSIX sockets? In such cases, you'd have to fill your code with conditional compilation or rewrite the whole thing.

I'd probably go with Java, too, but why chain yourself to one specific socket API when you have [ QtNetwork](http://doc.qt.nokia.com/latest/qtnetwork.html)?

---

### Post by nvteighen on 2011-08-28
> **GeneralZod said:**
> I'd probably go with Java, too, but why chain yourself to one specific socket API when you have [ QtNetwork](http://doc.qt.nokia.com/latest/qtnetwork.html)?

Because I didn't know its existence ;) I barely know Qt because I rarely do GUIs and when I do them, I use GTK+.

Meh, the sockets example was just an example. My point was that if you the C++ route, you'll have to be very careful in what libraries you choose to use, in order to not get trapped into OS-specific behavior.

---

### Post by OlyPerson on 2011-08-28
> **nvteighen said:**
> Because I didn't know its existence ;) I barely know Qt because I rarely do GUIs and when I do them, I use GTK+.

Meh, the sockets example was just an example. My point was that if you the C++ route, you'll have to be very careful in what libraries you choose to use, in order to not get trapped into OS-specific behavior.

That's why I mentioned Qt :) Cross-platform even with network programming.  You'd still have to be SOMEWHAT careful, but Qt handles a lot of stuff.

---

### Post by mandza on 2011-08-29
> **OlyPerson said:**
> That's why I mentioned Qt :) Cross-platform even with network programming.  You'd still have to be SOMEWHAT careful, but Qt handles a lot of stuff.

if i would use Qt, for running program do i need to install anything on my pc or it just work like .exe on windows?

---

### Post by nvteighen on 2011-08-29
> **mandza said:**
> if i would use Qt, for running program do i need to install anything on my pc or it just work like .exe on windows?

Yes, Qt has to be installed (btw, you'd also have in Windows, just that setups do that for you). You can automate this by creating a deb package and stating Qt as a dependency... or just tell people to install it (it's easy in most mainstream distros).

---

### Post by mandza on 2011-09-09
> **nvteighen said:**
> Yes, Qt has to be installed (btw, you'd also have in Windows, just that setups do that for you). You can automate this by creating a deb package and stating Qt as a dependency... or just tell people to install it (it's easy in most mainstream distros).

Thank you very much i will start with Qt.

---

### Post by CptPicard on 2011-09-09
> **sanderd17 said:**
> 
Java isn't completely interpreted (it's compiled to Java bytecode) so it's faster than interpreted languages, but because it's not native machine code, it's still slower than languages like C(++).

Actually, the bytecode is then JIT-compiled to native code prior to execution.

---

### Post by disabledaccount on 2011-09-09
WxWidgets are the best multi-platform toolkit. In comparison to QT or GTK it's way faster, produces less overhead and allows to use (almost) the same GUI code for gdi32/win API and linux API's based on QT and GTK. Thanks to that GUI looks "native" on any platform, unlike in case of GTK/QT. Furthermore wxWidgets offers excelent DateTime class, very fast and convenient object arrays, advanced event system, universal threads (both detached and joinable), and one of greatest things: hit statistics from memory allocators for strings - allows to extremely speed up strings operations wihtout wasting too much memory.

My favorite :)

---

### Post by WitchCraft on 2011-09-09
I'll second the motion on wxWidgets, that is, if you like C++.

But as a sidenote to the recommendations on Java, Perl and Python, why don't you try C# / VB.NET ?


MonoDevelop is a wonderful IDE (with a few shortcomings), but you can seemlessly exchange files between MonoDevelop and Visual Studio.

Also, you can write web applications just as well as desktop application with these languages.
For Linux compatibility reasons, I recommend you stick to C# instead of VB.NET.
If you go down that route, it might be useful to learn GTK (instead of wxWidgets or QT), because Mono promotes GTK# for .NET GUI applications that work across platforms.


The funny things is, Mono has a VM called IKVM, which is a Mono VM wrapper around the OpenJDK/JRE. 
This means you can start to mix Java and .NET, getting the best of both worlds :))

Another good things is there is IronPython, with which you can run Python functions and libraries in managed code ! 

Is some functionality/library not available in C# ?
For example a WikiMedia Markup parser ? 
No problem, use IronPython and reference a Python rendering library for this.
Then call the IronPython function from C#. And zong, you can use this functionality from .NET...

---

### Post by nvteighen on 2011-09-09
> **tomazzi said:**
> WxWidgets are the best multi-platform toolkit. In comparison to QT or GTK it's way faster, produces less overhead and allows to use (almost) the same GUI code for gdi32/win API and linux API's based on QT and GTK. Thanks to that GUI looks "native" on any platform, unlike in case of GTK/QT. Furthermore wxWidgets offers excelent DateTime class, very fast and convenient object arrays, advanced event system, universal threads (both detached and joinable), and one of greatest things: hit statistics from memory allocators for strings - allows to extremely speed up strings operations wihtout wasting too much memory.

My favorite :)

Wait. wxWidgets is just an abstraction layer which operates on the native GUI toolkit, whichever that is. So I don't believe it's faster... if that makes any sense in GUI programming, where the program will be most of the time idling for user input.

All other features you mention are useful only when used on C++, because of its limitations. They provide little more than what higher-level languages already provide natively, so that advantage doesn't count for wxPython, e.g.

What wxWidgets is amazingly good at is at what it was designed for: an abstraction layer to easy cross-platform GUI development. But be aware that both GTK+ and Qt are also cross-platform!

---

### Post by disabledaccount on 2011-09-09
> **nvteighen said:**
> Wait. wxWidgets is just an abstraction layer which operates on the native GUI toolkit, whichever that is. So I don't believe it's faster... if that makes any sense in GUI programming, where the program will be most of the time idling for user input.

All other features you mention are useful only when used on C++, because of its limitations. They provide little more than what higher-level languages already provide natively, so that advantage doesn't count for wxPython, e.g.

What wxWidgets is amazingly good at is at what it was designed for: an abstraction layer to easy cross-platform GUI development. But be aware that both GTK+ and Qt are also cross-platform!
To some point You're right, but first try, then talk.
1. GTK and QT on windows are deadly slow in comparison to wxWidgets, because they implement whole rendering engine while wxWidgets are just very thin layer on windows-native and hw-accelerated gdi.
2. using wxWidgets as wrapper for (f.e.) GTK (makes sense only on linux/unix) is also faster, because most of internal wx-classes are independant and faster than GTK.
3. You should read more about wxWidgets, then maybe You'll get interested in C# for wx.

---

### Post by nvteighen on 2011-09-10
> **tomazzi said:**
> To some point You're right, but first try, then talk.
1. GTK and QT on windows are deadly slow in comparison to wxWidgets, because they implement whole rendering engine while wxWidgets are just very thin layer on windows-native and hw-accelerated gdi.


First, speed at GUIs is almost irrelevant when they're correctly written, because GUIs are most of the time idling for user input. If your program does heavy computation, you usually put the GUI on a different thread than the heavy work.

Second, Skype isn't deadly slow on Windows and it uses Qt. My GTK+ on Windows example is even better, the SuperTux level editor, because it works at a very acceptable speed even though it's written in Mono C#. Ok, GTK+ and Qt *may* be slower than wxWidgets because of what you say, but I deny its relevance and my experience tells me that if there's any delay, it's completely neglegible.

> 
2. using wxWidgets as wrapper for (f.e.) GTK (makes sense only on linux/unix) is also faster, because most of internal wx-classes are independant and faster than GTK.


Impossible for the exact same reasons you say. The more abstraction you use, the slower everything gets because there's more to call. By definition, wxWidgets can't be faster than GTK+: 1) C++ is slower than C, specially when virtual tables are around, 2) wxWidgets has to convert its data structures into GTK+ ones, 3) all of this is irrelevant because the GUI will be idling anyway, so the supposed speed advantage of one toolkit over the another would be lost.

> 
3. You should read more about wxWidgets, then maybe You'll get interested in C# for wx.

You should read more about Qt, GTK+, understand the abstraction vs. speed trade-off, learn what the "I/O bottleneck" is and why it makes speed measurement completely irrelevant for any program that has a user interface.

Sorry for my tone, but you've been one of the first posters that has made me lose my patience on these forums.

---

### Post by disabledaccount on 2011-09-11
> **nvteighen said:**
> First, speed at GUIs is almost irrelevant when they're correctly writtenYeah, If You have one button named "Next". But If You have some graphics (f.e. charts) or data grids then it clearly shows which interface is faster.
F.e. last year I've written GUI for database management that was able to display/sort/search/adaptive filtering trough several milions of records and display results in wxGrid and wxChart - such big amount of data needs huge amount of processing power to just generate view. I've compiled it under GTK and gdi with modified multithreaded wxGrid and in both cases it was equivalently fast. GTK/QT on windows is slow even when only refreshing toolbars/buttons.

(btw. reason was that Excel or even Access is just crap when it comes to real and fast data management)

---

### Post by nvteighen on 2011-09-12
> **tomazzi said:**
> Yeah, If You have one button named "Next". But If You have some graphics (f.e. charts) or data grids then it clearly shows which interface is faster
F.e. last year I've written GUI for database management that was able to display/sort/search/adaptive filtering trough several milions of records and display results in wxGrid and wxChart - such big amount of data needs huge amount of processing power to just generate view. I've compiled it under GTK and gdi with modified multithreaded wxGrid and in both cases it was equivalently fast. GTK/QT on windows is slow even when only refreshing toolbars/buttons.

(btw. reason was that Excel or even Access is just crap when it comes to real and fast data management)

My point was 1) that I doubt that wxWidgets could be faster than GTK+ on GNU/Linux, 2) that in my experience GTK+ and Qt are not noticeable slow, even when it comes to GTK# on Mono.

Sincerely, I don't get quite get the point of your post. Was it Excel the reason why everything got slower or was it really GTK+ on Windows? Have you measured this?

OK. Of course, if you're showing a complex data grid, it might require time to show up. But what is it what requires time? Drawing the chart or processing the data? The former is just drawing stuff into the screen and if the library is well-designed, it shouldn't have any noticeable critical delay (gnome-system-monitor, e.g.). If the data is complex, then the issue is at the backend, I guess, and even a console ncurses-based UI would lag in that case. In that latter case, all you can do is to tell the user to wait, I think, but it'd be very rare that the issue was the chosen GUI toolkit. If it was, it should be reported as a bug.

---

### Post by JupiterV2 on 2011-09-12
> **mandza said:**
> for beginning i thinking to make a very small program that will display something like "hello world" on screen. but it will listenin port something like 3723 and it will be posible to send data to explorer with this program.

For Example: when i write in explorer 192.168.1.18:3723 it will display "Hello world"

How can i do this?

in the next stage i want to make two separate program one of them will be transmitter and another receiver, and receiver will have interface but transmitter not.

Thank you a lot for your replays Idefix82 and sanderd1. it was helpfull.

Edit: transmitter program will work on ubuntu only. so i just need help for linux now.

You may also want to look at [Golang]("http://www.golang.org"). There are tutorials/Youtube videos for doing this very thing in Go. It's original design was for web servers but works well as a general, all-purpose language. Writing a "hello world" server is as simple as about 5-6 lines of code (excluding newlines) in Go. A good intro might be this [video]("http://www.youtube.com/watch?v=-i0hat7pdpk").

---

### Post by disabledaccount on 2011-09-16
> **nvteighen said:**
> My point was 1) that I doubt that wxWidgets could be faster than GTK+ on GNU/Linux, 2) that in my experience GTK+ and Qt are not noticeable slow, even when it comes to GTK# on Mono.

Sincerely, I don't get quite get the point of your post. Was it Excel the reason why everything got slower or was it really GTK+ on Windows? Have you measured this?

OK. Of course, if you're showing a complex data grid, it might require time to show up. But what is it what requires time? Drawing the chart or processing the data? The former is just drawing stuff into the screen and if the library is well-designed, it shouldn't have any noticeable critical delay (gnome-system-monitor, e.g.). If the data is complex, then the issue is at the backend, I guess, and even a console ncurses-based UI would lag in that case. In that latter case, all you can do is to tell the user to wait, I think, but it'd be very rare that the issue was the chosen GUI toolkit. If it was, it should be reported as a bug.I'm sorry it's not that was avoiding the answer - I just had a lot of work and in fact forgot this topic... 

Ganerally: I've just wanted to point to wxWidgets as an alternative, **truly** multiplatform toolkit. What we were discussing here was the aspect of term "truly" - so I'll try to explain what I meant...
1) So it seems that You agree that GTK is slower on windows - the problem is GTK on Linux/Unix. The explanation is simple: It's the same situation like on windows - where wxWidgets are thin layer over complex, but native and thus fast API. To be more precise: every API has lower (faster but less convenient) and higher level functions - wxWidgets are wrapping low-level GTK functions (like drawing rectangles, lines, GL surface, etc) while using its own wxGrid class to manage the data for fields, methods of refreshing/redrawing, render-prefetch, scrolling (my example) - in other words native, higher level classes can be slower in such case.
2) "Not noticably slow" is exactly matter of complexity of GUI. AUI is just one example where dockable toolbars/windows are realised with less CPU load and memory requirements than in GTK (I mean GTK3 here).

Excell record/row number limit is only 0xFFFF. Access is different animal, but when there's possibility to get result of filtering with 300+ different filters at a time that can have f.e. 800 thousands of rows (or even more), then Access will die - at least, it will freeze for long time on a laptop with 4GB RAM and dual core 3GHz CPU. My app is able to process and display 1.4x10^6 records in about 4secs, scroll it smoothly and draw charts in a microsecond - using wxWidgets - tests were made with exactly 300filters active.
To be honest - wxWidgets App class is single threaded - it needs some modifications for GUI-multithreading, but it's very easy tweakable, most of what You need is available trough #defines.

---

