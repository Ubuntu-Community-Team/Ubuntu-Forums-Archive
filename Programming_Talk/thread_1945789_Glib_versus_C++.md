---
title: "Glib versus C++ ?"
date: 2012-03-23
forum: Programming Talk
---

### Post by TheHimself on 2012-03-23
For you, what are the pros and cons? Glib seems to give one more control (is more "low level") but its syntax is not as neat as C++. For example when I use GTK with C, I have to convert pointer types all the time and its easy to make mistakes which are not detected by the compiler.

On the other hand GNU, which I admire, does not seem to use C++.

Maybe a better alternative to both of them is Vala?

---

### Post by satsujinka on 2012-03-23
What are you doing that requires you to cast pointers all the time?

---

### Post by TheHimself on 2012-03-24
OK, maybe not literally al the time but since the pointers to widgets are of type "gtk_widget *", when I want to  pass them to a function that is designed for a specific type of widget (say gtk_dialogue), I have to recast the pointer.

Anyway, any answers to my question?

---

### Post by ibuclaw on 2012-03-24
> **TheHimself said:**
> On the other hand GNU, which I admire, does not seem to use C++.

GCC does have a C++ compiler, it is however conspicuously named g++. :)

---

### Post by r-senior on 2012-03-24
I don't have an answer, but another question.

What's your objective? Are you considering Glib as an alternative to the C++ STL? What are you writing?

Did you know there is also a glibmm (and gtkmm), which are C++ wrappers around glib (and Gtk3)? These avoid a lot of that casting that you have to do in C with GTK. I've dabbled with gtkmm and it was a lot more palatable to me than C and GTK.

But if you want productivity and simplicity, Python and Vala are worth looking at for GUI programming. I don't know Vala but with Python that Glib-type functionality is part of the standard library and you can use GObject introspection to tap into libraries like GTK3 and Pango.

---

### Post by ysangkok on 2012-03-24
This is a religious discussion and you should probably just try and code some sample programs in everything and see what you like best. People discuss this stuff so much, it's ridiculous.

