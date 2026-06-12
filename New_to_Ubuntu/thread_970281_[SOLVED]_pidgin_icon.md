---
title: "[SOLVED] pidgin icon"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by sazan on 2008-11-04
i hav pidgin installed in my system .. but to run it i hav to run it via terminal.. 

i know it is possible to create an icon for it and run it similar to firefox by simply clicking on it. but i dont knw how to do it.. did search for the same.. no success yet.. 

can anyone tel me d process how i can create d icon.. ??

---

### Post by Elfy on 2008-11-04
Is it not in the menu - if that's the case you can run alacarte to edit the menu.

If it is in the menu - you can right click it and add to either panel or desktop.

If that's not what you are trying to do I apologise

---

### Post by sazan on 2008-11-04
> **forestpixie said:**
> Is it not in the menu - if that's the case you can run alacarte to edit the menu.

If it is in the menu - you can right click it and add to either panel or desktop.

If that's not what you are trying to do I apologise

very thanks for ur response.. really appreciate it.. but i cant find pidgin in d menu.. act there r 2 things i want to achieve via this .. one to get this pidgin icon created and second to learn how it is done.. (if any scripting like bash is used then how it is used)..:p:p:KS

---

### Post by dustman on 2008-11-04
If you're using GNOME, you can right click the "Applications" menu in the upper left corner of the screen, then "Edit Menu". You'll get a window that contains all the submenus from the "Applications" menu, and with all the available applications. You can tick or untick any of those applications, and it won't appear next time you open the "Applications" menu (you will still have it installed though). I think Pidgin is in the "Internet" submenu.


Cheers!

Radu

P.S. If you want to create a script that'll run Pidgin, just decide where to put it, and how to name it (usually somewhere in your home folder), then open a console, and type:
```
nano SCRIPT_NAME
```
then just write in that file: ```
pidgin
```
To exit and save, press Ctrl+X -> press Y -> input the name of the file you want to save to OR just press enter (the name will be SCRIPT_NAME).
You'll have to change the permissions for this file (give it permission to be run):
```
chmod 755 SCRIPT_NAME
```

Then go to your Desktop -> right click -> Create new launcher -> enter the name, description and icon of the launcher, in the "Command" field you can input either just: "pidgin" (without the quotes :D), or you can browse to the location of your SCRIPT_NAME file, and select it. Your launcher will appear on the desktop, when you double click it, Pidgin is going to start.


Hope I wasn't too hard to follow (I don't have access to an Ubuntu machine right now, so I might have missed a step here or there :lolflag:), but I assume I was correct in my indications.

---

### Post by sazan on 2008-11-04
> **dustman said:**
> If you're using GNOME, you can right click the "Applications" menu in the upper left corner of the screen, then "Edit Menu". You'll get a window that contains all the submenus from the "Applications" menu, and with all the available applications. You can tick or untick any of those applications, and it won't appear next time you open the "Applications" menu (you will still have it installed though). I think Pidgin is in the "Internet" submenu.


Cheers!

Radu

P.S. If you want to create a script that'll run Pidgin, just decide where to put it, and how to name it (usually somewhere in your home folder), then open a console, and type:
```
nano SCRIPT_NAME
```
then just write in that file: ```
pidgin
```
To exit and save, press Ctrl+X -> press Y -> input the name of the file you want to save to OR just press enter (the name will be SCRIPT_NAME).
You'll have to change the permissions for this file (give it permission to be run):
```
chmod 755 SCRIPT_NAME
```

Then go to your Desktop -> right click -> Create new launcher -> enter the name, description and icon of the launcher, in the "Command" field you can input either just: "pidgin" (without the quotes :D), or you can browse to the location of your SCRIPT_NAME file, and select it. Your launcher will appear on the desktop, when you double click it, Pidgin is going to start.


Hope I wasn't too hard to follow (I don't have access to an Ubuntu machine right now, so I might have missed a step here or there :lolflag:), but I assume I was correct in my indications.



it worked fine with me.. .
thanks a lot..!!! :guitar:

---

### Post by dustman on 2008-11-04
Glad to hear that! 

Please mark the thread as solved :D.

Cheers!

Radu

---

