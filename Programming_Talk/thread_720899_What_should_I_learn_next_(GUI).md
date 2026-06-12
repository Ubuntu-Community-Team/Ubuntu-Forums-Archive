---
title: "What should I learn next (GUI)"
date: 2008-03-10
forum: Programming Talk
---

### Post by StOoZ on 2008-03-10
I was playing a bit with gtkmm and qt , gtk+ with netbeans.
now I wonder, Which one of those should I learn in depth? 
qt is nice, since its cross-platform, but , it requires some additional libraries that are not included with linux, compared to gtk+ .... im quite confused.

---

### Post by LaRoza on 2008-03-10
What languages are you interested in using?

Naturally, you will have to consult a manual for whatever you use, so it isn't all that much of a hassle to use more than one.

GTK (and its ports) and QT seem to be good choices, so you can't really lose.

You might want to look at wxWidgets:

* wxWidgets is free 
* wxWidgets looks native everywhere (that I have seen it)
* wxWidgets is easy to use (well, they all seem to be easy)
* wxWidgets can be used with many languages

---

### Post by StOoZ on 2008-03-10
im using C++.
a newbie question : can I use qt the make the gui and the native c++ libararies to make socket connetions?

im asking it , since it will basically be a software that was developed on linux but will work on both windows and linux...
thats why im aiming at ... (and no, I dont want to use java...).

---

### Post by LaRoza on 2008-03-10
> **StOoZ said:**
> im using C++.
a newbie question : can I use qt the make the gui and the native c++ libararies to make socket connetions?


Yes, as far as I know, you can. I don't see a reason why you couldn't.

---

### Post by lnostdal on 2008-03-10
> 
im asking it , since it will basically be a software that was developed on linux but will work on both windows and linux...
thats why im aiming at ... (and no, I dont want to use java...).


hum .. qt has a portable socket api .. if you want portability you should use that, not the native OS socket api (which isn't portable, of course)

edit:
here: [http://doc.trolltech.com/4.3/qtnetwork.html](http://doc.trolltech.com/4.3/qtnetwork.html)

---

### Post by Moezzie on 2008-03-10
Since you want it to be cross-platform and your using c++ i would recommend Qt. 
It as the same advantages as LaRoza said about wxWidget, exept for the many languages part. I know that there are bindings for pything, PyQt, witch work very well.

I have to recomend the Qt's documentation, its simply great!

---

### Post by StOoZ on 2008-03-11
thanks.
the documentation is indeed great, and I also got the book they recommend about : "C++ GUI Programming with Qt 4".
the reason I want to use it , is because the cross-platform capabilities.
I don't want to use java, and I still want to create a cross-platformed applications.

---

### Post by LaRoza on 2008-03-11
> **StOoZ said:**
> thanks.
the documentation is indeed great, and I also got the book they recommend about : "C++ GUI Programming with Qt 4".
the reason I want to use it , is because the cross-platform capabilities.
I don't want to use java, and I still want to create a cross-platformed applications.

If cross platform applications are your primary goal, you might want to look at another language. Python + Tkinter, Perl + Tk, Tcl/Tk, Java + Swing are more cross platform GUI solutions(Ruby can be thrown in there as well, I think it has Tk with it)

With those languages, you don't have to recompile or worry about binaries. Just write and run (compiling to byte code doesn't change it, as byte code is cross platform as well)

---

### Post by StOoZ on 2008-03-11
the reason I dont want to use these languages (yet...) is because im learning C++ , so for the moment, I would like to do things only with C++.

---

### Post by LaRoza on 2008-03-11
> **StOoZ said:**
> the reason I dont want to use these languages (yet...) is because im learning C++ , so for the moment, I would like to do things only with C++.

Makes sense. Well, I would recommend QT or wxWidgets. Both seem to do everything you want.

---

### Post by tseliot on 2008-03-11
With QT4 you can *almost* replace the whole standard library and make your life easier.

"An introduction to design patterns in C++ with QT4" is a book which can help you with this.

Oh, and working with QT4 is a real pleasure (with both C++ and Python).

---

