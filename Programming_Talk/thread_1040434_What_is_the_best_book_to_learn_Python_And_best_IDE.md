---
title: "What is the best book to learn Python? And best IDE for it."
date: 2009-01-15
forum: Programming Talk
---

### Post by NeonBible on 2009-01-15
I'm pretty much a beginner but I have some experience with programming languages.  I just haven't tackled very large projects.

I have read numerous books before and they all talk about the same stuff i.e. start with Hello World, some basic arithmetic, variables, conditions, loops etc.  So I don't want to read another book in that format.

I never put my knowledge into good use but I am want to start afresh, with Python, and tackle some projects which are a bit beyond basic.

So I guess I am more interested in understanding how to build a program, structure, design, good clean code.

Are there any good books which are project/tutorial based rather than teaching fundamentals? E.g. will teach me step by step how to create a simple word processor, and then gradually taking on more complex applications.

Also whats a good IDE for Python? I don't mind using just Python console and Vim, but I guess as a beginner I need to pay more attention to debugging.

---

### Post by fiddler616 on 2009-01-15
> **NeonBible said:**
> 
Are there any good books which are project/tutorial based rather than teaching fundamentals? E.g. will teach me step by step how to create a simple word processor, and then gradually taking on more complex applications.

Also whats a good IDE for Python? I don't mind using just Python console and Vim, but I guess as a beginner I need to pay more attention to debugging.
I'm afraid I'm not much help in the tutorial department. Although if you were serious about making a word processor, you should look into GUIs (GTK+ and WxWidgets are probably the two most popular here).
As for IDEs...prepare for a huge fight.
I generally use gedit and a console, although I'm learning Vim. I've also been known to use Geany, just because it has the big darn "Execute" button. It has code folding too, which can be nice. Other people are probably going to talk about IDLE, Eric, DrPython, etc. And if LaRoza were still here, he'd start bashing IDEs, and say that nothing beats a text editor and console. So my final answer? Investigate as many as you want, and then make your own decision.

---

### Post by NeonBible on 2009-01-15
thanks.

I'm not specifially looking to create a word processor, was just an example.

gedit is an IDE? I thought it was just a text editor.

---

### Post by insanecrazy4 on 2009-01-15
In my experience with using python so far i have found using online tutorials are best. Just google python tutorials and you will get a lot of great results. As for IDE, i like DrPython which can be found in the repos.

---

### Post by .Maleficus. on 2009-01-15
Well, unfortunately you probably won't find a book that jumps straight into "program" programming (text editors, music players, anything like that).  You need to really understand the language before you can do that, so a book like Learning Python or Programming Python is going to be your best bet (the latter being more advanced and assumes knowledge of the language).

As for IDEs, I've played with Komodo, WingIDE and Netbeans - all are pretty good but I'm currently using Netbeans.  Wing was probably the best but Netbeans had all the features I wanted and I don't need to purchase a liscense like with Wing.

---

### Post by fiddler616 on 2009-01-15
> **NeonBible said:**
> 
gedit is an IDE? I thought it was just a text editor.
It straddles the line. Syntax highlighting, Python console in sidebar, mass indenting/unindenting (the last two are standard plugins, AFAIK). You just need a console to actually run it.
As for tutorials
[http://www.ibiblio.org/swaroopch/byteofpython/read/index.html](http://www.ibiblio.org/swaroopch/byteofpython/read/index.html)
is a great mix of being concise but informative.

---

### Post by Juffo-Wup on 2009-01-15
> **fiddler616 said:**
> It straddles the line. Syntax highlighting, Python console in sidebar, mass indenting/unindenting (the last two are standard plugins, AFAIK). You just need a console to actually run it.
As for tutorials
[http://www.ibiblio.org/swaroopch/byteofpython/read/index.html](http://www.ibiblio.org/swaroopch/byteofpython/read/index.html)
is a great mix of being concise but informative.

I would still put it in the 'text editor' set, though, as it doesn't do project management (as far as I know), and many of those (text buffer-manipulating) functions can be found on traditional text editors, such as Vim and EMACS.

Anyhow, have you tried with PyDev for Eclipse? I haven't personally used it much, but it's there. It likes to yell at you while you configure it, though :P

---

### Post by alexmullins on 2009-01-15
Have you read [Dive Into Python]("http://www.diveintopython.org/"). Its a pretty good book. If you have previous programming experience then this book is for you. It doesn't devote a whole entire chapter to telling you what a variable is and how to use it. It jumps right in and how lots of example programs.

---

### Post by iQuizzle on 2009-01-16
i really liked the book [Core Python Programming]("http://www.amazon.com/Core-Python-Programming-2nd/dp/0132269937/ref=pd_bbs_sr_11?ie=UTF8&s=books&qid=1232084330&sr=8-11"). it's huge and it covers a lot, but i think it's pretty easy to follow and you really rip through it quickly. as for an ide, i dont use one so i can't say but you might look at SPE (stani's python editor). a lot of people seem to use it.

---

### Post by eye208 on 2009-01-16
Check out Geany. It's lightweight and supports many languages, including Python.

---

### Post by NeonBible on 2009-01-16
> **alexmullins said:**
> Have you read [Dive Into Python]("http://www.diveintopython.org/"). Its a pretty good book. If you have previous programming experience then this book is for you. It doesn't devote a whole entire chapter to telling you what a variable is and how to use it. It jumps right in and how lots of example programs.

Wow no messing about with this one.  Looks like the one for me and free to boot! Thank you!

I only want an IDE for auto complete and debugging really.  Am I right in thinking that you do not compile Python code? How does Debugging work?

---

### Post by djbushido on 2009-01-16
Debugging is like standard C++/C debugging, only without compiling. As far as I know.
The book I am using for python is Learning Python from O'Reilly. I really like it, though its ~$40.
My favorite IDE is Eclipse, because i like the support, big projects, etc. It's a big download, but make sure you also get the pydev package.
Happy to help more if needed.

---

### Post by Qtips on 2009-01-16
Hi,

You could read "Code complete". Check on amazon.

Cheers

---

### Post by peterbrewer on 2009-01-16
I found 'Rapid GUI Programming with Python and QT' a really helpful resource and puts you into some decent tutorials pretty quickly.

---

