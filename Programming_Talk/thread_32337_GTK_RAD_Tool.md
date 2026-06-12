---
title: "GTK RAD Tool??"
date: 2005-05-07
forum: Programming Talk
---

### Post by Kimm on 2005-05-07
I was woundering if anyone here know about some cind of RAD tool for GTK, not just like Glade, I mean a tool more like visual basic, I draw a form and write the code for it. I'd need this type of tool since I am writing an application that needs a GTK GUI, but I dont know any GTK, the rest of the app is done i.e. it canallredy do everything it was ment to do, but its not graphical.

I tried using Glade, but I dont know how to implement my code into the generated code.

btw, this is a C++ project, but could easily be ported to C...

---

### Post by fjleal on 2005-05-07
[QUOTE=Kimm]I was woundering if anyone here know about some cind of RAD tool for GTK, not just like Glade, I mean a tool more like visual basic, I draw a form and write the code for it. I'd need this type of tool since I am writing an application that needs a GTK GUI, but I dont know any GTK, the rest of the app is done i.e. it canallredy do everything it was ment to do, but its not graphical.

I tried using Glade, but I dont know how to implement my code into the generated code.

btw, this is a C++ project, but could easily be ported to C...[/QUOTE]
Take a look at Anjuta. The new version 2 will be out soon, and it seems to do want you need.

[http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)

Meanwhile, you can try version 1.2.2...

---

### Post by Kimm on 2005-05-07
I'm using anjuta, but I dont see how it can work the way you say?
there is no way to "draw" windows in anjuta, is there??

---

### Post by oracle2025 on 2005-05-07
On Linux, you have usually seperate tools, one for designing GUIs, another for writing your code, you could for example use Glade für GUI, und Anjuta for coding.

You will propable need to have a look at some GTK-Examples to understand how to integrate the Glade-Output into your project.

However, there are integrated tools available too. Take a look at [Gambas](http://gambas.sourceforge.net/) for example, Gambas provides an Environment more like you described before. It features a programming language that is a bit like VisualBasic.

Another Hint I'd like to give, is that you might want to consider python as a programming language if you want to do GTK+ Stuff.

---

### Post by vague- on 2005-05-07
You can use libglade with the Glade XML file.  All you need to do is save the output of Glade and then it can be loaded into your application dynamically.  There is libglade support for many languages (including being part of gtkmm, if you wish to use C++).  All you need to do is to assign the names for the callbacks, pretty much and you are writing the code applied to the widget you are looking at.

Any Glade user guide will show you how to set the callback names, but it is pretty easy.  I often have Glade open on one desktop and an IDE open on another desktop, and I do not find it cumbersome versus an integrated GUI designer.

---

### Post by Kimm on 2005-05-07
well I supose that does sound good... I'll try using glade and see what I can do...

> 
Another Hint I'd like to give, is that you might want to consider python as a programming language if you want to do GTK+ Stuff.


Yes, python is a great language but I still refrain from programming in it... I prefer truly binary languages since they run faster... Java is another language I somewhat disike, as long as its not compilerd using gjc

---

### Post by LordHunter317 on 2005-05-07
[quote="Kimm"]Yes, python is a great language but I still refrain from programming in it... I prefer truly binary languages since they run faster...[/quote]For a desktop GUI app, you'll never notice if the application is properly written.  And these days, languages compiled directly to machine code are not necessarily faster than languages that are interpreted or compiled to byte code.  Advancments in JIT methods of bytecode compiliation make bytecode languages very viable, and you can use similar techniques on interpreted langauges (ignoring the fact python can be compiled to bytecode anyway).

> Java is another language I somewhat disike, as long as its not compilerd using gjcThere are plently of reasons to dislike Java, but the fact it's bytecode is not one of them.

---

### Post by Kimm on 2005-05-07
argh, I can not do this!!

anyone got a good tutorial??? :-x

---

### Post by achaycock on 2006-02-21
I realise that this is a vastly over-late reply to your question, but for future reference you may wish to look into monodevelop and a UI development kit named 'stetic'. It's still in the ealy stages of development but if you're still trying to develop RAD applications in Linux it could be worth a shot.

---

### Post by celloandy on 2006-02-21
If you're using Glade and coding in C++, you'll end up using the C++ Glade bindings, which are a part of the gtkmm library set.  Once you've installed the necessary gtkmm files from apt, have a look at the chapter on using Glade from the gtkmm docs: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch19.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch19.html), which explains the procedures.  You may want to consult other chapters or their guide if you've never done GTK+ programming before.  I don't use C++, much, and have never used these bindings, but if they're anything like the bindings for Mono or Python, I don't imagine they're particularly difficult to master.

Andrew

---

### Post by damvcoool on 2006-10-30
You can try Gambas2 but you have to compile it your self.

as far as i know, it has a componet that allows programs to be made with GTK bidding so it take the look of GTK themes, what i mean is that you do the same but with the GTK for the controls, instead of QT.

GAMBAS and GAMBAS2 are just like visual basic, and the programing language is also similar, since it's BASIC :D :D

---

### Post by psychicdragon on 2006-10-31
MonoDevelop is probably the closest thing to Visual Basic.

---

