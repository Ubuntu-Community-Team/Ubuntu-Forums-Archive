---
title: "Samba Problem???"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by alpdo on 2008-05-12
i have ubuntu as file server i put in my programs made in foxpro 2.6 on a shared folder on my ubuntu box..

first i dit this on a command prompt on win98:

c:\foxpro\foxr -t -cmy.cfg program.app

this runs ok

but when i do this:


e: (i changed drive to a mapped drive e: on my ubuntu box)
then
run the same command

c:\foxpro\foxr -t -cmy.cfg program.app

when i press enter it give me the general failure reading drive...


question:
 is this a samba problem???? how can i fix this???

---

### Post by alpdo on 2008-05-13
i forgot to mention that the first time you do this it goes ok... but on the second it gives the error...

---

### Post by shinobitux on 2008-05-13
Ok, I'm not familiar with foxpro so bear with me.

I'm pretty confident this isn't a samba issue.

When you type the complete path from the "E:\>" prompt you are resolving the command relative to the C: drive since you enter the complete path.

Two things to try first:
- Do you have another windows computer? If so create a share and do the same thing you're doing with the Ubuntu server with it. You should encounter the same error.
- I'm more familiar with Ubuntu than windows but "c:\foxpro\foxr -t -cmy.cfg program.app" looks like you're trying to include cmy.cfg using the existing directory or environment path. Can you specify "-C:\path\to\cmy.cfg" for the config file?

"c:\foxpro\foxr -t -c:\path\to\cmy.cfg program.app"

I hope this helps.

---

### Post by alpdo on 2008-05-22
i didn't work... i also tried changing drive ... :(

---

### Post by mapes12 on 2008-05-23
I couldn't get sharing to work at all across my home LAN therefore I gave up on network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

---

