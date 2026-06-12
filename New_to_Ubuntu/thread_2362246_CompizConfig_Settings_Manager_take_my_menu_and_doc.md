---
title: "CompizConfig Settings Manager take my menu and dock away"
date: 2017-05-25
forum: New to Ubuntu
---

### Post by cuthead on 2017-05-25
I open CompizConfig Settings Manager and select none,reboot,my ubuntu 14.04 AMD64 menu and dock disappear,please help me take them back.

---

### Post by again? on 2017-05-26
Select none what???
FYI the unity interface is a plugin for the compiz window manager and if you deselect the Unity plugin...no launcher...no panel.
You can reset unity/compiz via terminal.
```
dconf reset -f /org/compiz/
```

Then reload compiz.
```
setsid unity
```

---

### Post by cuthead on 2017-05-28
thank you,reload compiz is working,but /org/ does not exist in my ubuntu

---

### Post by again? on 2017-05-28
> **cuthead said:**
> thank you,reload compiz is working,but /org/ does not exist in my ubuntu

You sure about that?
```
dconf list /
```

> glen@GU17:~$ **dconf list /**
com/
net/
org/
apps/
ca/
desktop/

---

### Post by cuthead on 2017-05-28
dconf does not work on my console.console say D-BUS does not work.
'dconf list /' is in /etc/dconf/db?so /org/ does not exist in my ubuntu?
can you share your X11 config?

---

### Post by #&amp;thj^% on 2017-05-28
Give this a try:
```
export $(dbus-launch)
```
Then follow guber2 advice again.

---

### Post by again? on 2017-05-28
Are you running the commands from a non graphical session?(tty)
Dconf uses Dbus which is only autostarted in a normal graphical session.

---

### Post by cuthead on 2017-05-28
I think terminal depending unity,unity depending xorg,xorg depending tty.reset unity may work,like guber2 say,but I press ctrl+alt+t,there is no terminal.

---

### Post by again? on 2017-05-28
You can access a terminal by placing a shortcut on your desktop while in a tty session.
You can login to a tty console by pressing ctrl+alt+F1 at the login(greeter) screen.
Login, then
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop
chmod +x ~/Desktop/gnome-terminal.desktop
```

ctrl+alt+F7 to take you back to the greeter.
Then login to your normal X session where you should have a terminal launcher on the desktop.

You may find the info in this post useful.
[https://ubuntuforums.org/showthread.php?t=2252171&p=13163967#post13163967](https://ubuntuforums.org/showthread.php?t=2252171&p=13163967#post13163967)

---

### Post by cuthead on 2017-05-29
```
sudo cp /usr/bin/gnome-terminal ~/Desktop
ccsm
dconf reset -f /org/compiz/
```
thank you guber2

---

