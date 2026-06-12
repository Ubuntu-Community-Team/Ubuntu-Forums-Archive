---
title: "Stuck in command line"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by vasilios on 2008-10-04
Hello. I just got my new computer yesterday, and I was trying shortcuts to flip the desktop cube. I accidentally hit Ctrl + Alt + F1 instead of Ctrl + Alt + 1.
Now, I am stuck in the command line. I have searched for commands to switch back to the GUI, and I found "startx" and "gnome&." When I type "startx," I get a message that says, "Fatal server error: Server is already active for display 0 If this display is no longer running, remove /tmp/.X0-lock and start again." When I type "gnome&," it says, "-bash: gnome: command not found."
Does anyone know how I can return to the GUI? I know it is installed because I was using it yesterday. Thank you for your help.

---

### Post by tuxxy on 2008-10-04
Try this

```
CTRL + ALT + F7
```

---

### Post by sdowney717 on 2008-10-04
or just turn it off and reboot. You somehow went to a terminal console.

---

### Post by PocketDog on 2008-10-04
Type **gnome-desktop** to start it if it isn't running. If you're trapped in a full screen Terminal just type **exit**

---

### Post by vasilios on 2008-10-04
That did it. Thank you very much.

---

### Post by lswb on 2008-10-04
Press Alt+F7 or Ctrl+Alt+F7. If that doesn't work try F8,F9 etc.

In ubuntu and most other linux versions, text-mode consoles, usually just called vt for virtual terminal, are accesible by pressing Ctrl+ALt+F1 through Ctrl+ALt+F6 from a GUI. To switch from a text-mode vt to another only Alt+Fx is necessary, the control key is not needed.

When X starts up it normally uses vt7 (sometimes if there are multiple users or logins or if defaults have been changed it could be running on another vt, usually vt8 and higher) so pressing Alt+F7 or Ctrl+Alt+F7 from another vt will return to the graphical desktop. These are default settings but they are seldom changed.

BTW, if you really get stuck at the CLI and want to restart the system, "sudo reboot" will do it or just press Ctrl-ALt-Delete. The computer will restart normally and let you login to the graphical desktop.

---

