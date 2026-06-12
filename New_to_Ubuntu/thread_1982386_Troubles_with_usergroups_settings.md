---
title: "Troubles with user/groups settings"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by hfa2010 on 2012-05-18
Hi guys, i'm experiencing some problem with my Ubuntu 12.04. The issue is that, yesterday when i was using VirtualBox i had to add my user to the vboxusers group due the usb sub-sytem wasn't acessible. Okay, so i run the command: sudo adduser henrique vboxusers; hoping that with it my user would too be part of the Virtual Box group. But today after i rebooted my system, i ain't able to use sudo commands. I already tried use the recuperation mode, but i receive error about code 1. Could someone help me?! :lolflag:
_______________________________________________________________________________________________________________________
I fixed it... :p The problem is that Canonical changed the admin privileges to sudo and i didn't knew that... So with the Debian that i have in dual boot here i changed the /etc/group and solved the problem.

---

