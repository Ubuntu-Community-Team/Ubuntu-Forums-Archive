---
title: "Change icon in launcher"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by Zvanochek on 2011-12-25
Interesting question this: can I change the icon that displays in the launcher bar in Ubuntu 11.10?

I was messing around earlier, and created my own launcher for MS Word on the desktop, complete with the MS Word icon (Yes I know you can drag and drop from the dashboard, but it was an exercise in using the terminal as I'm still new). When I tried to drag it from the desktop to the launcher, my nice shiny Word icon was changed to a spring icon, although the program still launched when clicked.

So my question is, should I ever feel the need to, can I change the icon that displays in the launcher bar?

I'm running Ubuntu 11.10 if that makes a difference.

---

### Post by mc4man on 2011-12-25
The icons shown on the launcher favorites items are determined by what is on the Icon= line in the 'whatever'.desktop that is associated to that launcher item.

So to change you open the .desktop in a text editor & adjust the Icon= line.

In some cases you'll need to full path to the icon's location to get it to display.
Why your desktop launcher (which is a .desktop file) didn't show the correct icon can't say, open a gedit window, then drag & drop the desktop launcher into to see how the .desktop is constructed - post if desired

(at times wine apps run from the launcher need some adjustment to get right & have the launcher icon open & control the program

---

### Post by Zvanochek on 2011-12-25
Ah, I thought it must be simple. Thanks for the reply.

---

