---
title: "Which Python GUI tool kit for at absolute beginner"
date: 2009-04-09
forum: Programming Talk
---

### Post by shingalated on 2009-04-09
Hello good folks, which Python GUI toolkit would be a good toolkit for a absolute beginner.  I have pretty little programming experience, and no GUI experience.  Should I go with wxpython, glade, PyGTK, or tkwhatever?
Thanks

---

### Post by flyingsliverfin on 2009-04-09
hey just my question too (though maybe not quite yet still have to finish the normal python guide that im using). Glad the question popped up somewhere.

have you looked at PYQT? 

personally I like the sound of PyGTK

---

### Post by sujoy on 2009-04-10
pygtk is simple to start with and yet good enough for major GUI programming

---

### Post by nvteighen on 2009-04-10
Possibly, none... GUI is harder than you might think, so I'd first try to gather more experience before trying it...

---

### Post by Yacoby on 2009-04-10
> **nvteighen said:**
> Possibly, none... GUI is harder than you might think, so I'd first try to gather more experience before trying it...
When using a decent library, I found writing GUI functionality incredibly easy. Really really tedious, but easy none the less. It got a bit easier with a GUI designer, but I still hate writing frontends.

I have only messed with wxPython, so I am not going to be able to give a conclusive overview.

---

### Post by MicahCarrick on 2009-04-11
My vote goes for using the Glade Interface Designer with pyGTK (using gtk.Builder)... but I'm a GTK guy so my opinion is biased. Each toolkit has its pros and cons. As a beginner, you might want to just pick one and then once you gain some experience, pick another and compare for yourself to find the one that suits your particular needs. wxWidgets will do the trick too.

---

### Post by days_of_ruin on 2009-04-11
I have used pygtk and don't have any problems with it.
But I would upgrade your ubuntu if you want the latest versions of any gui toolkit.:p

---

### Post by Sprut1 on 2009-04-11
I've used both wxPython and pyGTK, they both have their ups and downs, but designing in Glade3 over wxGlade is so much better. I suggest pyGTK.

---

### Post by bruce2000 on 2009-04-11
Hi,

I'm also a beginner to Python and have been tinkering with pyGTK for the last week or so, in order to build a simple GUI for a small project I've set myself. 

I wouldn't say I found it easy, but with a little help from tutorials on the web it wasn't that difficult either (and I have little experience of OOP.)

I would recommend you give pyGTK a try.

btw, In my opinion it's better for beginners to avoid using an interface builder like Glade, as it hides the GUI code.

---

### Post by hessiess on 2009-04-11
Try tkinter to bigin with, as its included with python, and is reasnably easy to use.

---

### Post by ajackson on 2009-04-11
> **bruce2000 said:**
> btw, In my opinion it's better for beginners to avoid using an interface builder like Glade, as it hides the GUI code.
I respectively disagree, GUI designers like Glade and Qt Designer are useful tools that help speed up development time, with Qt Designer files you can use pyuic to convert them into Python if you wish to see how the window is built up (I assume there is something similar for Glade).

At the end of the day they are tools to help make developing software easier, leaving you free to work on the tricky parts of the program rather than spending ages hand coding your own GUIs.

That is just my opinion, others (such as yourself) will have other views.

---

### Post by pmasiar on 2009-04-11
GUI is over-rated, learn programming in commandline. GUI adds many confusing problems, like events.

If you have to have GUI, easiest is EasyGUI (which has no events, so it is not really a GUI, it just looks like one :-) ).

See wiki in my sig for tasks to learn programming (which do not require GUI).

---

### Post by soapytheclown on 2009-04-11
i just wrote a program in pyqt for my dissertation, considereing the only programming id done before was all web dev related i found picking up pyqt very easy! it also comes with tools for gui creation although i prefered hand coding them!

---

### Post by happysmileman on 2009-04-11
> **ajackson said:**
> I respectively disagree, GUI designers like Glade and Qt Designer are useful tools that help speed up development time, with Qt Designer files you can use pyuic to convert them into Python if you wish to see how the window is built up (I assume there is something similar for Glade).

At the end of the day they are tools to help make developing software easier, leaving you free to work on the tricky parts of the program rather than spending ages hand coding your own GUIs.

