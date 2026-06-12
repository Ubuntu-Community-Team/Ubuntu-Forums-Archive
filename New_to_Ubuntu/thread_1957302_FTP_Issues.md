---
title: "FTP Issues"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by dolphin194 on 2012-04-12
I have a server running Ubuntu Server 10.04, and I installed vsftpd on it. Now, I am able to connect to it with ***only one program*** which is for ***windows only*** (bleh) The program is WinSCP.

I cannot connect to the server with any other application, such as the *Ubuntu connect to server*, *Mac connect to server*, *FileZilla*, *Web Browser*, or anything that is not *WinSCP*.

I need to be able to connect with other applications because I mainly use a Mac to manage the server. I don't want to install wine on my Mac.

---

### Post by dolphin194 on 2012-04-12
I figured out that if I set my FTP client to Active Mode, I can connect. But if I try to connect with passive mode, it times out on the *list* command.

I want to use passive. How do I fix my server to get the passive to work?

---

### Post by Manyrootsofallevil on 2012-04-12
> **dolphin194 said:**
> I figured out that if I set my FTP client to Active Mode, I can connect. But if I try to connect with passive mode, it times out on the *list* command.

I want to use passive. How do I fix my server to get the passive to work?

it's probably an iptables issue

have a look at this [http://www.cyberciti.biz/faq/iptables-passive-ftp-is-not-working/](http://www.cyberciti.biz/faq/iptables-passive-ftp-is-not-working/)

---

