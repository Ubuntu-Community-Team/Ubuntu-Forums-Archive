---
title: "[SOLVED] Removing un-wanted programs in wine"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-09-16
I tried to load DVD X Copy program to use in a Wine environment without
success & now would like to remove it. (I was hoping it might do the job where I couldn't with K9 copy). I tried to find it in System/Admin/Syn-Pkg-Mgr... Nothing there. Tried Add/Remove without any luck either... Tried moving files to 'Trash' & it still shows up in my Wine directory. Does anyone know how I can get rid of these files ?

---

### Post by alanmilne on 2008-09-16
Does it show up when you try Applications>Wine>Browse C:\Drive?

It may be in the Program Files folder, from where you can simply move it to deleted items.

---

### Post by howefield on 2008-09-16
a little further than the above post, if you go to applications > wine > uninstall wine software, that should bring up a window listing your installed programs and allow you to uninstall as required.

---

### Post by CoCoKnots on 2008-09-16
That's where I found the files & moved them to 'Trash'... They still show up as existing files when I goto App/Wine/Programs ???

---

### Post by alanmilne on 2008-09-16
Then go to System>Preferences>Main Menu, scroll down to Wine, right-click on the menu item you want to remove, and select delete. That should fix it.

---

### Post by CoCoKnots on 2008-09-16
The files are located in the Wine/Programs folder... When I tried the System/Pref/Main Menu/Wine... I couldn't get into see individual program files to trash.

---

### Post by alanmilne on 2008-09-16
Are you still trying to delete the files, or are you trying to remove the reference to them in the Wine menu? I have had this problem before when an application has been removed but the Menu is still there.

If you go to Applications>Wine>Browse C:\ Drive this will tell you if the files are still there, or not.

To simply remove the menu item go to System>Preferences>Main Menu and then click on the arrowhead beside Wine. This will open the Programs menu underneath it, from where you can right click on the menu item to delete it.

---

### Post by CoCoKnots on 2008-09-16
It allows me to 'Un-Check' to hide the file... But I am not able to delete them.

---

### Post by alanmilne on 2008-09-16
Instead of un-checking the file, try selecting it with your mouse and then clicking the right -hand button. This will open a sub-menu with delete as an option.

---

### Post by CoCoKnots on 2008-09-16
Tried that Alan... For what ever reason when I right clicl & choose the delete option... It doesn't do anything. The file remains.

---

### Post by alanmilne on 2008-09-16
Sorry about the delay, just had a call from my father.

I am still slightly confused about what is going on. When you say the files are still there, do you mean the menu item or the files on disk?

---

### Post by CoCoKnots on 2008-09-16
Would it be possible to get rid of the files with a Terminal command ?

---

### Post by CoCoKnots on 2008-09-16
When I go to System/Pref/Main Menu/Wine/Programs... They still show up there in light italics... I do not see them any where else. I assume they are not active at this point. I would feel better if I could just get rid of them.

---

### Post by alanmilne on 2008-09-16
I think we might be getting somewhere. If they are in light italics then they are hidden. Check the box to the left to unhide them, and then see if you can delete the menu item as before (with the right-click).

---

### Post by CoCoKnots on 2008-09-16
'Bingo' That was it. Thank you very much... Now I will be able to sleep tonight.

---

