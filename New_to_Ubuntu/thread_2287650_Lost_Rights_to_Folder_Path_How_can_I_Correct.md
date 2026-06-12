---
title: "Lost Rights to Folder Path How can I Correct"
date: 2015-07-21
forum: New to Ubuntu
---

### Post by robertzito on 2015-07-21
This past Saturday I installed snmp mib downloader, everything runs fine when I do an SNMPGET, but I started to receive a permission denied for "/usr/share/snmp/mibs/SNMPv2-TC-v1.mib: Permission denied". One of the main reasons why I switched to Linux was the ease to do SNMP so I know this error is new. Does anyone know how to correct this? do I just grant rights to the folder to me user?

---

### Post by dino99 on 2015-07-21
here are some links about it; maybe they will help:
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-an-snmp-daemon-and-client-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-an-snmp-daemon-and-client-on-ubuntu-14-04)
[http://www.ubuntugeek.com/how-to-configure-snmpv3-on-ubuntu-14-04-server.html](http://www.ubuntugeek.com/how-to-configure-snmpv3-on-ubuntu-14-04-server.html)
[https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bugs?orderby=-date_last_updated&start=0](https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bugs?orderby=-date_last_updated&start=0)

---

### Post by robertzito on 2015-07-21
Not sure why the problem started after I installed mib-downloader but I changed permission on the mib file and it is fine now.

---

### Post by oldos2er on 2015-07-21
Could you please mark the thread as 'Solved' under Thread Tools at the top of the page? It will help others who might be having the same problem.

---

