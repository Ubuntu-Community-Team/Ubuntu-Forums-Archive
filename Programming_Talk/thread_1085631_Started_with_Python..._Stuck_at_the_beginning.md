---
title: "Started with Python... Stuck at the beginning"
date: 2009-03-03
forum: Programming Talk
---

### Post by mal_conductor on 2009-03-03
** I have read this forum an decided to learn Python (many thanks to those who post pros and cons and programming insight)

Q1) I am using IDLE.  The book I am reading say to type "_name_".  How do I type underscores in IDLE.  For me, it just puts in a space?

Q2) I have one specific project in mind (my reason to learn Python).  I want to work with information in databases, but without databases. Is this possible?!!!!

I currently do it with combination of an Access databe, with relationships, and excel.  The Access database is to enter, store and query data.  Excel is to do calculations.

Q3) Can GUI's be created for Python applications? 
I want to develop a program with a GUI, but in the books I downloaded there is nothing about creating graphical interfaces.

Q4) What books do you recomend?
- I downloaded "Dive into Python" and "Building Skills in Python"

- I have only done programming from university. Fortran77 and Pascal. So I am not totally lost. I have never worked with VB.net

=============================

The FIX to the invisible underscores is to change the font.

Looks like Python does what I need to do.  I will follow the advise and concentrate on learning the language and worry about developing GUI's later.

Thanks to all

---

### Post by sujoy on 2009-03-03
1) idle prints underscores '_' just fine here.
2) python has excellent support for sqlite that uses files for database or even just in memory databases
3) yes python can be and is used for GUI programs. there are python bindings for gtk, qt, tk toolkits (others toolkits might be there too)
4) use what you already have and the python online documentation, which is an excellent resource

---

### Post by Flimm on 2009-03-03
2) You could just use dictionaries, depending on how advanced you want the code to be, and how many features you need.

4) I learnt PyGTK from the [tutorials](http://www.pygtk.org/tutorial.html) and especially the [reference manual](http://www.pygtk.org/reference.html) on their site.

---

### Post by mal_conductor on 2009-03-03
> **Flimm said:**
> 2) You could just use dictionaries, depending on how advanced you want the code to be, and how many features you need.

4) I learnt PyGTK from the [tutorials](http://www.pygtk.org/tutorial.html) and especially the [reference manual](http://www.pygtk.org/reference.html) on their site.

Flimm,  Thanx for the answer; however, I am confused.

What is PyGTK:
- Is it python-based developer?
- Do I still need IDLE or does PyGTK replaces IDLE?
- Is it an add-on that get imported into IDLE when developing?
- Does learning PyGTK replace learning Python, or learn PyGTK in addition to Python? or they are the samething?! 

*** I wanted to use PY2exe to deploy.  Can I still use Py2exe?!!

I am new at this. you can tell!!

---

### Post by days_of_ruin on 2009-03-03
> **Flimm said:**
> 2) You could just use dictionaries, depending on how advanced you want the code to be, and how many features you need.

4) I learnt PyGTK from the [tutorials](http://www.pygtk.org/tutorial.html) and especially the [reference manual](http://www.pygtk.org/reference.html) on their site.

Something I found recently that I wish I had found sooner:
[pygtk faq]("http://faq.pygtk.org/index.py?req=index")

For books I would recommend "Python in a nutshell" and "Learning Python" both from O'Reilly.

---

### Post by days_of_ruin on 2009-03-03
> **mal_conductor said:**
> Flimm,  Thanx for the answer; however, I am confused.

What is PyGTK:
- Is it python-based developer?
- Do I still need IDLE or does PyGTK replaces IDLE?
- Is it an add-on that get imported into IDLE when developing?
- Does learning PyGTK replace learning Python, or learn PyGTK in addition to Python? or they are the samething?! 

*** I wanted to use PY2exe to deploy.  Can I still use Py2exe?!!

I am new at this. you can tell!!


PyGtk is a gui toolkit.[http://pygtk.org/]("http://pygtk.org/")

---

### Post by stevescripts on 2009-03-03
mal_conductor - IDLE is written using Tkinter as its GUI toolkit.

Although many folks dont care for its appearance Tkinter is pretty easy to use, and has been around for a long time.  Many simple examples floating around this forum.  Mixing other GUI toolkits with IDLE, can lead to problems -  also, you don't require any sort of IDE - you can always write python with gedit, or any other text editor.

Good Luck with your programming.

Steve

---

### Post by nvteighen on 2009-03-03
I'd rather forget GUI programming for a while. Learn the language first. Otherwise, you'll be trying to do things without having the proper base knowledge to do it.

Also, keep in mind you don't need any IDE. A text editor like Gedit is enough to have some decent Python environment; use the plugins and you'll be ready.

In GNU/Linux environments it's absurd to deploy using binary executables; you know "executables" are defined by the permissions set so you just tell the script file to be executable and use the shebang (#!/usr/bin/env python)... and nobody will care if it is a Python or Perl script or a native-binary.

In Windows maybe Py2exe makes more sense.

---

