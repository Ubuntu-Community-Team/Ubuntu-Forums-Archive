---
title: "absolute newbie question"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by rfbeck on 2008-04-30
So, after I download and install and application using Synaptic Package Manager, how do I find it and run it? For instance I just installed "Celestia" the astronomy program. What do I do now?
______
Robert

---

### Post by newb1e on 2008-04-30
it's probably under Applications/Education

---

### Post by jorik42 on 2008-05-01
you can also try (via the command line)

"slocate celestia" (or a similar filename) and see what comes up.  

using the "apropos" command will search for a keyword; that might be useful as well.

---

### Post by piousp on 2008-05-01
Search in the menu, it should be somewhere in there.

Also, you can try to run 'celestia' con a terminal.

---

### Post by iSplicer on 2008-05-01
Don't worry, no question is too nooby here.

Again, the launcher should be in the applications menu, or you could hit alt+f2 and type celestia.

good luck!

---

### Post by daimaru on 2008-05-01
if it does not show up anywere in your "application menu" open a terminal and type in 
```
whereis celestia
``` if you find your program that way (it will probably be in /usr/bin) you can right click on your application menu -> select edit -> choose a category and then inside it create a new menu item. for the command to execute insert "/usr/bin/celestia" or whatever the path to your program was (it probably would also work to just type in celestia since its in your user path) click ok and you have your program in the menu.

---

### Post by freesitebuilder on 2008-05-01
I didn't realise until someone here told me, but if you right-click on an installed program in Synaptic, and choose properties it lists the paths to all the relevant files.

System > Preferences > Main Menu also lets you add programs that haven't added a launcher to the menu.

---

### Post by rfbeck on 2008-05-01
> **newb1e said:**
> it's probably under Applications/Education
That's where it was! Thanks guys.
______
Robert

---

