---
title: "Sudo boot commands"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by rxtx on 2008-06-30
Hi there- simple one.

What is the easiest way of running a command that requires root privileges upon boot?

I know i can edit /etc/hdparm.conf or by adding the command through sessions dialog, but how would I avoid the sudo portion of the deal? By adding the command I wish to execute to sudoers?

Cheers.

---

### Post by sujoy on 2008-06-30
add the commands to rc.local

---

### Post by rxtx on 2008-06-30
Thanks for the fast response. Does this script run with root level privileges or do I still need to prefix it with sudo?

---

### Post by geirha on 2008-06-30
It is run as root, so no need to use sudo, unless you want to use sudo to run it as a less privileged user.

---

### Post by rxtx on 2008-06-30
Thanks guys. That solves the problem with noip2 not running on boot.

I never got any joy with [this]("http://ubuntuforums.org/showthread.php?t=803847") thread though, which is a similar idea. I know that this needs to run on gnome startup via .gnomerc rather than at boot time, but for some reason, it wont stay active :(

---

