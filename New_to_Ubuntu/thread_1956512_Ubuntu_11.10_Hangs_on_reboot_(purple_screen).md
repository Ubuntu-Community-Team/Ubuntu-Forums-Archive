---
title: "Ubuntu 11.10 Hangs on reboot (purple screen)"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by samikkk on 2012-04-11
[LEFT][COLOR=black][FONT=Times New Roman][SIZE=4]Hello,[/SIZE][/FONT][/COLOR][/LEFT]
 
[LEFT][COLOR=black][FONT=Times New Roman][SIZE=4]Ubuntu 11.10 can't login within the gui window after update. [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=4]Yes, I can login through the command line (Alt+Ctrl+F1). but unfortunately, I can't login from gui window. Hangs on reboot (purple screen)[/SIZE][/FONT][/COLOR][/LEFT]
 
[LEFT][FONT=Times New Roman][SIZE=4]Thank you,[/SIZE][/FONT][/LEFT]

---

### Post by daslinkard on 2012-04-11
It sounds like your gnome-session has been uninstalled.  Log in the way that you normally would and then open up a terminal.

```
CTRL+ALT+T
```

Then type the following sudo command:

```
 sudo apt-get install gnome-session
```

Then try logging in again.

---

### Post by samikkk on 2012-04-14
> **daslinkard said:**
> It sounds like your gnome-session has been uninstalled.  Log in the way that you normally would and then open up a terminal.

```
CTRL+ALT+T
```

Then type the following sudo command:

```
 sudo apt-get install gnome-session
```

Then try logging in again.
[LEFT][COLOR=black][FONT=Times New Roman]I got this message when I tried to install [/FONT][/COLOR][COLOR=black][SIZE=3][FONT=Calibri]gnome:[/FONT][/SIZE][/COLOR]
[SIZE=3][COLOR=black][FONT=Calibri]gnome-session[/FONT][/COLOR][FONT=Times New Roman] is already the newest version.[/FONT][/SIZE][/LEFT]

---

### Post by souravc83 on 2012-04-14
Go to the terminal that you get after pressing Ctrl+Alt+F1.

Type
[HTML]unity --replace[/HTML]

After the command has executed, press Ctrl+Alt+F7 to come back to the graphical user interface.

---

### Post by samikkk on 2012-04-14
> **souravc83 said:**
> Go to the terminal that you get after pressing Ctrl+Alt+F1.

Type
[HTML]unity --replace[/HTML]

After the command has executed, press Ctrl+Alt+F7 to come back to the graphical user interface.
[LEFT][COLOR=black][FONT=Times New Roman]I got this message[/FONT][/COLOR][COLOR=black][SIZE=3][FONT=Calibri]:[/FONT][/SIZE][/COLOR]
[FONT=Times New Roman]warning: no Display variable set, setting it to: 0[/FONT]
[FONT=Times New Roman]unity-panel-service: no process found[/FONT]
[FONT=Times New Roman]compiz (core) - Fatal: Couldn't open display :0[/FONT][/LEFT]

---

