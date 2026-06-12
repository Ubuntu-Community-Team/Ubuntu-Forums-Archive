---
title: "Removing Top Bar and Bottom Bar of Ubuntu"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by jtfire55 on 2008-08-14
I would like it removed, anybody knows how to do this?

---

### Post by cpetercarter on 2008-08-14
I guess you mean the "panels" - the bars with icons etc at the top and the bottom of the screen.

Right click on one of them, select "delete this panel".

---

### Post by shizakapayou on 2008-08-14
You can't get rid of both, but you can make the remaining one small.  On mine, if you right-click the panel and go to Properties, I have 'Expand' unchecked, the size as low as it will go, and 'Show hide buttons' checked.  Using that I can slide it into the bottom-left corner of the screen.

I use avant-window-navigator, so getting the panels out of the way was good for me.

---

### Post by starcannon on 2008-08-14
This command will make them both go away.

```

gnome-session-remove gnome-panel

```

I don't know if they will stay gone though. If not I'm sure it can be made permanent.

If you do this and decide it was a mistake, then use this guide to set things back to default:

[http://ubuntuforums.org/showpost.php?p=5578191&postcount=10](http://ubuntuforums.org/showpost.php?p=5578191&postcount=10)

Good Luck and have fun, btw if you have no panels and need to get the terminal started, Alt-F2: gnome-terminal will get you a terminal.

Cheers,
Starcannon

---

### Post by fparedesg on 2008-08-25
You can open Synaptic and uninstall "gnome-panel"

---

### Post by pyromanic123boom on 2008-08-25
don't uninstall the gnome-panel. that would be irritating to fix in case you change your mind. Just right click a panel and "delete". If you can only delete one, make one as thin as possible and make it autohidden.

---

### Post by Jubei71 on 2008-10-03
I removed the bottom panel, but somehow the space the panel occupied is still occupied - but this I mean that when I try to maximize a window, the window won't extend into the the space formerly occupied by the bottom panel. 

How to fix this?

EDIT : Solved. It turned out that I had to disable an option in Cairo Dock. Sorry folks!

---

