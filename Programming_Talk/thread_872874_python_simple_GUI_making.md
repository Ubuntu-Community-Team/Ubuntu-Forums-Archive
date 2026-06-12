---
title: "python simple GUI making?"
date: 2008-07-28
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-07-28
hi

so i've learned enough python to write a basic object oriented program and was looking at how to do GUI programming in it.

ive noticed that it is all text writing to make the window controls like buttons and text boxes

i was curious if there is a way to use the drag 'n drop method that is used with C# (or at least in the Microsoft IDE i use in my windows partition) or if i have to hand code it like in C++

also what GUI module thing (like wx or tkinter) would u recommend?

---

### Post by Kadrus on 2008-07-28
PyGTK is good,so is WxPython(which is cross-platform),I personnaly don't like TK but you can use it.
[PyGTK Tutorial]("http://www.pygtk.org/pygtk2tutorial/index.html")
**WxPython Tutorials**
[WxPython.org Tutorial]("http://wxpython.org/tutorial.php")
[WxPython Linux Tutorial]("http://wiki.wxpython.org/AnotherTutorial)
[ZetCode tutorial includes tetris game(example)]("http://zetcode.com/wxpython/")
**TK**
[Python TK Tutorial]("http://www.pythonware.com/library/tkinter/introduction/")

---

### Post by jimi_hendrix on 2008-07-28
ok thanks ill assume theres no simple drag n drop like in c# and PyGTK is linux only?

---

### Post by SidStudios on 2008-07-28
I've actually got a quite excellent guide; it was made by one of my good friends who also joined my forums:
[http://hacktalk.org/forum/showthread.php?t=83](http://hacktalk.org/forum/showthread.php?t=83)
Good luck, I think that post is rather well written and easy to understand ;)

---

### Post by Kadrus on 2008-07-28
> ok thanks ill assume theres no simple drag n drop like in c#?
I think there is Kdevelop for that(not sure though).Install Kdevelop from Synaptic and test it.

---

### Post by nvteighen on 2008-07-28
PyGTK is the Python binding for GTK+ (The graphical toolkit used by the GNOME project), so it is cross-platform (e.g. Solaris, Mac, BSD, etc.), but don't know if it works in Windows... ;)

Anyway, GTK+ is a bit advanced.

---

### Post by jimi_hendrix on 2008-07-28
ok i will when i log on over to my ubutnu partition and ill post the results of kdeveloper

---

### Post by Steveway on 2008-07-28
If you use Python then you should check out Stani's Python Editor (SPE).
It even includes a graphical tool to click your own GUI together for wxpython. I think it was Boaconstructor that it uses, I'm not exactly sure.

---

### Post by Quikee on 2008-07-28
> **nvteighen said:**
> PyGTK is the Python binding for GTK+ (The graphical toolkit used by the GNOME project), so it is cross-platform (e.g. Solaris, Mac, BSD, etc.), but don't know if it works in Windows... ;)


It also works in Windows.. but the look is not native (compared to WxPython).

---

### Post by nvteighen on 2008-07-28
> **Quikee said:**
> It also works in Windows.. but the look is not native (compared to WxPython).
I see, thank you!

---

### Post by LaRoza on 2008-07-28
See the sticky on GUI toolkits and see my wiki. EasyGUI is the simplest (but least flexible)

---

### Post by jimi_hendrix on 2008-07-28
ok thanks

---

### Post by imdano on 2008-07-28
If you decide you want to use pygtk, you should check out [glade](http://glade.gnome.org/), which allows you to create GTK GUIs with dragging/dropping (sort of, it's more like point and click).

---

### Post by jimi_hendrix on 2008-07-28
glade looks nice...ill check all of this stuff out tomarrow and post back what i picked and why

---

### Post by LaRoza on 2008-07-28
I would like to point out to everyone responding that the sticky contains a list of all the toolkits mentioned here, a link to their site, a link to their GUI designer (like glade) and more references.

Please read the sticky and contribute to the information.

---

### Post by days_of_ruin on 2008-07-28
if you use glade be sure to read this great tutorial: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

### Post by slavik on 2008-07-29
glade and libglade until gtk builder kicks in :)

---

### Post by dtmilano on 2008-07-29
If you like glade approach, just take a look at [autoglade]("http://autoglade.sf.net"), which is (I think) easier than EasyGUI and much more flexible.

---

### Post by billenbois on 2008-07-29
> **slavik said:**
> glade and libglade until gtk builder kicks in :)

you can actually use gtk builder with glade:
juste make a project with glade-3 and convert the xml glade file.

i use it in C and its really nice (also doesnt need the extra glade lib anymore since its builtin gtk now :)


I would really recommend pygtk+gtkbuilder (via glade) as an easy and fast GUI making thing. (C+gtkbuilder via glade is equally easy, C or python is a matter of taste and speed here i guess)

---

