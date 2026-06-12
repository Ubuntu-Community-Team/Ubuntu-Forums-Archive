---
title: "Does Linux have an API?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by EleFlameMax on 2008-06-20
I'm not sure I understand the system of program building here on Linux. Are the widget toolkits like GTK as far as we get into an official API?

---

### Post by Xerp on 2008-06-20
There are loads of tools - what are you trying to achieve specifically. There is no one "Linux" API.

---

### Post by EleFlameMax on 2008-06-20
> **Xerp said:**
> There are loads of tools - what are you trying to achieve specifically. There is no one "Linux" API.

right, but isn't there a "one" Microsoft API? The thing that WINE emulates. Does Ubuntu have a main Development "SDK"?

---

### Post by sdennie on 2008-06-20
> **EleFlameMax said:**
> right, but isn't there a "one" Microsoft API? The thing that WINE emulates. Does Ubuntu have a main Development "SDK"?

Haha.  Part of the reason it took wine 15 years to get to version 1.0 is because there are 10,000 Microsoft APIs.

---

### Post by Xerp on 2008-06-20
You get the full source for virtually everything :)

WINE and Ubuntu are two very different kettles of fish.

For Ubuntu development, I'd suggest that you go here:

[https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)

For WINE development, take a look here:

[http://www.winehq.org/site/contributing#devel](http://www.winehq.org/site/contributing#devel)

For the Linux Kernel by itself, take a look here:

[http://www.kernel-api.org/](http://www.kernel-api.org/)

---

### Post by Nameless_one on 2008-06-20
"Linux" is just a kernel, that is, only VERY basic operations like a process scheduler, a file system and drivers. On top of that, though, reside desktop environments, like Gnome or KDE, which provide APIs for you to write applications compatible with each. 

if you want to write a regular application, you should use a toolkit like GTK+ or Qt. I think a "Linux API" is nothing like what you expect, and what you are looking for is a toolkit like the abovementioned. 

Bear in mind though, that GTK+ applications are Gnome-oriented and Qt applications KDE-oriented. If what you want is to write an application that runs independently from desktop environments, there could be other toolkits. One way I can think of right now is writing your app in Java, and designing everything yourself, although that might prove difficult. You're probably better off using a popular toolkit for starters. Most people, even though they are running Gnome, use some KDE applications and vice versa, anyway.

---

### Post by Methuselah on 2008-06-20
There is no official standard GUI api because there is no official standard GUI toolkit on linux. The most popular are the GTK+ and Qt toolkits.

And of course, there are system calls to do numerous non-gui things from launching a new process to opening a file.

In my messing around one thing I've found is that the linux APIs seem to fit organically into the nature of C whereas the win32 API always felt like something alien in style.

---

### Post by atomkarinca on 2008-06-20
Let's not forget [Etk]("http://www.enlightenment.org/").

---

### Post by Tuxoid on 2008-06-20
Okay, first a few questions:

1. What type of interface do you plan on developing for? command-line, GUI or is it a Library?

2. What do you want users to do with it (i.e. what is it's intended use?)?

3. If it's a GUI application, what kind of philosophy on customization, appearance, and interface design are you taking? This is important in matching human interface guidelines Linux's desktop environments.

[[COLOR="Blue"]Gnome's User Interface Guidelines[/COLOR]]("http://library.gnome.org/devel/hig-book/stable/")

[[COLOR="Blue"]KDE's User Interface Guidelines[/COLOR]]("http://wiki.openusability.org/guidelines/index.php/Main_Page")

If you are making a GUI-based Application, I would suggest taking a gander at the Human Interface Guidelines. Developers do not have to follow Human Interface Guidelines, but it's generally, it's a good idea. It can be a great way to gain respect from the developers of Gnome and KDE. Unfortunately, if Gnome developers see applications, on their platform, that have ignored their Human Interface Guidelines, they will mark usability bugs for that application.

---

