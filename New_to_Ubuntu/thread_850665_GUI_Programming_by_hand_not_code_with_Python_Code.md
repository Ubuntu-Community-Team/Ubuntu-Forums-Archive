---
title: "GUI Programming by hand not code with Python Code"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-07-05
Is their a program that lets you design a GUI by hand (like gambas) not by code (like wxpython) but the commands are in python?

A program similar to gambas or vb

Gambas with python code instead of gambas code would be perfect.

Thanks in advance

---

### Post by apswartz on 2008-07-06
Plucky, I don't think there is, but you might want to ask on a Python forum somewhere...

[http://www.google.com/search?num=100&hl=en&q=python+forum&btnG=Search](http://www.google.com/search?num=100&hl=en&q=python+forum&btnG=Search)

---

### Post by pluckypigeon on 2008-07-06
Hey! Thanks for your reply. 

I have asked in a couple of different forums. 

I'll keep this updated with the information when it comes in.

---

### Post by pluckypigeon on 2008-07-07
so far I have had boa-constructor (which I have used before) and XRCed recommended to me.

I did a whatis in terminal and got - xrced (1) - wxPython tools.

I have been to the sourceforge page [http://xrced.sourceforge.net/]("http://xrced.sourceforge.net/")

and apt-cache search gives - python-wxgtk2.4 - wxWindows Cross-platform C++ GUI toolkit (wxPython binding)
... which I am currently installing.

I'll update more soon

---

### Post by denham2010 on 2008-07-07
Hi,

Try Glade. It's in the official repositories (download with Synaptic).

Probably one of the easiest ways I have found to do GUI programming in linux.

1. Create your GUI in Glade using a wysiwyg interface and save your project. Remember to add your event handling function names to the gui widgets (ie "run_this_function" if this button is clicked)

2. Run the script glade2py (you may have to do a little google search for that one) on the glade file and this will generate a python script with all the event handling functions already present.

3. Add the event handling code in your python script functions.

4. Run your newly created programme and enjoy!

There are plenty of glade / python tutorials on the net to help you learn glade....google is good!

Enjoy!

---

### Post by pluckypigeon on 2008-07-07
Cool, I'll check that one out when I get a bit of time. :)

I've messed up my ubuntu installation at the moment:lolflag:

---

