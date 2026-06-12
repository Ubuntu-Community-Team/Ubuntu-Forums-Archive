---
title: "VNC woes - can connect but see a grey screen"
date: 2019-08-30
forum: New to Ubuntu
---

### Post by dctech1000 on 2019-08-30
I just loaded Ubuntu 18.04 LTS Desktop, installed xcfe4 and tight vnc server.
i am able to connect to the Linux box from my windows machine but only see a grey screen.  
My feelings is that the issue is the X windows and/or the desktop environment.  

Has as anyone gotten this to work?

---

### Post by TheFu on 2019-08-30
The gray root window means that X/windows is running, but usually either the WM or DE weren't started.
If the WM was started, you can click the mouse anywhere on the root window to see a menu.

I haven't used VNC in a very long time after discovering the NX protocol.  NX uses ssh for authentication and feels 2-3x faster than VNC.  The easiest implementation to use is x2go.  Because it only works over ssh using ssh-keys, ssh-tunnels, it is secure enough for use over the internet.  All the normal ssh anti-hacking tools also automatically protect any NX solution.  Let me know if you'd like to know more.

---

### Post by Skaperen on 2019-08-30
or google [x2go]("https://en.wikipedia.org/wiki/X2Go").

---

### Post by dctech1000 on 2019-09-02
Let me check this out. 
Thank you for your help.

---

### Post by dctech1000 on 2019-09-02
Thanks.

---

### Post by TheFu on 2019-09-02
It would actually help others if you said what you did, what worked, what didn't and what you finally decided to use.

If the issue is solved, "thread tools" button near the top has a "SOLVED" choice. That helps the community.

---

### Post by scorp123 on 2019-09-12
> **dctech1000 said:**
> I just loaded Ubuntu 18.04 LTS Desktop, installed xcfe4 and tight vnc server.
i am able to connect to the Linux box from my windows machine but only see a grey screen.  
My feelings is that the issue is the X windows and/or the desktop environment.  

Has as anyone gotten this to work?

Did you modify your "**xstartup**" file to actually do something, e.g. load XFCE? Because in its default state it will not do that.
Please check the content of this file: **/home/YourUser/.vnc/xstartup**

To make VNC start up XFCE that file should look something like this:

```

#!/bin/sh

#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

# Fix to make GNOME and GTK stuff work
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS

# exec /etc/X11/xinit/xinitrc
xrdb $HOME/.Xresources
xsetroot -solid grey

xfce4-session &

# before Ubuntu 18.04:
# gnome-settings-daemon &

# Ubuntu 18.04 and later:
/usr/lib/gnome-settings-daemon/gsd-xsettings &

```

That file is from one of my own machines and works tip top here. I hope it helps you solve your issue.

---

### Post by nmas2 on 2020-02-25
> **scorp123 said:**
> Did you modify your "**xstartup**" file to actually do something, e.g. load XFCE? Because in its default state it will not do that.
Please check the content of this file: **/home/YourUser/.vnc/xstartup**

To make VNC start up XFCE that file should look something like this:

```

#!/bin/sh

#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

# Fix to make GNOME and GTK stuff work
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS

# exec /etc/X11/xinit/xinitrc
xrdb $HOME/.Xresources
xsetroot -solid grey

xfce4-session &

# before Ubuntu 18.04:
# gnome-settings-daemon &

# Ubuntu 18.04 and later:
/usr/lib/gnome-settings-daemon/gsd-xsettings &

```

That file is from one of my own machines and works tip top here. I hope it helps you solve your issue.


This one worked for me. thanks!!!

---

