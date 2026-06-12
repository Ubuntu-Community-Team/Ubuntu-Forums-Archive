---
title: "How to view Ubuntu screen remotely from a Mac"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by swarup on 2012-10-18
We have a home office with all computers connected via a router. What do I need to do to enable remote desktop with the IMac (Mountain Lion OSX 10.8.2) viewing the Ubuntu (9.04 Jaunty) screen? (The Ubuntu distrib is old, but that is what I am using right now.)

Thank you!

---

### Post by stmiller on 2012-10-18
First, Enable Remote Desktop in Ubuntu

( [http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/](http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/) )


The on the Mac, open Safari. In the Safari URL bar put

vnc://ipaddress

For example, if the ip address of the Ubuntu machine is 192.168.1.12, put

vnc://192.168.1.12

---

### Post by Gnawnsense on 2012-10-18
My reply might be useless.. but I always had issues viewing remotely from Windows => Mac using built in utilities. Easiest way I found was TeamViewer. Completely free download, and excellent for remote access, especially since it works on all 3 operating systems.

I'd definitely give that a try if all else fails.

---

### Post by QwUo173Hy on 2013-02-22
> **stmiller said:**
> First, Enable Remote Desktop in Ubuntu

( [http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/](http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/) )


The on the Mac, open Safari. In the Safari URL bar put

vnc://ipaddress

For example, if the ip address of the Ubuntu machine is 192.168.1.12, put

vnc://192.168.1.12

Worked a treat for me, thank you. I'm running Ubuntu 12.04.2 and remotely viewing from Mountain Lion on a MBP.

---

