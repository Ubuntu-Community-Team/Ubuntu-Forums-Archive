---
title: "Python GUI creation"
date: 2007-08-06
forum: Programming Talk
---

### Post by cmat on 2007-08-06
Are there any tools that can speed up the task of making GUIs for Python?

---

### Post by slavik on 2007-08-06
Glade3 and libglade.

---

### Post by smartbei on 2007-08-06
There are tutorials on the internet about linking Glade and wxGlade to python. See:
[Google search - glade python tutorial]("http://www.google.co.il/search?hl=iw&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=glade+python+tutorial")

---

### Post by fatsheep on 2007-08-06
> **cmat said:**
> Are there any tools that can speed up the task of making GUIs for Python?

If you want a simple example of glade and pygtk in action you could take a look at the [GUI I just made](http://ubuntuforums.org/showthread.php?t=518395).

---

### Post by pmasiar on 2007-08-06
simplest way to create (very simple) GUI is [EasyGUI](http://www.ferg.org/easygui/) - it is so simple it even does not have events. :-) Of course you cannot create too complicated GUIs with it - just the easy ones :-)

---

### Post by LaRoza on 2007-08-06
> **pmasiar said:**
> simplest way to create (very simple) GUI is [EasyGUI](http://www.ferg.org/easygui/) - it is so simple it even does not have events. :-) Of course you cannot create too complicated GUIs with it - just the easy ones :-)

That is very interesting, it is going in my wiki...

---

### Post by tc101 on 2007-08-06
What about Boa Constructor?  I am just learning python and was planning to get into doing GUIs soon.  I read somewhere that Boa Constructor was a good tool.

I worked for years doing GUIs in Visual Basic and MS Visual Studio.  Those are great tools and I hope to find something in the open source world that is equally quick, easy and powerful.

---

### Post by tc101 on 2007-08-06
I installed Glade Interface Designer.  I created a new project.  I clicked on the window icon in the Palette and it created a window.  All of this works just like the tutorial said.  However, when I try to add any controls to the window nothing happens.  I click on a control in the pallet and it is not created in the window.  I try to drag it to the window and nothing happens.  What am I doing wrong?

---

### Post by Nekiruhs on 2007-08-06
> **tc101 said:**
> I installed Glade Interface Designer.  I created a new project.  I clicked on the window icon in the Palette and it created a window.  All of this works just like the tutorial said.  However, when I try to add any controls to the window nothing happens.  I click on a control in the pallet and it is not created in the window.  I try to drag it to the window and nothing happens.  What am I doing wrong?Click on the widget you want, then click on the window. You use containers to align them. Without containers only one widget per window is possible. Heres one of my glade files. Its in the tar.gz along with its python file.

---

### Post by tc101 on 2007-08-06
Thanks.  That is so simple, but I needed someone to tell me.

---

