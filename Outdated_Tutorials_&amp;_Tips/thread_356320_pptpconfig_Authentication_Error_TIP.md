---
title: "pptpconfig Authentication Error *TIP*"
date: 2007-02-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Xtreme it on 2007-02-08
Credit to: myself and pptpconfig (see below)
Ubuntu Version: 6.06LTS 32bit.
Application: pptpconfig 20040809, from Ubuntu repository.
Support: used at your own risk, but I'll try to help.

**_Background:_**
I'm using pptpconfig for a long time now, but had a specific VPN connection that was unused for at least 5 months. When I tried to start it again I got Authentication Errors.

I was sure I had the correct user/password but I still got the authentication error. It got even more wird when I used a different account and the connection worked.

**_Problem:_**
I went through the pptp configuration files and all was ok, correct user/password values. Then when searching the net I came across an [howto configure pptpconfig by hand]("http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand") at sourceforge.
There they tell the user to add some lines to */etc/ppp/chap-secrets* file. And it made me think...

The problem was that, in the mean time, I changed the user password for that connection, both at the server, and obviously, at pptpconfig front-end. And pptpconfig was supposed to change the password in chap-secrets file. **Wrong!** it didn't. Every time the password is changed a new line is added to chap-secrets, **but the old one is not removed**.

**_Solution:_**
Just open the */etc/ppp/chap-secrets* file and remove the wrong password lines.

NOTE:
Don't know if this problem still persists in more recent versions. My pptpconfig version is 20040809, updated from Ubuntu repository.

---

### Post by 3vi1 on 2007-02-11
Excellent find!  Thanks for sharing.

---

