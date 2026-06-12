---
title: "What Python GUI to use?"
date: 2008-08-28
forum: Programming Talk
---

### Post by aktiwers on 2008-08-28
I am writing a program that  one day is meant to run on some screens on a school showing people information about what location there class is at. 

I already got lots of help here and thanks for that :)

The program need to display scrolling text like the ones you see at the end of the movies or like you see on the terminals in the airport.

I have now build like a prototype of the program in Tkinter, but it really looks ugly and somehow laggy. The Tkinter Text widget(which I use for the scrolling text) also lags the ability to set a background image. Now I am thinking Tkinter is not the right toolkid for this kind of application.

What would you say is the best GUI framework to use with Python in this case and why?

---

### Post by LaRoza on 2008-08-28
See the sticky ;)

QT, GTK+ and wxWidgets are your major options. All are cross platform and free.

To showcase QT and GTK+ in Python, check out my thread here "System Restore" and run the two interfaces (not written by me)

GNOME and Xfce use GTK+, KDE uses QT. If you aren't using GNOME or QT, then it doesn't matter. All three have GUI designers as well.

---

### Post by days_of_ruin on 2008-08-28
> **aktiwers said:**
> I am writing a program that  one day is meant to run on some screens on a school showing people information about what location there class is at. 

I already got lots of help here and thanks for that :)

The program need to display scrolling text like the ones you see at the end of the movies or like you see on the terminals in the airport.

I have now build like a prototype of the program in Tkinter, but it really looks ugly and somehow laggy. The Tkinter Text widget(which I use for the scrolling text) also lags the ability to set a background image. Now I am thinking Tkinter is not the right toolkid for this kind of application.

What would you say is the best GUI framework to use with Python in this case and why?

Like LaRoza said there are several good options.Bear in mind that more
people here use gtk so you will get more help with that.

---

