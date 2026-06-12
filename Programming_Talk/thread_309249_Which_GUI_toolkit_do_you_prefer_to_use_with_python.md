---
title: "Which GUI toolkit do you prefer to use with python and why?"
date: 2006-11-29
forum: Programming Talk
---

### Post by pedrotuga on 2006-11-29
Ok... i tryed a few stuff but it allways gets to the point when is not so simple at the first time... it never is...

So far, what from all the tutorials i followed, the one on gui building using Boa ( wxwidgets ) was the one that let me understand better the way all things work.

this is a poll on the tookit, but please dont forgot to mention you favorite designer tool and why is it your favorite.

Dont get off topic discussing which one is the best, give YOUR opinion on your favorite.

---

### Post by nkhansen on 2006-11-29
I chose gtk, because it looks nice, and because it is rather easy to develop GUI's with glade. I haven't tried other kinds though :)

---

### Post by christhemonkey on 2006-11-29
In my opinion pyGTK, but mainly due to it being the only one i have ever used!

And the only designer tools i have ever used have been gedit and a terminal.

---

### Post by engla on 2006-11-29
gtk, because I found examples there quickly and the applications blend in perfectly with Ubuntu's Gnome desktop.

In addition, I'm thinking of trying to build something in C (I'm really more proficient in C), and the pygtk api is just a shadow of the C api, meaning I will already know it pretty well.

---

### Post by bradleyd on 2006-11-29
i have now used wxWidget and Gtk2. Both are good. I used Gtk2 more with perl. wxPython is pretty easy for small apps if you use wxGlade. There is definetly more examples in Gtk2.

---

### Post by ohgod on 2006-11-29
I like Gtk2, but that's all I've used.  As far as designing the gui, you should really give Glade a try.  It makes the gui design easy!

---

### Post by ZuLuuuuuu on 2006-12-15
Anyone using tk? I'm learning Python, I bought a book and it explains tk because it comes with Python installation. I think it is a big advantage that all the users that have Python have also tk.

I did some search to learn about which one is better (GTK, wxWidgets etc...), because I don't want to learn all the widget sets to decide myself, I don't have that much time :). As far as I saw, GTK is great looking (when there are two applications written in GTK and qt I prefer the GTK one definetly) but if you use it then the Windows users should also download pyGTK as well as GTK as well as Python, am I right? If yes, then this is useless, I think (Installing 2 other application to install 1 application and their verisons should match!?!?). It is also the case when you use wxWidgets. But if you use tk then the user just should download Python and that's it. But I don't know how the tk applications look like. I just know aMSN and I think it is one of the worst-looking applications I've ever seen on Linux. Also I remember that the developer of it complained in one of his messages on the forums that it is hard to make good-looking tk applications. But I read that tk uses native widget sets, so it should look like wxWidgets?

I will appreciate if you explain me why don't you prefer tk or prefer tk.

---

### Post by po0f on 2006-12-15
I've used PyGTK and Tkinter.  I prefer PyGTK because it looks better when the app is run on GNOME.

One thing to keep in mind is that PyGTK (and wxPython and PyQt) is more than just a window drawing toolkit, it is a wrapper around the *whole* GTK library.  In this sense, Tkinter is a lot easier to learn, and I found it quite easy to get a basic GUI up and running with Tkinter.  Though with my previous Tkinter experience, I found learning PyGTK easy as well.

PyGTK is definitely more feature-rich, and is a valuable addition to your programming repertoire.

---

### Post by dodle on 2008-10-05
I've been having trouble deciding which gui toolkit to use for Python and found this thread.  It looks to me like PyGtk is the most popular and that is what I have been practicing with.  I've heard that Qt has some licensing restrictions.  If that's true I won't want to learn that, and from what I understand PyGtk doesn't have any restrictions.  Anybody else have any input?

---

### Post by LaRoza on 2008-10-05
> **dodle said:**
> I've been having trouble deciding which gui toolkit to use for Python and found this thread.  It looks to me like PyGtk is the most popular and that is what I have been practicing with.  I've heard that Qt has some licensing restrictions.  If that's true I won't want to learn that, and from what I understand PyGtk doesn't have any restrictions.  Anybody else have any input?

This thread is two years old and a lot has changed.

PyGTK is used on Ubuntu, obviously.

QT doesn't have any restrictions to open source programs. Basically, QT says if you write it open source, you can use QT for free, but if you want to write commercial software, you have to pay. It has the best of both worlds I think.

See the stickies on GUI toolkits (Python has a lot of good ones, with varying degrees of difficult/flexibility) and make up your own mind, otherwise, you will get a bunch of "I like $TOOLKIT"'s like everyone else.

---

### Post by loell on 2008-10-05
I use **edje**

[http://wiki.enlightenment.org/index.php/Creating_Edje_User_Interfaces]("http://wiki.enlightenment.org/index.php/Creating_Edje_User_Interfaces")

because you can have UI animations of the lightest resource. ;)

---

### Post by y-lee on 2008-10-05
> **ZuLuuuuuu said:**
> Anyone using tk? I'm learning Python, I bought a book and it explains tk because it comes with Python installation. I think it is a big advantage that all the users that have Python have also tk.

But I read that tk uses native widget sets, so it should look like wxWidgets?

I will appreciate if you explain me why don't you prefer tk or prefer tk.

I have a couple of things i have did in tk one is a fractal generating application in python I have been working on. really it is more a demo kind of thing than a fully developed application, illustrating and testing the algorithms i use as well as the affine matrices of the IFS fractals it generates. I chose tk because i I thought it would be easy to implement and because i wanted to learn more about it. My first GUI program i wrote for linux used wxWidgets and that said I can clearly state that tk applications look nothing like wxWidgets. The wxWidget code I wrote looks more gnomish and tk looks terrible. It is possible  to get tk applications to look better (ie more native) but that [Motif]("http://en.wikipedia.org/wiki/Motif_(widget_toolkit)") look i just don't care for.

