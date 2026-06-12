---
title: "[SOLVED] Installing issues"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by CAPTNCRIPT on 2008-09-11
I just installed ubuntu and i've been mainly a microsoft user for my whole life i've come to a screen that is like that of command prompt and i'm looking to get to a gui to work with i'm not sure if maybe i installed the server version or something so I don't have the gui if someone could point me in the right direction that would be great

---

### Post by overdrank on 2008-09-11
> **CAPTNCRIPT said:**
> I just installed ubuntu and i've been mainly a microsoft user for my whole life i've come to a screen that is like that of command prompt and i'm looking to get to a gui to work with i'm not sure if maybe i installed the server version or something so I don't have the gui if someone could point me in the right direction that would be great

Hi and welcome, Did you download and install the desktop version? Could you tell us some system specs? 
What kind of command prompt, is it Busybox v1.1.3  initramfs

Also I have moved you post to its own thread instead of posting in the Beginners forum sticky. :)

---

### Post by CAPTNCRIPT on 2008-09-11
thanks for moving it and i believe i downloaded the desktop version and by command prompt i mean it's a black screen that you can type commands into it's not a desktop with icons and what not

---

### Post by Bulat Sirazetdinov on 2008-09-11
What is written on the screen ?

Try using this command:
```
startx
```
What does it say ?

---

### Post by oldsoundguy on 2008-09-11
In Ubuntu there are three primary ways to install.  One is to go to system> administration> synaptic package manager ... choose the items to install from the GUI, sign in and install.
Another is under Applications> add/remove programs.  That also is a GUI method of installing.
What you have is from Applications> accessories> terminal> and that requires that you enter lines of code .. in the main they will be cut and paste or copy .. in order to install items.  Terminal is also good for updating your files. (and yes, terminal is very similar to the command prompt, but you still have to use your password in order to function there, too!)
Terminal is very useful if you are going to install additional items such as from this help page: [http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

### Post by fiddler616 on 2008-09-11
@oldsoundguy: Nice info...but why? Read the OP again.
@OP: Try pressing Ctrl-Alt-F7. Ctrl-Alt F1-6 is different Terminals (not the X Window System), and F7 is the GUI.
If that does squat, then it's possible you don't have a desktop environment.
I believe the line of code is:
```
sudo aptitude install ubuntu-desktop
```
(I'm assuming you're using Ubuntu. If you're using kubuntu, xubuntu, etc. Then replace the ubuntu part with whatever it is. Ex. ...install xubuntu-desktop)
Windows to Ubuntu in a few sentences:
a)Good job finding the Forums, they will help you with EVERYTHING!
b)Unlike Windows, Linux has different "Desktop Environments" (GUIs on steroids). GNOME and KDE are the most common (thus the K in Kubuntu), and Xfce is really popular for older computers (Xubuntu).
c)Unlike Windows, the terminal is very useful, and the more you learn, the more efficient you'll be.
d)That said, there's GUIs for just about everything, and there's no *need* to learn the Terminal.
e) The 'start' menu is a lot more useful. So useful it has its own pane up top.
f) Read oldsoundguy's post on installation methods
g) Workspaces are great. Bottom right-hand corner. They're pretty intuitive, it's easier to just play with them than explain them. Think virtual monitors.
-----
OK, I'll try to not be hypocritical, and will stop straying from the OP.
(OP stands for Original Post(er)) (This means you)

---

### Post by Iowan on 2008-09-11
I doubt it'll work, but try CTRL-ALT-F7.  Most likely, you will just have another black screen... but you *might* get lucky!

---

### Post by CAPTNCRIPT on 2008-09-11
thank you all for your help

---

### Post by CAPTNCRIPT on 2008-09-12
I checked i have what is claimed to be the desktop version by the file when i type start x it tells me fatal servererror:
no screens found

waiting for x server to begin accepting connections 
giving up.
xinit: Connection reset by peer (errno 104): unable to connect to x server
xinit: no such process (errno 3): server error.
i am running regular ubuntu not xubuntu or kubuntu

---

### Post by CAPTNCRIPT on 2008-09-12
I'd also like to mention i did get this file from here and installed it through daemon tools to create a virtual cd to load it through

---

