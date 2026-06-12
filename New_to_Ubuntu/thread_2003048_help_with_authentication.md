---
title: "help with authentication"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by wlraider70 on 2012-06-13
I maybe going at this wrong so please let me know if I am way off base.


I have a small office network it has a dozen or so windows PCs. I have a Ubuntu server running samba. I have multiple folders being shared some that I want public and others that I want only some to have access to.

The issues seems to be in the authentication. Unless the share is set to public the users fail to log, even the SU. (see screen shot)

I was going to set samba as DC, but may of these PCs are home versions.

Can I use LDAP to authenticate the users individually? Can I use samba as a DC to do that? Is there a simple reason that my users wont work?

---

### Post by wlraider70 on 2012-06-13
It looks like my specific issues was the wrong security setting in samba. 

However I would still like to know if I can or should use one of the other authentication methods. Is there a way to samba as a DC without the full domain login in windows.

---

