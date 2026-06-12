---
title: "[SOLVED] Alt+F4 equivalent?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Sydius on 2008-07-10
I did something stupid and made a full-screen application with no way of exiting it (it only exits when you click the "X", which was no longer there upon it becoming full-screen).  I rebooted the computer, changed the code, and fixed the problem.

But, it caused me to wonder, is there some series of key presses or something else I can do to terminate an application that is full-screen?

---

### Post by tjwoosta on 2008-07-10
alt-f4 works fine to close windows for me  (same as windows)

if its not working for you just go to preferences-keyboard shortcuts then scroll till you see "close window" (then just give it a key combination to use)

---

### Post by Sydius on 2008-07-10
Oh, it's there.  I wonder why my program didn't close... I assume because it was pulling all the key presses and so they never got to Ubuntu?  Is there a way of dealing with programs like this?

---

### Post by roquefilipe on 2008-07-10
well, one solution could be to change to another console ctrl+alt+f1 and send a signal to terminate or kill to that process.

---

### Post by Sydius on 2008-07-10
> **roquefilipe said:**
> well, one solution could be to change to another console ctrl+alt+f1 and send a signal to terminate or kill to that process.

Thanks, I'll try that. :-)

---

### Post by sayakb on 2008-07-10
Ctrl+Q / Ctrl+W also closes/hides windows.

---

### Post by Yuki_Nagato on 2008-07-10
Potentially "Crt + Alt + D" to show the desktop.

---

### Post by nhandler on 2008-07-10
Another option is to to hit 'Alt+F2'. This launches the "Run Application" window. If you are unable to see the window, try hitting 'Alt+Tab' to switch to it. You can then type 'xkill' in the "Run Application" window. This will turn your curson into an X. Now, simply click on the application you want to quit to kill it. Be sure to save all of your work in the application before killing it with xkill.

Also, F11 is a common keyboard shortcut to make an application become fullscreen. You can usually hit F11 a second time to return the application to normal.

---

