---
title: "sssd.conf file missing"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by rwyeth on 2013-01-26
I'm new to linux and decided to play around with building a server to learn more.  I have been following the following guide: [http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/4/](http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/4/)
Everything has been going well. I have a functioning Kerberos Realm, and DNS and DHCP are working great. But, I installed SSSD and I have no /etc/sssd/sssd.conf file. I noticed when it was installing it showed

Setting up sssd (1.8.2-0ubuntu1) …
start: Job failed to start
invoke-rc.d: initscript sssd, action “start” failed.
… because /etc/sssd/sssd.conf is not available yet
Setting up libpam-sss (1.8.2-0ubuntu1) …

Any thoughts as to why I don't have an /etc/sssd/sssd.conf file?  I did find a /etc/init/sssd.conf file.  But, that doesn't appear to be what I need.  I'm running Ubuntu 12.04 Server.

---

### Post by rwyeth on 2013-01-26
It might also be interesting to note that the /etc/sssd/sssd.conf file is referenced in the /etc/init/sssd.conf file.

---

