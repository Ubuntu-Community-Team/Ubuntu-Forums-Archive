---
title: "want to install a couple windows VMs on ubuntu; should I use 20.04 server or WS?"
date: 2021-12-09
forum: New to Ubuntu
---

### Post by frevi on 2021-12-09
I'm about to go pick up my killer new laptop (i9, lots of ram, etc). The idea is to install ubuntu at the bottom, and two win10 virtual machines to start with, one for work and one for personal. Do I need to do this on Ubuntu server or is it possible on workstation? Is one or the other preferable? 

A few months ago I started doing a 20.04 server installation to put a couple of windows server VMs on, but had to stop for unrelated reasons before I got past getting 20.04 server installed on a native RAID. Other than that, I don't have much linux or ubuntu knowledge yet.

Any suggestions appreciated.

thx

---

### Post by naxal on 2021-12-09
Hello,

I am no expert so wait for others to reply for better explanation.

Underneath, Server and Desktop Ubuntu is the same. Server is kind of Desktop minus the Ubuntu for CLI (headless operation). You can have all Desktop features (add-on installation) in Server or add all server features in Desktop Ubuntu.

Both will do just fine but your platform being laptop, I may do Ubuntu Desktop for better out of a box experience

Thanks.

---

### Post by yancek on 2021-12-10
It is certainly possible to install windows in a virtual machine on the standard desktop of Ubuntu.  As stated above, the major difference with the server version is that there is no graphical user interface with the server version.

---

### Post by ActionParsnip on 2021-12-10
If you need a desktop UI then use the desktop. If you want low RAM and CPU footprint for the OS and are OK in pure CLI then use server.

---

