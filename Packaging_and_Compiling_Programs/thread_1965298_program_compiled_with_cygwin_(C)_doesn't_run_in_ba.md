---
title: "program compiled with cygwin (C) doesn't run in background"
date: 2012-04-25
forum: Packaging and Compiling Programs
---

### Post by z3nhakr on 2012-04-25
I'm working on cross-compiling a program for windows using cygwin that I wrote for Ubuntu in C. basically what the program does is monitor the systems status (fans, temp, etc.) and report possible security threats such as arp poisoning or multiple remote login attempts. So far I have been able to successively run it under windows but a blank terminal window stays open while it runs which is quite annoying when I'm using windows. Does anyone know how to run a cygwin compiled program in the background? btw it does run in the background on Ubuntu although it has the same problem under wine that it does under windows.

---

### Post by andrewc6l on 2012-04-25
Cygwin lets you build MS Windows apps - here's a link explaining how:

[http://www.cygwin.com/cygwin-ug-net/programming.html#gcc-gui](http://www.cygwin.com/cygwin-ug-net/programming.html#gcc-gui)

It might be easier just to create a shortcut to your app. Then in Explorer, right-click on the shortcut and say "Properties". You can then select Run: "Minimized" to have the window minimized when the app starts. You'll still see it in the task bar, but it won't open in your face.

---

### Post by z3nhakr on 2012-04-26
that might work but it will require an extra file which will make it harder to install on my network. is there any way to modify cygwin1.dll so that it runs backgrounded?

---

