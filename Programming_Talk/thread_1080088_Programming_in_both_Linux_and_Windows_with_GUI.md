---
title: "Programming in both Linux and Windows with GUI?"
date: 2009-02-25
forum: Programming Talk
---

### Post by remy06 on 2009-02-25
Hi all,

Need some advice and directions.I'm involved in a project that require to develop an application for both linux and windows(with complete GUI).

Basically, it involves socket programming as well I suppose,as it requires to sniff packets from a network and such.I'm not strong in programming,and I'm most familiar only with C/C++.

So here are my questions:
1) What are the tools,IDE,libraries available that allows me to develop the application for both linux/windows with GUI??Which is best suited for the project I am going to do?(hopefully they are easy to use..)

2) Is it possible that I can develop the application in linux,then simply port it over to windows?Or do I have to recode everything in windows?

3) Based on your experience,what other language/tools is more suitable or simpler to code this project?I am leaving this option as a last resort however,but may try consider looking into it if time permits.(the deadline is tight you see..)

So far I've heard about WxWidgets and GTK+.Do you guys recommend them or any other?The platform requirement I'm using is ubuntu and windows xp.

Appreciate your advice.

Thanks in advanced.

---

### Post by scourge on 2009-02-25
> **remy06 said:**
> So far I've heard about WxWidgets and GTK+.Do you guys recommend them or any other?

Gtk+ is not a complete enough cross-platform toolkit, and wxWidgets is just nasty in other ways. You should definitely try Qt 4.5 by Nokia. It's a fully featured C++ framework; not just for GUIs, but it also has threads, networking, and pretty much everything you need. I've found it very pleasant to use, especially compared to wxWidgets. There's an excellent book available for free: [http://www.qtrac.eu/C++-GUI-Programming-with-Qt-4-1st-ed.zip](http://www.qtrac.eu/C++-GUI-Programming-with-Qt-4-1st-ed.zip)

Nokia even released an IDE called Qt Creator, which I'm now using on Windows, Mac, and Linux. It has code completion, debugging tools, and built-in support for Perforce, SVN and Git.

> Is it possible that I can develop the application in linux,then simply port it over to windows?Or do I have to recode everything in windows?

If you use Qt, chances are that you won't write a single platform-specific line of code.

---

### Post by .Maleficus. on 2009-02-25
+1 for Qt.  scourge pretty much summed up everything in his post, but in any case, it's cross platform, has tools for just about everything (networking, GUI, Phonon for multimedia) and has libraries/wrappers for most major languages (C++, Python, Ruby, the list goes on).

---

### Post by remy06 on 2009-02-26
Thanks for the recommendation.

Just to clarify abit,does that mean if the application is created using Qt in linux,it is able to run in windows?

By the way,because I'm not sure if these tools can be used for my project yet(need to seek approval),is it possible to code GUI with just C/C++?

---

### Post by AcidHawk on 2009-02-26
For maximum portability my company uses Java.  You can use Netbeans or Eclipse as the IDE and it will run on anything that has a java runtime.  Very little to no porting, unless you are using os specific functions this is.

Oh, and both Netbeans and Eclipse run on both linux and windows, so if you start developing on linux and want to change half way through to windows it is a simple copy of the project from one platform to the other.

---

### Post by s1ightcrazed on 2009-02-26
How 'pretty' does it need to be? If this is just going to be a simple utility that doesn't need to be esthetically pleasing then I would suggest something like python/Tkinter (Tk bingings). For more complex projects that need to integrate into the desktop then I would second the C++/QT suggestions made by others.

---

### Post by soltanis on 2009-02-26
By the way, no one has suggested it yet so maybe I skimmed your post too quickly, but you should use libpcap for packet capturing. For cross-platform GUIage, Qt is the best option, as mentioned.

---

### Post by scourge on 2009-02-26
> **remy06 said:**
> Just to clarify abit,does that mean if the application is created using Qt in linux,it is able to run in windows?

Yes, you just need to compile the sources, and it will run on Windows and have the look and feel of a Windows app as well.

> By the way,because I'm not sure if these tools can be used for my project yet(need to seek approval),is it possible to code GUI with just C/C++?

If you mean pure ISO C or C++ with no 3rd party libraries, then no, it's not possible.

