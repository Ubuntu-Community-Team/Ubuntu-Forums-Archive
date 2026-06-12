---
title: "Just starting GTKMM, need a very simple tutorial"
date: 2011-05-20
forum: Programming Talk
---

### Post by u-noob-tu on 2011-05-20
after teaching myself C++ for about 3 months now, i think im ready for making gui interfaces with GTKMM. I know about the documentation at [www.gtkmm.org](www.gtkmm.org), but i just cant get my head around it. seems to start way up high instead if down low where i need to start. ive googled for tutorials but mostly got ones similar to the gtkmm documentation, e.g. not beginner friendly. so does anyone know of a good site for a gtkmm tutorial that wont make my brain hurt any more than it already does?

---

### Post by Mr. Shannon on 2011-05-21
You could try [[COLOR="Blue"]this[/COLOR]]("www.mrbrklyn.com/resources/programming-with-gtkmm.pdf") but I don't know how much easier it will be to understand.  I'v read some of the documentation [[COLOR="Blue"]here[/COLOR]]("http://developer.gnome.org/gtkmm-tutorial/stable/index.html.en") (what I think you are referring to) but I just searched for the book at the above link.  There just aren't that many tutorials on gtkmm.  There aren't many books either.  gtk and Qt are easer to find books for (not trying to get you to switch).  One thing you need to make sure you understand before trying to learn gtkmm is objects and understand them well.

I am planning on using the resources above to learn gtkmm once I finish learning C++.

---

### Post by cgroza on 2011-05-21
If you want to develop applications on multiple platforms, I suggest wxWidgets.
It has a very good tutorial for beginners.
[http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/)

---

### Post by u-noob-tu on 2011-05-21
> **cgroza said:**
> If you want to develop applications on multiple platforms, I suggest wxWidgets.
It has a very good tutorial for beginners.
[http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/)

at the moment i want to develop on Linux, specifically for GNOME, since its what i use everyday. right now im using Anjuta IDE (awesome program), but ill look into wxwidgets.

---

### Post by Mr. Shannon on 2011-05-21
As far as I know gtkmm will work on windows as well.

From my own research wxwidgets and gtkmm are somewhat different in their approaches, so before you decide to switch I would make sure that you like event tables.  As far as I know, wxwidgets uses event tables and gtkmm uses signals and slots (so does Qt I think).

Also, if you do switch, Code::Blocks is probably the bets IDE for wxwidgets.

---

### Post by u-noob-tu on 2011-05-21
> **Mr. Shannon said:**
> As far as I know gtkmm will work on windows as well.

From my own research wxwidgets and gtkmm are somewhat different in their approaches, so before you decide to switch I would make sure that you like event tables.  As far as I know, wxwidgets uses event tables and gtkmm uses signals and slots (so does Qt I think).

Also, if you do switch, Code::Blocks is probably the bets IDE for wxwidgets.

i just tried wxWidgets and made my very first GUI interface. the difficulty level has just risen significantly by doing that, but i certainly enjoyed it. i think ill go with wxwidgets for now until i can get a better grasp on gtkmm. plus, it seems there is a lot more documentation for wxwidgets.

---

### Post by cgroza on 2011-05-21
> **Mr. Shannon said:**
> As far as I know gtkmm will work on windows as well.

From my own research wxwidgets and gtkmm are somewhat different in their approaches, so before you decide to switch I would make sure that you like event tables.  As far as I know, wxwidgets uses event tables and gtkmm uses signals and slots (so does Qt I think).

Also, if you do switch, Code::Blocks is probably the bets IDE for wxwidgets.
wxWidgets has a Connect method now. The use of event table is not necessary, although I find the event tables more useful for binding menubar events..

---

