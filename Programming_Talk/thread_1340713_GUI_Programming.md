---
title: "GUI Programming"
date: 2009-11-28
forum: Programming Talk
---

### Post by ColdLunch on 2009-11-28
Hello!  I am pretty knowledgeable of a few languages: Python, C++, and Java.

Which language (not necessarily of these three) would be best for GUI programming?  

Thanks.

---

### Post by qalimas on 2009-11-28
I can't speak for Java or C++, I'm a web developer who is just now learning Python.  I find PyQt to be pretty nice.  I'm catching on well and I've never done any GUI apps before (aside from VB back in 2000).  So I'd think it a good place to start :)

---

### Post by jollysnowman on 2009-11-28
Take a look at what popular Linux apps are written in, and you'll see a lot of C/C++.

---

### Post by TennTux on 2009-11-28
Knowing C, C++, Java and a couple of others, I believe there are some basic questions you need to ask yourself first. Who will be using the app and what will it do. This may narrow your choices some.

Java will run on many platforms can be used for Stand-alone apps and in a browser Applets, and of course these would likely use the Swing Set of libraries that come with Java. However, with Java the code is generally available to the end user. There is obfuscation and other techniques, but you have to keep this in mind. Another issue with Java is that it sometimes is slow to start or may not be as zippy as C/C++, due to its interpreted nature, but once it's running in all but runtime environments it performs quite well. And there are extensions for runtime environments that may allow it to do what you need there too.

C/C++ does not in and of itself have GUI, so you will have to use a set of secondary libraries. On MS-Winxxxx this could be the Win SDK, MFC or .NET. There are some libraries like Qt that are cross-platform compatible. You do have to make sure that the libraries are supported on all the platforms you will be running on. And for running in various flavors and windowing systems on Linux there are specific libraries like Gnome and it's associated toolkit.

Depending on what your doing Client/Server using HTML with or without scripting may also be an option. Maybe even enhanced with some Applets,  ActiveX controls or other insitu compiled controls.

Putting the technical considerations aside, I like Java/Swing. It's well thought out, simple enough for someone without too much experience to use but doesn't prevent advanced users from doing what they want/need to do. And when worse comes to worse you can use JNI to decend to native code, perhaps written in C++.

Hope this helps.

---

### Post by ColdLunch on 2009-11-29
What python gui toolkit should I go with if I'm just a beginner?

---

### Post by WakkiTabakki on 2009-11-29
> **ColdLunch said:**
> What python gui toolkit should I go with if I'm just a beginner?
Glade for building a UI (you don't really want to code the UI, right?) and connect to it with pygtk. Check these tutorials out:

[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)
[http://www.overclock.net/application-programming/342279-tutorial-using-python-glade-create-simple.html](http://www.overclock.net/application-programming/342279-tutorial-using-python-glade-create-simple.html)

This one's "quite" thorough
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

/N

---

### Post by Virtual Liberty on 2009-11-29
Ruby and GTK+ :-\"

---

### Post by nvteighen on 2009-11-29
GUI programming is always hard and not meant for beginners. GTK+ is nice because it's a very well-planned API. My Qt experience is very limited and only through PyQt... I liked it too, but have not enough experience to have opinion on it.

The issue here is that while Python + GTK+ is a great combination because it allws you to quickly build an application without having to deal with lots of nasty details, it also incorporates some C-ish ways into Python code... something that sometomes can be a bit annoying.

---

### Post by Can+~ on 2009-11-29
> **nvteighen said:**
> GUI programming is always hard and not meant for beginners. GTK+ is nice because it's a very well-planned API. My Qt experience is very limited and only through PyQt... I liked it too, but have not enough experience to have opinion on it.

I don't see it as "difficult", but cumbersome, you need frequent trips to the documentation to find exactly what thing you need from a certain widget, it takes a lot of patience.

> Take a look at what popular Linux apps are written in, and you'll see a lot of C/C++

As usual, the "it's popular" argument raises it's ugly head.

As for the OP, GUIs are usually constrained by the time of the user to interact with it, so having a fast compiled language or a slow scripted won't make any difference. Both Java and Python are well suited for this, I would go for Python because of it's ease, but if it were for a corporate environment, Java would be my first choice.

---

