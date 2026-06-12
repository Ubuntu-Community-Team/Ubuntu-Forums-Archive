---
title: "vnc server on startup (x11vnc)"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by 0snyper on 2014-03-05
Checked, not going to work:
[http://ubuntuforums.org/showthread.php?t=1207558&highlight=vnc+server+startup](http://ubuntuforums.org/showthread.php?t=1207558&highlight=vnc+server+startup)

Been through this, Not working
[http://linuxlubuntu.blogspot.ca/2011/02/setup-vnc-server-for-lubuntu.html](http://linuxlubuntu.blogspot.ca/2011/02/setup-vnc-server-for-lubuntu.html)

been through this:
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

I'll take a look at this when I'm not at work and I'm not drained or tired:
[http://ubuntuforums.org/showthread.php?t=1868554](http://ubuntuforums.org/showthread.php?t=1868554)

To the best of my knowledge I'll need to run upstart when the system loads and have the command below run using upstart and or the terminal.
This: >  [FONT=Arial]**x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800 **[/FONT] does work in getting connected.
How to have this load on start up I do not know. Any takers?

Any help would be appreciated. Been at this for 4+ days after dealing with errors and all. (DVD drive decided it would take a dump on my head for good measure .... anyways) need some sleep and hope I can get this sorted whenever. 

Thanks,

---

### Post by steeldriver on 2014-03-05
Tried this one yet?

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

Please do read the comments about security via SSH tunneling if you're planning on exposing the box outside a NATed LAN

---

### Post by 0snyper on 2014-03-06
Thank you that worked. I appreciate it greatly and Its a huge weight off my shoulders. The plan was to have VNC running and from there take care of everything remotely in terms of any major setup of the machine itself. I do plan on exposing the machine outside of  "NATed LAN**"** just not yet.

Again thanks, I wish I had been less stubborn and decided to come here earlier. 

Kinda didn't want to bother anyone with what I expected to be trivial. :)

---

