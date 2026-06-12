---
title: "vnc gray screen with xfce"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by jwshgeek on 2012-10-13
I am trying to setup an xubuntu box with vnc, vnc run's but I get a gray screen when I connect, my xstartup is as follows"



# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
xfce4-session &
start xfce4 &

---

### Post by Toz on 2012-10-14
Hello and welcome to the forums.

Comment out > xfce4-session &
...and make sure there is no space between "start" and "xfce4" in your last line. Like this:
```
# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#xfce4-session &
startxfce4 &

```
If that doesn't work, there is a log file in your ~/.vnc folder that might help identify the problem.

---

### Post by jwshgeek on 2012-10-14
it worked once, but now it's back to the gray screen, the only error I'm seeing in the log is this:

Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxsetroot:  unable t$
/home/admins/.vnc/xstartup: 8: /home/admins/.vnc/xstartup: vncconfig: not found
/usr/bin/startxfce4: X server already running on display :0
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxrdb: Resource temp$
xrdb: Can't open display ':0'
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-C$
(xfce4-terminal:1885): Gtk-WARNING **: cannot open display: :0
Agent pid 1905
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxscreensaver: 04:26$

---

### Post by Toz on 2012-10-15
Try killing all of your vncserver sessions and starting over.

What command do you use to start to the vncserver?

---

### Post by jwshgeek on 2012-10-18
I ended up doing it a different way as tightvnc doesn't actually work for what I need to do.  

My solution is here: [http://ubuntuforums.org/showthread.php?t=2072040](http://ubuntuforums.org/showthread.php?t=2072040)

---