Btw i voted for wxWidgets tho really I know little about the rest, played around one day with GTK and haven't used Qt at all.

---

### Post by nvteighen on 2008-10-06
Who uses GUI toolkits? :twisted:

---

### Post by LaRoza on 2008-10-06
> **nvteighen said:**
> Who uses GUI toolkits? :twisted:

Two people we need on the sysres development team...

---

### Post by mike_g on 2008-10-06
> In addition, I'm thinking of trying to build something in C (I'm really more proficient in C), and the pygtk api is just a shadow of the C api, meaning I will already know it pretty well.I recently changed from using Gtk in C to pygtk and is so much better. I'd stick to python for it unless you really need to use C. Even if you are proficient with it its just so much extra work especially when you end up having to creat a complex struct for the parameters of each callback function. To me its just a big headache requiring 10x the volume of code, mostly tedious checks, with few significant gains.

> I like Gtk2, but that's all I've used. As far as designing the gui, you should really give Glade a try. It makes the gui design easy! 
I disagree, creating a ui in glade might be slightly easier if you dont know anything about gtk, but I cant see it doing any favours in the long run. I just made a prog with glade and tbh, I find it easier to hand code the UI. I also have more control over what goes on and dont have to deal with hideously bloated XML files. I was once saying how XML for GUIs was great before, but I have since changed mind.

---

### Post by LaRoza on 2008-10-06
There is very little point in responding to posts that are over 2 years old.

Look at who you are talking to before you respond.

---

### Post by nvteighen on 2008-10-06
> **LaRoza said:**
> Two people we need on the sysres development team...

:p

> **mike_g said:**
> I recently changed from using Gtk in C to pygtk and is so much better. I'd stick to python for it unless you really need to use C. Even if you are proficient with it its just so much extra work especially when you end up having to creat a complex struct for the parameters of each callback function. To me its just a big headache requiring 10x the volume of code, mostly tedious checks, with few significant gains.

You're so right. GTK+ is a great thing; a very interesting API full of nice features... but in C, as it has to rely on GLib permanently to make C the most OOP-ish possible, it hardens everything and coding in it finally gets into a real nightmere. PyGtk is much cleaner, as much of the C GTK+ toolkit's features are just replaced by Python primitives, making the code much natural...

---

### Post by loell on 2008-10-06
> **LaRoza said:**
> There is very little point in responding to posts that are over 2 years old.

Look at who you are talking to before you respond.

well yeah, but that very little point  has more relevance than some of those posts made just a minute or two ago. in "other" areas of the forum :lolflag:

---

### Post by indecisive on 2008-10-06
Python + pyGTK + Glade = Unmatched awesomeness

---

### Post by pedrotuga on 2008-10-09
sice this thread has been bumped, I cannot stress enough how awesome simpler solutions like **zenity** or **traitsui** are when it comes to simple tasks.

---

### Post by snova on 2008-10-09
As long as we're bringing back old threads, I thought I'd give my opinion.

I like Qt because it's the only API I know well enough to get anything done in. I tried GTK+ for about ten minutes once and stopped when I realized it was written in C and gtk_functions_look_like_this(). I don't know whether the C++ wrapper or PyGTK improve on this, though.

I haven't tried wxWidgets in a long time, but why switch toolkits when I'm already happy?

Knowing Qt is a plus for other reasons- since KDE is built on it, it'll be much easier to migrate should I decide to write a desktop-integrated application.

Qt Designer is a nice program for my purposes.

Tk is ugly and Zenity is for shell scripts. Sorry.

---

### Post by pedrotuga on 2008-10-09
> **snova said:**
> 
Tk is ugly and Zenity is for shell scripts. Sorry.
AFAIK zenity can be used to some extent with any language. Most of its functionality simply maps to a complex command.

You don't need to be sorry either way though ;)

---

### Post by indecisive on 2008-10-09
Qt is terrible.  It befouls the pure FOSS world with proprietary toolkits owned by companies (like Trolltech).  Glade is better than the Qt Designer and the look of function calls is no reason to use a specific toolkit.

---

### Post by pxhai on 2008-10-09
wxWidgets rulez!
If you read the wiki on wxWidgets site, you will know a lot of GUI toolkits out there: wx, Qt, GTK, FLTK, tk, ... Among them, there are 3 most famous toolkits: wx, Qt and GTK. I like wxWidgets the best, because the GUI I built will have native look'n'feel on most platform. On Windows, wx uses Win32 API, on Linux uses GTK, MacOS uses Carbon or smth (not tried Mac yet). Qt and GTK just use graphics primitive to draw controls and make a fake look'n'feel. I'm sticked with wxWidgets and use it for most of my projects. Qt is better than GTK on the programming perspective (who wants to wrote GUI in C language, so painful and time consuming. C++ is already made, why not use it?)

Advantages of wxWidgets (based on my experience):
_ More native look'n'feel
_ Easy to use, powerful and more complete
_ Intuitive, comprehensive: APIs like MFC, which is the first toolkit I used. Short learning curve. Well documented.
_ Using C++, and ported to almost any other languages, especially well integrated with Python, the most interesting programming language.
_ Free for commercial use (Qt not)
_ Many tool built on it: CodeBlocks - a great free IDE; wxFormBuilder - a excellent free form designer for wx; Boa Constructor: great IDE for Python and wxPython.
_ Run even on Palm, WinCE, ...

The drawback is that it does not have native look'n'feel on KDE. You must use Qt-GTK to imitate, or use Qt to create GUI. On GNOME, use wxGTK instead of standard GTK, and making GUI is much less stressful.

---

