---
title: "Desktop files and links"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by dennycraig on 2008-07-10
I have had certain files and program links displayed on my desktop for easy access. The other day I must have pressed the wrong button at the wrong time because now my desktop window is clean of all icons. I d not know what I did and so I do not know how to bring the icons back to my desktop. 

If i go to places and hit desktop it shows everything which should be displayed on my desktop but it will not transfer anything to the desktop display. 

How do I get my desktop window to display my desktop icons which are still in the proper desktop folder?????

I know it is an easy fix. I just can figure it out at this time. Please give me a hint:)

---

### Post by tjwoosta on 2008-07-10
did you by any chance use gconf-editor lately to change anything in nautilus?

---

### Post by nhandler on 2008-07-10
Open up ~/.config/user-dirs.dirs in your favorite text editor. Make sure that 'XDG_DESKTOP_DIR' is set to '$HOME/Desktop'. This variable controls what directory is displayed on the Desktop. Once you set this variable to '$HOME/Desktop', you should log out and then log back in. Hopefully, your icons should be back on your desktop.

---

