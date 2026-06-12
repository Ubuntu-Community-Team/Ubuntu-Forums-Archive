---
title: "Glade generates PyGTK?"
date: 2007-09-11
forum: Programming Talk
---

### Post by mevets on 2007-09-11
I was under the impression that the Glade Interface Designer would generate the GUI code for PyGTK. I have installed Glade and see under options I can set the project to be C, C++ or Ada95, but I really don't see an option for python. Is there a way to leverage the output (resembles html) of this designer in python? Maybe theres a separate build?

---

### Post by DoktorSeven on 2007-09-11
I don't ever remember seeing a Glade option to generate pure Python code.  Generally with Python, you save the .glade file and have your Python program load it (using python-glade2, the Python version of libglade that loads and parses Glade files).

With the newest releases of Glade, they've even taken out the C/C++ code generation and gone with just supporting libglade.

---

### Post by tseliot on 2007-09-11
the .glade files which you can create with Glade are XML files which you can use from Python thanks to python-glade2.

---

### Post by mevets on 2007-09-15
How do I start to begin one of these glade files into a python project?

---

### Post by tseliot on 2007-09-15
Have a look at this tutorial:
[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)

---

### Post by moephan on 2007-09-15
Mevets,

The short answer is "you don't". This is really easy, but it's different than systems like Winforms and such where the form designer gereates code. Once you start using it, yyou may find that you like it much better because glade keeps the layout and the functionality cleanly seperated. In fact, code generating is deprecated in Glade for all languages, and I don't think it will even be available in the next major version of Glade.
 

The way it works is that Glade produces an XML file. Then in your python code you hook into the signals defined in the XML file. Here's a nice page that goes over the basic approach:
[http://www.serpia.org/pygtk](http://www.serpia.org/pygtk)

The basic steps to use a Glade file in your python code are:

1. import pygtk and gtk.glade
2. create a dictionary of signals you defined in glade and functions you defined in your code.
3. pass that dictionary to the signal_autoconnect function of the top level widget you defined in glade (the widget tree).

The libraries you imported will parse the XML and wire up the events for you! I won't show all the code because there are good examples in the link above.

HTH

Cheers, Rick

---

### Post by charlie763 on 2007-11-19
You're in luck! [Gladex 0.4.1 was just released today]("http://ubuntuforums.org/showthread.php?t=617152"). It's a Python application which takes a .glade file written in the [ Glade User Interface Builder]("http://glade.gnome.org/") and generates code in Perl, Python, or Ruby. The generated code uses libglade to draw a GUI and is not raw pygtk code.

The  [ manual]("http://www.openphysics.org/~gladex/gladex-manual/") can help you get started quickly. You basically just design a GUI in glade and use Gladex to generate code. The generated code will have a templated function of each callback you define in Glade. It takes less than ten clicks to go from a .glade file to a program that will execute.

**Where can I find more information?**
Project main page: [http://www.openphysics.org/~gladex/](http://www.openphysics.org/~gladex/)
Download: [https://launchpad.net/gladex/+download](https://launchpad.net/gladex/+download)
Manual: [http://www.openphysics.org/~gladex/gladex-manual/](http://www.openphysics.org/~gladex/gladex-manual/)
Launchpad: [https://launchpad.net/gladex](https://launchpad.net/gladex)
Howto: [https://help.ubuntu.com/community/GladexHowto](https://help.ubuntu.com/community/GladexHowto) (outdated)
About wiki: [https://help.ubuntu.com/community/Gladex](https://help.ubuntu.com/community/Gladex) (outdated)

---

