---
title: "gnome color chooser for gusty"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by jryprt on 2008-05-08
Where do I get it from & how to install
I do have the gnome-color-chooser-0.2.3.tar.gz on the desktop if someone can tell me how  to install it 
Thank you Jerry

---

### Post by phidia on 2008-05-08
I don't know how that specific program works, but to install a program from a packed archieve you can unpack by right clicking it and chossing "extract here"

Alternatively you can open a terminal and type tar xvf (the file name)

from there cd into the directory created from doing the above which should be /gnome-color-chooser-0.2.3  there should be a text file on the install procedure in that directory. You can read it with less is you don't want to go back and forth from terminal to gui.
However normally the method for installing is, again in terminal, type make
and when that completes type sudo make install.
Note make sure you have build-essential installed (sudo apt-get install build-essential) to find the installed program press Alt+F2 and type in the program name. Hope that helps.

---