Check this out: [http://stackoverflow.com/questions/296992/glib-v-apr-pros-and-cons-of-each](http://stackoverflow.com/questions/296992/glib-v-apr-pros-and-cons-of-each)

Anyway, IMHO, with C++11 out, you can do a lot just using that. GNU uses C because UNIX uses C, it's all historical. C++ didn't exist back then. Yes, you can do everything with Glib, but IMHO void* and the like are not pretty.

Vala is a bit of a hack and it's not widely used and it uses source-level translation.

And again: the reason you're asking this question is because you don't see a clear answer online. And the reason you don't see a clear answer is that there isn't one universal answer. Also, see r-senior's reply.

I always try and get away with using the most high-level language. No reason to fiddle with manual memory allocation if your application doesn't have strict performance requirements that require that level of control.

---

### Post by MG&amp;TL on 2012-03-24
> **ysangkok said:**
> 

Vala is a bit of a hack and it's not widely used and it uses source-level translation.

And again: the reason you're asking this question is because you don't see a clear answer online. And the reason you don't see a clear answer is that there isn't one universal answer. Also, see r-senior's reply.



Disagree, agree. While it's true that vala compiles to C first, sometimes that's very convenient. Also, it has some excellent documentation over at [http://valadoc.org]("http://valadoc.org/") .

---

### Post by giowck on 2012-03-24
> **MG&TL said:**
> Disagree, agree. While it's true that vala compiles to C first, sometimes that's very convenient. Also, it has some excellent documentation over at [http://valadoc.org]("http://valadoc.org/") .

that's not a good doc. Look at Qt for reference. That's how doc should be done :P

---

### Post by ysangkok on 2012-03-24
> **MG&TL said:**
> Disagree, agree. While it's true that vala compiles to C first, sometimes that's very convenient. Also, it has some excellent documentation over at [http://valadoc.org]("http://valadoc.org/") .

I'm sure there are good docs for Vala somewhere, but that site didn't give me a good impression. Why are third party libraries on the front page? Anyway I tried clicking a few (v4l2, xcb, purple) and there were only signatures, no actual documentation.

Anyway, while lack of popularity alone shouldn't keep you from using a good language, I don't see why we can't get a clean break from the glorified assembler variant that is C. That alone is enough for me to disqualify Vala for many use cases. Not that I don't like fooling around in assembler! It just doesn't actually make sense most of the time.

How does debugging with Vala work? Can GDB reverse both steps and show me a backtrace with Vala source code?

If I really needed a compiled C-like language (for a hobby project, that is!), I'd go with D now. If you're doing enterprise software, it's not your decision, but I'm pretty sure they wouldn't use Vala either :P

---

### Post by MG&amp;TL on 2012-03-24
Okay, you win on that one. :P

Valadoc is for third-party libraries-Gtk and such, which is what it is designed for. You can find documentation for vala on the gnome website, dodgy though it is.

Yes, gdb works for vala, albeit a little weirdly sometimes.

---

### Post by satsujinka on 2012-03-24
> **ysangkok said:**
> I'm sure there are good docs for Vala somewhere, but that site didn't give me a good impression. Why are third party libraries on the front page? Anyway I tried clicking a few (v4l2, xcb, purple) and there were only signatures, no actual documentation.

Anyway, while lack of popularity alone shouldn't keep you from using a good language, I don't see why we can't get a clean break from the glorified assembler variant that is C. That alone is enough for me to disqualify Vala for many use cases. Not that I don't like fooling around in assembler! It just doesn't actually make sense most of the time.

How does debugging with Vala work? Can GDB reverse both steps and show me a backtrace with Vala source code?

If I really needed a compiled C-like language (for a hobby project, that is!), I'd go with D now. If you're doing enterprise software, it's not your decision, but I'm pretty sure they wouldn't use Vala either :P
If you want a clean break with C, then C++ is definitely not an option. :lolflag:

Which isn't to say that Vala is a good language. Certainly as a competitor to java or C#I'd consider it, but both of those languages aren't very fun to work with in the first place.

Business wise, scala, clojure, or some other JVM/.net languages is going to get used (I'll probably never understand why you'd want to use .net, but the JVM is a wonderful target for portability.)

For fun, go or Haskell are probably my favorites. Haskell has a gtk+ binding (go's is experimental) that works well, but isn't gtk+3 ready.

I consider D every now and then, but nothing about it stands out to me.

---

### Post by ysangkok on 2012-03-24
> **satsujinka said:**
> I'll probably never understand why you'd want to use .net

This thread has got to break some kind of record on the number of cans of beans opened. Anyway.

Tell me you can't find some items in [this table]("http://en.wikipedia.org/wiki/Comparison_of_C_Sharp_and_Java#Feature_comparison") that C# has that Java hasn't.

---

### Post by satsujinka on 2012-03-24
> **ysangkok said:**
> This thread has got to break some kind of record on the number of cans of beans opened. Anyway.

Tell me you can't find some items in [this table]("http://en.wikipedia.org/wiki/Comparison_of_C_Sharp_and_Java#Feature_comparison") that C# has that Java hasn't.

Java isn't the only JVM language available. So it really doesn't matter if C# has more features (ignoring the possibility that more features != better language.) Besides, I don't like either language very much.

---

### Post by TheHimself on 2012-03-30
Thanks for your replies. I specially found ysangkok's andr-senior's response helpful. Yes, it's better to try some languages for sample programs and see which ones suit one's purpose. 
I do programming as a hobby but am unreasonably concerned about performance!

---

### Post by ofnuts on 2012-03-30
> **ysangkok said:**
> This thread has got to break some kind of record on the number of cans of beans opened. Anyway.

Tell me you can't find some items in [this table]("http://en.wikipedia.org/wiki/Comparison_of_C_Sharp_and_Java#Feature_comparison") that C# has that Java hasn't.
This table says Java hasn't got pointers. 

[http://geekandpoke.typepad.com/.a/6a00d8341d3df553ef013488e672ee970c-800wi](http://geekandpoke.typepad.com/.a/6a00d8341d3df553ef013488e672ee970c-800wi)

---

### Post by nvteighen on 2012-03-30
Entering the discussion late, but let me state my point about GLib vs. C++:

You're discussing two completely different things. GLib is a library, C++ is a language. The main difference is that GLib actually only makes sense if you need OOP abstraction in C and you need C for some extrinsic reason you can't control. I don't know... you're working on a project where you need to rely on some specific C feature (I can think on a couple of them: standard ABI, easier interfacing with other languages, memory footprint... hatred against C++ :D).

On the other hand, if you want GLib only because you need OOP and structures like GList... then the most reasonable option is to switch to another language. I wouldn't recommend C++ because I consider it a terrible language (no, I won't discuss this again here)... and it won't save you too much from pointer castings :P However, C++ may work for you regardless of my opinions. Python, Perl, some Lisp, Javascript, Java are interesting options in my opinion.

If you're dealing with GTK+, then you're doomed to some GLib stuff, for obvious reasons. However, Python and PyGtk or some other high-level language with GTK+ bindings abstract all that stuff very well, so that's an option to consider.

Qt or wxWidgets are not an option if you want to stick with C.

---

### Post by TheHimself on 2012-04-01
> **nvteighen said:**
> Entering the discussion late, but let me state my point about GLib vs. C++:

You're discussing two completely different things. GLib is a library, C++ is a language. The main difference is that GLib actually only makes sense if you need OOP abstraction in C and you need C for some extrinsic reason you can't control. I don't know... you're working on a project where you need to rely on some specific C feature (I can think on a couple of them: standard ABI, easier interfacing with other languages, memory footprint... hatred against C++ :D).

On the other hand, if you want GLib only because you need OOP and structures like GList... then the most reasonable option is to switch to another language. I wouldn't recommend C++ because I consider it a terrible language (no, I won't discuss this again here)... and it won't save you too much from pointer castings :P However, C++ may work for you regardless of my opinions. Python, Perl, some Lisp, Javascript, Java are interesting options in my opinion.

If you're dealing with GTK+, then you're doomed to some GLib stuff, for obvious reasons. However, Python and PyGtk or some other high-level language with GTK+ bindings abstract all that stuff very well, so that's an option to consider.

Qt or wxWidgets are not an option if you want to stick with C.


OK, I meant "C plus Glib versus C++". I share some of your negative opinion on C++ however Python is not as fast as C or C++. Also about Java, I don't know any great applications written in Java (maybe just my own ignorance); I know OpenOffice but again it's not that fast neither eye-catching.

---

### Post by r-senior on 2012-04-01
Python is fast enough for a GUI application and you can always write critical sections in C.

[http://en.wikipedia.org/wiki/List_of_Python_software](http://en.wikipedia.org/wiki/List_of_Python_software)

It would probably help if you gave us an idea of what you plan on writing?

---

### Post by TheHimself on 2012-04-02
One thing I want to write is a pdf organizer (and viewer). Something like Mendeley desktop. Another thing I've already written is a photo management software. It's in C and uses GTK and the exiv2 application (not the library). When I started working on it more than 2 years ago, I didn't know about Shotwell. It still lacks some important features (it supports a prescribed set of tags and uses an ad hoc database system). Maybe someday I put it on Launchpad.

---

### Post by r-senior on 2012-04-02
I'm primarily a Java and Objective-C programmer but I've done quite a lot in C and dabbled with C++. For writing GUI applications for Linux I've tried Java with GTK bindings, C/GTK+ and C++/gtkmm.

I'm not what you'd call a Python fanboy. ;)

But I got drawn into Python for writing GUI apps and, despite not really knowing the language in comparison to Java and the C family of languages, I find Python with GTK bindings of some sort the most productive way to write native GNOME applications. It's just so easy in comparison to C/GTK or C++/gtkmm.

I understand wanting to have the speed of C/C++ because Python is comparatively slow, but when you use bindings into GTK, you don't notice. Python acts as more of a controller and all the GUI stuff is fast and responsive because it's written in C with a thin wrapper around it.

I'm not going to keep going on about Python, but if you want to try a few examples,the tutorial is pretty good:

[http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html)

---

### Post by eric-yorba on 2012-04-02
> **TheHimself said:**
> OK, I meant "C plus Glib versus C++".
That's a really weird comparison.  C++ doesn't have any concept of a standard main loop, asynchronous methods, signals, introspection, closures, etc.  GLib has a crapload of utilities and system calls that no C++ standard library has.

Seems to me if you want to do GLib programming you're better off with Vala and/or Python.  But if you really want to do C++ in the G-Object world, you should take a look at GtkMM.

---

