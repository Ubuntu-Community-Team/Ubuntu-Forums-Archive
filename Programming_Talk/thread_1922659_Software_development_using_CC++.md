---
title: "Software development using C/C++"
date: 2012-02-09
forum: Programming Talk
---

### Post by art_monu on 2012-02-09
Hii..
I am a beginner in the field of Computer Science. I have learnt both C as well as C++. I want to develop small softwares using C/C++.  Suppose I want to develop a calculator application for linux(preferably), I can write the necessary code to do the calculations but I don't know anything about how to develop the GUI of the calculator and how to link my program with the calculator buttons(GUI).. 
    Please tell me how to do that. I would be very grateful if you could point me to some online tutorial ao reference or some related book about software development using C/C++.
I couldn't find a place better than this to ask this question.. Please help me. :confused:

---

### Post by doobrie on 2012-02-09
> **art_monu said:**
> Hii..
I am a beginner in the field of Computer Science. I have learnt both C as well as C++. I want to develop small softwares using C/C++.  Suppose I want to develop a calculator application for linux(preferably), I can write the necessary code to do the calculations but I don't know anything about how to develop the GUI of the calculator and how to link my program with the calculator buttons(GUI).. 
    Please tell me how to do that. I would be very grateful if you could point me to some online tutorial ao reference or some related book about software development using C/C++.
I couldn't find a place better than this to ask this question.. Please help me. :confused:

I'd recommend looking at GTK.  The interface for C++ is GTKMM.  You can find lots of info on the site:

[http://www.gtkmm.org/en/](http://www.gtkmm.org/en/)

---

### Post by doobrie on 2012-02-09
You can also use Glade to design your user interfaces and then hook them up to your C++ code.  Glade produces an XML file that you can ship with your app that defines what the UI looks like.  If you like, you can incorporate this file into your executable though to stop people tampering with it!!

You can install Glade via the Ubuntu Software Center.

---

### Post by art_monu on 2012-02-09
How's Qt? Can I program GUI using C++ in that? Is there any good reference for Glade?

---

### Post by CptPicard on 2012-02-09
Qt is probably the nicest C++ GUI (and other stuff) framework there is... highly recommended.

---

### Post by doobrie on 2012-02-09
> **art_monu said:**
> How's Qt? Can I program GUI using C++ in that? Is there any good reference for Glade?

You can use Qt or GTK (or a few others TBH) - my preference is GTK, but everyone has their own favourites!

You can check out the docs for Glade at:

[http://glade.gnome.org/](http://glade.gnome.org/)

---

### Post by art_monu on 2012-02-10
thanks all. I think I will try Qt first..

---

### Post by doobrie on 2012-02-10
> **art_monu said:**
> thanks all. I think I will try Qt first..

Good luck :) .  Come back if you've got any questions.

---

### Post by ve4cib on 2012-02-11
If you're using Qt and C++ you might want to check out an IDE called QtCreator.  It has a really nice interface for creating Qt GUIs.

---

