---
title: "Remote desktop login and viewer"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Zebadim on 2008-11-21
Dear All,

I have been trying to access a windows xp computer (at work) from my ubuntu machine at home (8.04). The windows machine uses ssh and I was advised to use putty. I found a linux version of putty and installed. Apparently I can connect to my work computer fine using putty but the problem is how can I view the desktop. I tried downloading Gnome RDP but no luck on putting it to service (newbie problem most probably)... Any help appreciated!

Thanks in advance
Zebadim

---

### Post by silverglade00 on 2008-11-21
You need to enable remote desktop on the windows computer or install a VNC server.

---

### Post by doas777 on 2008-11-21
vnc is probably your best bet. I strongly recommend you set it up to tunnel through a ssh connection. running vnc over the internet is not safe unencrypted

---

### Post by Zebadim on 2008-11-21
Thank you for your help!

I am able to connect to the windows computer putty in a windows machine and using the windows remote desktop viewer. It is this last step I have not been able to do yet in ubuntu.

Any additional advice?

Best
Zebadim

---

### Post by bodhi.zazen on 2008-11-21
If you have a ssh server on the Windows box, forward the port over the ssh connection.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by Zebadim on 2008-11-21
> **bodhi.zazen said:**
> If you have a ssh server on the Windows box, forward the port over the ssh connection.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Hi again,

Can I use TightVNC? Is it possible to do it without installing any additional software in the windows machine (work)?

Thanks in advance
Zebadim

---

### Post by bodhi.zazen on 2008-11-21
yes you can.

---

