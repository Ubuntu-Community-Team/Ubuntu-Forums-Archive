---
title: "Develop Ubuntu Apps"
date: 2010-10-19
forum: Programming Talk
---

### Post by shubhkarman on 2010-10-19
I want to write applications for Ubuntu. I do not know much about programming but I want develop for Ubuntu. I am trying to learn Python right now. What do you think is the best way to develop apps for Ubuntu? Can you point me to some resources that can help me out with this?

---

### Post by juancarlospaco on 2010-10-19
**Nice choice** :)
You may use the python tools that you agree more, 
*i use TKinter, Wxwidget, web2py, others choose QT and such...*

---

### Post by shubhkarman on 2010-10-19
Thanks for the reply.. Could you point me to some beginner resources that help me start development for Ubuntu?

---

### Post by juancarlospaco on 2010-10-19
Web, crossplatform, nice features, the most easy web framework, uses built-in database sqlite, dont need install: 
[http://www.web2py.com/](http://www.web2py.com/)

Desktop GUI, Crossplatform, the most Easy GUI toolkit, fast, ugly by default but i got a module to use GTK with it: 
[http://www.nmt.edu/tcc/help/lang/python/tkinter.pdf](http://www.nmt.edu/tcc/help/lang/python/tkinter.pdf)

Desktop GUI, Crossplatform, not easy, GTK look and feel, ugly website, search for tutorials:
[http://www.wxpython.org/](http://www.wxpython.org/)

:)

---

### Post by shubhkarman on 2010-10-19
Cross-platform compatibility is not an issue. I just want my apps to be run and integrate well with Ubuntu. BTW, I've also heard about PyGTK. Can you tell me more about it?

---

### Post by juancarlospaco on 2010-10-19
Yes, PyGTK integrate well on Ubuntu, the problem is that PyGTK dont integrate at all on KDE,
so a lot of projects need to maintain 2 GUI Frontends, one using GTK, other using QT, 
double work, the app dont look the same on both, i dont like it, 
so my Tk/Wx apps dont need GTK, dont need QT, run on both.

Also, more big is the GUI Toolkit more lines of code you need, 
and more complex, more slow the app, if you code for fun is not so nice,
in example creating a working button on Tk is a one-liner :)

Using Web2Py you can forget about GUI, because is all web based.

---

### Post by shubhkarman on 2010-10-19
I don't really think I need my applications to run on KDE. Gnome is enough for me. ANd for can I use Web2Py to develop desktop apps? Then, can I even use Django to develop desktop apps?

---

### Post by juancarlospaco on 2010-10-20
Web2Py and Django are not for Desktop Apps.

I recommend you to try WxPython then :D

---

### Post by shubhkarman on 2010-10-20
OK. And how about using C# with Mono?

---

### Post by Some Penguin on 2010-10-20
...have you noticed the sticky threads yet?

---

### Post by Ahava591 on 2010-10-20
If you want to write open source software, you just need to write it then offer it to the public. Before you learn about the licenses, etc. you need to learn to program. I appreciate your desire to contribute directly to Ubuntu, but we have to crawl before we walk, walk before we run. 

Find out what commonly used programs use Python; then, find which ones you like. Read the source code for the programs you like and use daily. Learn from it. Look for stupid things that the original writers or the maintainers have done and figure out how you could do it better without breaking the program, without making it Hell for the maintainers that will come after you.

Remember always that the most time consuming, maybe the most common activity that any programmer, (especially open source programmers,) takes part in is maintaining code. 
I will estimate that maybe thirty to fifty percent of my time is spent actually writing original code, which also involves looking at reference material, (i.e., learning,) and at least fifty percent is going back through and figuring out what I did wrong, what I could do better, what is going to need to be changed to make it work with future technology.


Your questions have been about programming, basically. You need to learn this before you actually give anything away; there are other ways you can help, such as helping to translate documents, user interfaces, etc. into languages other than English, if you decide you don't want to help with programs. 

There are several stickied threads at the top of this section. You will need to better investigate these things for yourself before asking questions in the future. We appreciate your eagerness to learn and help out; and when you have problems, please just ask us for help and we'll do what we can.

However, these questions have been very general, with easily found answers if you'll take the time to properly search. 

Good luck, hope to see you around some more.

---

### Post by shubhkarman on 2010-10-20
@Ahava591 I am just a beginner. I am not talking about contributing to Ubuntu but creating software for Ubuntu.

---

### Post by directhex on 2010-10-21
> **shubhkarman said:**
> OK. And how about using C# with Mono?

Works fine. Gbrainy and Tomboy are C# apps, on a default Maverick install.

---

### Post by NightwishFan on 2010-10-21
You might take a look at this if you are like Gnome/GTK+. Vala is a language with a C#-like syntax that compiles to C. I am actually planning to pick this up myself at some point if I ever get around to it.
[http://en.wikipedia.org/wiki/Vala_%28programming_language%29](http://en.wikipedia.org/wiki/Vala_%28programming_language%29)


This is a program written in Vala:
[http://en.wikipedia.org/wiki/Shotwell_%28software%29](http://en.wikipedia.org/wiki/Shotwell_%28software%29)

---

### Post by shubhkarman on 2010-10-21
@NightwishFan I'll surely look at Vala. It seems to be great. Do you have any other ideas? Can I package Vala programs or C# programs to .deb? I know nothing about packaging.

---

### Post by NightwishFan on 2010-10-21
Yes, vala/gtk+ libraries and apps like shotwell are already packaged, so you can use them in Ubuntu. I do not develop/package much so I am not the one to ask how to do so.

---

### Post by juancarlospaco on 2010-10-21
*OP want to learn Python, i think we should help on that way...*

---

### Post by mainerror on 2010-10-22
I'm not really sure that OP even really knows what he wants.

---

### Post by NightwishFan on 2010-10-22
They can make up their own mind I suppose. I would like to see more Vala apps so I am pretty much always going to throw that out there. :D

---

