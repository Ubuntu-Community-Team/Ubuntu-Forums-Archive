---
title: "using start-stop-daemon to control a X display"
date: 2008-01-25
forum: Programming Talk
---

### Post by mikeym on 2008-01-25
HI,

I'm wanting to control a x display on another display :1. I'm using xinit to create the display and I had the idea of using start-stop-daemon to control xinit, but when I launch xinit with start-stop-daemon it wont find the screen.

Is there some way to achieve what I'm looking for? The other thing that occurd was using XDM?

---

### Post by mikeym on 2008-01-26
Sorry, that was my mistake. *star-stop-daemon* does work with xinit.

```

start-stop-daemon --start --quiet --pidfile ~/test.pid --make-pidfile --name xinit --startas /usr/bin/xinit -- -- :1
start-stop-daemon --stop --quiet --pidfile ~/test.pid --name xinit --startas /usr/bin/xinit

```

**But** I still have a few problems. I can't seem to specify a screen resolution for my XServer. When I try:

```

xinit -- -screen 1024x768 -depth 24 :1

```

I get:

```
xauth:  creating new authority file /home/mikey/.serverauth.7390

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux ubuntu 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Jan 26 10:29:46 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No Screen section called "1024x768"
(EE) Unable to determine the screen layout
(EE) Error parsing the config file

Fatal server error:
no screens found

```

That resolution is in my [xorg.conf file]("http://ubuntuforums.org/attachment.php?attachmentid=57601&stc=1&d=1201343966"). 

**Also** is there any way to switch between displays in the same way as [ctrl]+[alt]+F? using a command from the terminal?

---

