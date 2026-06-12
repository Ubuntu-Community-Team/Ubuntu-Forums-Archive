---
title: "question about python..."
date: 2007-04-26
forum: Programming Talk
---

### Post by hockey97 on 2007-04-26
Hi I got a question about python I am planning on making a program ect,  and for the gui I  am thinking to use thinkter, just want to know if it's like a gui program where you create window's ect or is it like a script type of code thing that you have to type then run to see the window that is created???

I want to import my own button art ect is that possible with the thinkter ???

and is their a module that has the funcutions of a webbrowser and a ftp server??

I am not fully new to python but I never made a full program before in python I have in c++ but need some help on what to use.

I do know programming basic's like var's and strings and functions and classes ect...

Thanks for your time.

---

### Post by pmasiar on 2007-04-26
Looks like you are beginner - which is not a problem, everybody started once. But to avoid frustration, you may want to start easy: learn to walk before trying to run. Start with command-line programs first. GUI is really much more complicated: you have to handle events, program flow is not as obvious.

Check programming tasks for beginners at LearnPython wiki (link in my sig). If you insist on GUI, try easyGUI: [http://www.ferg.org/easygui/](http://www.ferg.org/easygui/) - no events, no problems! :-)

Good luck!

---

### Post by AdamG on 2007-04-26
There are GUI designers for some other widget libraries (wxWidgets has wxGlade, which generates ugly but usable code) but I don't think there are any for TkInter. TK isn't all that hard to program, though; there are some good tutorials out there for it. 

TK does have a way to use images in buttons; check out the Tkinter.PhotoImage and Tkinter.Button classes. Basic usage is to initialize a Tkinter.PhotoImage instance, then use it as the 'image' attribute for a Tkinter.Button instance. Check out [this site]("http://www.faqts.com/knowledge_base/view.phtml/aid/4462"). 

I don't think there is an stdlib module for FTP server functions, but I may be wrong - there certainly is ftplib, but that's only the client side. 

As for the webbrowser thing, are you trying to write your own (not advisable!) or use an existing one? If you're wanting to just call the user's web browser, check out the webbrowser module. If you're trying to write screenscraper software, check out the urllib2, cookielib and httplib modules for some web browser functions. They don't do HTML rendering, but that's a whole nother topic, and a rather difficult one at that...

---

### Post by cwaldbieser on 2007-04-27
> **hockey97 said:**
> 
[...] and is their a module that has the funcutions of a webbrowser and a ftp server??


The twisted python modules have an FTP server, but there is a bit of a learning curve to use that framework.  The standard library gives you SocketServer (section 11.16), but that just helps you set up a generic server.  It doesn't implement any protocols.

---

### Post by dwblas on 2007-04-27
PAGE is a Python Tkinter GUI generator.  I have never used it though
[http://page.sourceforge.net/](http://page.sourceforge.net/)

---

### Post by hockey97 on 2007-04-27
Hi I am not really new to python, I know the basic syantax in python for var's and classes and fuctions.
I am plannning on makeing a web browser I am not really planning to build from scratch , if your a true programmer you know by now that heavy duty programming like alot of data we mostly steal from open source, so I don't plan on reall doing intense programming work just plan to combine different script's or modules to make my browser, I want to make the browser newish like I don't want to have the exact same fuctions as internet explorer.

I did some porgramming in c++  I mean by that was calculators I never done huge projects due to lack of time to spend.

I  ask here becuse I don't fully know the modules out their like thier names and what modules I need to look for to use ect.

I know what a web browser needs they need socket's protocal, and gui, and web controls and fuctions ect... thier is more to be said...... 

I just want to really what python supports in modules wise way. I have the time to spend for this so even if it's a big job to do I still want to make this, The reason is I want to know if I should persue programming as a career ect I am taking a college course in eletronics and I am in my last year of high school but don't know what to persue, I spend most of my time with computers.

So I got time from now to college.

I just want to soak my hands in python to see if it's any better than c++ I know nasa uses it and hear that python is much easier than c++.

I have like 7 programming books one is dos, 3 in c++, and 3 in embedded systems like arcade games and also making game engines these are college books.

I don't want to read stuff that explains what programming is like what are var's and strings and classes becuse I already now that.


Thanks for your time

---

### Post by pmasiar on 2007-04-27
OK then "dive into Python" is just right for you.

One advise tho. If you want to learn how big systems are made, start with something where it will be easier for you to visualize/check if all parts are working properly. Your gut feeling is right - making program ten times as long takes more than ten times the time. 20 or 30 times - or 100. :-(

Another thing to remember is: debugging is harder than writing the code. So if you write code as tricky as you can, by definition you are not smart enough to debug it :-)

So do not embark on complicated project before you finished some small ones. 

At the wiki in my sig there is page with tasks to solve, which will give you chance to build some data structures to implement tasks. Harder than homeworks you did so far, but simpler than real big projects. 

Excellent book is "Etudes for programmers" if you can get it somewhere - not cheap, so you can tell is good!

Another fun thing to try is [http://www.pythonchallenge.com/](http://www.pythonchallenge.com/) - series of increasingly complicated tasks, with forums and hints for each one. It might take you whole summer to solve them all!

If you want something closer to electronics, get involved with some running project. It will give you a chance to see real big project, how it is done, and save you from reinventing the wheel and writing loads of scaffolding code to make things run. Most projects are actively looking for developers and will help you to get in. As a bonus, you may get your name included as project member. Just check couple projects you might be interested, write to developers, and you will see which project will respond most positively.

---

### Post by hockey97 on 2007-04-28
Does anyone know any website that goes in depth in the python modules??

Thanks for the replies so far, I am taking my time, so far I been working on learning programming since 6th grade I started off with html.

My dad took C++ at college my sister suggested it to him he never did any programming my sister took the class told my dad it was easy and so my dod though if she can do it why can't he so he takes the class

and then fails it my dad said he never faild a class in his life lol and he got very frustrated with the class too hard for him and he then finds out my sister faild the class and got upset lol.

So I am trying to work my way up, I been learning from raw computer lango which is binary to c++ and well now python ect

Thanks for your time

---

### Post by pmasiar on 2007-04-28
Python home website has everything: [http://python.org/doc/](http://python.org/doc/)

C++ is hard, and *especially* for beginner - I am not surprised he failed. IMHO it is a travesty to teach C++ as first language. Even C would be better than C++ -- it is possibly the hardest mainstream language. Of course Python is the best - get your dad and try to learn Python together, it would be more fun!

---

