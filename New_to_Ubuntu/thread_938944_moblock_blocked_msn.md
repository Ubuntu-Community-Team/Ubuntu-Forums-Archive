---
title: "moblock blocked msn"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Jackie999 on 2008-10-05
I've just installed moblock 
```
moblock (0.9~rc2-21+hardy)
moblock-control (1.0-1+hardy)
moblock-nfq (0.9~rc2-17~hardy)
```And my kopete / msn won't connect. I'm getting:

"There was an error while connecting to the MSN server.
Error message:
Connection actively refused"

Posts say that the port 1863 needed to be whitelisted so I changed my /etc/moblock/moblock.conf to:

```
# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT="http https 1863"
```Then did a ```
sudo moblock-control restart
```I originally had the GUI installed but have since removed it since one post said changed to the moblock.conf would be superseded by the GUI.

It still doesn't connect...what am I doing wrong?

---

### Post by jre on 2008-10-06
Set
LOG_IPTABLES="LOG --log-level info"
and restart moblock.
Then do a "sudo tail -f /var/log/syslog". There you will see live blocked packets (and much more). Find the destination port related to your blocked msn packets and add it to WHITE_TCP_OUT.


General:
You can use mobloquer (GUI) and moblock. There's no point against that.
You will find all your changes to /etc/moblock/moblock.conf in /etc/default/moblock.
In the latter file mobloquer and debconf (the configuration program on package installation/updates) save all changes. It's recommended to add your custom changes there, too, because this eases updates.
Values in /etc/default/moblock overwrite values in /etc/moblock/moblock.conf.

---

