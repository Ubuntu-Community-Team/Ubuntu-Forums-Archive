---
title: "Python GUI"
date: 2012-03-27
forum: Programming Talk
---

### Post by netizen99 on 2012-03-27
I have created a python script for collecting some stock market data daily in My Ubuntu 11.10 PC. It work fine, now I want to create a GUI for it.

May I know what is the easy way to do so? For me, there are to many option rather than too few. What's I need is a easy to use one? What should I consider? Qt? tkinter? I'm a just a beginner for Linux/python programming.

---

### Post by nothingspecial on 2012-03-27
*Thread moved to **Programming Talk**.*

---

### Post by MG&amp;TL on 2012-03-27
PyGTK (gtk2) or python-gobject (gtk3) are quite good, there's loads of tutorials for pygtk, for gtk3 there's [http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html)

---

### Post by CynicRus on 2012-03-27
[http://wiki.python.org/moin/PyQt4](http://wiki.python.org/moin/PyQt4)

---

### Post by azzamite on 2012-03-27
[http://www.wxpython.org/screenshots.php](http://www.wxpython.org/screenshots.php)

The examples are quite useful.

---

### Post by alexfish on 2012-03-27
could have a look at

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

---

### Post by charlie_b on 2012-03-27
I would suggest Tkinter, for a beginner it is easy to learn. While perhaps not as powerful as some of the other toolkits, I think it is a good place to start.

---

### Post by cgroza on 2012-03-27
wxPython is worth looking at.

---

### Post by llanitedave on 2012-03-28
Normally I'd agree with those who recommended the powerful, full featured GUI toolkits, but for a beginner who just wants something simple and easy to learn, I think Tkinter is a great introductory GUI.

---

### Post by netizen99 on 2012-03-28
Woo, really the problem for linux is you have too many choices. What's advantage of various suggested tools?

---

### Post by r-senior on 2012-03-28
Have a look on [http://www.zetcode.com](http://www.zetcode.com). There are examples of each, apart from Python/GTK3 but the tutorial was linked earlier in the thread.

The trade-offs are simplicity vs cross-platform vs desktop integration. Also personal preference and availability of tools, e.g GUI designers. Run a few examples and dive in to whatever you think you'd be happy with. They deal with similar concepts so it's not too difficult to change your mind.

---

### Post by oldfred on 2012-03-28
I have done something similar for the last few years. It is easy to get the stock prices or history to download but then with a gui it becomes a lot more. 

I have used gtk, but wanted data in sql and decided I wanted to separate gui code from logic so I use glade to create gui and sqlite to store data. I got it to display daily download and extend my stocks value.

So then I decided to try qt with qt4 Designer to design gui. I was able to use the same python code for the sql statements but gui was totally different.

I would suggest using glade(gtk) or Designer(qt) to create gui, but it is a big leap as they have their own set of logic, and understanding some of the code with just something like Tkinker may be better to start with. My goal was more to learn python &  how to work with a gui. But I had some experience with MS Access and vba code behind the gui screens for sql statements. And I was still somewhat lost learning. I knew I could do something but needed exact syntax for python.

I am now trying to convert to python3 and finding lots of little issues that 2to3 does not handle.

---

### Post by netizen99 on 2012-03-28
In such case, I probably will start with tkinter first. Do I need install additional package first? It seem I can't start Tkinter sample by default installation

What package I should install?

In long run I want to allow my Nokia phone to access my data in my Ubuntu PC, but let me work with the PC first.

---

### Post by oldfred on 2012-03-28
synaptic has python-tk and python3-tk. 

I thought it was installed as part of python? 

What version on Nokia phone? They used to own qt and spun it off when they went to Windows phones and effectively obsoleted all their old operating systems.

---

### Post by netizen99 on 2012-03-29
really? let me check at home. My Nokia is 701 with Symbian Belle. I still prefer Symbian Belle as it still can do what I need and round 60% cost of Iphone for Android Smartphone.

---

### Post by MG&amp;TL on 2012-03-29
> **oldfred said:**
> synaptic has python-tk and python3-tk. 

I thought it was installed as part of python? 



I thought it was too. Evidently not, you can install (for python 2), *python-tk* or, (for python 3), python3-tk. import command is:

```
import Tkinter
```

---

### Post by nutrapi on 2012-03-29
my top picks are quickly for ease, pyqt for looks+ease and tk for cross-platform abilities without additional requirements.

---

### Post by alexfish on 2012-03-29
Here is an Interesting one not often mentioned,

Most languages have a means of process control , IE . set a variable to the command : instance "set a [exec lsusb] , where a = result of the "lsusb" command , or any "executable" or "executable script"
in this instance it could be "My-stocks-and-shares"

I use this method in most gui building, it really does not matter what the GUI builder base language is as long as it can handle process control or the ability to exec the script, and a reasonable method of parsing the data, "a common use in TCL" and a easy method of updating lists boxes or grids etc etc.

it did not take me to get the hang of this one "Kommander"
when in editor the resulting data is shows stdout or the stderr

although it has a run time , Well worth looking at , should be in the repos.

---

