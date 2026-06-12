---
title: "FTP login timeout value"
date: 2019-02-17
forum: New to Ubuntu
---

### Post by pd1831 on 2019-02-17
Hello All,

I am trying to run a ftp command from ubuntu 16. Connection to the server is getting established  and i can also download files using (mget) but my session getting timeout after 60 seconds . Is there any way, i can increase the timeout value within my ftp program . I don't have any admin access to the FTP server. 

 Thanks in advance. 

Regards
PD

---

### Post by col48 on 2019-02-18
No doubt others will be able to give a definitive answer, but I suspect without admin access to the server the answer is no.

I'm no expert, but a number of sources point out that ftp is not a secure way of transferring files.  For instance, in this forum...

[https://ubuntuforums.org/showthread.php?t=2234950](https://ubuntuforums.org/showthread.php?t=2234950)

---

### Post by pd1831 on 2019-02-18
Thanks for the reply and i agree FTP is not secure but ftp is the only way to connect our customer servers. I can access the content but the connection gets timed out within 60 seconds.

---

### Post by majcherek-maciek on 2019-02-26
Some UTM's/NGFW will drop ftp connections [as mentioned above security issues due to high risk of data leak ], it may be no server , client issue but firewall.

---

