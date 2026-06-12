---
title: "[SOLVED] change icon by the applications menu and add dock"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by macvswindows on 2008-11-03
I am very new to linux and ubuntu. So far I am enjoying it. I got a couple of questions.

1) How do I change the icon by the applications menu as it is shown in the picture?

2) How to add a dock like you see in mac os x?

Thank you for your help.

---

### Post by Sand Lee on 2008-11-04
To change that icon press Alt+F2 then run gconf-editor. Navigate to /apps/panel/objects/menu_bar_screen0. Then check off use_custom_icon, and then enter the path to that icon in custom_icon.

To install a dock, search for "dock" in Add/Remove. You'll find a greater variety in synaptic.

---

### Post by Paqman on 2008-11-04
The most popular docks are Avant Window Navigator and Cairo Dock.

---

### Post by macvswindows on 2008-11-04
> **Sand Lee said:**
> then enter the path to that icon in custom_icon

How would I do that? Do you use Edit Key when you right click it??

Thank you for your help.

---

### Post by Sand Lee on 2008-11-05
You have to double-click the blank field to the right of the option.

---

### Post by macvswindows on 2008-11-05
I figured it out now. When you double-click the blank field on the right side, you will type in the directory of your icon. It does not matter how big the icon is, it will shrink it for you to whatever the pixel setting you have for your panel.

---

### Post by jeddycakes on 2008-11-06
do you have to restart for it to take effect?

---

### Post by macvswindows on 2008-11-06
If you used main menu from the "add to panel" option it will work, so far I can only get the icon to change if you chose **main menu** instead of **menu bar**.  Since I can not figure out how to change the icon with **menu bar** yet. Once you double-click the blank field on the right side and add the directory of your new icon, it should automatically change the icon from default to your choice without restarting. Which mean it should take effect after you enter the directory.

---

### Post by Toshibawarrior on 2008-11-09
Apparently the Menu Bar icon doesn't want to change with gconf-editor...I've tried it for a while and nothing works. In the other hand I tried it with Main Menu and it worked instantly...I really don't know what's going on here. if anyone has any info about this let me know. The weirdest thing is that the stupid icon (in the menu bar) changes with some icon themes...but doesn't change manually......:(:confused:

---

### Post by macvswindows on 2008-11-10
I have the same problem as you, the icon would not change manually with Menu Bar but it will change manually with Main Menu.  This is weird, but I like the Main Menu better anyhow.

---

### Post by macvswindows on 2008-11-11
How do I make the vista start menu icon a full rounded shape and have little bit of the icon to stick out of the panel. Right now I have the vista start menu icon but only the top portion of the icon is cut off to line up with my panel. Here is the pictures to show what I have right now. 
**Attachment 1** is the panel I have right now, and you can see the top portion of the start menu icon is cut off. **Attachment 2** is the picture I want my panel to look. Have the top portion to stick out of the panel. Let me know how to do it?? Thanks

---

