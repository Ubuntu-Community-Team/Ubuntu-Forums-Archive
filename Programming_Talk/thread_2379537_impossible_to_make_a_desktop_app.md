---
title: "impossible to make a desktop app"
date: 2017-12-06
forum: Programming Talk
---

### Post by Carlosll on 2017-12-06
Hello

I have desired for months to make a simple app on linux but there is not enough resources or too much but dispersed all over the net. I am a programer, I know C and C++ but when I try to make an aplication I lost the days searching in the Nosense internet asking for why or where thoose libraries. I have tried to search for books that shows me to make a desktop app on linux but I can't find it. I go to ubuntu developer dot com and I found no clues at all about descktop programming. I installed an IDE for linux: anjuta and allways tell that somo libraries are missing. I go to the web page of anjuta and the manual have so few information. I have look for video tutorials and there is only one ""my first app in ubuntu" on youtube but further video tutorials are not. I following the tutorial I can not make a simple desktop app because some libraries and some environment paths that I have re checked for long don't work. 

I know C, C**. I understand that I have to use the gtk for the ui. why is so difficult to develop a simple desktop app on linux? 


which ide do you recommend me? thank you.

---

### Post by norobro on 2017-12-06
You said that you know C++ so perhaps these links will help:
[https://developer.gnome.org/gtkmm-tutorial/stable/index.html.en](https://developer.gnome.org/gtkmm-tutorial/stable/index.html.en)
[https://doc.qt.io/qt-5/](https://doc.qt.io/qt-5/)

I particularly like Qt. I use the Qt IDE (Qt Creator) for most of my C/C++ programming, Qt related or not.

---

### Post by faraco2 on 2017-12-07
Hi, 

if you wish to develop desktop applications for Linux and looking for a somewhat unified lists of tutorials for GUI programming (easily applied once you know how to compile/run them), I will highly consider to checkout [http://zetcode.com](http://zetcode.com) for further informations.

and GTK+3 official hello world quick introduction is pretty good too - [https://developer.gnome.org/gtk3/stable/gtk-getting-started.html#id-1.2.3.5](https://developer.gnome.org/gtk3/stable/gtk-getting-started.html#id-1.2.3.5)

If you are literally beginning to learn how to make a desktop application on the Linux platform, I highly suggest from my own experience to use a simple text editor and compile your programs from the command line.

I recommend it to just make yourself familiar with the pkg-config, makefile and the common GTK+ development workflows without using any IDEs if you are not yet already.

---

### Post by fallenshadow on 2017-12-12
Hi there,

I was like you once. I tried for years to make progress with creating my first programs with Gtk and C++. In the end I got far but I realized its too much of difficult and long process. I since switched to Qt and QtCreator as the IDE. I feel its the only way desktop development is fun and not too difficult at all in comparison.

---

### Post by gray74 on 2017-12-17
I am kind of new to desktop development.
But as far as I am concerned I agree with other comments. Qt would be the best choice if you know C++, which is a privilege.  
I would consider using Qt. Good documentation and good community.

---

### Post by Carlosll on 2017-12-18
Helo

Thank you all norobo, faraco2, fallenshadow, gray74. Thank you for showing me the Qtcreator and the otther links. I'm so happy I have finished my first helloword and now with the qtcreator I see the light. Thank you.

I have found the free version of Qt inside the Qt web page. And with the tutorial from youtube Now I'm learning. So, I will mark this thread as solved. 

If one day we meet I will invite you to drink some beers or something. Thank you.

---

### Post by sandman887 on 2017-12-24
I can empathize with people who struggle to find solutions. I have been trying for weeks to solve my problem, and I finally decided to ask for help. I always prefer to figure out my own problems, and ask only as the last resort. I agree that information is extremely unnecessarily difficult to find. To the point of madness. There are just so many libraries out there that it's difficult to find the one you need.

I like the assistance that the IDE in Qt provides when you hit the . and when you are typing in arguments. But I also like coding in ViM the traditional way, and most of what I use is based on Gtk.

---

