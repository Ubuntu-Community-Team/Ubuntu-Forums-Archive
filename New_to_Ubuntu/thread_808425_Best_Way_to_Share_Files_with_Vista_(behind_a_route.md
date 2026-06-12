---
title: "Best Way to Share Files with Vista (behind a router)?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by zggame on 2008-05-26
I have several PCs (2 vista, 1 XP and 1 linux boxes xubuntu 8.0.4) in my home with a router to cable modem.  The linux box does not read the I want some simple file sharing between them.  Mostly, I only need to communication between the linux and one windows machine.  The file share is not very heavy, occasionally only.  

I have a few options, I am not sure which will be better. 

1.  Use this vista/linux file share trick and set to access vista.

2.  Set up the ftp server in one or more machines.  I can set one machine with both write/read or more machines with only read.  

3.  Set up the sftp server in one or more machines. 

In case of ftp/sftp service, should I run the server all the time or open it only when using.  (I do not need the sharing all the time.  Maybe a couple of times every week. )

I only need the home network, I do not want outside to access them. One more complication, two of them are laptop with 802.11 with wpa-spk.  I am not sure whether that will affect.

---

### Post by mapes12 on 2008-05-26
I couldn't get sharing to work at all across my home LAN therefore I gave up on Samba network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

[http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh](http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh)

---

