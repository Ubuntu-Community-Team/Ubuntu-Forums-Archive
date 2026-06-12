---
title: "Ubuntu gui source"
date: 2010-06-03
forum: Programming Talk
---

### Post by TerraEnvy on 2010-06-03
Hello I am new to using Linux based platforms however I know the programming, My problem is that I want to get a hold of the source package for the ubuntu Gui so I can customize it to my own personal liking, however I do not know where to find it.
Any help is appreciated.

-Terra

---

### Post by diesch on 2010-06-03
You can get the source code for a package *some_package* using
```
 apt-get source some_package
```

The GUI contains many programs distributed over mayn packages so you need be a bit more specific on what exactly you want to change.

---

### Post by nvteighen on 2010-06-03
> **TerraEnvy said:**
> Hello I am new to using Linux based platforms however I know the programming, My problem is that I want to get a hold of the source package for the ubuntu Gui so I can customize it to my own personal liking, however I do not know where to find it.
Any help is appreciated.

-Terra

There's no "Ubuntu GUI".

GUI in GNU/Linux is created by using a component called the X Window System (aka "X.org" or simply, "X"), which is not part of GNU/Linux (moreover, it works on other platforms as well), although all most popular distros ship it by default. Everything works on the X Window System, but to help developers and also to get a uniform look-and-feel in programs, GUI toolkit libraries were created: Qt and GTK+ are the most popular.

Then, some people created suites of useful graphical programs, usually choosing a GUI toolkit because they liked the features and look it has, called Desktop Environments: GNOME and KDE are the most popular, using GTK+ and Qt, respectively, for all their officially distributed programs. There are several others available too (Xfce, GNUStep, e.g.).

Then, GNU/Linux distros choose what Desktop Environment to ship. Ubuntu uses GNOME, Kubuntu uses KDE and Xubuntu, Xfce. Debian usually ships with GNOME but makes KDE available at their repos. OpenSUSE uses KDE as default, but you can use GNOME if you wish...

So, those are the "layers" of the GUI of your GNU/Linux OS. What do you want? If you want the source of GNOME's core, you'll have to check the sources of gnome-panel, gconf and similar packages... but keep in mind that the file manager's source (Nautilus) is somewhere else... Or do you want to check the source of a particular program?

But if you just want to tweak the look of your GUI, it's very probable that using the configuration tools will be enough... specially in KDE, where almost everything is configurable. (In GNOME it also is... but it's usually a bit more difficult).

---

### Post by juancarlospaco on 2010-06-03
GTK, QT, Wx, TK *(...)*

---

### Post by TerraEnvy on 2010-06-07
Sorry the person who posted previously on this account does not have access to the Internet at the moment so I am posting for her.


What we are looking for is what package to get for the top panels bar.

We plan on changing it so 
A: it is not stuck to the top but can be moved anywhere (and not just the sides but in the middle of the screen if so desired)
B: Change the shape of the bar so it is no longer just a straight line.

We know everything needed programming related however we are unfamiliar with linux in general.

So looking at the replies I know I have to use 
 apt-get source *package needed*
However We don't know what package to retrieve for that.

Thank you for your help 
-Terra (friend of)

---

### Post by juancarlospaco on 2010-06-07
gnome-panel

---

### Post by Possum Films on 2010-06-07
It might be worth checking out cairo dock, since I think that might already do what you want to do. It is similar to the Mac OS X dock but can be customised to be a different shape or look different and it can also do just about everything the gnome panel can do (applications menu, running applications, log out/power off buttons, clock, etc).

Of course there's still no reason you shouldn't modify the gnome panel if that's what you want to do.

---

