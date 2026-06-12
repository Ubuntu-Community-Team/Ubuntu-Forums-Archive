---
title: "C++ Ide"
date: 2007-07-07
forum: Programming Talk
---

### Post by WastingBody on 2007-07-07
I'm moving more into Linux and I was wondering what a good C++ IDE would be. I would prefer to have a good GUI builder too.

---

### Post by kknd on 2007-07-07
Two months ago, I would tell you to use Anjuta + Glade.
Since I could not get any feature from Anjuta to work, plus some crashes, I can not recommend it to you.

For the small C++ that I have to do (basically some bindings for Java), I use Netbeans +  C++ pack. 
Maybe Eclipse CDT 4 is good too, but it dont worked for me too.

---

### Post by AlexThomson_NZ on 2007-07-07
IDE builder is Glade-3 (the more I use it the more I like it!)
IDE I use is Genie, fairly small simple editor.

_Important to understand:_ *Glade does not generate code on the fly (like VS, Delphi, etc.) it just creates an XML discription of your GUI.  Use the libglade library helper functions to access the GUI bits.*  It's really not too hard once you get started.  (apologies if that is obvious to you- I wasted a lot of time before discovering that!)

---

### Post by dempl_dempl on 2007-07-08
Kdevelop is a closest thing to Visual C++, Delphi and C++ Builder  it can get.
In latest version , it finally got internal Window (Form ) Designer, which made it a complete RAD tool.
You don't get as many components as with Delphi/BCB , but it gets  the job done.
Code completition works fine , with  couple of hick-ups :)

Plus it has couple of neat features that BCB, Delphi and Visual Studio don't. 



If you got used to Delphi , you can try Kylix ( if you used Delphi you know what is it ).

---

### Post by AlexThomson_NZ on 2007-07-08
We should point out too- if you are a Gnome man, use Glade, KDE use KDevelop, you can't really make a gnome app using KDevelop and visa-versa.

---

