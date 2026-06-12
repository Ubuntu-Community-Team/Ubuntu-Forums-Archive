---
title: "Programming Language good for standalone App with embedded Database"
date: 2011-04-09
forum: Programming Talk
---

### Post by jao_madn on 2011-04-09
Hi,  I would like to ask for someone more experience in programming, May i ask on where do i start or what langguage should i start inorder to create an APPS with nice GUI front end for visual display and a embedded Database in backend for records purposes, a stand alone apps, for example i want to create an apps with  a nice gui in linux and has an input using a barcode reader and check the barcode in the embedded DB if it is valid or invalid and report any output in a Nice GUI for visual confirmation and in the DB. A gui function or menu also to input data and generate report to the DB for records along with the details of that barcode.  Thanks for any reply.

---

### Post by simeon87 on 2011-04-09
Python + SQLite seems a good choice for this application. It's easy, simple and it allows you to embed a database in an application. For the GUI you could use Gtk or Qt. An added benefit is that Python is well-supported on Linux.

---

### Post by cgroza on 2011-04-09
For a GUI toolkit, I recommend wxPython.

---

### Post by jao_madn on 2011-04-09
Thanks for the reply..  I stumble accross this Quirkly ubuntu program its for GUI building right. How about this one..but i don't find a good ebooks for this apps seems python and gtk+ and sqlite lite has many ebooks tutorials around. or else someone knows others please recommend..im new one and willing to spend time and learn to accomplished my apps gools.  Thanks for any reply.

---

### Post by llanitedave on 2011-04-09
I don't know anything about Quirkly.  But I'm now doing exactly what you're asking about:  Building a standalone application with an embedded database.  And what's been recommended is just what I'm doing.  I'm using Python and SQLite3, because that is a library that already comes with Python.  I'm using wxPython for the GUI.  The only downside to wxPython is that it limits you to Python 2.x instead of being able to use the current Python 3.  However, the end result is very professional looking, since it uses your platform's native widgets to create fields, windows, buttons, and dialogs.

Don't kid yourself.  Building a user-friendly GUI is hard work.  Python itself is pretty easy to learn and works well, but whatever GUI builder you end up using, there are a lot of details to consider that aren't obvious at first.  There is no such thing as an EasyGUI, even if there are apps with that name.  It's not so much a programming challenge as a conceptual design challenge.
WxPython at least has very good and nearly complete documentation that is pretty easy to find.

---

