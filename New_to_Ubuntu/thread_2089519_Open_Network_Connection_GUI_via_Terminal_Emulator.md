---
title: "Open Network Connection GUI via Terminal Emulator"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by mknight1219 on 2012-11-29
I'm using NX Client to remotely control a computer installed with Oneric Ocelot Xubuntu. When I log in via NX Client, I have significant restrictions on what I have access to. One of these restrictions is editing my connection settings. I can bring up the Edit Connections option, but everything is greyed out.

What I would like to do is learn of a way that I can temporarily lift those restrictions after logging in, or figure out what command I need to feed into the Terminal Emulator to bring up the connection settings GUI with administrative privileges. I am familiar with entering "sudu" followed by a name of a program and thereby having the appropriate privileges, but I can't figure out what name the network connections GUI uses.

I realize that I could edit these settings by going into various files and manually tweaking things, but since I am a bit of a beginner with Ubuntu, I would really appreciate the comfort and ease of using the GUI interface.

---

### Post by mknight1219 on 2012-11-30
Well, it took a lot of searching and time, but I finally managed to answer my own question. For the benefit of whoever else might run into this issue, I will post my solution.

The simple answer is that the command name of the default network connection editor for Oneric Ocelot Xubuntu is "nm-connection-editor". I found this out with the help of this very useful post: [https://lists.ubuntu.com/archives/xubuntu-users/2007-November/000913.html](https://lists.ubuntu.com/archives/xubuntu-users/2007-November/000913.html)

Apparently, you can (1) go into synaptic packet manager (which I earlier found can be opened with administrative privileges by typing "sudo synaptic" in the Terminal Emulator), (2) search for the program that provides the GUI interface, which in this case is "network-manager-gnome", (3) right-click on this program and select "Properties", (4) select the "Installed Files" tab, (5) look for items in the list that are preceded by "/usr/bin/", (6) find an item that looks like what you want and use whatever comes after "/usr/bin/" as your command name. Thus, open "Terminal Emulator" and type in "sudo nm-connection-editor".

---

### Post by xana40 on 2013-03-13
mknight1219, This was extremely helpful :) Thanks for the tip about nm-connection-editor!

---

### Post by mknight1219 on 2013-03-13
Great. I'm glad I was able to be of use. Thanks for letting me know it helped.

---

