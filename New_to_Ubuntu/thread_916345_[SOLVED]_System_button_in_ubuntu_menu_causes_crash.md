---
title: "[SOLVED] System button in ubuntu menu causes crash"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by paulley_trolley on 2008-09-10
Applications works, places works, just system completely crashes it so hard that sometimes ctr alt backspace doesn't even fix it.  I'm talking about the ubuntu menu in the gnome panel.  I tried on both the one that's just the logo and the one that actually says applications, places and system, and everytime i go to system, it just crashes.  Nothing works except mouse, and sometimes ctr alt backspace doesn't even work. what should i do?  I should add that this started after i edited the usr/icons/share/scalable file to change the ubuntu thing to the apple icon, which didn't work by the way, but in the gnome panel properties, the ubuntu main menu comes up as an apple when you go to add to panel option, but in the actual bar, it still comes up as a ubuntu logo.

---

### Post by Crafty Kisses on 2008-09-10
Have you checked your X logs?

---

### Post by paulley_trolley on 2008-09-10
I don't know what that is

---

### Post by Shazaam on 2008-09-10
You can find it here...
```
/var/log/Xorg0.log
```
Look for lines that have EE or WW at the start.

---

### Post by paulley_trolley on 2008-09-10
Im good, i just reinstalled ubuntu thanks for the help.

---

