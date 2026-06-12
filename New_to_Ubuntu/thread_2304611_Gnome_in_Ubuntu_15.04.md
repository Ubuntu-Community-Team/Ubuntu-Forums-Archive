---
title: "Gnome in Ubuntu 15.04"
date: 2015-11-28
forum: New to Ubuntu
---

### Post by Jason_Hunter on 2015-11-28
I installed Gnome in Ubuntu 15.04, but when I restart gdm and log in, I only end up back with Unity. 

At the display manager, there is no way to select either Gnome or Unity. 

It says Ubuntu Gnome at the bottom of the display manager. 

When I search google for GNOME on Ubuntu 15.04, I only find a new distribution called Ubuntu GNOME. 

Any pointers to some documentation about how to install GNOME in Ubuntu?

I assume they can both be installed on the same system?

---

### Post by grahammechanical on 2015-11-28
What exactly did you install? The word gnome can refer to more than one software package. Ubuntu is built on Gnome 3 desktop environment (DE) but it does not use the Gnome 3 shell. Ubuntu uses Unity shell instead as the user interface (UI). Ubuntu also uses the LightDM display manager to provide login.

If you have installed Gnome Display Manager (GDM) and only that then you have only changed the software that manages the login.

What did you want to achieve? If you want the old look of Gnome 2 panel from about 5 years ago, then you can install gnome session flashback and that will give you 2 alternative login sessions - Gnome Flashback (Metacity) and Gnome Flashback (Compiz).

If you want the modern Gnone UI - Gnome shell, then install that and then choose that session at the LightDM login screen. 

Ubuntu Gnome is an official Ubuntu family member that is close to being what Ubuntu would have been like if the Ubuntu developers had chosen not to use Unity but Gnome 3 shell. And then there is Ubuntu Mate which is also an official Ubuntu family member that has the Mate desktop environment.

> The MATE Desktop has a rich history and is the continuation of the  GNOME2 desktop, which was the default desktop environment on many Linux  and Unix operating systems for over a decade. This means that MATE  Desktop is tried, tested and very reliable.

[https://ubuntu-mate.org/about/](https://ubuntu-mate.org/about/)

So, it all comes down to what it is you want to do.

Regards.

---

### Post by Jason_Hunter on 2015-11-30
I want the Gnome 3 Shell, ie, the current GNOME desktop. 

I have installed Gnome Shell and the rest of Gnome to my knowledge. I've also switched to GDM. 

Is it not possible to select a GNOME session from the GDM?

I have to switch back to lightdm to be able to select GNOME?

---

### Post by kansasnoob on 2015-12-01
This is a bit old but still applies:

[http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682)

That shows how to select/change sessions from the three common login screens.

Silly question - why install 15.04 when it has only 2 months left before EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

