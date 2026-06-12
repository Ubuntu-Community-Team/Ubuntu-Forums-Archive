---
title: "[SOLVED] Application programming and Web development?"
date: 2008-06-11
forum: Programming Talk
---

### Post by keiichidono on 2008-06-11
I want to get started on learning Application programming and Web development and i wanted to know what i need to know. I already have some soft history in Web development but i never really got into it. Now i want to make sure i study it good and proper and pick up application programming too. I found that i learned very well using web resources for HTML and CSS but what about the others? Should i go pay off my library debts and pick up some books? Or would i better off using the web? What are the best languages to pick up?

For application programming i want to develop applications for Linux, although i think i should learn something about Windows too. I'm mainly doing it so i can contribute code to projects i like and want to develop more like Firefox and Deluge and Pidgin and stuff like that. What would be the best way to get into this? What would be the best way to make sure i make good quality code and gain flexibility in important languages? What are the best languages to learn?

For anything i haven't covered or missed, I'd like to be filled in on that too. I'd also like to know what i should do concerning IDE vs. Separate tools.

---

### Post by jespdj on 2008-06-11
I guess that with "application programming" you mean desktop applications.

For that, you'll first need to learn a programming language. For Ubuntu desktop applications, [Python](http://www.python.org/) is probably one of the best choices to start with. Then you need to learn how to program user interfaces. The user interface toolkit that's used for the [GNOME](http://www.gnome.org/) desktop is [GTK+](http://www.gtk.org/). The Python binding for GTK+ is called [PyGTK](http://www.pygtk.org/). You'll want to learn about other GNOME API's too.

Ofcourse there are other programming languages (C#, Java, Ruby, C, C++, ...) and other GUI toolkits ([wxWidgets](http://www.wxwidgets.org/), [Qt](http://trolltech.com/products/qt/) - the native toolkit of KDE, ...).

For web application development there are also a number of different technologies. [PHP](http://www.php.net/) is probably an easy programming language to start with for web development.

See the stickies in this forum for more info.

---

### Post by xlinuks on 2008-06-11
You're asking too many questions, one would have to write a book to answer them all.
First off you need to understand that you should concentrate on one thing cause what you're willing to do is too much and will require you many years to get "productive".
I know that Firefox is written (mainly) in C++, Pidgin is prolly in C. Thus you need C/C++. Thus I would suggest learning these languages and the libraries that they use.
If you concentrate on anything your will will collapse regardless of whether you agree with me.
CodeBlocks/Eclipse/NetBeans are good IDEs for C/C++ programming.

---

### Post by Kinnza on 2008-06-11
i would actually suggest that you wont start with c/cpp cause they are a bit more to handle

i would recommend learning java, that way you dont need to worry about windows or linux... it will work on all platforms (unless you do some weird system calls or something like that)

about the web programming, it really depands on what
i think that php is probably the best way to start, but there is always .net (asps) and j2ee (jsps) to learn but those are used more by cooperation. plus, php+mysql is free and easy to install on linux

like said before me, you really need to be more specific about what exactly you wanna program

---

### Post by xlinuks on 2008-06-11
If you learn Python (as jespdj suggests) you won't be able to contribute code to Firefox and alike as you state in
> I'm mainly doing it so i can contribute code to projects i like and want to develop more like Firefox and Deluge and Pidgin and stuff like that.
until you actully learn the languages they are written in. Besides Linux and Windows are mainly programmed in C/C++ (and most known "seriuos" applications like Firefox, Gimp, Blender..).

---

### Post by pmasiar on 2008-06-11
I would recommend to split your learning into couple steps.

1) Realize that HTML/CSS is not "programming" - it is visual design. You can make changes and see results immediately. That's nothing like in programming: in programming, you build mental model in your mind, transform it into code, try to run, there is error, and you need to find where it is: in your mental model, in translation to code, or in your understanding how the code works. It is **very** non-obvious what is wrong, rather different from HTML.

If you cannot handle those abstractions, maybe you should consider be web designer, not a programmer. You can still learn some basic programming (Javascript/AJAX), but forget about contributing to Firefox core: that is extremely complicated, it will take couple years to get to that skill level for average programmer. Unless you are genius, of course :-)

2) Learn basic programming: see sticky FAQ for this discussions. Python is the best language, in opinion of most ppl.

3) Decide in which area of programming you want to specialize: web apps are very different from desktop: you need to master different sets of libraries and/or frameworks, different approaches of solving problems.

4) Then, select a project you want to contribute, and possibly learn language it uses. Most programmers are skilled in multiple languages and use the one most appropriate to the job at hand. There are others, who know only one, and use it for anything: if all you have is hammer, everything looks like a nail, right? :-) By the time you are ready, Python will be everywhere :-)

Become expert, skilled enough to contribute to one of those widely used projects, will take average programmer couple of years, at least. So make it in steps, and don't forget to have fun on the way:  PythonChallenge, pygame for writing games, and many other websites will help you to get there, but it is major effort and major time dedication, not easy. But fun!

See my sig for links. Good luck!

---

### Post by Mickeysofine1972 on 2008-06-11
I found the following languages are the ones I get more to do lateley:

PHP - web development 
C/C++  - good for making things work fast
Python - good for making GUI applications and commandline

If your gonna get into PHP development I would recommend using the code igniter frameworks as it has made live very easy for me when I develop PHP/AJAX type applictions for the web. (JavaScript if you wanna do Ajax BTW :-D)

C/C++ for linux I find is easier done using code::blocks as you IDE.

And Python, Gedit with the Python console plugin makes live easy too.

Mike

---

### Post by keiichidono on 2008-06-12
Thanks for the responses guys. I think i will focus more on web development rather than desktop application programming.I'll be sure to read the stickies, and I'll get into Python as soon as possible. It actually turns out the program i want to contribute to mostly (no bias, it just need a lot of features it lacks) which is Deluge, is made using python and some C. Again, thanks for the help. :D

---

