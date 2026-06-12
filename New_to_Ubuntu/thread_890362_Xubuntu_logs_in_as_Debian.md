---
title: "Xubuntu logs in as Debian?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by FreeFrag on 2008-08-15
Xubuntu ran an update, and the next day when I tried to log in it only displays a Debian login screen, after which the machine only displays a background and cursor. As usual, Google provided no solutions and the people I usually can get help from made themselves conveniently unavailable. Please keep in mind I have minimal terminal experience, the best I know to do at this point is ctrl+alt+F1. If anyone can help me to get the standard Xubuntu login screen back I'd appreciate it. Thanks!

---

### Post by InfinityCircuit on 2008-08-15
System -> Administration -> Login Window

Go to Local and change the theme.

---

### Post by FreeFrag on 2008-08-15
I don't have access to a GUI beyond the incorrect login screen.

---

### Post by InfinityCircuit on 2008-08-15
What do you mean? You can't log in? You have gdm installed but no window manager?

---

### Post by FreeFrag on 2008-08-15
I mean that all I get is a cursor and a desktop background. I don't get toolbars or icons or menus...

---

### Post by kerry_s on 2008-08-15
at the log in screen, choose failsafe session, when you get to the terminal type> nautilus <press ctrl+h,right click .gnome2 and rename it to something else, just in case you need to put it back.
now type> exit <to get back to the log in screen, select gnome in the session menu and log in.

good luck

---

### Post by FreeFrag on 2008-08-16
I don't have access to a session menu, all I get is username/password at the login screen. Also I don't want to use Gnome, I'm trying to get back to using Xfce.

---

### Post by kerry_s on 2008-08-16
> **FreeFrag said:**
> I don't have access to a session menu, all I get is username/password at the login screen. Also I don't want to use Gnome, I'm trying to get back to using Xfce.

what, is there nothing else at the login screen but the box where you enter in?

at the log in screen press> ctrl+alt+f2
log in
type: sudo killall gdm
type: sudo apt-get remove --purge gdm
type: sudo apt-get install gdm
type: sudo reboot

did you mix repos or something? you do know debian is not ubuntu, using debian repos will toast your install.

---

### Post by FreeFrag on 2008-08-16
I probably did. :>

It still tries to log in as debian after that.

---

### Post by kerry_s on 2008-08-16
> **FreeFrag said:**
> I probably did. :>

It still tries to log in as debian after that.

probably just best to reinstall.

---

### Post by FreeFrag on 2008-08-16
irreplacable data loss ftw

---

### Post by FreeFrag on 2008-08-16
I don't like doing double posting but I figured I'd update since I managed to get it.

When using [FONT="Courier New"]startxfce4[/FONT] it would claim to already be running on display 0, so I started it on another display with [FONT="Courier New"]startx -- :1[/FONT]. It brought up the normal display that I'd been trying to get to. I attempted to go to the login configuration from the first page of this thread (when rebooting it still brought up the Debian login) but it said that GDM wouldn't start because it's not the default display manager. I then followed the directions found [here]("https://answers.launchpad.net/ubuntu/+question/32411"), changing it from XDM to GDM:

ctrl+alt+F1
[FONT="Courier New"]sudo /etc/init.d/xdm stop[/FONT]
[FONT="Courier New"]sudo nano -B /etc/X11/default-display-manager[/FONT]
change [FONT="Courier New"]/usr/sbin/xdm[/FONT] to [FONT="Courier New"]/usr/sbin/gdm[/FONT]
ctrl+x, y, enter
[FONT="Courier New"]sudo /etc/init.d/gdm[/FONT]

It didn't work entirely, so I did [FONT="Courier New"]sudo dpkg-reconfigure gdm[/FONT], changing it to GDM from there, and followed it with [FONT="Courier New"]sudo /etc/init.d/gdm force-reload[/FONT]. After restarting I got the correct login screen back and it works fine except that using Last Session results in the cursor & background only issue so I have to manually select an Xfce session.

Edit: At some point toward the start of the process here, I also had to delete the X0-lock file that X generates, but I don't remember where since I'm typing all of this from my unreliable short-term memory.

---

