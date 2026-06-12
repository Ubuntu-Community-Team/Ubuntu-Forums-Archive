---
title: "[SOLVED] Update Manager hangup caused error."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-10-26
I ran update manager today and half way threw it hung.  I had to do a hard reset to get the computer running again.  When I tried to rerun update manager I got the dreaded:
> dpkg --configure -a error.  I went into terminal and ran dpkg --configure -a.  I immediatly got the following error message:
> terminator@terminator-desktop:~$ sudo dpkg --configure -a
[sudo] password for terminator: 
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

What do I need to do to get rid of this error message?

---

### Post by bumanie on 2008-10-26
You need to run the command as root > sudo dpkg --configure -a That should work.

---

### Post by ajgreeny on 2008-10-26
I note you did do it as root with sudo.  Do you know which package caused the problem in the first place?  If not open synaptic and have a look in the system tray of the window for any noted broken packages, and if there are any go to **Edit->Fix broken packages**.  That may help, but if not I can't help more, I'm afraid.

---

### Post by handydan918 on 2008-10-26
[Here is a pretty good guide]("http://www.mepislovers.org/forums/showthread.php?t=10870") on using apt and dpkg to manipulate packages. It is not written for Ubu, but for a more standard Debian based distro, so sudo is not invoke in the guide. Just remember to prepend any commands with sudo, and it should work fine.

---

