---
title: "Logging out results in black screen!"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by DisappearingOak on 2012-03-13
Every time I use 'Log out' in kubuntu, what happens is that the screen goes black. The cursor is still there and I can move it and when I hover it where the password box is, the cursor changes to type cursor, so the login screen is rendered but I'm only seeing black. I can log in successfully too, but the whole screen stays black. There is no problem like this when booting up normally but only happens if I use Log Out option. please help.
I'm using ubuntu 11.10 with kde, and system is:
Gigabyte GA-880gm-d2h, AMD 965 processor, 4gb ram, onboard radeon hd 4250 graphics.

---

### Post by doctorzeus on 2012-03-13
> **DisappearingOak said:**
> Every time I use 'Log out' in kubuntu, what happens is that the screen goes black. The cursor is still there and I can move it and when I hover it where the password box is, the cursor changes to type cursor, so the login screen is rendered but I'm only seeing black. I can log in successfully too, but the whole screen stays black. There is no problem like this when booting up normally but only happens if I use Log Out option. please help.
I'm using ubuntu 11.10 with kde, and system is:
Gigabyte GA-880gm-d2h, AMD 965 processor, 4gb ram, onboard radeon hd 4250 graphics.

Sounds like its not holding it in the video buffer properly, a temporary fix is try switching to a tty (e.g. ctrl+alt+F1) and then back again (ctrl+alt+F7)..

Hope this helps

---

### Post by Zorael on 2012-03-17
When logging out, X tries to unload everything and reuse its current session, for efficiency. Try changing its behavior to instead exit completely and start up fresh.

In **/etc/kde4/kdm/kdmrc** at around line ~512;
```
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
**TerminateServer=true**
```
You need superuser permissions to edit this file, so hit Alt+F2 and run '**kdesudo kate /etc/kde4/kdm/kdmrc**'.

Remove any octothorpe (**#**) in front of the line in bold. If it's not there at all, add the line somewhere in the '**[X-:*-Core]**' section.

---

