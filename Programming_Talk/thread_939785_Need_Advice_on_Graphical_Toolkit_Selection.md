---
title: "Need Advice on Graphical Toolkit Selection"
date: 2008-10-06
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2008-10-06
Hello,

I know this question is asked before too many times but mine is a little specific.

I'm gonna make a software which will receive data (from serial or USB port) and then display graphical charts on screen accordingly. I'm learning GTK+ but the program will be coded in C++ most probably (because I suspect there is not a good cross-platform serial or usb port library written in C).

My concern is that GTK+ does not have a canvas widget, I guess, like Tk has? So, can graphical charts which are refreshing themselves in a few seconds be done in GTK? How are Inkscape and GIMP achiving the very high-level drawing areas of theirs (I don't need, though, as high-level canvas widget as theirs)?

Should I learn a different graphical toolkit like wxWidgets, FLTK, Qt or something? I don't prefer Qt for its license.

The program will definately be coded in C or C++, so I don't accept "use Python" as answer :)

---

### Post by LaRoza on 2008-10-06
> **ZuLuuuuuu said:**
> 
Should I learn a different graphical toolkit like wxWidgets, FLTK, Qt or something? I don't prefer Qt for its license.

The program will definately be coded in C or C++, so I don't accept "use Python" as answer :)

QT doesn't have a restrictive license, unless you have one.

QT and wxWidgets are for C++, so if you use C, you will be more limitted.

---

### Post by days_of_ruin on 2008-10-06
> **ZuLuuuuuu said:**
> Hello,

I know this question is asked before too many times but mine is a little specific.

I'm gonna make a software which will receive data (from serial or USB port) and then display graphical charts on screen accordingly. I'm learning GTK+ but the program will be coded in C++ most probably (because I suspect there is not a good cross-platform serial or usb port library written in C).

My concern is that GTK+ does not have a canvas widget, I guess, like Tk has? **So, can graphical charts which are refreshing themselves in a few seconds be done in GTK?** How are Inkscape and GIMP achiving the very high-level drawing areas of theirs (I don't need, though, as high-level canvas widget as theirs)?

Should I learn a different graphical toolkit like wxWidgets, FLTK, Qt or something? I don't prefer Qt for its license.

The program will definately be coded in C or C++, so I don't accept "use Python" as answer :)

**Yes you can do that in gtk**

---

### Post by kknd on 2008-10-06
Actually, you can draw on almost any widget using Cairo (GTK >= 2.6 are draw with Cairo), but its more common to draw on a GtkDrawingArea.

---

### Post by ZuLuuuuuu on 2008-10-06
> **LaRoza said:**
> QT doesn't have a restrictive license, unless you have one.

The project has the probability of going commercial with closed source system.

> Yes you can do that in gtk

Thanks, then I will continue my journey to the GTK.

I also found this chapter on gtkmm book:

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-drawing-clock-example.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-drawing-clock-example.html)

If creating a clock is possible (which is also refreshing itself on every second) then graphic charts should also be possible.

---

### Post by LaRoza on 2008-10-06
> **ZuLuuuuuu said:**
> The project has the probability of going commercial with closed source system.


Ah, then it would, however, you'd be no more restrictive yourself ;)

---

