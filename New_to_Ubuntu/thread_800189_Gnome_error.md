---
title: "Gnome error"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-19
When i logged in this popped up 

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

evertything works fine but i dont know if its in the system or something.

---

### Post by EnergySamus on 2008-05-19
Hi!
Try reinstallng Ubuntu. Before you do, backup using the Live CD!!!

EnergySamus

---

### Post by AndyCooll on 2008-05-19
> **EnergySamus said:**
> Hi!
Try reinstallng Ubuntu. Before you do, backup using the Live CD!!!

EnergySamus
Before you go to such extremes, just try rebooting your pc/laptop. I occasionally get that message and a reboot does the trick.

:cool:

---

### Post by mr-Kirch on 2008-05-19
Reboot worked

---

### Post by shazbut on 2008-05-19
Better yet, just do a ctrl-alt-backspace.  I used to get that message a bit with 7.10, not so much with 8.04.

---

### Post by NIT006.5 on 2008-05-25
FYI, I've been having this error every time I log in for the past week. It turned out to be a problem with my loopback interface, which was no longer defined in /etc/network/interfaces. Took 10 seconds to fix once I eventually discovered that this was the problem. So, um yeah, I think the "reinstall" suggestion was a tad extreme.... I've never done a reinstall of Ubuntu unless hardware has crashed... there's almost always a way to fix it.... it just takes a lot of digging sometimes. :)

---

### Post by ericeclifford on 2010-05-03
I am getting this problem, and created my own post in the beginners forums, but to the above poster, may I ask how you solved it.

---

