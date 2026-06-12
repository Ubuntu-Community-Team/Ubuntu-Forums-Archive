---
title: "Developing GUI applications for ubuntu and gnome"
date: 2010-04-16
forum: Programming Talk
---

### Post by Systix on 2010-04-16
Hello,

I am interested in learning to developing my own small graphical user interface applications for Ubuntu. 

I am not new to programming, I have written many Visual basic.net applications for windows and command line programs for linux in Python and C, But never GUI's...

What programming languages and IDE environments (if any) would you recommend?

What set of libraries are the best for developing gnome GUI's? (Ive heard GTK dotted around the place).


Thanks :)

---

### Post by AgentWD-40 on 2010-04-16
I'm studying the same stuff right now. I'm using Glade to put together interfaces and using code::blocks for my IDE. Mostly I've just been messing around so far, but I'm looking to buy a book on GTK+ development soon.

---

### Post by cmat on 2010-04-16
If you want to make nice GUIs and want and extensive amount of controls available wxPython fits the bill. There are many applications in Ubuntu written with it. You can also use wxGlade in the repos to build source files for Python and many other languages.

Here's some tutorials for wxPython, [http://zetcode.com/wxpython/](http://zetcode.com/wxpython/)

wxWindows, which wxPython is derived from is for C++ if you want to use C++. wxPython uses native toolkits installed on the system so you can make cross=platform applications too without changing your code. A database client I wrote worked without modification on Windows and Ubuntu.

---

### Post by wojox on 2010-04-16
Ceck out [Anjuta]("http://projects.gnome.org/anjuta/") . It's in the repo's.

---

### Post by AgentWD-40 on 2010-04-16
Anjuta looks pretty cool! I think I'll give that one a try this weekend. How well does it integrate with Glade?

---

### Post by jase21 on 2010-04-17
GTK and Qt are two popular GUI libraries.

---

### Post by phrostbyte on 2010-04-17
Gnome uses GTK+ and KDE uses Qt. Since "Ubuntu" uses Gnome, most desktop apps are written in GTK+ for "Ubuntu". (ie. not "Kubuntu", the KDE variant).

GTK+ has an absurd number of bindings for almost every language you'd care to use. :) Even VB.NET, although C# is a better choice under Linux (more advanced compiler/tooling).

Most apps written specifically for Ubuntu are written in Python, because it is the preferred language of Canonical. Python has extremely good tooling in Ubuntu and there are a wealth of resources on how to develop GUI apps in Python. It's also a very easy language to learn.

---

