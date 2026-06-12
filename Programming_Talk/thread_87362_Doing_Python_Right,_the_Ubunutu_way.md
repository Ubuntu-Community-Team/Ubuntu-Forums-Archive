---
title: "Doing Python Right, the Ubunutu way?"
date: 2005-11-07
forum: Programming Talk
---

### Post by moephan on 2005-11-07
Hi all -

Please excuse me if this questions have been answered already.

I picked up Python over the weekend, and wrote an app I am finding fairly useful. It's a GUI app, and I'd like ti behave like a normal Ubuntu application. Being new to Linux and Ubuntu, now that I have a good start on the script, I have a few questions about the normal ways to do things:

1. How is a python application typically distributed? What is the Ubuntu way of sharing the app? Since the app is a set of 3 or 4 .py files, and uses about 5 or 6 images, how do I keep these altogether and create a point of entry for users? For example, if this was a .NET app I would compile all the code into an .exe assembly, including the images, that I would add to the resources for the project. Users would just click on the .exe file.

2. The app runs "iwlist" which requires priveledges to run. How to I make that little box pop up for users to enter their passwords? 

3. What if I want to start a shared project? Is there a place where I would post the code, invite people to use it, submit changes, etc...?

TIA.

cheers, Rick

---

### Post by flower on 2005-11-09
check : [http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)

---

### Post by Retrix on 2005-11-09
[QUOTE=moephan]1. How is a python application typically distributed? What is the Ubuntu way of sharing the app? Since the app is a set of 3 or 4 .py files, and uses about 5 or 6 images, how do I keep these altogether and create a point of entry for users? For example, if this was a .NET app I would compile all the code into an .exe assembly, including the images, that I would add to the resources for the project. Users would just click on the .exe file.[/QUOTE]

I suggest you have a look at the source and packaging for serpentine. It is in the main distribution and uses python so it is a good example to model off. #apt-get source serpentine to take a look.

[QUOTE=moephan]2. The app runs "iwlist" which requires priveledges to run. How to I make that little box pop up for users to enter their passwords?[/QUOTE]

gksudo is what you're after.

[QUOTE=moephan]3. What if I want to start a shared project? Is there a place where I would post the code, invite people to use it, submit changes, etc...?[/QUOTE]

Sourceforge, your own site, ..., wherever you want really.

-Sam

---

### Post by majikstreet on 2005-11-12
2) gnome-sudo is the command, not gksudo.
3) I would say sourceforge, too.

---

### Post by kelsey23 on 2005-11-12
Well there are .pyc files, which are encrypted I belive. Also when you say "like a normal GNU/Linux application" do you mean with the Human controls instead of the X window that it typically comes in? It would help if you would speciify what extensions you are using to write your GUI (Tkinter, wxWindows), etc. If it is Tkinter, I know that it will always behave like the X way. I do belive there are some python development tools for GTK+/Gnome though.

---

### Post by maubp on 2005-11-14
*.pyc are compiled python files (generated from the *.py files).

You might want to read about the Python DistUtils (which will work on Windows to by the way), but I don't know how that applies to making a Debian style package for Ubuntu...

---

