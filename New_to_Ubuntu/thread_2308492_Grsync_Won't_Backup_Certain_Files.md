---
title: "Grsync Won't Backup Certain Files"
date: 2016-01-03
forum: New to Ubuntu
---

### Post by quaesitor2 on 2016-01-03
There are certain files grsync won't backup. I get this error message when I try to backup the file that grsync keeps missing:

ssh: Could not resolve hostname file: Name or service not known 
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code 255) at io.c(226) [Receiver=3.1.1]
Rsync process exit status: 255

---

### Post by nerdtron on 2016-01-03
```
ssh: Could not resolve hostname file: Name or service not known 
```

Are you using hostnames instead of IP addresses? This errors show it can't find the host that rsync is connecting to.

---

### Post by quaesitor2 on 2016-01-03
> **nerdtron said:**
> 

Are you using hostnames instead of IP addresses? This errors show it can't find the host that rsync is connecting to.

I'm not using either. The files I am trying to backup are on a hd inside of a vantec enclosure. The hard drive suffered bsod. I am trying to backup the hd before I commence with repairs via hirens boot cd.

---

