---
title: "Desktop questions"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2011-10-21
A couple questions. 

Right clicking on the desktop brought up a menu.. I changed it and now I would like it back. When I Right click I have Terminal, web browser, obconf exit.. Things like that.. I checked a box and now it's gone... (I know.. Slap my hands for messing around :) )

Also How to I get more Icons On the desktop? Like home/document folder, recycle bin? Things like that. (That's what I was trying to do when I changed the right click menu. )


Edit.. 
Got my home folder and Trash to the desktop.. Only need the right click back.

---

### Post by Rex Bouwense on 2011-10-21
As to your second problem, all you need to do is right click the item in the drop down menu and you will get the option of making a desk top shortcut.  I am still researching the first.

Sorry, I was too late.  I had to boot into Lubuntu to make sure that what I was going to tell you was correct.  I'm still researching the other.

---

### Post by Rex Bouwense on 2011-10-21
What is the menu you get when you right click now?  I am having trouble replicating your problem or rather your situation.  Also which version of Lubuntu are you using?

---

### Post by dingo on 2011-10-21
For your first question try:

```
pcmanfm --desktop-pref
```

Then check (or uncheck) the box "Show menus provided by window managers when desktop is clicked" found under the "Advanced" tab.

---

### Post by BuzzStPoint on 2011-10-21
Current Lubuntu 11.10

If I recall what I did,

Right click on the Desktop, should pop up a menu. I think I chose the bottom menu item. In the advanced tab ( I think) there was a check box. I checked that. 

Tried to get a screen of the right click but it disappears when I Print screen.
Now it has changed and the right click menu is now:

Terminal Emulator
Web Browser
-----------------
Desktops
-----------------
Obconf
Reconfigure
Restart
-----------------
Exit


Thats it.

---

### Post by BuzzStPoint on 2011-10-21
> **dingo said:**
> For your first question try:

```
pcmanfm --desktop-pref
```

Then check (or uncheck) the box "Show menus provided by window managers when desktop is clicked" found under the "Advanced" tab.


Thats it!!
Thanks a bunch.

---

