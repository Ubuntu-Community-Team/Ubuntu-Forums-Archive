---
title: "where are my panels"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by zhanglini on 2008-05-01
Help!
I must have over tweaked my Hardy!
This morning when I boot it up, the desktop is empty, no more panels.  Rebooted several times, samething!
Questions:
1. How do I get to the command console with shortcut keys?---not that I know what to do with it.
2. How do I restore my panels?
Thanks a lot!

---

### Post by horry on 2008-05-01
> **zhanglini said:**
> Help!
I must have over tweaked my Hardy!
This morning when I boot it up, the desktop is empty, no more panels.  Rebooted several times, samething!
Questions:
1. How do I get to the command console with shortcut keys?---not that I know what to do with it.
2. How do I restore my panels?
Thanks a lot!

Hi, I hope this can help you.
Alt+F2, and then input 'gnome-panel'.
Good luck.

---

### Post by mrdosa on 2008-05-01
TYPE THE FOLLOWING IN BASH!

Code:
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

will restore the default setting!!

---

### Post by zhanglini on 2008-05-01
Hi guys,
I will try both when I get home.
I am a noob, can you explain that bash thing?  I need more like a step-by-step instruction.  Thanks a lot in advance!

---

### Post by mrdosa on 2008-05-01
Well, I am learning too. But bash I guess is a really powerful version of DOS!! And as you have lost both the panels, which I did once, then type the command above. Which will restore your default settings!
I guess, someone will answer you better.
Alt+F2 will give you a small box, you type gnome-terminal in it and enter.
This will open up bash, where you can do the above!

---

### Post by seshomaru samma on 2008-05-01
bash=terminal
go to Applications>accessories>terminal
copy paste this into the terminal
```
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &
```
press enter

---

### Post by zhanglini on 2008-05-01
> **seshomaru samma said:**
> bash=terminal
go to Applications>accessories>terminal


Well, I don't have panels, so I can't go to >Apps>....
I hope ALT+F2 can trigger the terminal.  This morning I have tried all kinds of combination (probably including ALT+F2) and nothing worked.  Is AlT+F2 Ubuntu-defined?
Thanks

---

### Post by zhanglini on 2008-05-02
Ok guys, I used Alt+F2, enter the commands you suggested, and it did not work --- I am sure there is something I did wrong, the devil is in the detail!
Being an impatient person, I decided to reinstall, I have a separate /home, so it might actually save time....
Thank you guys for all the help!

Please close the thread.

---

