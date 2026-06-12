---
title: "Gui programming in Linux"
date: 2008-06-05
forum: Programming Talk
---

### Post by KingTermite on 2008-06-05
Ok....I've been a developer for a while (about 10 years). I've done embedded and some Windows GUI stuff (even a little java). I'd like to start playing with some GUI programming for Linux.

I've seen mention of GTK+, Qt and I know native X Window programming and Java exist.

1) Are there others I'm missing?
2) What would be the best to learn/use for any UI type programming in Linux (and why)?

Thanks for any input.

---

### Post by mike_g on 2008-06-05
I think theres a sticky about this.

It also depends what language you are using. If youre using Java then swing is very easy to use, but IMO looks kind of ugly. GTK is coded in C, but theres wrappers for C++, Java, Python and probably a load of other languages. I had a go at that and I quite liked it, but if you want to make it cross platform/WM then you need to add it as a dll with your prog. Never used QT myself. I think wxWidgets is another possibility.
Also, I heard that SWT for java uses native widgets if thats what youre after.

---

### Post by KingTermite on 2008-06-05
Thanks for the input. I've used Java Swing ( a long time ago ) and I agree....I didn't like it much, not that pretty.

I grabbed a book on Qt at the libary last week and from a teeny bit I've looked at it so far, it sounds very similar to GTK. It's a C/C++ framework that has been ported to other platforms.

I guess I'm more looking for "what do most people in the linux world normally use?". What's the most common framework for GUI application development?

---

### Post by ivze on 2008-06-05
As far as I know, there are legal troubles with QT. GTK/GTK+ are free. So, better use GTK.

---

### Post by samjh on 2008-06-05
GTK+ combined with C, C++, or Python, is very very popular.

Especially on Gnome and Xfce environments, GTK+ with Glade and Python is a common choice for small and medium-sized projects.

Attached is a quick example of a GTK+/Glade/Python program I knocked up (tar file: extract hellogtk.glade and hellogtk.py).  Type a name in the field, click the button, and it will say hello to you. :)  You'll need to have python-glade2 package installed.

[quote=ivze]As far as I know, there are legal troubles with QT. GTK/GTK+ are free. So, better use GTK.[/quote]There are no legal troubles with Qt.  Its licensing troubles were completely resolved in June 2005, when Qt was released under GPL.

Trolltech also has an agreement with the KDE Foundation to release Qt under a BSD license if Trolltech becomes defunct or bought out.

Qt is a fantastic toolkit with perhaps the best documentation seen in the FOSS world.  Speak not evil! :)

---

### Post by maximinus_uk on 2008-06-05
There are no legal issues with QT. Maybe 5 years ago things were different.

QT and GTK are both good GUI kits. KDE uses QT, whilst Gnome uses GTK. So I'd say just pick whatever you think looks better. Both sides come with dialod designers (Glade for GTK and QTDesigner for QT).

Good luck!

---

### Post by LaRoza on 2008-06-05
> **ivze said:**
> As far as I know, there are legal troubles with QT. GTK/GTK+ are free. So, better use GTK.

No, QT is could actually be considered a brilliant move for free software. For free software, QT is free. For non free software it isn't. So it essentially encourages free software and sapps money from those that aren't free. A pretty good arrangement if you ask me.

(If you didn't ask me, too bad ;))

There are many toolkits, and the sticky has the link to the thread. (wxWidgets was left out, along with Tk)

---

### Post by LaRoza on 2008-06-05
> **KingTermite said:**
> 
1) Are there others I'm missing?
2) What would be the best to learn/use for any UI type programming in Linux (and why)?


0. Yes, but don't worry about it.
1. No best, use what you want. (If you want to make a fast decision, GNOME/Xfce apps use GTK, and KDE apps use QT, but either will run fine on the other.)

---

### Post by pmasiar on 2008-06-06
> **LaRoza said:**
> No, QT is could actually be considered a brilliant move for free software. For free software, QT is free. For non free software it isn't. 

Not only that, QT has foundation which has access to the code and if Trolltech goes belly up or someone buys it and stops releasing free code, foundation will release code under GPL. so QT is 100% safe now.

BTW you need to understand that this extra double safety is result of jiu-jitsu move of FOSS with GNOME: if Trolltech did not did that, they would never achieved as much as they did , because people would just use really free toolkit. They were forced to make it 100% GPL free with guarantee - this is exactly what RMS wanted accomplish with GPL.

Resistance is futile, you will be assimilated :-)

---

