---
title: "Python/QT or GTK tutorial"
date: 2007-11-16
forum: Programming Talk
---

### Post by TSP on 2007-11-16
Hi! i am learning Python and i trying to find some basic tutorial about building GUI's in QT (better) or GTK..without luck..all the tutorials i found are about C++..anyone have some tutorial/book/web with this info?

Thanks!

---

### Post by smartbei on 2007-11-16
Try searching google for "python qt" (without the quotes). The first result is a very thorough book on the basics. Try similar tactics for gtk.

If you need more specific help, don't hesitate to ask. :)

---

### Post by LaRoza on 2007-11-16
My wiki has information on GTK with Python.

---

### Post by dwblas on 2007-11-17
Try here as well
[http://python-eggs.org/?row=2](http://python-eggs.org/?row=2)

---

### Post by charlie763 on 2007-11-19
You're in luck! [Gladex 0.4.1 was just released today]("http://ubuntuforums.org/showthread.php?t=617152"). It's a Python application which takes a .glade file written in the [ Glade User Interface Builder]("http://glade.gnome.org/") and generates code in Perl, Python, or Ruby. The generated code uses libglade to draw a GUI and is not raw pygtk code.

The  [ manual]("http://www.openphysics.org/~gladex/gladex-manual/") can help you get started quickly. You basically just design a GUI in glade and use Gladex to generate code. The generated code will have a templated function of each callback you define in Glade. It takes less than ten clicks to go from a .glade file to a program that will execute.

**Where can I find more information?**
Project main page: [http://www.openphysics.org/~gladex/](http://www.openphysics.org/~gladex/)
Download: [https://launchpad.net/gladex/+download](https://launchpad.net/gladex/+download)
Manual: [http://www.openphysics.org/~gladex/gladex-manual/](http://www.openphysics.org/~gladex/gladex-manual/)
Launchpad: [https://launchpad.net/gladex](https://launchpad.net/gladex)
Howto: [https://help.ubuntu.com/community/GladexHowto](https://help.ubuntu.com/community/GladexHowto) (outdated)
About wiki: [https://help.ubuntu.com/community/Gladex](https://help.ubuntu.com/community/Gladex) (outdated)

---

