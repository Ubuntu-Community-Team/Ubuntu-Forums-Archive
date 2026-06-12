---
title: "HOWTO: Put a fully transparent shell on your desktop (requires Compiz-Fusion)"
date: 2007-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by phaedOne on 2007-08-26
I will show how to create a conky'esque transparent shell using only gnome-terminal and Compiz-fusion.  Check out the attached screenshots.

[SIZE="3"]**Part 1:**[/SIZE]

Create a new profile in gnome-terminal (Edit->Profiles->New), name it "*trans*".  Set the following characteristics:

Cursor blinks: **off**
Show menubar: **off**
Initial title: **trans**
Dynamically-set title:** Isn't displayed**
Color scheme: **Black on white**
Transparent Background: **on**
Set the transparency down to** "None"**
Scrollbar: **disabled**

The important part here is that now the gnome-terminal is gonna have the title *trans*.  We can now target the gnome-terminal windows that are using trans profile from inside CompizConfig by using *title=^trans$*  

[list]The ^ at the begining means for the title to match it must start with the word *trans*, The $ at the end means the title must end after trans.  This prevents it from matching other phrases that include "trans" for example "The *trans*formers"   (See:[Regular Expressions]("http://www.grymoire.com/Unix/Regular.html")).  You can match windows by other things than their title  (See: [[How To] Use opacity values and Window Rules]("http://forum.compiz-fusion.org/showthread.php?t=1768")).[/list]

[SIZE="3"]**Part 2:**[/SIZE]

Have an instance of gnome-terminal open with the trans profile so you can see whats happening to it as you follow the rest of the howto.  Open CompizConfig (System->Preferences->CompizConfig).  

Make sure you have the **regEx** plugin enabled.  

Go to the **Window Decoration** plugin and add *any & !title=^trans$* to the* Decoration windows* field.  This will skip adding window borders to our trans terminals.

Go to the **Window Rules** plugin.  Add *title=^trans$* to the following fields (This will turn the terminals into a widget-like windows,  *Sticky* will put them on all sides of the cube):
[list]Skip taskbar, Skip pager, Below, Sticky, Non resizable windows, Non minimizable windows, Non maximizable windows, Non closable windows[/list]
In the * Fixed Size Window*s section click add.  Use *title=^trans$* for the the *Sized Window* field and put the height and width you want for your shells.

Go to the **Place Windows** plugin, go to the *Windows with fixed positions* tab, in *Windows with fixed positions* click add.  Put *title=^trans$* in *Positioned Windows* field and put x and y coordinates of the default position you want for your shell (top-left corner is 0,0).  After they have loaded you can move them by Alt-Dragging them.   

To run the transparent gnome-terminal use:
```

gnome-terminal --window-with-profile=trans

```
Edit:
The guide will put the same shell repeated on all sides of the cube.  You could put a different shell on each side of the cube. To do this create a profile following the fist part of the instructions above but change the title to *trans1*.   Now make three new profiles using this first profile as its base.  Change the titles of these profiles to:  *trans2*, *trans3*, *trans4*.   Now follow the second part of the instructions above using *title=^trans[1-4]$* instead of *title=^trans$* to match the windows.  Now you want to set each one to appear on a  fixed side of the cube.  Go to the **Place Windows** plugin, go to the *Windows with fixed positions* tab, in *Windows with fixed viewports*.  Here add each of your four windows ( *title=^trans1$*, *title=^trans2$*, ...)  along with the viewport you want them to be in.

[SIZE="1"]
dock: avant-window-navigator
widgets: conky /  [theme]("http://ubuntuforums.org/showpost.php?p=3197911&postcount=505")


[/SIZE]

---

### Post by frodon on 2007-08-26
Nice guide thanks :).

For the record the same thing can be done without compiz using devilspie :
[http://ubuntuforums.org/showthread.php?t=202249](http://ubuntuforums.org/showthread.php?t=202249)

---

### Post by Yes on 2007-08-27
Great guide!  

I do have one question, though:  I can't seem to get my terminal to be the proper size, or to be in the proper location.  Any idea why this could be?  

Thanks.

---

### Post by phaedOne on 2007-08-28
> **Yes said:**
> Great guide!  

I do have one question, though:  I can't seem to get my terminal to be the proper size, or to be in the proper location.  Any idea why this could be?  

Thanks.

To make it resize and position corerctly try loading the terminals in a script before compiz loads i.e:

```

#!/bin/sh
gnome-terminal --window-with-profile=trans1 &
gnome-terminal --window-with-profile=trans2 &
gnome-terminal --window-with-profile=trans3 &
gnome-terminal --window-with-profile=trans4 &

sleep 3
compiz --replace &

```

---

### Post by Yes on 2007-08-30
Alright, I got it in the right position, but for some reason on certain webpages it treats it like the trans terminal - that is, it takes away the window decoration, and makes it unmovable and un-resizeable.  Any idea why that would be?

Thanks.

---

### Post by phaedOne on 2007-08-30
> **Yes said:**
> Alright, I got it in the right position, but for some reason on certain webpages it treats it like the trans terminal - that is, it takes away the window decoration, and makes it unmovable and un-resizeable.  Any idea why that would be?

Thanks.

Make sure in the Window Decorations plugin you have !title=^trans$ .... note the "!"

---

### Post by Yes on 2007-08-31
Great, it works now.  Thanks!

---

### Post by phaedOne on 2007-09-01
> **Yes said:**
> Great, it works now.  Thanks!

to be safe use 

```

any & !title=^trans$

```

---

### Post by derekr44 on 2007-09-07
Is this possible with Beryl?

---

### Post by Anpheus on 2007-09-07
Is there a way to put this below the icons, or enable Super+Left/Right to switch desktops (I have it set to rotate the cube left or right when no window is selected) when clicking on it?

---

### Post by Tantor on 2009-01-09
If you want to prevent the Show Desktop button from minimizing your transparent terminal, you may start gconf-editor and uncheck this value:

/apps/compiz/general/allscreens/options/hide_skip_taskbar_windows.

By the way, does anyone know how to start a gnome-terminal in a specific workplace? I want my terminal to be automatically launched in Desk 2 at startup, but I haven't found a way to do it.

---

### Post by coca12 on 2009-01-09
Great guide...Thanks!

---

