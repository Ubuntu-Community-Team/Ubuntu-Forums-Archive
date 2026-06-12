---
title: "Which one is best for beginners to work on GUI ?"
date: 2012-06-05
forum: Programming Talk
---

### Post by prismctg on 2012-06-05
Which one(Pyqt,Pyslide,PyGTK ,wxPython) would be better option for beginners when it needs to work on GUI.

---

### Post by lei00 on 2012-06-05
I remember that PyGTK had a pretty good documentation :)

---

### Post by r-senior on 2012-06-05
Do you need your applications to be cross-platform?

If not, and you want to integrate best with the Gnome desktop, GTK3 with GObject introspection is the best choice IMO (not PyGTK, which is deprecated).

[http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html)

There's a GUI designer called Glade which works with GTK3. There's also Ubuntu Quickly, which is based on Python, GTK3 (I think I read it was updated to GTK3) and Glade:

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

For cross-platform use, I've used wxPython and I found it slightly easier to code than GTK3 (although the GUI design tools weren't as good). Qt is also cross-platform and has a good GUI design tool (but I've not used it, so I'll let others comment on that). GTK libs can be installed on Windows/Mac but QT and wx are usually considered to be the better cross-platform toolkits.

Or there's TkInter of course, which is often recommended for beginners who want to write applications that are uglier than an ugly duckling.

Pyslide -- never heard of it for writing applications.

---

### Post by prismctg on 2012-06-05
yes it must be cross-platfrom

---

### Post by PeterP24 on 2012-06-05
> There's a GUI designer called Glade which works with GTK3. There's also Ubuntu Quickly, which is based on Python, GTK3 (I think I read it was updated to GTK3) and Glade:

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

+1

> Or there's TkInter of course, which is often recommended for beginners who want to write applications that are uglier than an ugly duckling.

I've started with it - and I found it to be indeed very ugly. My guess is that it is not worth it - the time you spent learning Tkinter could be spent by learning a full fledged gui toolkit like wxPython. Besides it is missing functionality.

> I remember that PyGTK had a pretty good documentation 

Also, PyQt and wxPython have "pretty good documentation". Well - (almost) scratch wxPython which sometimes sends you to read the C++ documentation of wxWidgets. But, nonetheless wxPython comes with an archive full of examples - that helped me a lot.

Never heard of PySlide also. 
My recommendation - wxPython, PyQt or PyGTK.

---

### Post by 11jmb on 2012-06-05
I'm not much of a GUI programmer myself, but I've been happy with wxpython for my limited use.

The online documentation was outstanding IMO, and I didn't find anything that would get in the way of a novice programmer (coming from a fairly experienced programmer who is a GUI novice)

I started making python GUI's with tkinter, but as has been said before, I was unable to create a reasonable-looking GUI. At first, I thought it was just my lack of experience, having only used swing, where creating a good-looking GUI is impossible, but I was able to make a much nicer interface as soon as I started using wxpython.

---

### Post by trent.josephsen on 2012-06-05
My experience is word for word identical to 11jmb's.

---

