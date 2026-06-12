---
title: "Difference between dav/davs"
date: 2017-09-04
forum: New to Ubuntu
---

### Post by sirajuddin97 on 2017-09-04
Hi, I'm using Ubuntu 16.04 and recently found out that I can use **dav://server.ip** and **davs://server.ip** if I want to connect to my WebDAV server. They both work fine and there is no issue at all, I'm just wondering what the difference is? Does the *s* in *davs* stand for secure or something like that? Just like FTP and SFTP? I don't know, I'm just guessing. 

Thanks in advance.

---

### Post by SeijiSensei on 2017-09-04
Yes, DAVS connections are encrypted.

---

### Post by sirajuddin97 on 2017-09-04
> **SeijiSensei said:**
> Yes, DAVS connections are encrypted.

Should I use DAV or DAVS? Is it unsafe to use DAV because it's not encrypted? And is there any difference in speed?

---

### Post by SeijiSensei on 2017-09-05
I doubt you would see any perceptible difference in speed.

DAV usually requires that a username and password be sent to the remote site.  Without encryption these passwords can be sniffed, though in practice that isn't too likely.  Once, a couple of decades back, I was using telnet to connect to a machine I had located in a server farm.  Someone else on the provider's network had installed a password sniffer, grabbed the password for one of my accounts, and hacked my server.  These days I use SSH and OpenVPN tunnels to connect to remote machines securely of course.

---

### Post by sirajuddin97 on 2017-09-06
> **SeijiSensei said:**
> I doubt you would see any perceptible difference in speed.

DAV usually requires that a username and password be sent to the remote site.  Without encryption these passwords can be sniffed, though in practice that isn't too likely.  Once, a couple of decades back, I was using telnet to connect to a machine I had located in a server farm.  Someone else on the provider's network had installed a password sniffer, grabbed the password for one of my accounts, and hacked my server.  These days I use SSH and OpenVPN tunnels to connect to remote machines securely of course.

Makes sense. Thanks for your reply man.

---

