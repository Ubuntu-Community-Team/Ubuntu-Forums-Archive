---
title: "ubuntu partition"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by Krabun on 2013-07-11
I installed Ubuntu 12.04 in a dual boot config with windows 7 on the Windows D-partition. When I log in to Ubuntu I can see every partition except that D-partition. On that partition there are also other files.

---

### Post by oldfred on 2013-07-11
Is this a wubi install?

       [URL="http://www.psychocats.net/ubuntu/wubi"]http://www.psychocats.net/ubuntu/wubi
[/URL]
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

IF wubi, then in Nautilus file explorer you should see /host as an option which is the host file system used. You have an install inside a NTFS partition.

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    


[URL="http://www.psychocats.net/ubuntu/wubi"]
[/URL]

---

### Post by Krabun on 2013-07-11
Thanks!

---

