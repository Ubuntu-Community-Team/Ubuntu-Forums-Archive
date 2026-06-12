---
title: "x11vnc troubles."
date: 2010-11-05
forum: Programming Talk
---

### Post by Caky on 2010-11-05
Hi,

I'm using x11vnc and need some help.
I want to attach the x11vnc to a screen/pid.

I'm using this code atm.
x11vnc -create -shared -forever -nocursor -rfbport _PORT_ -passwd _PASS_ -remote `screen -r 11020`

It doesn't work right atm..
Another thing is that i can type in SH if I remove the -remote command, how to block that ?
So you can only enter the screen/pid.

Thanks.

---

### Post by dwhitney67 on 2010-11-05
I have not used x11vnc, but I use vncserver, which I got by installing this package:
```

sudo apt-get install vnc4server

```
To launch the server, I had to create a *~/.vnc* directory:
```

cd ~
mkdir .vnc
chmod 700 .vnc

```
Then I created (maybe modified?) the *xstartup* file within the *~/.vnc* directory:
```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER

gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &

```

Finally, to start the VNC server, I created a script in *~/bin* called *vnc_setup*; it's contents are:
```

#!/bin/bash

vncserver :$1 -nohttpd -DisconnectClients=0 -NeverShared -localhost -depth 24 -geometry $2


```
Here, the $1 represents the display number you wish to use (0-9), and $2 the geometry (eg. 1440x800).  For example, to run the script:
```

./vnc_setup 3 1440x800

```

Once this is all setup, then you require a client app to connect to this server.  I personally use JollysFastVNC (on my Mac).

I'm sure x11vnc is conceptually similar to what I have described above.

---

### Post by Caky on 2010-11-05
Hi,

Thanks for your reaction, but that's not really what I want.

I just want to start the server by using 1 command, which attaches the server to a screen. And the server should shutdown if the screen exits.

---

### Post by krunge on 2010-11-05
> **Caky said:**
> Hi,

I'm using x11vnc and need some help.
I want to attach the x11vnc to a screen/pid.

I'm using this code atm.
x11vnc -create -shared -forever -nocursor -rfbport _PORT_ -passwd _PASS_ -remote `screen -r 11020`

It doesn't work right atm..
Another thing is that i can type in SH if I remove the -remote command, how to block that ?
So you can only enter the screen/pid.

Thanks.

What are you trying to do??

screen(1) is a terminal based way to keep a bunch of shells on a machine that you can detach from and reattach to later (e.g. when you ssh back in.)

x11vnc is a program that exports a graphical display (e.g. X server or Linux or Macosx graphical console) via VNC.

Note that -create runs the virtual X server Xvfb.
And -remote sends a message to an already running x11vnc.

I'm really confused what you are trying to do...

---