That is just my opinion, others (such as yourself) will have other views.

He never told the guy to never use a designer, but he said he should learn how to actually code the GUI as well.
If OP is looking for a career with programming or intends to get involved with open source projects he WILL need to know how the libraries work.
Or if he intends to do complicated stuff that the designers either don't support or are very difficult to do (Dynamically creating GUIs based on user input would be one example.)

And even if he uses the designer all the time, he'll still need to know how to actually interact with the widgets, which still involves learning to code with them.

---

### Post by Xender1 on 2009-04-11
i also have a similiar question. i want to start coding python but do not know what to code it in (i have coded python in terminal using 'python' and then coding). Where should i program my python programs to then save them and run/edit later?

---

### Post by sujoy on 2009-04-12
> **Xender1 said:**
> i also have a similiar question. i want to start coding python but do not know what to code it in (i have coded python in terminal using 'python' and then coding). Where should i program my python programs to then save them and run/edit later?

just use a text editor you are comfortable with. gedit, geany, vim .. whatever

then write the program in the file and save it (preferably with a .py extension)

now you can run it from the terminal as 
$ python filename.py

or you can add this line at the very begininning of the file.
```
#!/usr/bin/env python
```
then give it execute permission. chmod +x filename.py
and run it from the terminal as 
$ ./filename.py
or
$ /full/path/to/filename.py

---

### Post by defaultusername on 2009-04-12
I've only used wxWidgets. Designing GUIs involves similar concepts across the board, so translating something written with wxWidgets into PyGTK or PyQT shouldn't be too difficult.

---

### Post by ajackson on 2009-04-12
> **happysmileman said:**
> He never told the guy to never use a designer, but he said he should learn how to actually code the GUI as well.
If you read what I said I didn't say anything about not learning how to code GUIs by hand. I said that the designers are useful tools and provided an example of how you could see the Python code version of a Qt GUI. That is often a good way to learn, start with the generated file, make changes and see how that affects the GUI.

> If OP is looking for a career with programming or intends to get involved with open source projects he WILL need to know how the libraries work.
Did I say he didn't need to know? Again I said designers were useful tools.

> Or if he intends to do complicated stuff that the designers either don't support or are very difficult to do (Dynamically creating GUIs based on user input would be one example.)
Again I said designers were useful tools, I didn't say that he **must** use a designer for GUI work.

> And even if he uses the designer all the time, he'll still need to know how to actually interact with the widgets, which still involves learning to code with them.
Again where did I say he didn't need to know how to use the libraries?

At the end of the day designers are tools, they help you make GUIs, they don't replace the need to understand how to interact with widgets or how to work with events. There are cases when they aren't suitable tools for the job.

Edit: I was saying that I disagreed with the opinion that beginners should avoid using designers. How you turned that into me saying the beginner should always use a designer and not worry about learning the underlying libraries I don't know :)

---

### Post by bruce2000 on 2009-04-13
Just to clarify - I was referring to it being better for *beginners* to hand code the GUI. Once you have experience then sure use a designer if you want to speed up development. If there is a way to see the Python code generated by Glade that would be great, but as I don't know of one I found I've learnt more by hand coding the GUI.

---

### Post by happysmileman on 2009-04-13
> **ajackson said:**
> 
I was saying that I disagreed with the opinion that beginners should avoid using designers. How you turned that into me saying the beginner should always use a designer and not worry about learning the underlying libraries I don't know :)

I misunderstood, sorry.

---

### Post by god0fgod on 2009-04-13
I've only used PYGTK and I find it easy to understand, although the documentation on some things could be improved.

However, it's quite buggy and can crash in some cases. These crashes can be fixed but it's difficult and they shouldn't occur in the first place.

I'm on here in fact to try and find a fix for a pygtk problem I've gotten.

---

### Post by YyYo on 2009-05-12
In my opinion GTK in general is a easy/nice/stable GUI library.
I have been using it for 2 years with programming lanuages:
 - perl => gtk2
 - python => pygtk
 - mono => GTK#

But again _it is my opinion_. I suggest you to start work with it and maybe with WxWidgets together and then choose the _better one for you_

---