### Post by Jonas thomas on 2011-04-09
I haven't played around with Mono Develop too much. Perhaps someone who has can comment on this
Monodevelop is the open source IDE for C#.  Last time I researched linux database/Mono a year or two ago  I wasn't too impressed the database stuff.  I just did a quick google and it appears that things may have moved along a bit.
[http://monodevelop.com/Documentation/Database_Addin]("http://monodevelop.com/Documentation/Database_Addin")

---

### Post by slavik on 2011-04-10
Anything + SQlite/GTK/QT

---

### Post by ukripper on 2011-04-11
If only doing GUI python programming for ubuntu -- > Quickly is the quickest and better suited. However Python, wxpython and SQLITE will do the job for bit more complex. 

How to Quickly:
[http://screencasts.ubuntu.com/taxonomy/term/86](http://screencasts.ubuntu.com/taxonomy/term/86) 
[http://www.youtube.com/watch?v=9EctXzH2dss](http://www.youtube.com/watch?v=9EctXzH2dss)





.

---

### Post by jao_madn on 2011-04-11
> **llanitedave said:**
> I don't know anything about Quirkly.  But I'm now doing exactly what you're asking about:  Building a standalone application with an embedded database.  And what's been recommended is just what I'm doing.  I'm using Python and SQLite3, because that is a library that already comes with Python.  I'm using wxPython for the GUI.  The only downside to wxPython is that it limits you to Python 2.x instead of being able to use the current Python 3.  However, the end result is very professional looking, since it uses your platform's native widgets to create fields, windows, buttons, and dialogs.

Don't kid yourself.  Building a user-friendly GUI is hard work.  Python itself is pretty easy to learn and works well, but whatever GUI builder you end up using, there are a lot of details to consider that aren't obvious at first.  There is no such thing as an EasyGUI, even if there are apps with that name.  It's not so much a programming challenge as a conceptual design challenge.
WxPython at least has very good and nearly complete documentation that is pretty easy to find.

 @llanitdave: Thanks for the interest, information and knowledge you share. Can you share the apps you just made if you don't mine.

---

### Post by juancarlospaco on 2011-04-11
Python + SQLite

---

### Post by deathadder on 2011-04-11
SQLite is a nice fast database to use in standalone applications. There's dozens of GUI's around to create the schema you want and interfaces for pretty much any language you would want (C/C++/Java/Python/Perl/C#).

At the moment I'm developing a GUI in C# using SQLite and I have to say it's much easier than some alternative data storage possibilities (XML etc). 

But yeah, anything and SQLite is the way to go! :)

---

### Post by llanitedave on 2011-04-11
> **jao_madn said:**
> @llanitdave: Thanks for the interest, information and knowledge you share. Can you share the apps you just made if you don't mine.

Nothing to share yet -- it's still under construction.  I've got a long way to go.  But I'll be glad to when it's done.

---

### Post by safarin on 2011-04-12
Good information, I also need to do GUI with databases soon but don't have basic knowledge/programming in Python/SQLite. I will keep eye on this thread and will share information if I have later.

Can system programming combine with GUI and databases? I use C programming for system, taking data from sensors and need to control the output using system and GUI.

---

### Post by deathadder on 2011-04-12
@safarin - There's no reason why not no, there's bindings for [SQLite in C]("http://www.sqlite.org/c3ref/intro.html") so you can simply pass the data from your sensors through to a database function that inserts the data and have a GUI polling the database. 

You'd probably want a separate GUI app though to make things simpler. So you have a server / client approach, where the server (sensor) grabs data and writes it to the database. Then your client (GUI) can read the information from the database. You also wouldn't be limited to C for the GUI (not my favourite language for GUIs).

---

### Post by safarin on 2011-04-12
> **deathadder said:**
> @safarin - There's no reason why not no, there's bindings for [SQLite in C]("http://www.sqlite.org/c3ref/intro.html") so you can simply pass the data from your sensors through to a database function that inserts the data and have a GUI polling the database. 

You'd probably want a separate GUI app though to make things simpler. So you have a server / client approach, where the server (sensor) grabs data and writes it to the database. Then your client (GUI) can read the information from the database. You also wouldn't be limited to C for the GUI (not my favourite language for GUIs).

Wow~!! I never know about this binding.. honestly, I still newbie in C programming... If you don't mind.. Could you please give me keywords for me to "googling" or some link that could help me or other guys like me.. ;)

Thank you deathadder.

Edit: Sorry.. You also include a link with your post.. I just noticed it. :P

---

### Post by deathadder on 2011-04-12
Without wanting to take over a thread, bindings or wrappers for a language is another way of describing a library. 

So, if you want to develope a SQLite database application in C you need to know if there is a library that will translate your C into something the database understands (basically). You would then Google for "sqlite wrapper language" or "sqlite bindings language" where language is C (in this case) or Python/Java/any other language.

If you knew you wanted to use SQLite, but weren't sure on what language to do your development in you could Google for "sqlite bindings". The second hit of which takes you here: [http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers](http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers)

You can repreat this for most technology, if you want to develop against GTK/XML/etc.

---

### Post by safarin on 2011-04-12
@deathadder
Thank you for sharing. New knowledge for me! :D

---

### Post by directhex on 2011-04-12
> **deathadder said:**
> Without wanting to take over a thread, bindings or wrappers for a language is another way of describing a library. 

So, if you want to develope a SQLite database application in C you need to know if there is a library that will translate your C into something the database understands (basically). You would then Google for "sqlite wrapper language" or "sqlite bindings language" where language is C (in this case) or Python/Java/any other language.

If you knew you wanted to use SQLite, but weren't sure on what language to do your development in you could Google for "sqlite bindings". The second hit of which takes you here: [http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers](http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers)

You can repreat this for most technology, if you want to develop against GTK/XML/etc.

This isn't really the commonly used terminology.

A library provides functionality, directly in a given language - for example, libsqlite3-0 is a library, written in C. When you use it in C, you refer to it as a library. launchpadlib is a library written in Python. When you use it in Python, you refer to it as a library.

A "wrapper" or "binding" is a layer which allows you to use a library using the "wrong" programming language - for example, GTK# is a Mono binding for the C-based GTK+ library. libqt4-ruby are Ruby bindings for the C++-based Qt.

The term to use for the standard SQLite library is definitely "library" if you're using C. If you're using a non-C language which wraps the C library, that's a binding. And if you're using a reimplementation in a non-C language (such as the fully C#-based csharp-sqlite) then you call it a library again.

The distinction in language is considered important because it portrays the (potentially slow) added layer of abstraction involved.

---

### Post by JacksSmith on 2011-04-13
For Linux operating system the Python is the best in creating nice GUI with SQLite for embedded database.

---

### Post by slavik on 2011-04-13
> **JacksSmith said:**
> For Linux operating system the Python is the best in creating nice GUI with SQLite for embedded database.
I disagree. Perl is better than Python for creating a nice GUI with SQLite for embedded database.

---

### Post by deathadder on 2011-04-13
> **directhex said:**
> This isn't really the commonly used terminology.
Sorry, I wasn't very clear on what I was trying to say there. Let me try again now I've got a little more time...

bindings or wrappers for a language is another way of describing a translation library.

So, if you want to develope a SQLite database application in Python you need to know if there are wrappers that will translate your Python into something the database understands (basically). You would then Google for "sqlite wrapper language" or "sqlite bindings language" where language is Python (in this case) or C#/Java/any other language. 

If you knew you wanted to use SQLite, but weren't sure on what language to do your development in you could Google for "sqlite bindings". The second hit of which takes you here: [http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers](http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers)

You can repreat this for most technology, if you want to develop against GTK/XML/etc. 

directhex is absolutley right in pointing out that a library is written in the same language as the original application while wrappers/bindings are used to hook another language into it. So they are translating and therefore can suffer performance issues. 

Also, my example of SQLite and C is a bad one because SQLite is actually written C so it's a library, I've modified that to make a little more sense.

---

### Post by slavik on 2011-04-13
> **deathadder said:**
> Sorry, I wasn't very clear on what I was trying to say there. Let me try again now I've got a little more time...

bindings or wrappers for a language is another way of describing a translation library.

So, if you want to develope a SQLite database application in Python you need to know if there are wrappers that will translate your Python into something the database understands (basically). You would then Google for "sqlite wrapper language" or "sqlite bindings language" where language is Python (in this case) or C#/Java/any other language. 

If you knew you wanted to use SQLite, but weren't sure on what language to do your development in you could Google for "sqlite bindings". The second hit of which takes you here: [http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers](http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers)

You can repreat this for most technology, if you want to develop against GTK/XML/etc. 

directhex is absolutley right in pointing out that a library is written in the same language as the original application while wrappers/bindings are used to hook another language into it. So they are translating and therefore can suffer performance issues. 

Also, my example of SQLite and C is a bad one because SQLite is actually written C so it's a library, I've modified that to make a little more sense.
This is the reason OpenGL performs very poorly when called from Python ;)

---

### Post by directhex on 2011-04-13
> **JacksSmith said:**
> For Linux operating system the Python is the best in creating nice GUI with SQLite for embedded database.

It's a pretty subjective matter. It's really down to the dev as to what makes them productive. I work very poorly in Python, for example

---

### Post by ukripper on 2011-04-14
Right tool for right job!

---

### Post by jao_madn on 2011-04-16
I hope someone post there finish apps. Its much better to know while studying the language theres a reference or motivation since you are looking to a working apps.  Thanks.

---

