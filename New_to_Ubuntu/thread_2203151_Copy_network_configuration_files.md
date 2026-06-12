---
title: "Copy network configuration files"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by Jim_Lawrence on 2014-02-01
The Ubuntu network configuration GUI sets up my network perfectly, with no help from me other than to share my local ethernet connection (internet sharing). I would like to copy the files that comprise this setup in order to set up a console-only machine. Can someone tell me which files I need to copy over? Thanks.

---

### Post by steeldriver on 2014-02-01
Hello and welcome to the forums

The GUI applet in a standard Ubuntu desktop installation is a front end for the network-manager service, and saves its configuration in /etc/NetworkManager/NetworkManager.conf (with individual connection information usually saved in the /etc/NetworkManager/system-connections/ directory)

However, most true console-only (server) setups don't use network-manager at all, they use a separate networking service configured via the /etc/network/interfaces file - copying the files won't help in that case

---

### Post by Jim_Lawrence on 2014-02-01
OK, thanks. I am trying to enable a simple network where one wired connection is connected to the internet and firewalled, and the other is a connection to a local network, and shares the internet from the first ethernet connection. Ubuntu does it easily with the GUI, but I have little idea how to do it from the command line, or which files to edit.

---

