---
title: "Best programming language for Ubuntu?"
date: 2011-10-11
forum: Programming Talk
---

### Post by carlosgs91 on 2011-10-11
.

---

### Post by karlson on 2011-10-11
You probably need a better subject...

> **carlosgs91 said:**
> Hi, I have learnt the basics about Python and wxPython but I was wondering what's the best way to create an applicaiton in Ubuntu. What GUI toolkits may I use to create a GUI application


There are 3 that are used most commonly: GTK+, QT, wxWidgets.

> , should I use Python? 

Your choice GTK+ is natively C, the others are natively C++, but there are Python packages for all 3.
> Where are the APIs available?

Not sure I understand the question.  All 3 should be installable from UBUNTU repositories.

> 
Is it Glade ok? How do I import a .glade file into a python file? 


Is Glade OK for what?  I suggest you read [http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/) for the second question.

> All the tutorials I have tried give me segmentation fault or things as messed up as that :/

Thanks

You would need to be a little more specific.

---

### Post by cgroza on 2011-10-11
There is no right answer for this kind of question. I say it depends on what you are trying to accomplish.

---

### Post by Pynalysis on 2011-10-11
Python using Tkinter module is an option to consider as well.

---

### Post by uahmed on 2011-10-13
Hi

Here are few good links for you ,

Python development videos,Toutorial , Screenshots

[http://showmedo.com/videotutorials/python](http://showmedo.com/videotutorials/python)

PYQT :
[http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/classes.html](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/classes.html)
[http://zetcode.com/tutorials/pyqt4/firstprograms/](http://zetcode.com/tutorials/pyqt4/firstprograms/)

Wx :
[http://www.wxpython.org/docs/api/wx-module.html](http://www.wxpython.org/docs/api/wx-module.html)

I hope it will work for you , Although Tkinter is more easy to understand .

---

### Post by kostkon on 2011-10-14
> **carlosgs91 said:**
> Hi, I have learnt the basics about Python and wxPython but I was wondering what's the best way to create an applicaiton in Ubuntu. What GUI toolkits may I use to create a GUI applicaiton, should I use Python? Where are the APIs available?

Is it Glade ok? How do I import a .glade file into a python file? All the tutorials I have tried give me segmentation fault or things as messed up as that :/

Thanks
You can start from [here]("http://developer.ubuntu.com/"), the ubuntu developer portal.

Hope that helps.

---

### Post by Trisket on 2011-10-17
> **karlson said:**
> You probably need a better subject...


 rude.

---

### Post by juancarlospaco on 2011-10-17
> **Pynalysis said:**
> Python using Tkinter module is an option to consider as well.

^ This

---

### Post by gnometorule on 2011-10-18
Why would anyone call karlsson rude for pointing out that the 'subject' (line) chosen by this post is (1) naive, (2) not helpful, and (3) not really related to the actual question asked - which seems furthermore not very thought through - when he (karlsson) then proceeds to give a long and patient answer? That's simply beyond me, if it wasn't tongue-in-cheek.

---

### Post by Alan D on 2011-10-20
> **carlosgs91 said:**
> Hi, I have learnt the basics about Python and wxPython but I was wondering what's the best way to create an applicaiton in Ubuntu. What GUI toolkits may I use to create a GUI applicaiton, should I use Python? Where are the APIs available?

Is it Glade ok? How do I import a .glade file into a python file? All the tutorials I have tried give me segmentation fault or things as messed up as that :/

Thanks

What sort of application do you want to make exactly? You have something in mind, but you are asking in a vague sort of way. But this means we can only give vague answers.

Part of gaining skill in programming is the ability to ask solid questions, both of others and yourself. 

Question: I want to recreate the calculator application. What is the best tool?
Answer: Python and wxpython can do that effectively and fast.

Question: I want to write a text editor. Is c a good idea?
Answer: No, I would say it isnt. You'll be managing a bunch of little details that gtk and python can take care of for you.

Question: I want to write a simple game. What API should I use?
Answer: Python and pygame will let you learn at a good pace. Later more complicated games might call for C++.

Later after you learn a bit about programming, you might ask:

Question: how can I gain more insight in how programs work?
Answer: Learning assembler will help with that, even though you probably wont write full applications with it. 

Question: How can I become a more flexible programmer? I have studied python and C/C++ for a few years now.
Answer: Haskell has a different approach to programming. Study that or other functional programming languages. You might like Lisp as well.

So the questions you ask should be as specific as possible. Then we can use our experience and familiarity to provide you with a short and wise path to what you want.


So carlosgs91, what do you want to make first?

---

