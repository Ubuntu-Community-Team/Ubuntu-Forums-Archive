---
title: "OO-API wrapper for win32 / GTK"
date: 2008-07-06
forum: Programming Talk
---

### Post by henchman on 2008-07-06
Hello everybody.

Just for my personal pleasure :) i would like to write a cross platform c++ / d (not yet sure) oo-api wrapper. While i have no choice on windows, i would like to take GTK for the linux versions (no current plans for OSX, but may be added later on).

As iam currently more experienced with win32 (only _very_ basic GTK knowledge), i would like to start there. Now a few questions:
[LIST]
[*] am i right that there is no absolute positioning in GTK?
  ( lets say: this button has a 10px left and a 30px top spacing between itself and his parent element )
[*] if it is like that, it will be the easiest to write my own (gtk-like) boxes on top of the win32 wrappers to get a consistent interface for cross platform use, right?
[*] there will surely be widgets, were there will be no counterpart for the other platform, so the program will have to emulate them by painting them. I would like to use a cross platform graphics engine for that, perhaps SDL. SDL brings sound support, too. This may be a later issue and i will surely be too lazy to code sound support myself ;) Any pros or cons or equal/better alternatives for SDL? eg. Cairo perhaps?
[/LIST]

Iam still collecting thoughts not to run in the wrong direction, so if someone tells me iam completely wrong and it's all stupid, that's okay :KS

Again, its more or less just for learning these apis but then lateron keep it more simple :)

---

### Post by mssever on 2008-07-07
Sounds like what you're wanting to do is very similar to wxWidgets. You might want to examine that project to see how they do things.

---

### Post by henchman on 2008-07-07
thanks for the friendly advise, but thats lame :-) as i want to write it mysql... but thanks anyway :)

---

### Post by kknd on 2008-07-07
There is absolute positioning in GTK. But, absolute positions sucks.

---

### Post by WW on 2008-07-07
> **henchman said:**
> thanks for the friendly advise, but thats lame :-) as i want to write it mysql... but thanks anyway :)
I was really scratching my head over how you could ever hope to write such an API in *mysql*; then I realized you must mean *myself*.  (Been doing a lot of database work lately? :) )

---

### Post by Vadi on 2008-07-07
There's Gtkfixed or something widget that allows absolute positioning.

But please do not use it! At all! It's absolutely evil. Please read up on tables / vertical boxes / horizontal boxes for nice alignment and widget properties like expand, fill, and shrink.

Also, I'd recommend going through this excellent tutorial ([click]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")) to quickly get an understanding of the basics.

---

### Post by henchman on 2008-07-09
Thank you all :)

---