---

### Post by skirkpatrick on 2009-02-26
Well, I have to disagree with the comment about wxWidgets, probably because I'm using it.

I've written several programs for our networked system that passes data around between the programs running on the same or different computers.  One of my programs that interfaces with a factory floor machine, communicates with an ODBC database, has a local UI, and has a built-in webserver for a remote UI results in a 3MB statically linked executable for Windows.

I use Eclipse for my development with MinGW for the compiler toolchain on Windows and simply recompile it under Linux with GCC.  I've even built it for ARM Linux to run on a small embedded computer with a touchscreen interface.

---

### Post by scourge on 2009-02-26
> **skirkpatrick said:**
> Well, I have to disagree with the comment about wxWidgets, probably because I'm using it.

You mean the comment about wxWidgets being nasty? If so, my point still stands. Based on my personal experience, here's just a few reasons to choose Qt over wxWidgets:

- It's way easier to create and compile projects with Qmake than with cmake, bakefiles, hand-crafted makefiles, or whatever else you may use with wxWidgets.
- Signals and Slots are a safer, easier to use, and more flexible way of having objects communicate with each other.
- Qt's documentation is far superior to wxWidgets'.
- wxWidgets isn't as cross-platform as one would assume. Even something as simple as application menus can work fine on one platform, but fail on others (especially on a Mac). Graphics programming is another area where I found it difficult to get the same results on all target platforms. Qt has very high-level but still high-performance widgets like QGraphicsView. There's nothing like that for wxWidgets.
- Qt Designer vs. Glade/wxDesigner/etc. Easy win for Qt Designer.

Seriously, why would anyone choose wxWidgets over Qt, especially now that Qt is licensed under the LGPL? I've yet to meet anyone who's tried both frameworks and prefers wxWidgets. And if I do, I'd love to hear what makes wxWidgets so great.

---

### Post by OutOfReach on 2009-02-26
Another +1 for Qt, plus it's API is much easier to understand than GTK's IMO.

---

### Post by HotCupOfJava on 2009-02-26
+1 for Java. If the virtual machine is installed on both platforms, you're good to go. The Swing classes give you great GUI functionality, and can even be customized to look like the native windowing system. If you don't have alot of experience with Java, an IDE like Netbeans can go a long way toward helping you with the GUI stuff.

---

### Post by mmix on 2009-03-08
Gtk+ 2.x is enough.

Showcase is here: [http://www.wireshark.org/](http://www.wireshark.org/)

---

### Post by jimi_hendrix on 2009-03-08
does it need to be C/C++? in higher level languages like python you can be reading from a socket in 3 lines

---

### Post by remy06 on 2009-03-29
yeah.cause we are more familiar with C/C++,and with the tight schedule,i doubt we can attempt to familiarize with other languages at the moment.

---

### Post by jimi_hendrix on 2009-03-29
You can use QT, wxWidget and GTK then i guess

---

### Post by nvteighen on 2009-03-29
Keep in mind Qt has no C bindings! If you want Qt, then, you better know how you're going to use your C code or you may find yourself trapped.

---

### Post by jimi_hendrix on 2009-03-29
> **nvteighen said:**
> Keep in mind Qt has no C bindings! If you want Qt, then, you better know how you're going to use your C code or you may find yourself trapped.

wxWidget doesnt have C bindings either i think

---

### Post by nvteighen on 2009-03-29
> **jimi_hendrix said:**
> wxWidget doesnt have C bindings either i think
You're right.

---

### Post by ZuLuuuuuu on 2009-03-29
GTK+ is complete, actually, but it doesn't aim to be what Qt is (at least for now). So it does not have sockets. If you are familiar with C++ and need sockets + GUI and does not need C bindings then Qt is very well suited for you. I looked at wxWidgets some time ago and it's API was veeeery ugly, it is a macro heaven if you like macros (I don't like using macros all over the code)... GTK+ is very elegant and has C/C++ (and many other) bindings. If you need C bindings then you have to go with GTK+ and some other library for sockets.

---

### Post by kknd on 2009-03-29
I use GTK on a fairly large application for both Windows and Linux. There are some issues on Windows, but 97% of things works as expected.

QT works flawlessly on both systems, so choose the one you like most.

---

