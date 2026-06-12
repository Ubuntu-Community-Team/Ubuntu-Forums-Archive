---
title: "instant messaging.."
date: 2008-05-24
forum: Programming Talk
---

### Post by karan mangat on 2008-05-24
hi
i am trying to make an instant messenger, for linux.
i have a good knowledge of c/c++. i started with learning socket programming
which was more of using system calls. 

1. should i be using only system calls so as to implement it
2. can i use qt4 so as to implement it.

which option is better?
cant decide.

thanks.

---

### Post by pmasiar on 2008-05-24
If you think that Qt4 is relevant to IM, you need to learn more first before being ready :-)

Also, I recommend to join any from many existing IM projects before starting yet another new one.

---

### Post by LaRoza on 2008-05-24
> **karan mangat said:**
> hi
i am trying to make an instant messenger, for linux.
i have a good knowledge of c/c++. i started with learning socket programming
which was more of using system calls. 

1. should i be using only system calls so as to implement it
2. can i use qt4 so as to implement it.

which option is better?
cant decide.

thanks.

How to start a project:

* You have an itch. 
* You have a language and toolset (C++ I am assuming if you want to use QT4). 
* And now it is time to look at available libraries.

Try libpurple: [http://developer.pidgin.im/wiki/WhatIsLibpurple](http://developer.pidgin.im/wiki/WhatIsLibpurple)

You can use qt4 with it if you wish. There is also no language called c/c++ and QT4 is not for C (as far as I know)

---

### Post by Majorix on 2008-05-24
An IM client for Linux? Even though it sounds good, it seems to me like nobody will use it (no offense to you) because they will be too lazy to sign up for your service.

Other than that, I wouldn't code for Linux-only. There are actually very few programs which haven't been ported to Windows or OSX (cross-platform, as we call). Easiest way for this in my mind is to use Python. C++ isn't the definition for cross-platform development.

As suggested, I would suggest looking into sourcecodes for popular IM-clients before starting to code your own, so that you have an idea of how things work and earn some exp.

I encourage you to take this road. Don't be a lazy *** like myself :D Good luck!

@pmasiar:
What is wrong with using Qt4 for his project?

---

### Post by CptPicard on 2008-05-24
pmasiar: [http://doc.trolltech.com/4.0/qt4-network.html](http://doc.trolltech.com/4.0/qt4-network.html)

I would not want to introduce a Qt dependency only for some socket wrapper though. Whole different story if he's aiming for a Qt/KDE app.

---

### Post by pmasiar on 2008-05-24
I have no problem someone using Qt for this project, just I do not see why toolkit for GUI frontend should be important decision made up-front. Obviously frontend could be made by using anything (including Qt). But if OP is not aware of such trivialities, I deeply suspect s/he is not ready to solve real complicated problems down the line to IM, that's why I questioned it.

---

### Post by LaRoza on 2008-05-24
> **pmasiar said:**
> I have no problem someone using Qt for this project, just I do not see why toolkit for GUI frontend should be important decision made up-front. Obviously frontend could be made by using anything (including Qt). But if OP is not aware of such trivialities, I deeply suspect s/he is not ready to solve real complicated problems down the line to IM, that's why I questioned it.

QT actually has libraries for almost everything. (With C++ anyway, I don't use QT). It's libraries as far as I know can completely replace the standard ones.

But I do agree, the GUI toolkit is the last thing to think about, unless one is using an existing library like libpurple.

---

### Post by karan mangat on 2008-05-25
cant find any documentation on libpurple.
plus i considered qt4 as i felt it had libraries (wroth using) for
my project. i am a novice in using libraries.only worked with ncurses. 

problem i am facing is that i cannot choose between the 2:
1. as i want to make a simple IM(such that it just sends and receives message to/from another computer), should i use system calls provide by the OS, or
2. use some library so as to do so
   (what i feel is using a library make things easier)

thanks

---

### Post by Lau_of_DK on 2008-05-25
> **karan mangat said:**
> 
2. use some library so as to do so
   (what i feel is using a library make things easier)

thanks

In my oppinion you should go right ahead and use Qt4. First off there is nothing in the Linux world that comes close to the ease of GUI design (that is, while not being extremely ugly) that Qt gives. Secondly Qt has some very nice classes that replace mostly everything else, including several networking classes. (there is an exhaustive list on their website).

Secondly, when its something as simple as passing a few messages back and forth, just jump right in an do it. A simple server/client  could have been completed in the time this thread has been running :)

Starting point: sudo apt-get install eclipse
next up: [Download Qt eclipse integration(link)]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")
Finally: [Follow this guide to integrate(link)]("http://trolltech.com/developer/downloads/qt/qteclipse-installmanual")

Best of luck,
Lau

---

### Post by LaRoza on 2008-05-25
> **karan mangat said:**
> cant find any documentation on libpurple.


It is only one link away on the site I linked to.

---