### Post by KingTermite on 2008-06-06
> **LaRoza said:**
> 1. No best, use what you want. (If you want to make a fast decision, GNOME/Xfce apps use GTK, and KDE apps use QT, but either will run fine on the other.)

OK....good info. I guess I didn't realize when I posted, but that was an underlying question. I wanted something that would work both for KDE and Gnome.

BTW, I have used Tk (ActiveState perl on windblows). It was nice and simple, but I don't think it would be that great for anything other than a small project.


So it seems its down to Qt and GTK. Which of these two do you fellow coders prefer, and why?

Which has an easier model/framework to work with?
Which is faster/more responsive (in the GUIs created)?
How about memory used for GUIs created?

---

### Post by days_of_ruin on 2008-06-06
pyGtk ftw!

---

### Post by fred.reichbier on 2008-06-06
I'd say: read some docs and use what _you_ like. pygtk and qt are similar in some points, although there are many differences. you'll see: all gnome people will suggest pygtk, all kde people qt :P

Oh, aahm... I've tried wxWidgets, too, and it's quite nice. Looks native on Windows and MacOS (?) and uses gtk+ in Linux :D

---

### Post by LaRoza on 2008-06-06
> **pmasiar said:**
> 
Resistance is futile, you will be assimilated :-)

Now we need to get CptPicard...

> **KingTermite said:**
> 
So it seems its down to Qt and GTK. Which of these two do you fellow coders prefer, and why?

Which has an easier model/framework to work with?
Which is faster/more responsive (in the GUIs created)?
How about memory used for GUIs created?

There are other threads on this.

Consider that VLC, Opera, and the entire KDE project uses QT and Xfce/GNOME and all of their apps use GTK, they are equal. They also have GUI designers (see sticky).

---

### Post by mike_g on 2008-06-06
For some reason I thought that VLC uses wxWidgets.

---

### Post by KingTermite on 2008-06-06
> **LaRoza said:**
> There are other threads on this.
Feel free to point some out. Trying to search for "GTK" and/or "Qt" in a linux programming forum is like trying google for the rock band "Live" (e.g. searching for a particular drop of water in Niagara Falls).

---

### Post by unoodles on 2008-06-06
wxWidgets is my recommendation. It's cross-platform and has libraries for multiple languages.

"""For some reason I thought that VLC uses wxWidgets. """

It does.

---

### Post by LaRoza on 2008-06-06
> **mike_g said:**
> For some reason I thought that VLC uses wxWidgets.

It may have changed to it, [http://en.wikipedia.org/wiki/Qt_(toolkit)#Applications_built_using_Qt](http://en.wikipedia.org/wiki/Qt_(toolkit)#Applications_built_using_Qt)

> **KingTermite said:**
> Feel free to point some out. Trying to search for "GTK" and/or "Qt" in a linux programming forum is like trying google for the rock band "Live" (e.g. searching for a particular drop of water in Niagara Falls).

[http://www.google.com/search?client=opera&rls=en&q=site:ubuntuforums.org+gtk+vs+qt&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=site:ubuntuforums.org+gtk+vs+qt&sourceid=opera&ie=utf-8&oe=utf-8)

They are all pointless. Use what you want.

---

### Post by samjh on 2008-06-06
> **KingTermite said:**
> So it seems its down to Qt and GTK. Which of these two do you fellow coders prefer, and why?

Which has an easier model/framework to work with?
Which is faster/more responsive (in the GUIs created)?
How about memory used for GUIs created?

It depends on your purpose.

Qt is far more than just a GUI toolkit.  It is a large library which includes networking, multi-tasking, database access, among other features (including the GUI, of course).

GTK+ is just a GUI toolkit and nothing more.

In my opinion, if you are developing an application which requires both a GUI as well as those other features I have listed for Qt, and you prefer to work with one highly integrated set of libraries, choose Qt.  But if you just want a GUI toolkit and prefer to pick and choose libraries for other functions, then use GTK+.

---

### Post by kostkon on 2008-06-06
Most people here seem in favor of *QT*, bah!

I would recommend you to use the [*Gnome Libraries*]("http://library.gnome.org/devel/references"), if you are mostly targeting the *Ubuntu* desktop or just *GTK* if you want to make it cross-platform (*Windows*, *Mac OS X*).

Don't forget to check the [*Clutter* library]("http://www.clutter-project.org/") if you want to make a visually rich GUI (with plenty of effects, hehehe! :twisted:) a la *Mac OS X*'s [*Core Animation*]("http://www.apple.com/macosx/technology/coreanimation.html").

---

