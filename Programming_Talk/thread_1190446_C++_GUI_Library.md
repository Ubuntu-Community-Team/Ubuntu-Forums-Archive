---
title: "C++ GUI Library"
date: 2009-06-17
forum: Programming Talk
---

### Post by Java Geek on 2009-06-17
I have to write several programs for Kubuntu which have GUIs. Can anyone give me pros and cons of each? E.G. GTK, OpenGL, or anything else. This code must be written in C++, otherwise I would definitely use Java's Swing!

---

### Post by Mirge on 2009-06-17
My very inexperienced opinion is Qt 4. I'm told it's well documented, uses C++, and from what I've used with it thus far, it seems to be pretty dang neat and relatively easy.

I haven't tried GTK, but I have heard that GTKmm is a C++ wrapper for GTK.

Also have wxWidgets, FLTK and others to choose from.

EDIT: One con to Qt 4 though is its dual licensing. You can choose from the LGPL license or a commercial license (which is quite expensive!).

---

### Post by Java Geek on 2009-06-17
Thank you Mirge, I'll look into it!

---

### Post by SledgeHammer_999 on 2009-06-18
> **Mirge said:**
> EDIT: One con to Qt 4 though is its dual licensing. You can choose from the LGPL license or a commercial license (which is quite expensive!).

This is old stuff. Qt4 is under LGPL for commercial use too nowadays.

---

### Post by Mirge on 2009-06-18
> **SledgeHammer_999 said:**
> This is old stuff. Qt4 is under LGPL for commercial use too nowadays.

[http://www.qtsoftware.com/products/licensing/licensing](http://www.qtsoftware.com/products/licensing/licensing)

---

### Post by SledgeHammer_999 on 2009-06-18
for the LGPL version:
> This version of Qt is appropriate for the development of Qt applications (proprietary or open source) provided you can comply with the terms and conditions contained in the GNU LGPL version 2.1

They offer a commercial license for who want to program with closed source **and** not comply with LGPL

---

### Post by Mirge on 2009-06-18
> **SledgeHammer_999 said:**
> for the LGPL version:


They offer a commercial license for who want to program with closed source **and** not comply with LGPL

Don't really know how you'd release a program commercially and supply source code... unless you were selling support or something for the software.

---

### Post by johnl on 2009-06-18
LGPL would mean that you don't need to release the source code to your program if you link with the QT libraries.  You would only need to release any changes made to the library itself.

This is the (basic) difference between LGPL and GPL.

---

### Post by Mirge on 2009-06-18
> **johnl said:**
> LGPL would mean that you don't need to release the source code to your program if you link with the QT libraries.  You would only need to release any changes made to the library itself.

This is the (basic) difference between LGPL and GPL.

Ahhh okay :). Thanks for clarifying!

---

### Post by fr4nko on 2009-06-18
In my humble experience:
Qt is very good from the technical point of view but I don't like it because:

[LIST]
[*] the C++ custom preprocessor (moc, or something like that)
[*]the willing to provide with the library everything you may need, even general purpose utilities. I consider this a defect typical of commercial applications of frameworks. The library tend to became huge and the programmer is tied to use Qt for everything he need, even to concatenate strings or things like that.
[/LIST]
Having said that, Qt can be an excellent choice, it is just that I don't like it.

But the toolkit of choice for me is another one, the FOX toolkit. I like it because is lean, simple minded and yet powerful and the applications looks nice even if it is not at the level or other mainstream toolkits. It is also cross-platform and it is actively developed.

I will avoid gtkmm because it is just a wrapper around gtk, so IMHO it is better to use gtk directly but the API are in C, not C++.

Francesco

---

### Post by Habbit on 2009-06-18
> **fr4nko said:**
> I will avoid gtkmm because it is just a wrapper around gtk, so IMHO it is better to use gtk directly but the API are in C, not C++.

Gtkmm is not "just a wrapper", it's a true binding which fully embraces the OO paradigm, lets you connect events to class members, etc.

---

### Post by zolookas on 2009-06-18
Kubuntu comes with KDE which uses Qt.
Qt applications are usually written in C++.
So Qt is what you need. Try QtCreator IDE.

---

### Post by loell on 2009-06-18
another C++ cross platform GUI framework you might wanna check is **fox**.

---

### Post by kike_coello on 2009-06-20
you should definitely use gtk, its easy to program, in a week i was able to program the gui for a poker timer, and there are a bunch of tutorials online

---

