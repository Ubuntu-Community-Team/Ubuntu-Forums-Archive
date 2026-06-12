---
title: "Login Screen System Beep"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by icyest on 2008-11-28
At the login screen when it asks you to type in your name and password, the system beeps when you hit backspace at a blank text box.

e.g. When I have incorrectly typed in a login name, I tend to hold down the backspace key. When all the letters are erased, my finger is still on the key. It makes an annoying system beep. How to I turn off the system beep? Windows doesn't have it. Macs don't have it.

---

### Post by Bölvaður on 2008-11-28
System &#8594; Preferences &#8594; Sound  (*added* or type "gnome-sound-properties" from Alt+F2 or terminal)

Chose the "Sounds" tab and disable alert sounds... or just everything.

---

### Post by crazyness003 on 2008-11-28
Well, a little bit more info would be nice. 
**In Hardy**: There should be an option in System &#8594; Preferences &#8594; Sound called "System Beep". Just untick it.

**In Interpid**: The old way was dropped (a bug? possibly). You have to either: edit gconf, blacklist the device or disable all alert sounds
i'll try to get a workaraound. but it requires doing some manual editing.

[COLOR=Red]EDIT:[/COLOR] Check this out [http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)

---

