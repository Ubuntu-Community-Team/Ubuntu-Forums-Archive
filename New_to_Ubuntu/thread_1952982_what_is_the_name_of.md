---
title: "what is the name of ?"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by josephmills on 2012-04-05
Hello there I would like to say that I am posting this in the Absolute Beginner Talk section . Because I am a Absolute Beginner when it comes to this. 

does anyone know the name of the tool or code that is used in Ubuntu server when installing like how they make purple backgrounds with questions. Or like when you install mysql how it asks for you password like this [http://lirent.net/wp-content/uploads/2008/04/ubuntu-install-mysql4.png](http://lirent.net/wp-content/uploads/2008/04/ubuntu-install-mysql4.png) 
or like this 
[http://static.howtoforge.com/images/perfect_server_ubuntu_11.10_ispconfig_3/5.png](http://static.howtoforge.com/images/perfect_server_ubuntu_11.10_ispconfig_3/5.png)
How would one go about making one of them ? 
thanks

---

### Post by Paqman on 2012-04-05
There's a package called [dialog]("apt:dialog") that can be used to create that kind of interface.

Just Google "bash dialog" for some tutorials on using dialog.

---

### Post by josephmills on 2012-04-05
Thanks Paqman =D>

---

### Post by codemaniac on 2012-04-05
I guess you want to create a terminal based installation wizard .
Never tried it yet but you could look at **urwid**, which is a Python-based GUI toolkit library. . It lets you write programs using GTK-style widgets and event interfaces for a text-based interface.

Here is the link for you to look at .
[http://excess.org/urwid/](http://excess.org/urwid/)

---

### Post by Cheesemill on 2012-04-05
It could be ncurses.
[http://en.wikipedia.org/wiki/Ncurses](http://en.wikipedia.org/wiki/Ncurses)

---

### Post by josephmills on 2012-04-05
Sweet thanks ! I will give them all a shot why not right. And yes it is for [https://launchpad.net/zpanelcp](https://launchpad.net/zpanelcp)
the installer script

---

