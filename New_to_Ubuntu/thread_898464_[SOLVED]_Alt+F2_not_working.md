---
title: "[SOLVED] Alt+F2 not working"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by medfojo on 2008-08-23
Alt+F1 will show the application menu, but Alt+F2 doesn't do anything.  It's supposed to start a terminal, no?

I checked the keyboard shortcuts and it isn't mapped to anything.  I assume it isn't supposed to be mapped because it should just be inherent in the system.  This is just an uneducated guess though.

Can anyone tell me why Alt+F2 doesn't start a terminal?  Thanks.

---

### Post by gjoellee on 2008-08-23
ALT + F2 doesn't start the terminal, but something that isn't really much different. In most commpn cases the thing you use ALT + F2 is for start applications.

---

### Post by ace007 on 2008-08-23
Under Prefs>>Keyboard shortcuts you can change it.  And it doesn't launch a terminal, it opens the panel run dialog. Which is a gnome-panel application. If yours is not mapped, it may have happened when you installed/uninstalled or changed some other settings.

---

### Post by medfojo on 2008-08-23
What starts a terminal?  If I start a terminal from the system menu and run emerald --replace it starts emerald, but if I close the terminal emerald dies with it.  I read in another thread that starting a terminal with Alt+F2 will allow emerald to keep running after closing the terminal.

---

### Post by Iowan on 2008-08-23
> **medfojo said:**
> Can anyone tell me why Alt+F2 doesn't start a terminal?  Thanks.
Try CTRL-ALT-F2  (Actually CTRL-ALT-F1 through CTRL-ALT-F6.)
  CTRL-ALT-F7 takes you back to desktop.

---

### Post by ace007 on 2008-08-23
For a more permanent solution you can go to advanced settings of Compiz and under "window decorations" you can change the command line to emerald replace

---

### Post by jpeddicord on 2008-08-23
> Try CTRL-ALT-F2 (Actually CTRL-ALT-F1 through CTRL-ALT-F6. CTRL-ALT-F7 takes you back to desktop). Probably not what they were looking for. ace007 is right, go to System > Preferences > Keyboard Shortcuts, and look for "Show the panel run application dialog." Click it, and press Alt+F2 to assign it.

---

### Post by medfojo on 2008-08-23
Doh!  I forgot I remapped the run dialog to Alt+` (this is what I used for 'run' app i made in windows, but ubuntu came equipped).

Thanks for all the input.

btw, this is my 3rd day with ubuntu and i am DEFINATLEY here to stay.  I am amazed.

---

