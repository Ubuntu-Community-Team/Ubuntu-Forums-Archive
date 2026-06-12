---
title: "My first look at Qt"
date: 2007-08-01
forum: Programming Talk
---

### Post by Obeleh on 2007-08-01
Hello all. 

Im an industrial automation student, I learned some C @ school and VB6 @ work (mostly from Ifix) Recently i've been following this nice Python tutorial. So I decided to take it from te commandline to the GUI :) And I noticed that Qt has the looks of Borland Builder and Visual Basic when it comes to creating apps. I googled this tutorial: [http://www.cs.usfca.edu/~afedosov/qttut/](http://www.cs.usfca.edu/~afedosov/qttut/)

My Python version = 2.5.1
Qt = 3.3.7

So all I needed was this PyQt. I've posted a rarfile and inside there is a screenshot of Synaptic.

Im at the very last step of the tutorial... The compiling.

```
python mygui.py
```

wich results in this error:

```
obeleh@obunteh:~/Test$ python MyFirstPy.py
Traceback (most recent call last):
  File "MyFirstPy.py", line 1, in <module>
    from qt import *
ImportError: No module named qt

```

Did I forget to do something? Perhaps I need to activate this PyQt thing? Could someone tell me where I went wrong and how I should do it instead? 

Thanks in advance

Sjuul Janssen

---

### Post by Obeleh on 2007-08-01
Couldnt see my attachment Trying here..

---

### Post by Obeleh on 2007-08-01
Trying again :( Im sorry for all these posts. But I cant add an attachment in editmode apparently

Woot it worked now :)

---

### Post by Motoxrdude on 2007-08-01
Sorry, cant help you. But as a future note select the "Go advanced" in the edit mode to add attachments ;).

---

### Post by Steveway on 2007-08-01
It works here. In the screenshot I can see that you don't have python-qt3 installed, maybe it's that.
Yes, if you use qt3 in your program you need of course python-qt3 not 4.
<!DOCTYPE UI><UI version="3.3" stdsetdef="1">

---

### Post by Obeleh on 2007-08-02
Thanks it works now... I just expected the versions to be downwards compatible :)

---

