---
title: "command to switch to CLI from GUI"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by SFitkin on 2008-07-03
I am aware that ctrl+alt+f1 switches me to the command line, and I'm not having any problem with it, but I was looking for an alternative.

Is there any command I can type into a terminal in the GUI to switch to console #1?

The reason is; I need to log straight into the CLI.  I am setting xubuntu up on a computer for my work, but it can't have any options (room for error) before it gets to the CLI.  I want it all automated.

In the end, I'd like to start xubuntu, log in, have the CLI automatically start, enter log in credentials automatically, then type "telnet (ip address)".  I don't want to have to touch it at all after I enter my log-in/pass for the gui.

I am fairly new to Ubuntu.  If someone could help, it would be appreciated.

---

### Post by phidia on 2008-07-03
What you want, I think, is to switch [runlevels]("http://en.wikipedia.org/wiki/Runlevel") Try /sbin/init 2
Hope that's helpful.

---

### Post by Dr Small on 2008-07-03
Forget Telnet. It's old, outdated and unsecure. Use OpenSSH.

---

### Post by AnarkistNZ on 2008-07-03
Try what Phidia said, and also yes. Use SSH for remote access, not telnet.

---

### Post by ZabiGG on 2008-07-03
Hi,

From what I understand, you don't even have to enter the GUI at all if you don't want to.

From the log on page (or greeter or whatever)

Click on **Session**

and choose either

Secure remote connection 
or
Failsafe terminal

Since the log on defaults to Last session, from the next time you log on, you'll end up using the same interface as long as you want until you change it yourself.

Hope this helps,

Z.

---

