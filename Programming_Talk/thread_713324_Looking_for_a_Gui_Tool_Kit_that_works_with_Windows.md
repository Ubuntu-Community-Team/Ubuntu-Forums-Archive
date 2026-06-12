---
title: "Looking for a Gui Tool Kit that works with Windows, Gnome/KDE and OSX"
date: 2008-03-02
forum: Programming Talk
---

### Post by thenetduck on 2008-03-02
Hi

I am going to try to make a couple of apps with C# (I like MonoDevelop a lot :) ) and I am a little confused on GUI implementation. The only gui have I every successfully used was Javas javax.sing. 

I was wondering, if I use a GTK+ tool kit to handle my graphics, will it work in Windows and OSX aswell? is there a better tool kit to handle cross platform graphics etc. 

Perhaps I have to create a new graphical implementation for each OS ? 

Thanks for the help,

The Net Duck

---

### Post by Jessehk on 2008-03-02
AFAIK, Trolltech's Qt is the most cross-platform toolkit. It's extremely well-documented, and there are hundreds of described examples. The only problem? It's a C++ toolkit. There might be C# bindings though....

[http://doc.trolltech.com/](http://doc.trolltech.com/)

---

### Post by thenetduck on 2008-03-02
Can you tell me (besides actual code structure etc.) if there are any advantages to programming in Mono with C# vs C++? Isn't the limiting factor the graphics tool kit? or is there some other limiting factore that Mono handles better than C++? 

I guess I am still trying to understand the concept of the .NET and Mono applications vs just building a program in c++. 

Thanks
 
The Net Duck

---

### Post by slavik on 2008-03-02
gtk#

---

### Post by mssever on 2008-03-03
wxWidgets was created for precisely this purpose--though GTK can be separately installed on Windows (as in GIMP). wx is a C++ library, but there are bindings available for a number of languages. I don't have any experience with Mono, so I don't know if wx is available for that platform. However, both Ruby and Python are cross-platform, have wx bindings, and aren't tied to whatever Microsoft's whim of the day might be.

---

