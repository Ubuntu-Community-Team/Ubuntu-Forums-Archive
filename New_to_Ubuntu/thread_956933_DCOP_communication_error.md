---
title: "DCOP communication error"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by chinex004 on 2008-10-23
how do i solve this. An error notifier pops up each time i try to run programs like Amarok, wireshark and makes the program eventually hang.

---

### Post by nnamdi on 2008-10-23
DCOP stands for Desktop COmmunication Protocol. It's a light-weight interprocess and software componentry communication system. The main point of this system is to allow applications to interoperate, and to share complex tasks. Essentially, DCOP is a ‘remote control’ system, which allows an application or a script to enlist the help of other applications. Unfortunately, DCOP is associated with the K Desktop Evironment. To run a KDE application in Gnome, that requires the DCOP server, you will need to install the kde libraries. You can do this via this command from a terminal (or via a gui alternative method, in add/remove or the synaptic package manager):


or 

[http://ubuntuforums.org/showthread.php?t=511300&highlight=DCOP](http://ubuntuforums.org/showthread.php?t=511300&highlight=DCOP)

---

