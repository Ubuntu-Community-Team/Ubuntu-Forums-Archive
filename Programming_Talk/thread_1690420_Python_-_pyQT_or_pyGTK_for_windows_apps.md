---
title: "Python - pyQT or pyGTK for windows apps"
date: 2011-02-18
forum: Programming Talk
---

### Post by Nico-dk on 2011-02-18
After 6 days of fiddling with Python, I now consider myself an expert ... No, not really ;)

I did spent the last 6 days getting acquainted with Python, and even though I still have a long way to go, I'd like to dabble in some GUI applications.

Before switching to Ubuntu, I created a number of HTAs (Html App), and thought it would be good training remake some of those using python and a GUI framework.

The apps I make mostly create text files dependent on user input, and the will be used by 50+ year old women ... sorry, I mean 50+ year YOUNG women. Therefpor the apps should be able to run under windows w/o too much hassle (I'll cross the bridge of making actual .exes out of them, when I get to it). 

So, here I am, asking you, the experienced users, what GUI framework should I use:

**pyQT or pyGTK?**

pyQT should be cross platform, correct?
Haven't been able to confirm the same for pyGTK

I'm ruling TKinter out for now, since I prefer a WYSIWYG for the GUI creation. 

As always, any and all feedback is greatly appreciated :)

---

### Post by Some Penguin on 2011-02-18
Both exist for Microsoft Windows platforms, AFAICT.

Quite subjectively, one might judge that Qt on resembles the fairly traditional Windows GUI appearance more closely and thus might be easier to pick by your intended user base.

---

### Post by Nico-dk on 2011-02-18
Thanks :)

Managed to find a (superficial) comparison between several GUI frameworks ([http://stackoverflow.com/questions/3993269/pygtk-vs-pyqt-vs-wxpython-vs-tkinter](http://stackoverflow.com/questions/3993269/pygtk-vs-pyqt-vs-wxpython-vs-tkinter)). Looks like I'll take the pyQT road.

---

### Post by forrestcupp on 2011-02-18
I can confirm that pyGTK works with Windows, as I've used it before.

I'd probably go the QT route, too, though.

---

### Post by oldfred on 2011-02-18
I have been playing with python and wanted to learn to do some things like I used to do with MS Access.

I like the geany editor. And I have used Glade for GTK and Qt 4 Designer for QT. Once I set a screen with glade or designer I then can use my code behind the scenes. I would like to use the same code with two different front ends but my test app is pretty simple right now.

---

### Post by cgroza on 2011-02-18
Why don't you take a look at wxPython too, while you are in your way to search a toolkit.

---

### Post by Nico-dk on 2011-02-19
Thanks all, I might give wxPython a spin.

Found lots of good documentation on Qt, and whipped up a basic gui last night. I really like how I can create any interface in minutes, and generate the needed .py files for it too in Qt4 desginer, and then move on to the fun part; the actual coding :)

---

### Post by nvteighen on 2011-02-19
Nowadays, GTK+ and Qt are almost equally powerful. There are just philosophy differences that are reflected on how the respective APIs are... and the look-and-feel, of course.

---

