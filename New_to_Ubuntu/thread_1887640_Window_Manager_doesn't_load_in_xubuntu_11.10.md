---
title: "Window Manager doesn't load in xubuntu 11.10"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by rymp on 2011-11-27
When I turn on my computer, the home folder opens for some strange reason and there is no window manager around it. The panel and wallpaper load just fine, but my cursor is a black X instead of a white arrow. I have to go to the terminal and run "xfwm4 &" to get the window manager to start. After I do this everything is fine. Does anyone know how to make the window manager start correctly?

---

### Post by ajgreeny on 2011-11-27
I think I remember reading that this is a bug in the Xubuntu 11.10 version.

You can restore xfwm4, which manages window  decorations, by pressing Alt+F2 and running xfwm4. To restore panels,  press Alt+F2 and run xfce4-panel. 
If  the window decorations and/or panels don’t start automatically on  login, add the respective commands to your session from Settings ->  Sessions and Startup -> Application Autostart.

---

### Post by rymp on 2011-11-27
Thank you, I added the command to the startup programs and also removed Thunar from the session tab so the home folder would not pop up.:D

---

### Post by chrb on 2012-01-27
Launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361)

---

