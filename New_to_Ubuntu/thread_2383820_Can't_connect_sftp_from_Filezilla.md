---
title: "Can't connect sftp from Filezilla"
date: 2018-01-30
forum: New to Ubuntu
---

### Post by tomo1026 on 2018-01-30
I'm very new to Ubuntu.

I set up Ubuntu on AWS and tried to connect from Filezilla to the sftp server but I got the error message: Connection refused
I can connect to the server with ssh terminal using pem file.

[Server]
 AWS EC2 Ubuntu 16.04.3
Inbound port 22 is opened in security group
SSHD: OpenSSH_7.2p2 Ubuntu-4ubuntu2.4, OpenSSL 1.0.2g  1 Mar 2016

[Client]
MacOSX 10.12.6
Filezilla 3.24.1

I appreciate any helps.

---

### Post by TheFu on 2018-01-30
I don't know anything about AWS.  Do they alter the normal config of ssh/sftp to prevent sftp from automatically being available?  Are there specific userids that are allowed/blocked from using sftp?  For example, root is disabled on default Ubuntu Server installs, so if root is being used .... 

The server-side config files are in /etc/ssh/

---

