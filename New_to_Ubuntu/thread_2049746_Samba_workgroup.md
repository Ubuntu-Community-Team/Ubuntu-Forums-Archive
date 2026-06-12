---
title: "Samba workgroup"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by wiradog on 2012-08-29
Hi Guys,

Have been following the official 'How to' for a small office config for Samba. I have changed the workgroup in the smb.conf, but as shown in the following it is still showing 'Workgroup' for the server ubuntu-mikenas.

How can I change this, and is this likely to be the problem of client 'Julia' not being able to connect to the server?



#-o

---

### Post by steeldriver on 2012-08-29
Did you reboot - or just restart the smbd service?

When I changed the workgroup on my mythbuntu box recently I found that it needed a reboot to propagate the name change - service restart didn't do it

---

### Post by wiradog on 2012-08-29
Thanks steeldriver, spot on.

---

