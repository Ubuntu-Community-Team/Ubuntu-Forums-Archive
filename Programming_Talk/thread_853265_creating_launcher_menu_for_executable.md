---
title: "creating launcher menu for executable"
date: 2008-07-08
forum: Programming Talk
---

### Post by KB1LQC on 2008-07-08
I created a program in C that runs a script and a glade GUI.

I want to make a menu launcher (I used the menu editor in preferences) but that didnt work.  The program does not launch when selected in the menu.  However it works fine if I open it in the folder that it is located in.



thanks in advance!

---

### Post by nanotube on 2008-07-08
> **KB1LQC said:**
> I created a program in C that runs a script and a glade GUI.

I want to make a menu launcher (I used the menu editor in preferences) but that didnt work.  The program does not launch when selected in the menu.  However it works fine if I open it in the folder that it is located in.



thanks in advance!

did you specify the full path to the program in your launcher?

---

### Post by soxs on 2008-07-08
try to create a /usr/bin script which includes in /usr/bin

```
#!/bin/bash
cd /dir
./program
```
```
chmod +x /usr/bin/yourprogramstarter
```

use that now to run it via the launcher menu, this should always work, at least it did it for me and gives you the possibility to run it from any console at any location

---

### Post by KB1LQC on 2008-07-09
Thank you!

---

### Post by gargy69 on 2008-07-09
I second that Thank You!  That was EXACTLY what I needed, SOXS.  Soxs roxs :guitar:

---

