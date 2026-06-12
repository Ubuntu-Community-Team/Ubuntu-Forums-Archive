---
title: "can gnome 3 programs run on ubuntu?"
date: 2011-08-18
forum: Programming Talk
---

### Post by nickos on 2011-08-18
Is it possible for a gnome app to run on ubuntu?Cause i have seen some apps that are both on gnome and ubuntu with GTK+.

---

### Post by slavik on 2011-08-18
why would you think you wouldn't be able to do that?

---

### Post by nickos on 2011-08-18
> **slavik said:**
> why would you think you wouldn't be able to do that?


well , heres my experience :

i bought a mouse and cant get it working on gnome.
I decided to move on ubuntu,user which i have been for a long time.
I was not able to install anjuta 3.0 on ubuntu as well as the required packages,but could get the mouse working.
 So my question is that if i made an application on gnome using anjuta 3.0 and GTK+ 3 Will it be working on ubuntu since i was not able to install it properly?:confused:

---

### Post by Zugzwang on 2011-08-18
@OP: You seem to be mixing up a couple of things. Moving from Gnome to Ubuntu is like switching from a book that you don't like to a library: the types of the two things don't match. Gnome is only a Desktop environment, but no full Linux distribution, while Ubuntu is. So being unable to get a mouse running in Gnome is like being unable to park a car next to a ferry - if you can't do that, then it's not the fault of the ferry.

On the other hand, if you want to develop for GTK3, install the necessary package: [libgtk-3-dev]("http://packages.ubuntu.com/search?keywords=libgtk-3-dev").

Anjuta 3 appears to be not available for Ubuntu yet, so you can either stick with an older version or try to compile it yourself, as you already tried. There should however be nothing wrong with the older version, even if you write a GTK 3 program.

---

### Post by nickos on 2011-08-18
> **Zugzwang said:**
> @OP: You seem to be mixing up a couple of things. Moving from Gnome to Ubuntu is like switching from a book that you don't like to a library: the types of the two things don't match. Gnome is only a Desktop environment, but no full Linux distribution, while Ubuntu is. So being unable to get a mouse running in Gnome is like being unable to park a car next to a ferry - if you can't do that, then it's not the fault of the ferry.

On the other hand, if you want to develop for GTK3, install the necessary package: [libgtk-3-dev]("http://packages.ubuntu.com/search?keywords=libgtk-3-dev").

Anjuta 3 appears to be not available for Ubuntu yet, so you can either stick with an older version or try to compile it yourself, as you already tried. There should however be nothing wrong with the older version, even if you write a GTK 3 program.

alright then,which seems that GTK+ 3 apps i make on gnome wont be able to run on ubuntu right?

---

### Post by Zugzwang on 2011-08-18
> **nickos said:**
> alright then,which seems that GTK+ 3 apps i make on gnome wont be able to run on ubuntu right?

Absolutely no problem. First of all, a GNOME is installed by default in Ubuntu (which makes me wonder why you distinguish between Gnome and Ubuntu as the latter always contains the former). Then, compiling a GTK+ program on a Ubuntu platform will work if the packages are installed (which are available for sufficiently late Ubuntu distributions). Even if they are not installed, you can still compile your program with static linkage on another computer and just copy the executable to a Ubuntu computer. The only thing is that if you compile for 64-bit and copy the executable to a 32-bit kernel running computer, this won't work. But that's it.

---

