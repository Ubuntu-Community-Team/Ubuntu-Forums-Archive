---
title: "Conky causes window title bars to remain visible"
date: 2015-12-27
forum: New to Ubuntu
---

### Post by Herdo on 2015-12-27
Conky is causing my window title bars to remain visible if I use the "-" minimize button to minimize an open program.  This doesn't happen if I Alt+Tab to "Show Desktop" but it also happens if I click on the icon of a maximized program in my Docky. If I then click on the desktop it fixes it and acts normally an focuses on the desktop.  Anyone have any idea how to fix this?  I've played around with various settings in compiz settings manager and unity tweak tool, as well as the system settings.  I'm using the "Show the menus for a window in the window's title bar" setting in the system settings.

Here are some screenshots to give a better idea of what I'm talking about:

Chrome title bar still on the top of the screen and Docky isn't visible due to "Window Dodge" setting.  Docky still thinks a window is populating the screen so it stays hidden.

[IMG]http://i.imgur.com/vL3Yzbl.png[/IMG]


After left clicking on the desktop once, the title bar disappears and Docky shows back up.

[IMG]http://i.imgur.com/yjtYQT3.png[/IMG]

---

### Post by Herdo on 2015-12-27
And of course, after some more searching for an answer, I've solved it myself.

For anyone else who runs into this problem, the solution can be found here:

[http://ubuntuforums.org/showthread.php?t=2156795&p=12704546&viewfull=1#post12704546](http://ubuntuforums.org/showthread.php?t=2156795&p=12704546&viewfull=1#post12704546)

You will need to install "compiz-plugins" to access the "Window Rules" category in CompizConfig.

```
sudo apt-get install compiz-plugins
```

---

