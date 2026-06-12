---
title: "Compiz doesn't work?"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by BruceCM on 2012-03-15
It won't shrink my launcher icons! Can't get my unity, either. Did get Cairo, in software centre but can't find it in the Dash. There some code to sort any of that out, please?:o

---

### Post by grahammechanical on 2012-03-15
If you have installed Compiz Configuration Settings Manager (CCSM) and your adjustments are not having any effect then there are 2 possible reasons, in my mind.

1) You are logging into Ubuntu 2D.

2) You have installed some other User Interface.

In either case, CCSM will only work with Ubuntu (Unity 3D).

Have you run additional drivers and have you activated a proprietary video driver that will give the 3D capabilities of your video card?

What version of Ubuntu are you using? What modifications have you tried?

Regards.

---

### Post by ajgreeny on 2012-03-15
If you open a terminal and use command ```
echo $DESKTOP_SESSION
```it will tell you if you are running unity 2D or 3D.

---

### Post by BruceCM on 2012-03-15
Thanks. Run additional drivers but there don't seem to be. It's Ubuntu 11.10 64 bit, with Gnome. Changing that to KDE possible, is it? Ran the code, it just says 'ubuntu' afterwards, is that 2D, then? It used to work, on here, though! (Compiz & My Unity) Before I had to reboot, sadly.

---

### Post by kentfx on 2012-03-23
Compiz is another Ubuntu application written by people for their own computers, who neglected to consider that there is a large range of other machines in common use with major variations in core hardware, configured in innumerably different ways.  The coders fail to understand what it means to cause tens of thousands of hours of people's time in trying to make defective applications work on their machines.

Ubuntu Central really shouldn't post badly conceived or broken code on their public sites.  At the very least, Ubuntu should include a detailed listing of the machine(s) and operating environments that the code was tested on, and warnings that it may well fail in other environments.  Better still, don't recommend applications that haven't been exhaustively tested.

---

