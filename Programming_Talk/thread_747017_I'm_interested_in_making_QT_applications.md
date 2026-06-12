---
title: "I'm interested in making QT applications"
date: 2008-04-06
forum: Programming Talk
---

### Post by TheOrangePeanut on 2008-04-06
I guess QT3 would be the way to go since I'm using KDE3, right?  If I use QT3, then later, when QT4 is more widespread and KDE4 is being used primarily, how hard will the transition be?  Surely it wouldn't be like learning a new api, right?

---

### Post by LaRoza on 2008-04-06
Googling for the differences yields: [http://doc.trolltech.com/4.2/qt4-intro.html](http://doc.trolltech.com/4.2/qt4-intro.html)

---

### Post by tseliot on 2008-04-06
Here is how you can port your qt3 application to qt4:
[http://doc.trolltech.com/4.2/porting4.html](http://doc.trolltech.com/4.2/porting4.html)

I suggest you to start with QT4 though. Your applications will work on KDE3, KDE4, GNOME, OSX, Windows.

---

### Post by xelapond on 2008-04-06
QT4 was out during KDE3.  I would recommend you start with Qt4, because it is more widespread and superior to Qt3.  What language are you going to do it in?

---

### Post by hums07 on 2008-04-06
> **TheOrangePeanut said:**
> I guess QT3 would be the way to go since I'm using KDE3, right?
No. I have used Qt4 in KDE3 and everything goes well.

---

### Post by TheOrangePeanut on 2008-04-06
Ah, okay, I didn't know that Qt4 was already that mature.  

I'm going to be coding in C++ or Python.  I haven't decided yet.  On one hand, I already have a good understanding of C++; on the other hand, Python would probably be pretty simple to learn; on yet another hand that I don't have, I don't know how the resources stack up as far as QT with C++ versus Pyqt :)  I guess we'll see... what would you guys recommend?

---

### Post by tseliot on 2008-04-06
I use PyQT4 and it's very easy to learn and to use. I warmly recommend you [this book]("http://www.amazon.com/Programming-Python-Prentice-Software-Development/dp/0132354187/ref=pd_bbs_1?ie=UTF8&s=books&qid=1207506274&sr=1-1").
This book explains how to use the designer, etc. it's a great book.

Switching from one language to the is very easy and sometimes you have to use C++ syntax for Python too. For example this is a line of code which I wrote (Python+PyQT4) :
```
stream << self.textEdit.toPlainText()
```

And we don't use "<<" in Python.

Furthermore the API is pretty much the same. I can read the documentation for C++ and use it with Python.

For rapid development I recommend Python. If you need better performance then switch to C++. I haven't had problems with Python so far.

If you choose C++ I can recommend [this book]("http://www.amazon.co.uk/Introduction-Design-Patterns-Perens-Source/dp/0131879057/ref=sr_1_4?ie=UTF8&s=books&qid=1207506508&sr=1-4") and/or[ this book]("http://www.amazon.co.uk/Programming-Prentice-Source-Software-Development/dp/0132354160/ref=sr_1_1?ie=UTF8&s=books&qid=1207506508&sr=1-1").

---

