---
title: "Python 3.x and PyQt install commands"
date: 2014-10-16
forum: Programming Talk
---

### Post by rich1939 on 2014-10-16
I've been away from Ubuntu for a few years and need some help in issuing the appropriate apt-get commands to install Python 3.x and PyQt, with its GUI development program. I saw a concise post concerning this a few weeks ago, but didn't write the commands down. Now I just installed Ubuntu 14.04 and need a list of the appropriate commands to install these programs.

I'd also like a suggestion on what IDE to use for PyQt development. I had previously used CODEBLOCKS for C++ and GTK a development, but am open to a more appropriate IDE for PyQt development.

I'm an old-timer, with many years of programming experience, but am a neophyte in getting setup for PyQt development on Ubuntu. Any help, suggestions, lists of commands to get me started,will be greatly appreciated.

Thank you.

Rich Parker

---

### Post by ian-weisser on 2014-10-18
Python 3.4 is already installed with 14.04.

---

### Post by rich1939 on 2014-10-18
> **ian-weisser said:**
> Python 3.4 is already installed with 14.04.

Thanks for the confirmation about Python 3.4. I also need to install PyQt and the GII development app, and any documentation on using PyQt on Ubuntu.

---

### Post by oldfred on 2014-10-18
I normally install using synaptic.
But I now see pyqt4 & there is  pyqt5. 
Have not tried converting anything to qt5 yet and do not see much in Ubuntu, yet.

I have just used geany and when I reinstall Ubuntu install a few basic pyqt. But then when I run my little test programs they some up with something I forgot and I go back in install those.
Then I find I forgot qt4-designer and my python-qt4-sql.

[http://zetcode.com/gui/pyqt4/](http://zetcode.com/gui/pyqt4/)
[http://lionel.textmalaysia.com/a-simple-tutorial-on-gui-programming-using-qt-designer-with-pyqt4.html](http://lionel.textmalaysia.com/a-simple-tutorial-on-gui-programming-using-qt-designer-with-pyqt4.html)

---

### Post by Erik1984 on 2014-10-19
The package you need for Qt**5** development on Ubuntu with Python is 
```
python3-qt5
```
This will install the necessary python modules for Qt5 development.

There is also a package that contains **pyuic5**. This is a CLI tool to convert the interfaces (.ui files) designed in the GUI application (QT Designer) to .py files.
```
pyqt5-dev-tools
```

---

### Post by rich1939 on 2014-10-19
Thank you, Eric. That's exactly what I needed. I knew it would be simple...I have just been away far too long. 

-Rich

---

