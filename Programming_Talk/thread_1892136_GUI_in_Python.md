---
title: "GUI in Python"
date: 2011-12-07
forum: Programming Talk
---

### Post by CoffeeRain on 2011-12-07
I would like to do some GUI programming in Python. I am semi familiar with wxPython, but was wondering what would be better, wx or tkinter. Also, what language are most applications made in?

---

### Post by F.G. on 2011-12-07
i used the pyqt4 module recently to make a GUI, it (obviously) uses QT4. that's a pretty handy one as it is also cross platform and pretty easy to use. 
i think tkinter is for the TK platform, which is also cross platform, and in my (very brief experience) pretty easy to use.  i don't what the most popular is though.

---

### Post by papibe on 2011-12-07
I'm not that well verse in this topic, but I think gtk+ could be an interesting option. There a screencast tutorial series that I found very helpful. Find the firt one here: [GNOME Screencasts Episode 1: The Basics]("http://www.omgubuntu.co.uk/2011/06/gnome-screencasts-taking-tutorials-to-the-next-level/").

Hope it helps.
Regards.

---

### Post by dodle on 2011-12-07
I Generally use wxWidgets/wxPython, but I have have used pyQt. I would recommend either of those. I've tried a little of pyGtk, but it seemed a little more confusing than the others. wx wraps around Gtk+, so anything you write in wx will look like a Gtk+ app unless you use wx's custom widgets.

