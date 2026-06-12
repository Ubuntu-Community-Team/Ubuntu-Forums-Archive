---
title: "vino shuts down after logout"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by ben5 on 2014-10-24
So when I am connected to an ubuntu PC via vino when I chose to log out the user on ubuntu it kicks me out.  Then I am unable to log back in until someone goes to the machine and physically logs into the user again. 

I want to be able to access the ubuntu PC after logging out so that I can perform the login of the user myself without the help of someone physically at the machine.

Any ideas?

---

### Post by ben5 on 2014-10-24
FYI - So I notice when I log out this process stops
/usr/lib/vino/vino-server --sm-disable

So I tried logging in via SSH and and running that process but I get this
$ /usr/lib/vino/vino-server --sm-disable
**Cannot open display:**

Any ideas?  How to either make vino NOT stop when user is logged out or how to start it again without someone at physical machine to login?

---

### Post by steeldriver on 2014-10-24
AFAIK vino-server is a *desktop sharing* server - it needs the user to be running an active desktop session else there's nothing to share

If you want to run independent remote sessions, then you could use a standalone VNC server such as tightvncserver or vnc4server

If you really want to be able to log in via the GUI remotely i.e. "share" the display manager, then it's possible with x11vnc (see for example [http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/) which describes the basic method well even though it's for 11.10) and *may* be possible with vino-server - but I haven't tried it.

---

