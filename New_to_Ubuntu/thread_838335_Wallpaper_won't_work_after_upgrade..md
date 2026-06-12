---
title: "Wallpaper won't work after upgrade."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by osc1882 on 2008-06-23
Hi, I don't know if I need to file this under bugs or what. I just did a upgrade (06-23-08), it required a reboot and I came back and my wallpaper was gone. No big deal I thought to myself, I will just reset the paper. So I found my wallpaper again, told it to set, hit close and the window goes away but the wallpaper is not set. It will not let me set a wallpaper after the upgrade. 

If anyone has any ideas let me know. And maybe, just maybe, I won't be the only one with this problem and tomorrow's upgrade will fix it.

---

### Post by osc1882 on 2008-06-23
Oh, and my Applications bar and the running programs bar (top and bottom bar) is no longer transparent like I had it set.

---

### Post by aashay on 2008-06-23
Do the folders on the desktop still show normally? Do you get a right-click menu for the desktop?
Also, assuming you are running compiz, you can set the wallpaper using the cube or (in newer builds) wallpaper plugin.

---

### Post by osc1882 on 2008-06-23
No, no icons, can't right click. I don't know if I have a new version of Compiz or not, but I went into the settings and alot of my settings have been changed. So it might have upgraded Compiz.

---

### Post by aashay on 2008-06-24
Heres the solution: 
Nautilus is currently not handling the desktop. To make it do so...
1) run gconf-editor
2) Navigate to apps->nautilus->preferences
3) Enable (tick) show_desktop key
Hope it works
You might have to logout and login for it to take effect

---

### Post by osc1882 on 2008-07-09
Just so everyone knows. It magically worked after I restarted the computer. I'm not sure what the hang up was.

---

### Post by kekegg on 2010-09-30
I disabled the show desktop option, then start, now it works.

---

