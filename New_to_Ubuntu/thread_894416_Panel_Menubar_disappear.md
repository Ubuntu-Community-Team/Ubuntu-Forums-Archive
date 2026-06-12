---
title: "Panel Menubar disappear"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by zfauzi04 on 2008-08-19
Suddenly, when I booted I couldn't find my panel menubar.Try to left click the mouse and somehow, there is no option to trigger the menubar. Appreciate for help. thanks.

---

### Post by Tux.Ice on 2008-08-19
rightclick on your upper menubar and select add to panel.

from the window that pops up select menu bar from the list and press add.

then right click on the actual menubar and select move, and move it to where you like. lock it there by clicking once (leftclick). done. the other white bar is caled a spacer if you want to add that as well.

---

### Post by zfauzi04 on 2008-08-19
thanks for the assistance however, the problem still remains unresolved. Actually, there isn't any menubar to click for me to add other panel. What I have only are the application icons or shortcuts that I've created.

Need to know how I can get to at least the menubar. thanks.

---

### Post by tarps87 on 2008-08-19
Try running gnome panel in the terminal:
```

gnome-panel
```

---

### Post by manturafs on 2008-08-19
i believe i have a similar problem and I've been searching the forums for days to figure this out and tried everything.  thought I'd finally post.

basically if you go to terminal (ctrl-alt-f1) and type gnome-panel, i get an error message.  doesn't matter if i use sudo or gksudo in front of it either.  If i don't use sudo, it just says:

Cannot Open Display

With gksudo i get a similar message, but it's preceded by GTK-WARNING.

Related to that, I reinstalled ubuntu-desktop, gnome-panel, deleted previous gnome settings (.gnome, .gnome2, .gconf, etc.) Nothing seems to be working!

---

### Post by Tux.Ice on 2008-08-19
screenshot?

---

### Post by cgkades on 2008-08-19
<alt>+<F2> type "gnome-panel" in the run box (without the quotes)

---

### Post by manturafs on 2008-08-19
sorry, i can't take a screenshot.  i can't access the menu's, right click doesn't work, etc.  however, since this is ubuntu hardy, all you can see is the default wallpaper when it boots in (i have it autoboot to a user so I don't even see the login screen).  i don't see any mounted drives or files that i saved to the desktop.

> <alt>+<F2> type "gnome-panel" in the run box (without the quotes) 

i guess i also forgot to mention that alt-f2 doesn't work either.  nothing pops up.  the only commands i can run have to be in terminal i think.

---

### Post by cgkades on 2008-08-19
i guess you could do "ps aux | grep gnome" and kill all the processes, then.. not 100% on this part, but startx, or gnome-wm, somthing like that.. i'm not sure of the x11 start command for ubuntu


*edit.. now that i think about it, you'll have to kill all your x11 stuff too. xorg i think it is. if you cant get it to work, how much would you loose if you just re-installed?

---

### Post by Expl0ited on 2008-08-19
Does it help you if you create a new user. If it does, I suggest you just use a new user and chalk it up to bad luck :D.

It how I fixed my gnome problems.

BTW. CTRL ALT F1 then sudo adduser username

then CTRL ALT F7 and log out, then log back in.

---

### Post by manturafs on 2008-08-21
> **cgkades said:**
> i guess you could do "ps aux | grep gnome" and kill all the processes, then.. not 100% on this part, but startx, or gnome-wm, somthing like that.. i'm not sure of the x11 start command for ubuntu


*edit.. now that i think about it, you'll have to kill all your x11 stuff too. xorg i think it is. if you cant get it to work, how much would you loose if you just re-installed?

how do i do this in terminal?  i'll try this as a last option.

> **Expl0ited said:**
> Does it help you if you create a new user. If it does, I suggest you just use a new user and chalk it up to bad luck .

It how I fixed my gnome problems.

BTW. CTRL ALT F1 then sudo adduser username

then CTRL ALT F7 and log out, then log back in.


I'll try this as well.  i haven't gotten around to it because i can't login.  my screen flickers between the login box and the mouse busy graphic.  it won't let me type anything so i'll have to fix taht first...

---

