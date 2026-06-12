---
title: "How do make software run at startup?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ianb72 on 2008-06-06
I have just installed and got working my RT2500 wireless card with rutilt but how do I go about getting rutilt to run at startup of Ubuntu??

Cheers
Ian

---

### Post by quelx on 2008-06-06
Add the script you want started to **/etc/rc.local**

---

### Post by Phonan on 2008-06-06
If you just want to run RutilT at the startup, go to System-> Preferences-> Sessions. It'll open right to the "Startup Items" tab. Click Add, and some information fields will pop up. "Name" can be whatever you want, likely RutilT. "Command" is whatever you type in a terminal to start your program of choice. I believe RutilT is just "rutilt" Finally, Description can be whatever you want as well, like "RutilT network setup." There you go. Good luck setting this up!

---