**wx/Gtk+:** Looks good on Gnome, terrible on Kde unless you are using QtCurve/Gtk-Qt Theme Engine.
**Qt:** Looks good on Kde and Gnome
(Don't know about Unity)

---

### Post by juancarlospaco on 2011-12-07
Use HTML5 for the GUI

---

### Post by CoffeeRain on 2011-12-07
The concept of using a web programming language to develop a GUI application seems intriguing. How would it work, and where would be a tutorial?

---

### Post by rushikesh988 on 2011-12-07
ya html5 is fun but i also don't know how to use it...

---

### Post by cgroza on 2011-12-07
Well, what I heard is that Tkinter is more often used for programming administrative tools because it does not require the installation of an extra GUI toolkit since Tkinter is already bundled with the default python distribution.

wxPyhton/Others are more orientated towards general user applications.

---

### Post by deonis on 2011-12-07
I was thinking about the same thing about two years ago. TK is nice and stable but very ugly and has  less widgets than WX, QT, GTK. My advise would be WX! It's easy to understand, you have nice widgets which looks good on both windows, Linux and Mac. You can make pretty much anything you want  and its lighter than QT. QT seems to be more powerful, but it is heavier and  I do not know much about it.   Try wxglade for WYSIWYG design of GUI. You will need python-wxgtk2.8 or 2.6 libs to start coding 


cheers

denis

---

### Post by memilanuk on 2011-12-07
> **deonis said:**
> I was thinking about the same thing about two years ago. TK is nice and stable but very ugly 


Hence the ttk widget extensions.  See here: [http://www.tkdocs.com](http://www.tkdocs.com) for examples.  I have a hard time seeing how this would be considered 'very ugly':

[IMG]http://www.tkdocs.com/images/gridexample2.png[/IMG]


> and has  less widgets than WX, QT, GTK.

True... but how many do you need, really?  (not being a smart-a$$, honestly asking)  Again, ttk extends the widget set of default tkinter.

> Try wxglade for WYSIWYG design of GUI

I do really, really wish someone made a tkinter version of glade...

As an aside... would [quickly]("https://wiki.ubuntu.com/Quickly") not do about everything that has been already suggested (python, wx, glade, etc.)?

---

### Post by deonis on 2011-12-07
Makeup your mind in here: 

[http://wiki.wxwidgets.org/WxWidgets_Compared_To_Other_Toolkits#Qt](http://wiki.wxwidgets.org/WxWidgets_Compared_To_Other_Toolkits#Qt)

you will see the same thing as we already said ...

---

### Post by 11jmb on 2011-12-08
> **juancarlospaco said:**
> Use HTML5 for the GUI

HTML5 is awesome for portability, because you can use it for just about any domain (desktop, mobile, web) and have a functioning GUI. I find that all of the HTML5 GUIs I have seen are not as professional looking, though.

Same with java apps, they never come out as sharp as the other options. It seems to me that the best looking apps use a graphics toolkit designed directly for their domain. 

Therefore, GTK would be my first choice for Ubuntu programming. Perhaps somebody here can say how it looks in Unity (I don't use it), but it looks great on standard Gnome and it looks good on my xfce desktop as well. It does look like garbage on KDE, though, as somebody has already pointed out.

---

### Post by Simian Man on 2011-12-08
QT is far and away the most professional, and portable free GUI toolkit.  QT programs look good and work well across all systems and it has all the features you could ever want.  The fact that it has a complete and well-used Python binding makes it a no-brainer IMHO.

---

### Post by CoffeeRain on 2011-12-08
Thanks for the suggestions. I'm starting to learn tkinter, and if that doesn't work out, I'll try QT. So far I've found that tkinter is easier to use than wxPython.

---

### Post by CoffeeRain on 2011-12-08
So, in Tkinter, I created a window, and put widgets in it, but the window is in the background behind my Terminal. I can't find a command online to put focus on the window. At least not one that works. What can I do?

---

### Post by deonis on 2011-12-08
You seem repeating my mistakes ... use QT or wxPython. pyQt however, is no longer supported by the official sources. Use Wxglade or wxFormBuilder to do the GUI for you!

---

### Post by juancarlospaco on 2011-12-08
> **CoffeeRain said:**
> The concept of using a web programming language to develop a GUI application seems intriguing. How would it work, and where would be a tutorial?

> **11jmb said:**
> HTML5 is awesome for portability, because you can use it for just about any domain (desktop, mobile, web) and have a functioning GUI. I find that all of the HTML5 GUIs I have seen are not as professional looking, though.


How a GUI looks like on HTML5 ...?, see yourself

[IMG]https://lh3.googleusercontent.com/-iuYUxz0FQb4/TsmIwOTSoTI/AAAAAAAAA0s/FCunGAzO6mo/s640/nethelper3.jpg[/IMG]

[IMG]https://lh3.googleusercontent.com/-45KQMrz-rvQ/TsazwakNkUI/AAAAAAAAA0I/Spv6BJtA0tY/s640/imgappalone.jpg[/IMG]

They are Real working apps, no Mockup, no Gimp :)

HTML5 is not a web programming language, you dont even need to know programming.
I think theres no better GUI than HTML5, looks amazing on any device/os/whatever,
because you dont even need to know Programming, you cant program on HTML5,
its just a markup, like writing into a Wiki, or writing an XML, it always Display.

For Heavy Processing on Backend i use:
[http://bottlepy.org](http://bottlepy.org) or [https://www.djangoproject.com](https://www.djangoproject.com)
For Development IDE i use: [http://ninja-ide.org](http://ninja-ide.org)
For GUI i use HTML5: [http://www.html5rocks.com](http://www.html5rocks.com)
QML now also renders on-the-fly to HTML5 too: [https://gitorious.org/qmlweb/pages/Home](https://gitorious.org/qmlweb/pages/Home)
If you want a WYSIWIG IDE Point'n'Click RAD: [http://maqetta.org/](http://maqetta.org/)

The Unity project dont use GTK, only..., it uses a Mix of toolkits.

---

### Post by Simian Man on 2011-12-08
> **juancarlospaco said:**
> How a GUI looks like on HTML5 ...?, see yourself

Different strokes for different folks, but that looks incredibly ugly to me.

---

### Post by juancarlospaco on 2011-12-08
> **Simian Man said:**
> Different strokes for different folks, but that looks incredibly ugly to me.

I like the way you Troll..., and i agree,
i didnt say its beautiful, is kind of "OnDemand" software,
based on Clients requests, the second its based on a Design posted on OMG Ubuntu, 
notice we are not discussing Design... lets go back to Topic :)

---

### Post by CoffeeRain on 2011-12-08
Thanks for stuff! :lolflag: I'll look into QT.

---

### Post by trivialpackets on 2011-12-08
Check out developer.ubuntu.com and quickly.  It uses PyGTK.

---

### Post by CoffeeRain on 2011-12-08
Never mind, I can't find a good download. What I tried (I'm pretty sure it's the official site) told me to install something else, and that also told me to install something else. :( I'll have to keep trying. So... About that focusing a window in tkinter...

---

### Post by Dhiraj Thakur(Invincible) on 2011-12-09
i dont know who said pygtk was confusing it worked perfectly for me.i think it all depends on how you write the code.
Still good luck after all it's your decision.

---

### Post by CoffeeRain on 2011-12-09
No, wxPython was confusing. I couldn't download PyQt. If anyone knows where a good download is, then that's cool.

---

### Post by F.G. on 2011-12-09
PyQt4 is in the repos, so you can get it from synaptic.

---

### Post by llanitedave on 2011-12-09
When I was trying to decide between toolkits, I went with wxPython simply because there is such a huge mass of well-written documentation available for it.  Ttk doesn't seem quite so well explained, and neither did QT.  Maybe that's changed by now, I don't know.

---

### Post by samjh on 2011-12-10
> **deonis said:**
> pyQt however, is no longer supported by the official sources.

That is misinformation.

PyQt is still going strong and there is no sign that Riverbank Computing will abandon it.  PySide has run out of Nokia funding, but it is still being developed by OpenBossa.

It's perfectly fine to use PyQt.

---

