---
title: "shorewall blocking vsftpd ssl connection"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by duceduc on 2012-02-14
I had vsftpd setup on 10.4 server edition and have upgraded to a faster pc with 11.10 server edition installed. I install vsftpd and am able to connect using non ssl. However, when I try to connect via ssl connection, I cannot log in. It seem shorewall is blocking the connection. If I disable it, I can log in.

I do not know where to look for in shorewall. I have added, port 20,21 to the shorewall rule files. I am using filezilla to connect.

On my 10.4 server, I didn't have any issue connected to ssl. I am stumped.

---

### Post by duceduc on 2012-02-15
ok, I got it fix. I need to open my pasv ports in shorewall rules file.

> ACCEPT:ULOG net fw tcp 21,55535:65535

---

