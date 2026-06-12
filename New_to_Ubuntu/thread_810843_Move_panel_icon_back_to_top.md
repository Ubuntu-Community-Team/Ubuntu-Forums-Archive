---
title: "Move panel icon back to top?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by gspaulding on 2008-05-28
I inadvertently moved the network connection icon from the upper panel near the user name on the right to the bottom panel.  There is no option to move it from the bottom panel and I cannot drag it either.  How do I get it back to its original location.  Icons on the top panel have a 'move' option, but now that it is on the bottom, there is no move option.
Thanks in advance.

---

### Post by Dougie187 on 2008-05-28
You could right click on the top panel and go to "Add to panel" Then find the icon you want to add and add it to that panel. Then remove the other icon from the bottom panel using the "Remove from panel". I would think move would work, also check if it is Locked to the bottom panel.

What I mean by the last comment is, what options do you have when you right click on the network connection icon in the bottom panel.

---

### Post by gspaulding on 2008-05-28
Thanks Dougie, but there is no option to remove from panel for this icon, nor an option to unlock the panel.  There is no option to move it.

---

### Post by drs305 on 2008-05-28
I believe it's called Notification Area in the Add Panel choices.

---

### Post by gspaulding on 2008-05-28
Ok, progress and screw-up.  I right-clicked beside the icon (not on the icon) and got the move option.  I moved it back to the top.  Because I had added the notification panel at the top per drs's post, I then tried to delete that, but the entire top panel was removed.  How do I get it back?

---

### Post by drs305 on 2008-05-28
I have good and bad news. Unless you made a backup I am not sure you can restore it to it's original without rebuilding it. However, you can create a new one by right clicking and selecting new panel. The easiest way to restore some of the shortcuts is to drag them from the Systems menu items directly to the panel and let go. It will place them there. Items that aren't already in the menus you can build by right clicking the panel, selelcting Add to Panel, and either selecting an item already displayed or creating a custom launcher.

Here is some other good news, although a delivered a bit too late. You can save most of the panel settings in case you lose them in the future. Some custom shortcuts aren't saved, but most of the panel can be restored.

To save the panel settings, run the following. You can select any path and name you like:
```
gconftool-2 --dump /apps/panel > **~/Desktop/panel_settings**
```

These commands will restore and refresh the panels:
```
gconftool-2 --load **~/Desktop/panel_settings** && killall gnome-panel
```

---

### Post by gspaulding on 2008-05-28
Thanks drs305.  I'll try the suggestion, but may resort to a re-install since I've only been up a couple of days.  All I had accomplished so far was to get my broadcom wireless working.  I will backup the settings this time when I get things put back.

---

