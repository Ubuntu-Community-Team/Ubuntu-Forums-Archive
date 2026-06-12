---
title: "HOWTO: Add OpenOffice.org draw to the menu"
date: 2006-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by steve.horsley on 2006-06-07
For some reason, OpenOffice draw is not in the menu for Dapper. To add it, edit the file **/usr/share/applications/ooo-draw.desktop** and find a line near the bottom that says > NoDisplay=true and change it to > NoDisplay=falseThis will make openoffice draw appear in the menu under Graphics (along with GIMP etc). 

If you prefer it to appear in the Office menu along with the other OpenOffice applications, edit the same file and find a line near the top that says:> Categories=Graphics;VectorGraphicsdisable this line by putting a hash in front like this:> #Categories=Graphics;VectorGraphics and add a new line beneath it like this:> Categories=Application;Office;Drawing

---

### Post by CronoDekar on 2006-06-07
Hu, I didn't even notice that it wasn't there.  Thanks for the tip!

---

### Post by Ferio on 2006-06-08
Or you can use Alacarte and uncheck its checkbox. It's an easier way if you'd rather use a GUI.

---

### Post by Geekboy on 2006-06-12
Thanks, that worked fine.

What is alacarte?

---

### Post by Chrissss on 2006-06-12
[QUOTE=Geekboy]What is alacarte?[/QUOTE]
The Gnome Menu Editor

[http://www.realistanew.com/projects/alacarte/](http://www.realistanew.com/projects/alacarte/)

CU
 Christoph

---

