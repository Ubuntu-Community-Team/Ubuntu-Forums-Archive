---
title: "Gnome-scheduler commands"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by palloy on 2011-11-08
All I want to do is run LibreOfficeCalc on my spreadsheet every day at 9am.

I have installed Gnome-sheduler and can understand everything except the command and the output.
From the terminal this works:
~$ libreoffice --calc /media/truecrypt1/.../rainfall.2011.xls

but it doesn't work in the g-s command box - nothing happens at the appropriate time.
The help says running a GUI app needs DISPLAY=:0.0 first
so I wrote a script ~/runrainfall 

   DISPLAY=:0.0
   libreoffice --calc /media/truecrypt1/.../rainfall.2011.xls

made it executable, and put "~/runrainfall" in the command box - nothing happens.
Using just "runrainfall" - nothing happens.

The thing under the command box is set to Default Behaviour, but I have tried all possibilities and nothing happens.

Any help gratefully accepted.

---

