---
title: "Connecting in pidgin through pptp vpn"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Duffadash on 2008-10-29
First the problem; when connected through a pptp vpn connection, I cannot seem to connect to ANY service in pidgin; Neither MSN, nor google talk, yahoo, aim, icq or anything else for the matter...
Do anyone know what could be the problem? Or better yet, how to fix it?

---

### Post by mandragor on 2009-02-08
This reply is probably too late for the original poster, but hopefully
this will be useful to someone..
The solution seems to be to lower the MTU of your connecting. In my case,
using Kvpnc, I lowered it from 1492 to 1400.

I've also seen some recommend setting your account to use the "http 
method", but for me it wasn't necessary or successful.

---

