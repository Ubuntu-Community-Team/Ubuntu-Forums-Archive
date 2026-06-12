---
title: "[SOLVED] messed up my ubuntu theme"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Norfeldt on 2008-11-19
Hello everyone

I was playing with some themes about MAC look (which I will never do again until next time;)) in the appearance window (by dragging in some files) and in Emerald. Until I realized that it looked stupid. Then I tried to change it back again.. But the close, minimize and maximize buttons is still in the wrong place:confused:
And the Ubuntu logo in the upper left corner is replace by a big blue GNOME foot (played with other themes too)..

Anyone know that to do?

---

### Post by SpenceMakesSense on 2008-11-19
if u look in the emerald settings for the theme somewhere in the is the ooption to change to the windows layout for minimize etc. buttons. or you could just disable emerald and use whatever gtk theme was installed. And the gnome symbal instead of the ubuntu is just a gtk theme issue. Just switch back to an original ubuntu theme and it should work.
I figure you've see this site
[www.gnome-look.org](www.gnome-look.org)  ?

---

### Post by Norfeldt on 2008-11-20
I have disable emerald (in the Compiz Fusion Icon) but without any luck. Then I tried to remove it by uninstalling emerald in the synaptic package manager (didn't remove the file libemeraldengine0) and the close button in the windows is still at the wrong place?
more suggestions?

---

### Post by fooman on 2008-11-20
have you tried going to system > preferences > appearance and clicking on a different theme there?

if that does not fix it...then while your in there,  click on the "customize" button > control tab, and choose a different item from that list.

---

### Post by Norfeldt on 2008-11-20
Yes have been trying that for a long time.. but no luck... It's very strange..:(

Maybe I should try to install emerald again and then install another theme with the buttons the right place...

Or do you (or anybody) have another suggestion?

---

### Post by fooman on 2008-11-20
you say emerald is uninstalled?

before you reinstall it try this...open your home folder and in the toolbar, click view.  put a check next to "show hidden files"

find the .emerald file,  right click on it and "move to trash"

restart and see what you have.

then try reinstalling emerald.

---

### Post by m_duck on 2008-11-20
This may not be entirely correct due to not being in Ubuntu/Gnome at the moment but, it's worth a shot :D

If emerald is not selected, it should have reverted back to using metacity. Press alt + F2 and type in the box:
```
gconf-editor
```Then navigate to "Apps -> Metacity -> General". Now, in the right hand pane there should be an entry called "button_layout" with "menu", "minimise" etc in it. If you change those to the order you want it should change the title bars. It might need a restart but that *should* fix it.

EDIT: Just checked in ubuntu intrepid and you can change the button order for metacity that way. No restart required.

---

### Post by Norfeldt on 2008-11-22
> **fooman said:**
> you say emerald is uninstalled?

before you reinstall it try this...open your home folder and in the toolbar, click view.  put a check next to "show hidden files"

find the .emerald file,  right click on it and "move to trash"

restart and see what you have.

then try reinstalling emerald.

Tried it.. but no luck:(

---

### Post by Norfeldt on 2008-11-22
> **m_duck said:**
> This may not be entirely correct due to not being in Ubuntu/Gnome at the moment but, it's worth a shot :D

If emerald is not selected, it should have reverted back to using metacity. Press alt + F2 and type in the box:
```
gconf-editor
```Then navigate to "Apps -> Metacity -> General". Now, in the right hand pane there should be an entry called "button_layout" with "menu", "minimise" etc in it. If you change those to the order you want it should change the title bars. It might need a restart but that *should* fix it.

EDIT: Just checked in ubuntu intrepid and you can change the button order for metacity that way. No restart required.

It worked :)
THANKS!

---

