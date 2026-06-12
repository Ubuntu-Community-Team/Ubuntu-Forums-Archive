---
title: "Remaking the bottom bar in GNOME?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-15
What exactly would I have to do to create an identical bar/program tray to the one found at the bottom of a default install of Ubuntu? I'm trying out docks, and have become rather increasingly curious to try one full-time instead of it. Yet I want to take the preemptive measure to know how to reverse what I'm doing should results not be satisfactory.

Thanks for your help in advance. :)

---

### Post by Elfy on 2008-09-15
I can't remember quite what is in a default bottom bar - but it is as simple as adding a panel then add what you want to it with right click Add to Panel.

You can restore both the top and bottom panels to default if necessary.

Edit - this is what I was looking for if you do end up with no panles at all - [http://ubuntuforums.org/showpost.php?p=5578191&postcount=10](http://ubuntuforums.org/showpost.php?p=5578191&postcount=10)

There's nothing to stop you having only one panel, it's what I do - takes up less room - I use main menu instead of menu bar it takes up less room.

---

### Post by Grimhound on 2008-09-15
> **forestpixie said:**
> I can't remember quite what is in a default bottom bar - but it is as simple as adding a panel then add what you want to it with right click Add to Panel.

You can restore both the top and bottom panels to default if necessary.

And how would I restore them to default? Is there some terminal command for that, or?

---

### Post by howefield on 2008-09-15
Another possibility to consider is right clicking the panel instead of deleting, and select properties and check the box next to show hide buttons.

This will let you slide the panel to the side whilst you experiment with your dock. Once you're done you can slide the panel back into position. Or of course delete if you want to stick with a dock.

---

### Post by 0004tom on 2008-09-15
Right click the top panel, New Panel, it should go to either side, or bottom, 
then right click the new panel and Add To panel, 
add Window Selecter, Work space switcher, and Deleted Items, not sure about the Show desktop button

---

### Post by akiratheoni on 2008-09-15
Right-click on an existing panel -> Add to Panel.

---

### Post by howefield on 2008-09-15
> **Grimhound said:**
> And how would I restore them to default? Is there some terminal command for that, or?

Right click the top panel and select new panel. 

Right click the new panel and select add to panel, from the list that comes up, choose Show Desktop, Workspace Shifter and Deleted Items.

You can right click each icon and move them into postion.

---

### Post by Elfy on 2008-09-15
> **Grimhound said:**
> And how would I restore them to default? Is there some terminal command for that, or?

I edited my post

---

### Post by TJCIB on 2008-09-15
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Reboot and done.

This will get your panels back to how they were when you did a fresh install of the OS.  So your customizations will be lost.

Another option, instead of deleting the directory, is to just rename/move it...then you would have it backed up.

I know the "rm -rf" command is a bit taboo...you could always do it manually through nautilus.

*edit* Wow, in the time I type my post I am the 8th reply...too slow

---

### Post by Grimhound on 2008-09-15
Thanks guys. You've been quite helpful. :)

---

