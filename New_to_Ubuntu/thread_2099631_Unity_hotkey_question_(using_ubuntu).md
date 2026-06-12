---
title: "Unity hotkey question (using ubuntu)"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by ghantauke on 2012-12-30
In a nutshell my question is: Is there any way to make the window resize done by ctrl + super + left/right permanent?

I usually tend to use two windows each taking half of the screen. This can be easily done by the keyboard shortcut key I mentioned above. But the problem with that hotkey is that when I minimise one of those windows and restore it, it goes back to its original size. Is there anyway to make the window resize done by that hotkey permanent so it doesn't go back to its original size after minimising it?

---

### Post by vanadium on 2012-12-30
In principle, you should be able to achieve the effect you want by going to the "grid" plugin in Compiz Config Settings manager. Go to the "edges" tab, disable "Snap windows back to original size"

However, on my system, this removes the Window decorations: you cannot move/switch windows anymore. Setting the option back on and restarting restores compiz. (to restart, press Ctrl+Alt+T to open a terminal, then "sudo reboot now". There must also be a gnome command that does not require root privileges, but I so not know it => edit: foud it: "gnome-session-quit". This allows you to log out and log back in: much faster, more elegant and no root access needed). 

So the option is there, but does notwork (at least for me). That is why the use of Compiz Config Manager is not standard recommended.

---

