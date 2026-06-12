---
title: "Terminal server client probs"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by vidur on 2008-11-18
I'm trying to connect to my PC at work (Windows XP) using terminal server client in Ubuntu 8.04.

The window shows up...it tries to login when i connect but I get an error
BadAtom (invalid atom parameter)

Any idea ...whats happening?

---

### Post by superprash2003 on 2008-11-18
another way out is using vnc.. easy to configure..

---

### Post by cmnorton on 2008-11-18
I've seen this error, and have forgotten what causes it. However, here are two things to check.

1) Make sure you are specifying rdp://hostname when you enter the host, and that hostname is resolvable in dns or /etc/hosts.

2) Make sure your remote active desktop "stuff" is enabled on the Windows side. You right click on My Computer --> Manage --> Services

I've attached what that looks like to this post. 

Offhand, I cannot remember which of these is the magic remote desktop server that comes with XP (and probably Vista). You'll have to fiddle.

Good luck.

---

### Post by vidur on 2008-11-22
vnc doesnt work out !

Any solutions guys ?  Whats this BadAtom error?

---

### Post by superprash2003 on 2008-11-22
why not just use logmein [www.logmein.com](www.logmein.com) to remote control windows xp

---

### Post by cmnorton on 2008-11-22
Please post your connect line:

It should look something like rdp://xp-host

where xp-host is the real name of your Windows xp host.

Can you use Windows remote desktop to log into this system? Try that. If you cannot do that.

As to this error, you'll need to Google for it and also make use of the Launchpad resources (Ubuntu Launchpad).

As to bad atom, where are you getting this?

---

