---
title: "Firestarter needing a pw"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-03
I would like to make firestarter begin by itself at startup, but it needs a password to even boot up. This is a problem cause if one of my family members needs to get on my computer, they won't be able to. Is there a way around this, or am i just &@$*@( outta luck?

---

### Post by meindian523 on 2008-06-04
It needs a password but you can allow your family to start up firestarter using their own password by adding them to the sudoers group.But problem is that then they can do all administration tasks including package management and user admin with their password.

I have no idea how you could allow only Firestarter to be started using a sudo password.But something to keep in mind is that Firestarter is only a GUI configuration frontend for the real firewall which is the inbuilt commandline iptables.So Firestarter doesn't need to be running for you to be protected.It needs to be running only if you want to change some rules but don't want to go to the command line for it.

---

### Post by Sef on 2008-06-04
> I would like to make firestarter begin by itself at startup,

A firewall comes with Ubuntu called IP Tables.  Firestarter is just a front end GUI for it.

---

### Post by ramjet_1953 on 2008-06-04
Unless you are using port forwarding for something like Azureus, or require port forwarding for any other things like it, Firestarter is superfluous. 

Also, running the Firestarter GUI requires root privileges. Running applications in root mode is a security risk when connected to the Internet.

Also another thing to consider is that if you are behind and ADSL router it has a hardware firewall protecting you.

Regards,
Roger :cool:

---

### Post by Cadmus on 2008-06-04
Firestarter doesn't have to be running in order to provide protection. If you've set up rules in Firestarter they're always there, even if the Firestarter program isn't running.

---

### Post by sayakb on 2008-06-04
Correct! You do not need firestarter to be running on startup. Still if you want to add it anyway, do this:
At a terminal
```
sudo visudo
```
And at the end, add this line:
```
%groupname ALL=NOPASSWD: /usr/sbin/firestarter
```
Where groupname should be replaced by your own group-name.
You should reboot once for this to work.

---

### Post by niceguy123 on 2008-06-08
I can access gmail. Could this be caused by Firestarter? I've never ran it and am working in a new installation of Hardy 8.04

How can I check and fix this if needed?

---

