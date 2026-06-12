---
title: "Looking for Python tutorial that has a GUI connecting to a database"
date: 2014-02-19
forum: Programming Talk
---

### Post by PopsTheSailor on 2014-02-19
I'm new to Python and am going to write my own cookbook program to help me learn the language. I'm looking specifically for a tutorial that involves connecting a Python GUI front end to a back end database. I haven't picked the DB or the GUI tool yet and would prefer something on the easier side but again, I want the tutorial to specifically include connecting text boxes to tables, searching the data, etc..

Anyone know of one?

---

### Post by oldfred on 2014-02-19
You are jumping into the deep end of the pool.

I did the same several years ago,except my choice was financial based and there are a lot of other programs, but I also wanted to learn python. I still really do not know what I am doing, but have a somewhat working system.

My experience was years of dBase, and then Access with vba and using sql in code not just linking to queries.  

But I had to learn a new programing environment, python, gui generator, and a new sql front end so I could test my sql statements.
I choose geany, glade for pyGTK, python 2.7, sqliteman and sqlite. But each of those can be many other choices.
After getting a system somewhat working I changed GUI from GTK to qt with QT4 designer.
I spent a lot of time searching for examples with bits of code, small apps that I could copy into geany and see how they work, etc.

But now python is version 3 and qt is up to version 5, and I have yet to try to convert to those. (more fun).

I found a lot of downloadable pdfs and some examples, but it depends on what versions & gui you want.

Note sure if all these links still work.
[http://www.python.org/](http://www.python.org/)
qtdesigner image viewer code
[http://www.harshj.com/2010/04/page/2/](http://www.harshj.com/2010/04/page/2/)
Simple first designer & python example
[http://lionel.textmalaysia.com/a-simple-tutorial-on-gui-programming-using-qt-designer-with-pyqt4.html](http://lionel.textmalaysia.com/a-simple-tutorial-on-gui-programming-using-qt-designer-with-pyqt4.html)
[http://zetcode.com/tutorials/pyqt4/](http://zetcode.com/tutorials/pyqt4/)
PyQt v4 - Python Bindings for Qt v4
[http://www.opendocs.net/pyqt/pyqt4.html](http://www.opendocs.net/pyqt/pyqt4.html)
[http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qtsql.html](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qtsql.html)
GUI Programming with Python: QT Edition older 
[http://www.commandprompt.com/community/pyqt/book1](http://www.commandprompt.com/community/pyqt/book1)
creating/using UI files
geany python3
[http://terminalobsession.blogspot.com/2012/06/how-to-get-geany-to-use-python3-as-its.html](http://terminalobsession.blogspot.com/2012/06/how-to-get-geany-to-use-python3-as-its.html)

HOWTO Create Python GUIs using HTML
[http://www.aclevername.com/articles/python-webgui/](http://www.aclevername.com/articles/python-webgui/)
[http://docs.python.org/tutorial/index.html](http://docs.python.org/tutorial/index.html)
Recipes, sample code
[https://help.ubuntu.com/community/PythonRecipes](https://help.ubuntu.com/community/PythonRecipes)
[http://code.activestate.com/recipes/langs/python/](http://code.activestate.com/recipes/langs/python/)
Gui & editors:
[http://wiki.python.org/moin/GuiProgramming](http://wiki.python.org/moin/GuiProgramming)
The Python GTK+ 3 Tutorial
[http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html)
[http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)

Editors:
Too many choices but many are free so you can try them
[http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors)

This was one of the first I used for gtk.
builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)

---

### Post by PopsTheSailor on 2014-02-19
Great info! The tool set is my other conundrum. I think at this point I just need to select them. I've been reading a lot of opinions and gotten nowhere. The great thing about the internet is there is a lot of info and opinions out there. The bad thing about the internet is there is a lot of info and opinions out there.

I think I'm leaning to Qt and sqlite with Python 3. I started with 2.7 but for my situation, I think 3 is the way to go. It's Python's future and it looks like I would have to get pretty far into the weeds before it impacts me and I don't expect to get that technical with my little programs I want to write.

---

### Post by oldfred on 2014-02-19
I have only tried a couple of things with python3. For a lot of my simple tests the only thing I had to change was the print statement. And I think now the latest 2.7 accepts the old ver2 print and the new ver3 print(). With geany there is not a debugger so I have a lot of print statements and comment them in & out if I want to check what a variable is doing.

---

### Post by xb12x2 on 2014-02-19
> **oldfred said:**
>  I changed GUI from GTK to qt with QT4 designer.


First, thanks for providing the links.

What were your reasons for changing the GUI from GTK to qt with QT4 designer?

---

### Post by oldfred on 2014-02-19
I think originally qt had some restrictions, since changed. But I do not ever plan on selling or distributing my klugey app. I have seen a few posts by those who really know python and I am a long way from that, but my system works for me and I still am learning, so restrictions were not important. 
I started with GTK as I use Ubuntu. But I also use several qt apps in Ubuntu like K3b and KMyMoney, so did not see any disadvantage to qt now. 

But it seems a bit easier to do some internal things inside a grid with qt and to display grids which I am using. I had set all my back end database import, update & query in a separate python file, so with the gui developer it was not a huge task to convert. Some learning curve on differences on how to do some details.

---

