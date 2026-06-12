---
title: "Samba sharing"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-05-26
I am trying to set up a home dc/file/print server.  I have it set up where my windows computers can see the shares, but when prompted i can only login as guest(it is grayed out, so i cannot specify another username).  i will eventually have this set up as a dc so it will be already authenticated for file shares, but right now how can i have it to where you have to specify a username and password when trying to log into the share?

---

### Post by mapes12 on 2008-05-26
I couldn't get sharing to work at all across my home LAN therefore I gave up on Samba network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

[http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh](http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh)

:guitar:

---

### Post by Happy_Man on 2008-05-26
For Samba, I especially like Stormbringer's howto:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Guaranteed to work with XP and Vista, and a cinch to set up. 

Hope this helps!

---

