---
title: "Duplicate ~/Desktop behaviour"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Bodsda on 2008-06-05
Hey, ive been looking for a solution to this for a while without joy so i thought id ask here. 

NOTE: Desktop (cap) will mean the folder, desktop (no cap) will mean the actual graphical desktop window.

~/Desktop shows its contents on the desktop without use of symbolic links. I'm after an exact behaviour duplicate with another folder say ~/pictures. I dont want to have to move the contents of pictures and i dont want to have to make links to Desktop.

can it be done? if so how!!

thanks in advanced gusy ;~)

---

### Post by nhandler on 2008-06-06
This can be done quite easily. Start by editing ~/.config/user-dirs.dirs in your favorite text editor. There should be a line that says:

> XDG_DESKTOP_DIR="$HOME/Desktop"

You want to change that to be:

> XDG_DESKTOP_DIR="$HOME/pictures

Now, save and exit the file. You can either logout, reboot, hit Ctrl+Alt+Backspace, or type "killall nautilus" in a terminal. After you do one of those things, your desktop should show all of the files/folders in ~/pictures.

---

### Post by Bodsda on 2008-06-06
is there a way of having say 

```
XDG_DESKTOP_DIR="$HOME/Desktop" && "$HOME/Pictures"
```

---

### Post by kidders on 2008-06-14
> **Bodsda said:**
> is there a way of having say 

```
XDG_DESKTOP_DIR="$HOME/Desktop" && "$HOME/Pictures"
```

No ... your desktop can't be in more than one place at the same time.

---

