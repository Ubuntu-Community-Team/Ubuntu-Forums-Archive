---
title: "Program written with Qt Designer"
date: 2007-08-15
forum: Programming Talk
---

### Post by NeillHog on 2007-08-15
After recently coming over to Kubuntu I found that an important utility I needed was missing in the Linux world so I wrote it in Python and created a GUI for it with Qt Designer.

My question is - If I now want to let some one else have the program do they need to have Qt installed?

If so, this makes life rather more complicated than I had hoped. I can not see any one going through the entire installation process at [ftp://ftp.trolltech.com/qt/source/INSTALL](ftp://ftp.trolltech.com/qt/source/INSTALL) just for a small utility. It took over an hour on my PC.

Is there any way of bundling up everything that my friend needs and sending it him so that it will work "out of the box" on his Linux system?

Thanks as always. I appreciate all your help.
Neill

---

### Post by JustAboutRealJAR on 2007-08-15
I'm pretty sure it doesn't take much more than 10 minutes to install the qt libraries...

I know it takes a long time to install the design utilities, but users don't need all that stuff, and also if they're installing your app via synaptic, the qt libraries should be installed as a dependancy.

I could be wrong but I'm almost certain this is how it works

---

### Post by Jucato on 2007-08-15
Your friend doesn't need to have Qt Designer installed if all he needs to do is to compile and run the program. Qt Designer is only necessary if he wants to view or modify the .ui files. However, to compile the program, he still needs the Qt headers and libraries (libqt3-mt-dev or libqt4-dev), but that's not surprising since you need headers/libraries for anything you want to compile in the first place.

If you want, you could probably just give your friend the compiled/binary form or package it into a .deb for him.

---

### Post by NeillHog on 2007-08-16
Thank you both for your answers. This is what makes Python /Linux fun - Good answers to questions.

Unfortunately I am very new to Linux (four weeks) and Python (one week) so hardly "the expert".

Do I understand you correctly that I can send a Linux user my .py files and as long as he/she has done sudo apt-get install libqt4-dev beforehand then they should run?
That is a lot simpler than all the stuff I went through.

Another, but similar question. My program is written in a documents called xx.py and calls the GUI which is in yy.py Obviously any one who wants to run my program will nee both files. Is there any easy way to combine them (other than in a zipped file). I suppose I still have my Windows head on an am thinking of the exe that I could send containing everything.

Thanks again and sorry about all the questions but it is better to ask than do things wrong :-)

Neill

---

### Post by JustAboutRealJAR on 2007-08-18
I don't know. I'm new to python programing as well, but I would also like to know about that.

---

### Post by Max Luebbe on 2007-08-18
Python is an interpreted language - so if your end user has installed the necessary libs they can run your .py files. If there is a configuration error, or they don't have the libraries the interpreter will choke on the first import statement that tries to access QT and can't find it.

With regards to distributing your app to end users, read up on python's [distutils]("http://docs.python.org/dist/dist.html") package

---

### Post by pmasiar on 2007-08-19
> **NeillHog said:**
> Do I understand you correctly that I can send a Linux user my .py files and as long as he/she has done sudo apt-get install libqt4-dev beforehand then they should run?

Yes. The "sudo apt-get install libqt4-dev" is much simpler, and much more reliable, than any GUI installer, isn't it?

Assuming, of course, that the other user has same distro you have, or at least debian-based distro, which uses apt-get. Also, did you used only standard libraries, or installed something special too?

There are always some moving parts - especially in such flexible system like open-source operating system + other parts. It might be that different distros have different versions of Python, which have different libraries, etc, but you should be fine 99% of the time.

> My program is written in a documents called xx.py and calls the GUI which is in yy.py Obviously any one who wants to run my program will nee both files. Is there any easy way to combine them (other than in a zipped file). 

As always, there are couple ways to do it. "Proper" way is to use distutils, as mentioned, which will create distributable package. But for such simple task as you have it is too much hassle.

I recommend you to write down instructions (save this, create dir, copy that, type this, etc), then try to follow them, installing your code on different computer. Will it work? You can easily create 10GB partition with another Ubuntu install, and try it there. Or at least at different directory on your computer.

Next time when you want to create simple GUI, you may want to look at EasyGUI python module. Not as fancy as the one you used, but much simpler.

Good luck!

---

### Post by Mirrorball on 2007-08-19
If his program is in Python and his friend won't modify it, I think the only real dependency here is python-qt4, not libqt4-dev, right? His friend won't have to compile anything.

---

### Post by Jucato on 2007-08-19
Well, the OP was a bit vague on what he would need his friend to do with his program, or how his fried is going to use it.

If your friend just wants to run the Python program, Mirrorball is right, all he needs to have installed is the python-qt bindings, python-qt3 or -qt4, depending on which version of python you used to create it. That's all that is needed to run a Python program using Qt.

---

### Post by Max Luebbe on 2007-08-19
If you use distutils, it becomes very easy to manage installations of the actual python code....

Why not distribute with an install script and an uninstall script

the install scripts would run the appropriate apt-get to grab the dependencies, and then use the install command on your python distribution to install it.

Doing something like this takes much complexity out of the process, because your end user doesn't need to worry about missing dependencies.

---

### Post by pmasiar on 2007-08-19
> Why not distribute with an install script and an uninstall script
Yes but still you need to know if it is Red Hat or debian system at minimum. OP never specified what distro her friend uses.

---

