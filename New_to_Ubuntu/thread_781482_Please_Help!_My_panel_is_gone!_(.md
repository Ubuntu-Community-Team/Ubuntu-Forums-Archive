---
title: "Please Help! My panel is gone! :("
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Kosimo on 2008-05-04
Hello guys, today I turn on my Hardy, and I HAVE NO PANEL!!

alt + f2 doesn't works either...    I could open firefox by seleting an icon in my desk and choose (open with) ...

wow...


How can I fix this?




I tried restarting many times but is always the same. Any idea?

Thank you guys

---

### Post by Kosimo on 2008-05-04
Somebody knows what is the (starting name) for gnome-panel? 

I can may try to start it and then problem solved.

---

### Post by SickTwist on 2008-05-04
Right-click on the desktop, select "Create Launcher..." and use /usr/bin/gnome-terminal for the command. Then you can use that icon to start a terminal. Run "gnome-panel" to start the panel. If that doesn't work, run "metacity --replace" to force the metacity window manager to run. (Compiz may be running and having problems.)

Hope that helps.

---

### Post by Kosimo on 2008-05-04
> **SickTwist said:**
> Right-click on the desktop, select "Create Launcher..." and use /usr/bin/gnome-terminal for the command. Then you can use that icon to start a terminal. Run "gnome-panel" to start the panel. If that doesn't work, run "metacity --replace" to force the metacity window manager to run. (Compiz may be running and having problems.)

Hope that helps.

Hello!!!

Thank you so much for helping!

When I choose (create launcher) doesn't do anything, so, I can't create lanuchers to run anything...   About compiz,  I'm running metacity as my Radeon Mobility 9200 doesn't works with compiz in Hardy...

Any other idea?      Thank you again

---

### Post by SunnyRabbiera on 2008-05-04
were you running one panel or two?

---

### Post by Kosimo on 2008-05-04
> **SunnyRabbiera said:**
> were you running one panel or two?

One panel.
Located in left side.

---

### Post by SickTwist on 2008-05-04
Switch to another virtual terminal (press ALT+CTRL+F1 at the same time), log-in using your username and password, then run this exactly the way it's typed:

DISPLAY=:0 gnome-terminal

That will cause gnome-terminal to launch on your desktop. Press ALT+F7 to go back to the desktop. Try running "killall nautilus" to force nautilus to stop running (nautilus is responsible for displaying icons and wallpaper on the desktop and it could have locked up). Also, try running "gnome-panel" from the terminal to try to force the panels to start.

---

### Post by Kosimo on 2008-05-04
Ooops...

I could open terminal... Then I found the problem...

```
-laptop:~$ gnome-panel
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found

```


I remove evolution yesterday... But looks like I also remove the gnome panel!  

I'm gonna try to install it now by  sudo apt-get install gnome-panel

---

### Post by SickTwist on 2008-05-04
OK, glad you found it. Make sure nautilus is installed too (that may be why you cannot create a new launcher).

sudo apt-get install nautilus gnome-panel

---

### Post by Kosimo on 2008-05-04
Cool, now I've got my panel back! ;)

Nautilus was installed BTW, and since I installed gnome-panel I can create lanchers again.  

Thank you so much guys for helping.

---

