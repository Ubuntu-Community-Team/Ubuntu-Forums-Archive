---
title: "Python user Desktop switching program"
date: 2007-09-14
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2007-09-14
Hi, I want to make program for tomorrow , for the software freedom day, I need to make a program that will log out from Gnome, and log in KDE, for demonstration of Ubuntu.
Does any one know how can I?

P.S> Python program.

---

### Post by bobbocanfly on 2007-09-14
All you would need to do is close the current X sessions, start KDE. Could probably be done very easily with a BASH script but no idea how to do it in Python.

---

### Post by DamjanDimitrioski on 2007-09-14
Hey, if don't know how can it be done in Python.
Please tell me then how can that be done is BASH, or maybe in sh or c,c++, mono or what ever solution you have.

---

### Post by scooper on 2007-09-14
If you don't need to log out and in again you can use chvt, e.g. "chvt 9" to go to virtual tty #9.  If you run X in display #1 it will appear in a different vt.  When I run "startx -- :1" I get a new default xsession in vt #9.  My normal X session (display 0) is in vt #7.

So you have to set up 2 X sessions ahead of time and then programmatically switch back and forth (as root) using "sudo chvt 7" and "sudo chvt 9".  You get the idea.  You'd have to figure out the best way to run the other DE in display #1.  You could make another user that defaults to KDE and pre-start the KDE session from its login.  Obviously you can also just use Ctrl-Alt-F7 and Ctrl-Alt-F9 to switch manually.

Hope this helps.

---

