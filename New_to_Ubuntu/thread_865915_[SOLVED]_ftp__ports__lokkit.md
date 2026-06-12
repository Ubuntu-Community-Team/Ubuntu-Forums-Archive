---
title: "[SOLVED] ftp / ports / lokkit"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by kesstephen on 2008-07-21
I am running 7.10 as a client machine and trying to connect to a server using FTP.
I have LOKKIT installed with High security.
I am using FILEZILLA having already tried gftp.
Filezilla says it has connected to the server and then says:
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE I
Response:	200 Type set to I.
Command:	PASV
Response:	227 Entering Passive Mode (nnn,nn,nn,nn,nn,nn).
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing

When I try the Network Configuration Wizard test in Filezilla I get the following:
Checking for correct external IP address
IP 192.168.1.100 bjc-bgi-b-baa
Response: 510 Mismatch. Your IP is nn.nnn.nn.nnn, ih-bbe-gj-cce
Wrong external IP address
Connection closed

What am I doing wrong?
(Please note the 'nn.nn' etc are not the actual returns but I thought this may be sensitive information.  I am probably wrong).

Thanks for any help in advance.

---

### Post by ELGL on 2008-07-21
I'm not exactly sure yet what is going wrong, but it could have multiple causes.

Is the server you're trying to connect to on the same network or are you connecting over the internet?

Here are some things you could try or look in to,

You're trying to connect using passive mode, while the server may only accept active mode. To change to active mode, go to Edit -> Settings -> Connection -> Transfer mode and click active.

192.168.1.100 is your internal address, to find your external address you can go to [http://www.whatsmyip.org/]("http://www.whatsmyip.org/")
Or go to Settings -> Connection -> Active mode, under Active Mode IP, click, Get External Ip address from the following IP.

It could be a firewall/router issue,
If you are using a router, it could be blocking the return traffic from the server or lokkit could be blocking that traffic.

---

### Post by dracayr on 2008-07-21
this belongs in the networking forum. But, as far as I know, before issueing a PASV command, you have to have two ports N and N+1 open. see also [http://www.slacksite.com/other/ftp.html#passive](http://www.slacksite.com/other/ftp.html#passive)

dracayr

---

### Post by kesstephen on 2008-07-22
when I changed the setting to Active from Passive it connected straightaway.

I agree that it would probably be a network issue for someone a bit more experienced but from the solution hopefully you can see why the post was placed in Absolute Beginner.

thanks again.

---

