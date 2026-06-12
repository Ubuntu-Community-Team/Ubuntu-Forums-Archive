---
title: "I'm programming on Windows, I want to program for Ubuntu on Ubuntu"
date: 2007-01-02
forum: Programming Talk
---

### Post by Ubempi on 2007-01-02
Hi there!

I'm a newbie in what refers to Ubuntu (and Linux in general). 
I'm a Windows programmer with little experience.

I'm wondering where can I start to make an application I'm currently building with SharpDevelop (+ MySQL) on Windows.

I'm trying to make something to register all the movements on my kind-of-Kiosk.

Nothing too big but my principal concern is about easiness, so I want to control each keystroke and the focus on all of what is seen (or not) on screen. It would be better if I can put some animations on the interface.

It needs to be easy because it will be mostly used by my mother.

I'm starting with the well known textboxes and filling listviews for the products and that stuff, managing keydown events (SharpDevelop is for .NET).

But doesn't seem to convince me. I'll try again but this time I want to switch to Ubuntu.

Which language should I start with? Which IDE?

Thanks in advance and sorry for my English.

---

### Post by DavidBell on 2007-01-02
I would suggest either

Code::Blocks nightly build with wxWidgets, C::B is a C++ IDE with wxWidgets built in. wxWidgets is crossplatform GUI and other stuff, I have found wxW good for transistion to linux because C++ compiles more or less without changes between MS Vis Studio, C::B (windows), C::B (linux), wxHatch (linux), also I guess Eclipse, Netbeans, so you can move over gradually. Downside is C++ is a bit lower level than C# so may be not your thing.

Java with Eclipse or Netbeans, again cross platform. Java is closer to C# (I think Sun threatened to sue MS). I had a look at both IDEs, didn't like Eclipse at all, thought Netbeans looked quite nice with good integration with GUI designer and code editors.

C# programs can also run in linux *in theory* via the Mono project, but don't really know enough about it to say if theory and practice are aligned.

DB

---

### Post by pmasiar on 2007-01-02
You forgot to mention your preferred language. Is it C++? 

For people with little programming experience, I always recommend Python as first programming language. It comes with IDE, called IDLE. WxPython is popular GUI thing (which i don't use).

You can get up to speed coding faster in python than in C/C++/java, especially if you are beginner. If you can code in C++ a little, you will be surprised how much simpler Python is ;-)

If you don't need real database server with multiple users and stuff, python comes with sqlite - single-user database library (not a server), simpler to use than MySQL.

If it is for your mother, another option could be bunch of command-line programs started from icons, each doing some part of your app. I have no idea what you want to do, so it is just wild guess. Good luck!

---

### Post by kalikiana on 2007-01-02
I recommend Python - not only for beginners. It's easy and uncomplicated, also very portable.
If you want to use it for Windows choose either pyGtk or wxWidgets, since qt is commercial on Win32.

---

### Post by Mirrorball on 2007-01-03
Qt is free on Windows for free programs. It's only commercial for commercial programs.

---

### Post by mallo on 2007-01-03
Nobody cited [Anjuta]("http://anjuta.sourceforge.net/") a beautiful IDE for C, C++, and now Java, python (I used it for C++).

If you want to read about GTK programming look at: [www.gtk.org](www.gtk.org) and have a look to glade project and libglade (With glade and libglade you can build a nice gui and integrate it in a very simply way in your programs).

If you like shell try to build some dialogs using zenity (zenity --help) I like it very much :).

---

### Post by Ubempi on 2007-01-03
Thanks to all! good information...

I think I'll use Python because I need to finish it as soon as posible.

Now I'm on Ubuntu 6.10 (I was on Windows before). I'm impressed, this was easy a lot, configuring the Internet connection, the video playing is as smooth as in Windows (i use vlc on both and the last version has it all: on a fresh installation of Ubuntu -> sudo apt-get install vlc <- with the main server for Universe and Multiverse repositories and you can play all types of video and audio, one command, thats all ;)

back into this post... Thanks again!

---

