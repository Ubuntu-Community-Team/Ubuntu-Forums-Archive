---
title: "Visual Studio for KDE?"
date: 2010-06-24
forum: Programming Talk
---

### Post by kooldino on 2010-06-24
Is there such a thing as a Visual Studio environment to create KDE applications?

---

### Post by slooksterpsv on 2010-06-24
KDevelop or MonoDevelop are the only ones I know of.

Personally I like Eclipse for C/C++. Eclipse does look like Visual Studio - try it out. Actually here's a screenshot:

---

### Post by nrs on 2010-06-24
KDevelop is the only KDE IDE. Though you can use the rest with KDE of course.
[http://www.kdevelop.org/index.html?filename=4.0/screenshots.html](http://www.kdevelop.org/index.html?filename=4.0/screenshots.html)
ATM you have to write your own CMakeLists.txt or Makefile.

---

### Post by Queue29 on 2010-06-25
Qt Creataor!! IMHO it's the best IDE available on the Linux platform, though its soul purpose is for c++ (qt) development. 

[http://qt.nokia.com/products/developer-tools/](http://qt.nokia.com/products/developer-tools/)

---

### Post by kooldino on 2010-06-25
> **nrs said:**
> KDevelop is the only KDE IDE. Though you can use the rest with KDE of course.
[http://www.kdevelop.org/index.html?filename=4.0/screenshots.html](http://www.kdevelop.org/index.html?filename=4.0/screenshots.html)
ATM you have to write your own CMakeLists.txt or Makefile.

Does KDevelop have a GUI interface / form editor?

> **Queue29 said:**
> Qt Creataor!! IMHO it's the best IDE available on the Linux platform, though its soul purpose is for c++ (qt) development. 

[http://qt.nokia.com/products/developer-tools/](http://qt.nokia.com/products/developer-tools/)

Interesting!  This may do the trick.  I'm downloading it now...got any tutorials or anything?  I'm totally new to linux development.

---

### Post by phrostbyte on 2010-06-25
> **kooldino said:**
> Does KDevelop have a GUI interface / form editor?

Yes of course. Qt Creator does as well.


> 
Interesting!  This may do the trick.  I'm downloading it now...got any tutorials or anything?  I'm totally new to linux development.

[http://doc.qt.nokia.com/](http://doc.qt.nokia.com/)

---

### Post by kooldino on 2010-07-27
I hate to say it, but I'm pretty lost on QTCreator.  I guess I figured it would be more like Visual Basic.

Sure, I can make forms and such, but then I have no idea where to go from there.  I tried reading the docs, but they were a bit over my head.  I was hoping for more of a simple step by step intro to get me started.

For instance, I made a button named "QPushButton" on mainwindow.ui, and I expected this code to work:

```
void MainWindow::on_pushButton_clicked()
{
    QPushButton.text = "hello";
}

```

Is there a QT Creator for dummies or something?

---

### Post by MarkMcCartney on 2010-07-28
I am also looking for something a little more like VS. We have developed an inhouse application and I want to move it to linux. The goal is to turn windows off and go with Linux completly. I can port to webbased but would like a desktop IDE simple one that is. I herd that the mono project were developing a IDE VS like product. If someone has info on this can they post a link.

PS my first post :popcorn:

Cheers
Mark

---

### Post by WitchCraft on 2010-07-28
> **MarkMcCartney said:**
> I am also looking for something a little more like VS. We have developed an inhouse application and I want to move it to linux. The goal is to turn windows off and go with Linux completly. I can port to webbased but would like a desktop IDE simple one that is. I herd that the mono project were developing a IDE VS like product. If someone has info on this can they post a link.

PS my first post :popcorn:

Cheers
Mark

The mono project is about C# support, not C/C++.
QT is about C++, with no C# binding AFAIK.
Mono is for C#, and the IDE is called monodevelop 
apt-get install monodevelop

Mono Visual Basic is kind of a neglected byproduct. Stick to C#.

If you want C# binding for your widgets, stick to GTK#, that is to say GTK+ if you develop in C/C++, and not QT.
Glade is the Visual IDE used for creating GTK forms.


wxWidgets is another alternative. It has the better license, and IMHO is technically better than QT.
The IDE for wxWidgets is wxFormBuilder.
wxWidgets also has C# bindings, but the mono-project is GTK centric.


When I developed a replacement X-manpage-viewer application in wxWidgets (converting manpages to html and displaying it in a browser window), it came to my attention that the GTK project seems to be better than wxWidgets. I had to compile wxWebkit (230 MB shared library to integrate a Webkit-based browser).

The GTK webkit binding was much smaller, like 2 to 20 MB.
However, I never compared the functionality. I suppose wxWidgets was a 'tiny'(about 200 MB) bit more complete.
The advantage of wxWidgets is that it ony is an abstraction interface to native APIs, much like MFC. That way your applications looks like native Windows or Linux applications, and not like GTK/QT. Unfortunately, that can cause problem when you want to create more creative GUIs, because buttons/images/tabs and spaces aren't the same size everywhere.

As said, if you want to use mono/C#, stick to GTK+.

---

### Post by Zugzwang on 2010-07-28
@kooldino: 

Normally, in development documentation in "the Linux world", people assume that you *first* try building some very minor applications without IDE and *then* move to an IDE. This way, you will get to know if the troubles you are having come from the IDE or not.

Having said that (even though it might be unrelated to your problem), the following link is useful for QT beginners:

[http://doc.trolltech.com/4.5/how-to-learn-qt.html](http://doc.trolltech.com/4.5/how-to-learn-qt.html)

Having a look at your example, you appear to be not so familiar with C++. First of all, "QPushButton" is the class name of your push button and not the object name. Setting the text can only work on an object. Then, assigning a Text using the "=" operator is very un-C++-ish. While technically this could work by operator overloading, there's a rule of thumb that getters and setter function are normally used for such purposes. Thus you might want to use the "setText" function. See, e.g. here: [http://doc.trolltech.com/4.5/qpushbutton.html](http://doc.trolltech.com/4.5/qpushbutton.html) Finally, it is likely that the push button is only stored as a pointer, so you will need to dereference the pointer before accessing the objects' functions. This can be done by replacing the "." by "->".

Thus, the code you might want to have might look like:
```

void MainWindow::on_pushButton_clicked()
{
    pushButton->setText("hello");
}

```

Adjust the identifier "pushButton" according to how you named the button.

---

