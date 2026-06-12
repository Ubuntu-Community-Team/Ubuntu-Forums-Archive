---
title: "How to modify default right click context menu in ubuntu 14.04..."
date: 2015-03-25
forum: New to Ubuntu
---

### Post by shubhamjindal-1994 on 2015-03-25
I wanted to add 2-3 more options apart from conventional copy and paste in the right click context menu pop up...Where can I find the related xml files and system scripts...

---

### Post by Vladlenin5000 on 2015-03-25
There's not *A right-click context menu* but several, depending on the... Context (desktop, within a program, etc.).
Here some suggestions regarding Nautilus (Files in newer releases): [http://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/](http://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/)

---

### Post by shubhamjindal-1994 on 2015-03-26
Thanx Vladlenin,
Even for Nautilus, how can I change the menu without using nautilus-action tools...but by using scripts of my own...Or at least tell how does the nautilus-action work?

---

### Post by mc4man on 2015-03-27
> **shubhamjindal-1994 said:**
> Thanx Vladlenin,
Even for Nautilus, how can I change the menu without using nautilus-action tools...but by using scripts of my own...Or at least tell how does the nautilus-action work?
To add directly to the context menu(s) requires either modifying the nautilus source code  or creating a nautilus extension, both well beyond the scope of your question

To use your own scripts then you could also look at installing nautilus-scripts-manager, scripts go into ~/.local/share/nautilus/scripts & are available in the context menu > Scripts > 
The advantage of nautilus-actions is actions can be set to appear only on specific target mimetypes and or file extensions. N-a ca also run personal scripts as the command used.

---

### Post by shubhamjindal-1994 on 2015-03-27
Thanx Sir,
Though I am good with programming and shell scripting...I will work upon your suggestion and avoid changing nautilus source code! THanx a lot. That will be all for now! :D

---

