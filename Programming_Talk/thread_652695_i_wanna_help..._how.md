---
title: "i wanna help... how?"
date: 2007-12-29
forum: Programming Talk
---

### Post by pavel989 on 2007-12-29
Hi, i have, i guess, a controversial question. I don't specifically want to make applications, instead get more into the heart of ubuntu and help out. what language should i learn? The thing is, i might not even be needing to ask this question, but i wanna keep the open source community, and something that ive found i have trouble with, is finding out what language what is written in. (if that makes sense?)

like, how was gparted written? what about ubuntu? what languages can i use to expand them?

or XGL or compiz... i have an endless list. but what language should be a basis?

i have some programming experience. mainly in VB and ruby. i guess very little, python c++ and BASIC.

I could really use some guidlines here and resources.

---

### Post by LaRoza on 2007-12-29
**NO FLAMING ALLOWED**

Most of Linux programming involves C, however, Python, Perl, Java, C++ and others are common.

I would suggest learning a language and finding a project to help with, or find a project you are interested in and learning the language.

[http://freshmeat.net/](http://freshmeat.net/) (You can search by language)
[http://sourceforge.net/](http://sourceforge.net/)


My personal advice is in my wiki.

---

### Post by pavel989 on 2007-12-29
Thanks!

---

### Post by Tundro Walker on 2007-12-30
With some VB experience under your belt, and with a lot of Ubuntu being Python-oriented, I'd say taking on Python is a good idea.  The syntax is easy to read, write and understand.  It's fairly forgiving, since you can do procedural coding (stepping through instructions) as well as object-oriented coding (creating classes / objects that each have their attributes, commands, etc).
You can search the repo's for the &quot;Dive into Python&quot; book, which offers a good start.  If you want a physical book, I found the &quot;Python Programming for Absolute Beginner&quot; to be pretty good ... it uses games for a lot of its examples, since most folks like to create a game when learning a language in order to make it fun.  It teaches how to do the basic scripting as well as introducing the Tkinter GUI structure and also using Pygame to create graphical games.
You can use gedit for Python syntax highlighting.  You can also get Dr. Python, or, my favorite so far, Geany, from the repo's, which are more Python-specific.  For GUI's, you can use Glade from the repo's.  It provides a WYSIWYG environment to create the GUI structure by hand, then you can do the Python coding that supports the buttons and such.

~~~~~~~~~~~~

An alternate choice, but, in my opinion, more left-brained, is learning C or a derivative of it (C++ or C#).  A lot of folks code things in C++ and use the gcc compiler to compile their code.  A lot of folks also use MonoDevelop (which is sort of Linux's version of Microsoft's Visual Studio) to do C++ & C# development.  MonoDevelop also supports VB.NET coding, but I didn't have much success when trying it out.

~~~~~~~~~~~~

If you want to stick with VB, you can use Gambas, which is a pretty good VB take-off.  It's basically like VB, but the author has modified it to be a bit better.  Gambas is a total development environment, not only letting you code command-line projects, but also WYSIWYG gui creation.  It comes with some sample projects, a pretty good help system, and a compiler to create your executable program.  The only problem with Gambas is that most folks will need to go into the repo's and install the Gambas run-time packages in order to use anything you develop in it.  Ubuntu users don't have that problem with Python or Mono projects, because Ubuntu comes with Python and Mono run-time environments already installed.

Hope this helps.

---

### Post by pavel989 on 2007-12-30
> **Tundro Walker said:**
> With some VB experience under your belt, and with a lot of Ubuntu being Python-oriented, I'd say taking on Python is a good idea.  The syntax is easy to read, write and understand.  It's fairly forgiving, since you can do procedural coding (stepping through instructions) as well as object-oriented coding (creating classes / objects that each have their attributes, commands, etc).
You can search the repo's for the &quot;Dive into Python&quot; book, which offers a good start.  If you want a physical book, I found the &quot;Python Programming for Absolute Beginner&quot; to be pretty good ... it uses games for a lot of its examples, since most folks like to create a game when learning a language in order to make it fun.  It teaches how to do the basic scripting as well as introducing the Tkinter GUI structure and also using Pygame to create graphical games.
You can use gedit for Python syntax highlighting.  You can also get Dr. Python, or, my favorite so far, Geany, from the repo's, which are more Python-specific.  For GUI's, you can use Glade from the repo's.  It provides a WYSIWYG environment to create the GUI structure by hand, then you can do the Python coding that supports the buttons and such.

~~~~~~~~~~~~

An alternate choice, but, in my opinion, more left-brained, is learning C or a derivative of it (C++ or C#).  A lot of folks code things in C++ and use the gcc compiler to compile their code.  A lot of folks also use MonoDevelop (which is sort of Linux's version of Microsoft's Visual Studio) to do C++ & C# development.  MonoDevelop also supports VB.NET coding, but I didn't have much success when trying it out.

~~~~~~~~~~~~

If you want to stick with VB, you can use Gambas, which is a pretty good VB take-off.  It's basically like VB, but the author has modified it to be a bit better.  Gambas is a total development environment, not only letting you code command-line projects, but also WYSIWYG gui creation.  It comes with some sample projects, a pretty good help system, and a compiler to create your executable program.  The only problem with Gambas is that most folks will need to go into the repo's and install the Gambas run-time packages in order to use anything you develop in it.  Ubuntu users don't have that problem with Python or Mono projects, because Ubuntu comes with Python and Mono run-time environments already installed.

Hope this helps.

meh i didn't get too far into VB, but ive been considering moving onto python, thing is, im already working with ruby. and i doubt that ill be able to remember which uses which command. but it seems as though python is the ultimate language here.

EDIT:::: python being ultimate for my purposes

---