### Post by Bachstelze on 2012-06-05
Same, but replace wxpython with PyQt. :p PyQt also has a [nice book](http://www.amazon.com/dp/0132354187) about it.

---

### Post by memilanuk on 2012-06-06
> **PeterP24 said:**
> 
Never heard of PySlide also. 


Mostly compatible with PyQT, but with somewhat less restrictive (for commercial use) licensing, backed by Nokia

---

### Post by pauljwells on 2012-06-06
I've only used wxPython, but it works very well for what I needed and seems to keep a very 'Pythonic' syntax. I have linux, osx and windows boxen in my menagerie and I can code wx on any and run on any and it all looks native to the OS when running.

---

### Post by mechsin on 2012-06-21
I am a mechanical engineer and use PyQt I find it pretty straight forward and very flexible. The Qt documentation is good but mostly in C++.  It isn't difficult to translate thought if you have a good understanding of OOP. I would defiantly recommend it over Tkinter. There are a lot of good Python examples for it out there as well. The book mention earlier is good as well I own it. It comes with a who bunch of examples which are actually free they can be downloaded from the book website. I think you ment to say PySide not Slide, PySide is mostly an exact copy of PyQt just with different licensing. From what I have read they are completely interchangeable. A PyQt import statement can be replaced with a PySide import statement and everything should work. Haven't tried it thought.

---

### Post by trent.josephsen on 2012-06-22
> **mechsin said:**
> I would defiantly recommend it over Tkinter.

There's no need to be so recalcitrant.

---

### Post by alexfish on 2012-06-23
> **mechsin said:**
> I am a mechanical engineer and use PyQt I find it pretty straight forward and very flexible. The Qt documentation is good but mostly in C++.  It isn't difficult to translate thought if you have a good understanding of OOP. I would defiantly recommend it over Tkinter. There are a lot of good Python examples for it out there as well. The book mention earlier is good as well I own it. It comes with a who bunch of examples which are actually free they can be downloaded from the book website. I think you ment to say PySide not Slide, PySide is mostly an exact copy of PyQt just with different licensing. From what I have read they are completely interchangeable. A PyQt import statement can be replaced with a PySide import statement and everything should work. Haven't tried it thought.

Just out of interest , did you try "Monkey Studio" IDE

---

### Post by mechsin on 2012-06-23
> 
Just out of interest , did you try "Monkey Studio" IDE


No I haven't. I did just take a look at the website though and it seems like something I could use. I don't really use any IDE per say though. I mostly program at work where we have Windows so I just use a combination of Notepad++ and Ipython to debug and write most of my stuff. Recently some less computer savvy engineers have joined our team and weren't comfortable with just a notepad editor and command window so they started using Eclipse. Although I will bring up Monkey Studio.

> 
There's no need to be so recalcitrant.


Sorry did mean to come of that way. I have use Tkinter some. It is good if you need to create a simple gui without installing a bunch of other stuff, but lets face it is kind of ugly and if I were going to recommend a GUI interface to learn I think that Qt has more to offer. Of course Qt is what I learned first so I am going to have a little bit of bias.

---

### Post by trent.josephsen on 2012-06-23
> **mechsin said:**
> Sorry did mean to come of that way.
I was making a joke because you typed 'defiantly' when you obviously meant 'definitely'. :lolflag:

---

### Post by mechsin on 2012-06-23
Oh ha I didn't even notice that :)

---

### Post by alexfish on 2012-06-23
[QUOTE=mechsin;12048902]No I haven't. I did just take a look at the website though and it seems like something I could use. I don't really use any IDE per say though. I mostly program at work where we have Windows so I just use a combination of Notepad++ and Ipython to debug and write most of my stuff. Recently some less computer savvy engineers have joined our team and weren't comfortable with just a notepad editor and command window so they started using Eclipse. Although I will bring up Monkey Studio.


I tried it some time ago , thought it interesting , as regards QT and python ,

as regards the phrase "IDE" , Personally I would have called it a "GUI" interface.


regards

alexfish

---

### Post by trent.josephsen on 2012-06-24
"GUI interface" and "IDE" mean very different things.

---

### Post by madjr on 2012-06-24
this beginners guide from the ubuntu app creation contest might also be helpful:

[http://www.omgubuntu.co.uk/2012/06/its-not-to-late-to-enter-ubuntu-app-creation-contest-and-win-a-laptop](http://www.omgubuntu.co.uk/2012/06/its-not-to-late-to-enter-ubuntu-app-creation-contest-and-win-a-laptop)

---

### Post by Garyu on 2012-06-26
> **prismctg said:**
> Which one(Pyqt,Pyslide,PyGTK ,wxPython) would be better option for beginners when it needs to work on GUI.

You spelt PySide wrong. PySide is pretty much the same as PyQt4, but it seems that PySide is better implemented for Python 2.x and PyQt4 is better implemented for Python 3.x, although the difference is probably negligible since both use Qt.

When I started, I tried to use Glade with GTK (don't know if it was PyGTK or GTK3 or whatever), but I just found it really frustrating. wxPython was even worse for what I wanted to do. As soon as I found Qt everything went really easy. So at least for me, as a beginner, Qt was the optimal choice.

PyQt4 also comes with its own database classes, networking, etc. And all of that of course connects really easy to widgets. So you can save some serious time by going that way. Also check out the book linked above "Rapid GUI programming with Python and Qt", which is really an excellent book.

---

