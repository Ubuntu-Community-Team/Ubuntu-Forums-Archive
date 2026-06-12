---
title: "a solution for packaging to .deb"
date: 2010-06-13
forum: Programming Talk
---

### Post by JakeFrederix on 2010-06-13
I've recently posted a question as to how you are supposed to package a .jar to a .deb.
Turns out it's not that hard, but the process could be more user-friendly.

In attachment is a script called makeDeb, and it does just that.
It will prompt you for everything it needs to know to make a .deb (name of the program, name of the package, where to find the icon, ... ) and build one.
This .deb will contain the necessary scripts to install a desktop-entry (so that your program appears in the gnome-menu) and to remove that entry when you remove the package.

If you make adjustments, be so kind as to email me the script.

Kind regards,
Jake

*_note:_ this is only useful if you're trying to turn a .jar in a .deb*

---

### Post by nvteighen on 2010-06-13
> **JakeFrederix said:**
> I've recently posted a question as to how you are supposed to package a .jar to a .deb.
Turns out it's not that hard, but the process could be more user-friendly.

In attachment is a script called makeDeb, and it does just that.
It will prompt you for everything it needs to know to make a .deb (name of the program, name of the package, where to find the icon, ... ) and build one.
This .deb will contain the necessary scripts to install a desktop-entry (so that your program appears in the gnome-menu) and to remove that entry when you remove the package.

If you make adjustments, be so kind as to email me the script.

Kind regards,
Jake

*_note:_ this is only useful if you're trying to turn a .jar in a .deb*

Didn't try because I'm not a Java developer, but I wanted to add a little and related rant about Debian packages:

<rant mood="mad">
Debian packaging is a nightmere for anything that's not meant to be used with Makefiles, as the build process needs them... Packaging C and C++ is a breeze and easy, but... use Python and you'll have to jump into the distutils + python-support/python-central combo in order to have a sanely created Debian package. Use something else and you'll need to take account whether an arcanely documented debhelper script is there to help you or not...

So it doesn't seem strange to me that someone had to write a script to package a .jar into a .deb. Maybe the "idea" is that one should package Java in Debian not using .jar, but the whole bunch of .class files?
</rant>

---

### Post by JakeFrederix on 2010-06-13
But you wouldn't really be able to do anything with those .class files.
So the .debs created by this script simply copy the .jar into the file-system somewhere, and then make a .desktop-entry to run the .jar.

It's a tad stupid, but it works.

Jake

---

