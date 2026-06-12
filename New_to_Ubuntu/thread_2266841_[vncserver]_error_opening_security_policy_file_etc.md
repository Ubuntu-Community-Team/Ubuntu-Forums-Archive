---
title: "[vncserver] error opening security policy file /etc/X11/xserver/SecurityPolicy"
date: 2015-02-25
forum: New to Ubuntu
---

### Post by van5 on 2015-02-25
I try to start vncserver

```
$vncserver
Starting applications specified in /home/user1/.vnc/xstartup
Log file is /home/user1/.vnc/home1:1.log
```

Inside /home/user1/.vnc/home1:1.log I find 

```
error opening security policy file /etc/X11/xserver/SecurityPolicy
```

How can I fix it?

P.S.
content of my ~/.vnc/xstartup was
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
#unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
```

Following [http://ubuntuforums.org/showthread.php?t=1480094&p=9324498#post9324498](http://ubuntuforums.org/showthread.php?t=1480094&p=9324498#post9324498) I modified it to 
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
```

and restarted the Xserver by executing
```
sudo service lightdm restart
```
then I executed ```
vncserver
``` again, but that doesn't seem to have any effect on the content of ~/.vnc/xstartup

---

### Post by van5 on 2015-03-03
up

---

### Post by steeldriver on 2015-03-03
What version of Ubuntu, and which variety and version of vncserver (vnc4server? tightvncserver?)?

A bit of googling seems to suggest that error is not necessarily fatal - can you see a running (or listening) vnc process?

FYI "the Xserver" that's run by lightdm shouldn't affect "the Xserver" that's run by vncserver (it's not a 'desktop sharing' kind of vnc)

---

### Post by van5 on 2015-03-21
steeldriver, thank you for your reply.

The error was indeed not fatal: I was able to connect to the desktop using "screen sharing" application.

However, when I connected, I didn't see the usual gnome panel, the usual background picture and the open skype window (that was open on the desktop) - just grey background and a terminal window open.
Furthermore, I started the gnome-panel and tried to turn off the computer remotely. It didn't work, although I checked the parameter "let other users to view your desktop" and "allow other users to control your desktop" remotely.

What should I do to remotely connect "properly"?





> What version of Ubuntu, and which variety and version of vncserver (vnc4server? tightvncserver?)?

ubuntu 12.04 lts

I'm not sure what version of vncserver I'm running (I start it with the command vncserver)
ps -e | grep vnc returns nonzero time for Xvnc4
ps -e | grep light returns zero time for lightdm

---

### Post by steeldriver on 2015-03-21
It sounds like you should be using the default 'Desktop Sharing' server (vino-server) instead of vncserver - vncserver is for running standalone X sessions and requires you to specify the details of the session separately in a ~/.vnc/xstartup file (else you get the default gray screen that you are describing)

---

### Post by van5 on 2015-06-01
> **steeldriver said:**
> It sounds like you should be using the default 'Desktop Sharing' server (vino-server) instead of vncserver - vncserver is for running standalone X sessions and requires you to specify the details of the session separately in a ~/.vnc/xstartup file (else you get the default gray screen that you are describing)

Thank you for the reply. I tried vino and x11vnc - they fail with different types of mistakes.

However, it seems vncserver works - it shows grey screen with the terminal. Can someone please help me configure it?

Update: gnome-classic seemed to work
[https://askubuntu.com/questions/172384/vnc-grey-screen-and-start-on-boot-12-04](https://askubuntu.com/questions/172384/vnc-grey-screen-and-start-on-boot-12-04)

---

