---
title: "Adding DNS server problem (maybe)"
date: 2016-02-11
forum: New to Ubuntu
---

### Post by sonicwind on 2016-02-11
I have Ubuntu Desktop 14.04 LTS. I use my system on both wireless and sometimes wired (Ubuntu is on external HD).

I don't know if I have a problem or not. I wanted to add some extra DNS servers to my system. I used these directions:

[B]Copy and paste: gksudo gedit /etc/resolvconf/resolv.conf.d/tail

Add these lines to the bottom of the text file (however my file was empty when I opened it, which I read was probable):

nameserver 8.8.8.8                 [/B](these are both Google DNS servers)[B]
nameserver 8.8.4.4

Save modified file and close it. Then in terminal: sudo resolvconf -u

Then check it with: more /etc/resolv.conf[/B]

I did that. Now I read the proper way to do this is via network-indicator | Edit Connections... | <name> | Edit... | IPv4 Settings | DNS servers

My question is: Am I going to have problems? I can still get to websites but maybe the changes take effect on reboot.

Can I change it back and do it this other way? How would I change it back? Open it back up and blank it out and save? The file was originally blank and now this is what it changed to:

[B]nameserver 127.0.1.1
search wowway.com
nameserver 8.8.8.8
nameserver 8.8.4.4[/B]

I should add that wowway.com is my ISP.

---

### Post by newbie-user on 2016-02-11
Adding extra DNS servers just means that if you can't reach one DNS server, your computer will try the next.

---

### Post by sonicwind on 2016-02-11
My question is that I apparently did it the wrong way and whether I should undo it somehow and do it the other way.

---

### Post by SeijiSensei on 2016-02-11
Put those nameserver directives in /etc/resolvconf/resolv.conf.d/head rather than tail.  The servers will be placed ahead of the default, 127.0.1.1.

---

### Post by ajgreeny on 2016-02-11
You do not need to reboot, simply restart networking, easiest done from the network icon in the panel; Disable networking ->Enable networking.

---

### Post by sonicwind on 2016-02-11
OK I didn't make any changes but I finally got around to restarting things and everything still works with wireless. I think I'm just going to leave it be.

Thank you newbieuser, SeijiSensei and ajgreeny for replying. I'll mark this solved.

---

