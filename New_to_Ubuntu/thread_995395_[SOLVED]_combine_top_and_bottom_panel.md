---
title: "[SOLVED] combine top and bottom panel?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by gordon55y on 2008-11-27
Hi,
  I just installed Ubuntu 8.10.
I have the default, one panel on the top and one on the bottom.
I would like to put all the items onto one panel.
Is it possible to put all the items in one panel?


I see that I can move and autohide, but only helps somewhat.

---

### Post by Shwefty on 2008-11-27
Absolutely!  Mine is combined too.  The bottom taskbar, when clicked on, has an option to "delete this panel".  So, right click and "Add to Panel" on the top panel the items you want/need from the bottom bar.  Then, when done, right click on the bottom panel, then "Delete this Panel".  You can always right click on the top panel and select "New Panel" if you want it back.

---

### Post by drs305 on 2008-11-27
If you are going to start playing with your panels, here are a couple of commands that may come in handy:
The first one saves the panel data to a Desktop file, the second restores it.
```

*Save:*
gconftool-2 --dump /apps/panel >$HOME/Desktop/panel.save 
*Restore:*
gconftool-2 --load $HOME/Desktop/panel.save 

```

---

### Post by gordon55y on 2008-11-27
Thanks for the info.
I cannot find one item in the "Add to Panel".
That is the bottom panel has a list of running programs.
How can I add that to the top panel?

---

### Post by Keen101 on 2008-11-27
> **gordon55y said:**
> 
That is the bottom panel has a list of running programs.
How can I add that to the top panel?

It should be called "**Window List**"

and yeah, you could either unlock everything, and move them from one panel to the other, or just delete one panel and add the things you want back.

---

### Post by kansasnoob on 2008-11-27
I do mine one applet at a time, building the top panel the way I want it, then deleting the lower panel, and moving the upper panel to the bottom:

[ATTACH]94430[/ATTACH]

---

### Post by gordon55y on 2008-11-27
Ok, got it, one panel.
I am now an expert on panels.
I notice that I can move an item using the middle mouse
button (scroll wheel).

---

### Post by gordon55y on 2008-11-27
Oh, I just discovered drawers.
But when I put something in the drawer, the contents
of the drawer are written sideways.
How can I rotate them 90 degrees?

---

### Post by Shwefty on 2008-12-04
A good question which I don't know the answer too... durn. #-o

---

