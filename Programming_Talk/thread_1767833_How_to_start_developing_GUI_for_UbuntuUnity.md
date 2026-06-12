---
title: "How to start developing GUI for Ubuntu/Unity"
date: 2011-05-26
forum: Programming Talk
---

### Post by jamesjenner on 2011-05-26
G'day peoples,

I've got a background with quite a few languages, C and C++ included. As I'm getting more into Ubuntu I've been curious as to what is involved with programming GUI applications within Ubuntu and the Unity environment. I know there is information around about developing for Gnome, but I'm not sure on the implications of Unity (though I'm aware of Application Indicators). 

I do have a reasonable knowledge of Unix, rough understanding of aspects of Linux but nothing at all about Gnome or KDE other than what they are and that one uses mainly C and other other C++.

I'm interested in any guides or HOWTO's that state how to get started doing this for Ubuntu (standard, not KDE or any other DE), any information on IDE's to use (eg. can Eclipse be used, etc) and what the best path is to take to develop a GUI application for the Unity environment.

I'm also happy to play around with low level stuff to do some 'fancy stuff' but at first I would like to learn the standard GUI framework.

Cheers,

James.

---

### Post by r-senior on 2011-05-26
I wouldn't claim to be an expert but I'm in the process of doing the same thing (using Python/GTK) and I'm not finding that there's that much to do in terms of supporting Unity ...

The application displays an application menu (aka global menu) without modification - just add the menu to the window as normal. In Ubuntu Classic it appears within the window, in Unity it appears up on the panel.

If you create a .desktop file (in ~/.local/share/applications for testing), the Dash will pick up the application, it shows up in the Unity launcher, you can pin it to the launcher and so on.

Things like notifications are provided by libraries, e.g. pynotify in the case of Python.

I can't comment on doing things like adding to the notification area but if you search for juancarlospaco's weather indicator thread from within the last couple of weeks, that's one example.

---

### Post by jamesjenner on 2011-05-26
Hey mate,

Yeah, that's how I started. I was interested in gdesklets back in 10.10 (which have proven frustrating) and then started looking at conky (which is python and can be LUA). But after posting this thread I started doing some further googling and came across:

[http://developer.ubuntu.com/](http://developer.ubuntu.com/)

Not sure yet if it will tell me everything I need to know but looks like it's what I wanted. Also found the following which are interesting:

[http://unity.ubuntu.com/projects/unity/](http://unity.ubuntu.com/projects/unity/) - regarding unity with links about the APIs and doco, with an interesting page on ideas to develop for unity, something to look at me thinks!

[http://unity.ubuntu.com/projects/appindicators/](http://unity.ubuntu.com/projects/appindicators/) - application indicators with links to an overview and the API's, should be useful.

So I think I've kinda answered my main question, about how to get started.

Anyone doing GUI development using an IDE? My searches on Eclipse only found very old articles (was searching with gnome, maybe there is a more appropriate search?). I am more than comfortable using a shell and vi, but I suspect I will be far more productive using an integrated environment with debugger.

Oh one question I had forgotten to ask was regarding version control/source hosting. The corner of my world has gone git mad lately but I know a few people use sourceforge and then there is launchpad and a few others as well. Is launchpad the recommended one to use or is git and others considered okay?

---

### Post by jamesjenner on 2011-05-26
Just been playing around in the developer site mentioned above. Decided to skip the Quickly stuff as I like to know what's going on and why so playing with Anjuta. Annoying how it wants projects to be hosted on what's it, fair enough to encourage open source, but I wouldn't want to bother anyone else with half baked ideas as I learn the API's for Gnome and remember those many years ago when I used to work with C.

Shame Gnome isn't C++. I was hoping it was as I would have thought an oop approach would have been more logical for a graphical framework, but at the end of the day I know I'm going to have far too much fun :)

---

### Post by SledgeHammer_999 on 2011-05-26
Let me tell it again for the nth time(not to you personally)

**DO NOT CONFUSE** GNOME or KDE WHEN THINKING ABOUT **GUI**. These are two separate things. 

Do you want to create GUI applications? If yes then you need a **gui toolkit** or **gui framework** as you said. In Linux there isn't a standard one(we have free choices). The 2 mainstream ones are **[Gtk+](www.gtk.org)** and [Qt](http://qt.nokia.com/). 

GNOME uses Gtk+
KDE uses Qt.
**BUT YOU CAN USE** a Qt application in Gnome and vice versa with no side-effects.

Since you want to target the GNOME desktop environment and want to do it in C++ I **suggest** you use [Gtkmm](www.gtkmm.org). Gtkmm provides C++ bindings for the C API of Gtk+.

PS: Another notable gui toolkit is [wxWidgets](www.wxwidgets.org)

---

### Post by jamesjenner on 2011-05-26
> **SledgeHammer_999 said:**
> Let me tell it again for the nth time(not to you personally)

**DO NOT CONFUSE** GNOME or KDE WHEN THINKING ABOUT **GUI**. These are two separate things. 

Do you want to create GUI applications? If yes then you need a **gui toolkit** or **gui framework** as you said. In Linux there isn't a standard one(we have free choices). The 2 mainstream ones are **[Gtk+]("http://www.gtk.org")** and [Qt]("http://qt.nokia.com/"). 

GNOME uses Gtk+
KDE uses Qt.
**BUT YOU CAN USE** a Qt application in Gnome and vice versa with no side-effects.

Man that's confusing but makes sense now you have explained it. I'll have to do a tad more research to get my mind about the architecture of both. Shame the Ubuntu development site doesn't make this distinction clear, it talks about developing under Gnome from memory, which doesn't help in removing the confusion. Oh I understand they're trying to attract application writers but at the end of the day I would rather see a guide on the architecture and what appropriate frameworks exist, what the common patterns are and how best to approach development in the various areas. 

Last night I found a series of tutorials about Gnome (their words, development in Gnome). But I only just quickly read the first few, haven't seen any mention of Gtk+ or Qt.

> **SledgeHammer_999 said:**
> Since you want to target the GNOME desktop environment and want to do it in C++ I **suggest** you use [Gtkmm]("http://www.gtkmm.org"). Gtkmm provides C++ bindings for the C API of Gtk+.

PS: Another notable gui toolkit is [wxWidgets]("http://www.wxwidgets.org")

I'm happy to develop in whatever is the 'standard' language and 'standard' framework. I have a sneaking suspicion that it's not as simple as that, but if for example C and Gtk+ is the most commonly used approach (which may not even make sense, I've not checked out Gtk+ yet) then that is the path that I would prefer to follow. So recommendations based on that would be appreciated. 

I've read that Unity runs in a 3d environment, thus providing true transparency, etc. Does this mean that there is a framework now to develop applications to utilise the true 3d nature of Unity or is it just a case of using the existing application based utilities ignoring whether it runs under Gnome, KDE or Unity?

Btw, a sticky documenting this stuff would be really handy under the Programing Talk area (or if there is another more appropriate place). Specially if it's been raised a lot, I looked for a sticky through the forums before posting and tried searching, but it was difficult to filter out all the unwanted results.

---

### Post by SledgeHammer_999 on 2011-05-26
> **jamesjenner said:**
> Man that's confusing but makes sense now you have explained it. I'll have to do a tad more research to get my mind about the architecture of both. Shame the Ubuntu development site doesn't make this distinction clear, it talks about developing under Gnome from memory, which doesn't help in removing the confusion. Oh I understand they're trying to attract application writers but at the end of the day I would rather see a guide on the architecture and what appropriate frameworks exist, what the common patterns are and how best to approach development in the various areas. 

Last night I found a series of tutorials about Gnome (their words, development in Gnome). But I only just quickly read the first few, haven't seen any mention of Gtk+ or Qt.



I'm happy to develop in whatever is the 'standard' language and 'standard' framework. I have a sneaking suspicion that it's not as simple as that, but if for example C and Gtk+ is the most commonly used approach (which may not even make sense, I've not checked out Gtk+ yet) then that is the path that I would prefer to follow. So recommendations based on that would be appreciated. 

I've read that Unity runs in a 3d environment, thus providing true transparency, etc. Does this mean that there is a framework now to develop applications to utilise the true 3d nature of Unity or is it just a case of using the existing application based utilities ignoring whether it runs under Gnome, KDE or Unity?

Btw, a sticky documenting this stuff would be really handy under the Programing Talk area (or if there is another more appropriate place). Specially if it's been raised a lot, I looked for a sticky through the forums before posting and tried searching, but it was difficult to filter out all the unwanted results.


Gnome, KDE, Unity all have APIs available mainly for non-UI things. I cannot expand on this however.

You also have to understand that there is no "standard" programming language in Linux. The 3 most used ones are C, C++ and Python. Then comes C#, Java etc. I **suggest** that if you are comfortable with any language you use that. Both Gtk and Qt have bindings for many languages. Most distros ship with python and C# (and other) interpreters.

I don't know anything about Unity(I use Debian). But I know one thing for sure it is neither "standard" nor "mainstream".

---

### Post by jamesjenner on 2011-05-28
> **SledgeHammer_999 said:**
> Gnome, KDE, Unity all have APIs available mainly for non-UI things. I cannot expand on this however.

You also have to understand that there is no "standard" programming language in Linux. The 3 most used ones are C, C++ and Python. Then comes C#, Java etc. I **suggest** that if you are comfortable with any language you use that. Both Gtk and Qt have bindings for many languages. Most distros ship with python and C# (and other) interpreters.

I don't know anything about Unity(I use Debian). But I know one thing for sure it is neither "standard" nor "mainstream".

I understand what your saying but I would have thought that there are advantages to choosing one framework over another and choosing one language over another, purely from the produced binary point of view, also from the point of view of conforming with the style of the DE. I'm always interested in efficient and optimised code but I do like tools that make coding easier. However in my experience this comes at a cost. 

When I've used alternate frameworks/libraries I have found to end with a different look and feel, dependant on how that framework has implemented UI components (not talking about Gnome here). So maybe this isn't a concern for Gnome, but I would have thought it might be.

So at the end of the day I would have thought there would be one framework/API's for a language that would result in the most efficient and compliant Gnome application. Also the framework/API would be the one that is consistently the most up to date with changes in the Gnome environment.

Cheers,

James.

---

### Post by SledgeHammer_999 on 2011-05-28
> **jamesjenner said:**
> 
When I've used alternate frameworks/libraries I have found to end with a different look and feel, dependant on how that framework has implemented UI components (not talking about Gnome here). So maybe this isn't a concern for Gnome, but I would have thought it might be.

So at the end of the day I would have thought there would be one framework/API's for a language that would result in the most efficient and compliant Gnome application. Also the framework/API would be the one that is consistently the most up to date with changes in the Gnome environment.

Cheers,

James.

There a few ways to see if different frameworks fit well in your desired DE.

1. Make a sample Qt application and run it under Gnome/Xfce and see if it fits as you want.

2. Install a Qt app from the repos and run it in Gnome/Xfce. I recommend qBittorrent.

The programming language is irrelevant. But if you are **really** concerned about fitting in then you should choose Gtk+ for Gnome/Xfce and Qt for KDE.

NOTE: wxWidgets is the same as using Gtk on Linux. On Linux it uses the Gtk API and on Windows the native API.

---

### Post by jamesjenner on 2011-05-28
no worries, thanks for the suggestions. 

Cheers,

James.

---

