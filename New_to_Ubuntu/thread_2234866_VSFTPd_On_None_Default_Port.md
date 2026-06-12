---
title: "VSFTPd On None Default Port"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by thedude76 on 2014-07-17
Hi,

I've configured vsftpd to listen on a none default port (e.g. listen_port=2021), however when I do this and restart the vsftpd service, client FTP connections hang waiting for the user password (tested with both FileZilla and Ubuntu Desktop FTP command line client).

If I change the port back to the default (21), all is fine! :(

Any ideas?
Is there a know issue with changing the vsftpd listening port, or am I missing some config options?

Thanks,
Mark

---

### Post by ubudog on 2014-07-21
What kind of firewall is setup on this box?

---

