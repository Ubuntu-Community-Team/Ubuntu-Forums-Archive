---
title: "Mini-HOWTO: Run native Linux games from X without KDE (Gnome)."
date: 2006-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by z-vet on 2006-03-25
KDE eats appreciable amount of resources and games may be laggy even on fast machines. I run my favorite UT 2003 from within it's own X session and it looks better and runs smoother. Here is how.
[color=#CC0000]Warning[/color]: Disadvantages of this method is that we need to disable kdm (gdm) at startup. And to shut down KDE (Gnome) when gaming... Good thing is that you get a real performance boost.  
Open a terminal emulator and do (Gnome users replace nano with gedit):
```
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager.orig
sudo nano /etc/X11/default-display-manager
``` 
This file contains only one line: 
```
/usr/bin/kdm (or /usr/bin/gdm in case of Gnome)
```
Delete this line and save a file.
Find out what is your game's executable and remember it's full path. In my case it's /usr/local/games/ut2003/ut2003, yours may be different.
Now close KDE (Gnome) and reboot (reboot needed just once for the changes to take effect). When the system boots up you will stay in text-only mode with login prompt. Login with your username and pass. To start X do:
```
startx &
```
To start a game do:
```
startx -e /path/to/your_game_executable
```
Enjoy.
BASH will remember this command, so you don't need to type it in each time you want to start a game, just use standard up-arrow to list previous commands.
When the game is closed, you stay in X session. Kill it with Ctrl-Alt-Backspace to get to prompt again. Then startx & for KDE or Gnome. 
In case you want to rollback, it's simple: 
```
sudo rm -f /etc/X11/default-display-manager
sudo cp /etc/X11/default-display-manager.orig /etc/X11/default-display-manager
```
Reboot.

---

