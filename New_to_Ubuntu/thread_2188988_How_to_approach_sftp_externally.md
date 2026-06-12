---
title: "How to approach sftp externally?"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by wolfenstein538 on 2013-11-20
Hello,

I have setup a sftp server through ssh and enabled keyauthentication and chrooted the users. Everything works fine internally. I can use FileZilla to upload and download items, but I want to access the server externally. The server is located at work and I want to access it at home. I don't want to use VPN or VNC , just via the browser or Filezilla. Is this feasible?

Many thanks in advance,

---

### Post by Lars Noodén on 2013-11-20
It is possible.  

If the machine itself has an external IP address, you should be able to access it directly, if the network at work does not block incoming SSH. If it does, you'll have to arrange with the network administrator for access to be opened for that port for that machine. 

If the machine does not have an external IP address, you'll either have to use a jumphost/gateway and log in via that first or else have a port on your external router forwarded to port 22 on your machine.  For that latter option you'll have to work out something with your network administrator.

---

### Post by wolfenstein538 on 2013-11-20
Thanks, I will give it a shot.

---

