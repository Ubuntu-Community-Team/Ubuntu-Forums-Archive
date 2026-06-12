---
title: "Can't get past login screen"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by durnurd on 2008-11-05
I've recently upgraded to 8.10.  Doing this made the printer on my computer inaccesable to other computers on the network.  I tried reinstalling CUPS and dealing with that, which then moved to changing SAMBA config, which then caused my computer to not show up on the network.

So I restart my computer.  I got to the login screen, but now as soon as I log in, it kicks me back out to the login screen.  This happens with any user and any session.  Switching to ttyX causes the same thing to happen:

Ubuntu 8.10 odin tty1

odin login:root
Password:

Ubuntu 8.10 odin tty1

odin login:

I've gone into recovery mode, and uninstalled CUPS and Samba completely to no avail, and I can't reinstall them because I don't have the packages downloaded.  I've gone through all the options on the recovery menu as well.

HELP!??!?

---

### Post by Cypher on 2008-11-05
Do you usually login as root or a regular user?

---

### Post by durnurd on 2008-11-05
I usually login as a normal user.  No username works when I try to log in from graphical prompt or ttyX

---

### Post by Cypher on 2008-11-05
Can you get back into recovery mode and then take a look at the files /var/log/auth.log and /var/log/messages which should contain information about your login attempts and see if there are any helpful messages there to help us figure out why you can't login..

---

### Post by durnurd on 2008-11-05
Looking at auth.log, I see several messages like:

gdm[xxxx]: pam_nologin(gdm:auth) cannot determine username

every time I try to log in


In messages, I also see:
kernel: [  xx.xxxxxxx] segfault at 0 ip 000074f37cead6c .... error 4 in pam_smbpass.so[xxxx+xxx]

---

### Post by durnurd on 2008-11-05
After looking up pam_smbpass.so segfauly, I found that this is a common error.  Fixed it with

apt-get remove libpam-smbpass

Now I just need to reinstall everything

---

### Post by durnurd on 2008-11-05
Alright, well, I've got CUPS and Ubuntu Desktop installed again.  Compiz doesn't work anymore, though.  The windows are undecorated, and none of the actions work (like window switching or cube rotation).

Additionally, I'm still trying to get CUPS to work.  I can access [http://localhost:631](http://localhost:631) but not [http://odin:631](http://odin:631) (to allow other computers on the network access to the printer).  How do I do this? (Should this be in another thread?)

---

