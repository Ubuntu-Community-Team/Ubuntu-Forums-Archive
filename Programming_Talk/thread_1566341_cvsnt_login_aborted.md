---
title: "cvsnt: login aborted"
date: 2010-09-02
forum: Programming Talk
---

### Post by jburger on 2010-09-02
Dear ubuntu forum,

I have setup a cvsnt server on my ubuntu system to be able to access cvs via eclipse
but i got some problems configuring the pserver.

Currently i am trying to login via the shell to test my pserver login and i get the 
message [login aborted] CVSLock 2.2 Ready.

There is no additional error text. I have also searched in the /var/log files for additional error infomation but everything looks fine.

Can anyone help me?

I have configured the /etc/cvsnt/PServer file:
- set repository path name, 
- default = public = online = 1, 
- encryption=compressionlevel=0, 
- no pem files, 
- LockServer=localhost:2401 
- LockServerLocal=0

/etc/inetd.conf:
cvspserver stream tcp nowait /usr/bin/cvs -f --allow-root=CVSROOT-path authserver   

HINT: for CVSROOT-path i use /home/csdb/cvs my cvs root directory.

restarted the cvsnt server.

Configured the currentuser (csdb) as admin.
Add cvs passwd for current user. 
Add user to CVSROOT/admin file.

I use the following login command:
cvs -d : pserver:csdb@localhost:/CVSROOT-path login 
cvs password:
cvs [login aborted] CVSLock 2.2 Ready

If I open a telnet connection to cvs It seems that a connection can be opened:
telnet localhost 2401
Trying ::1...
Traying 127.0.0.1...
Connecting to localhost.
Escape character is '^['
CVSLock ready 2.2 

If I try to open a eclipse connection I get the following error message:
Could not connect to host: Connection refused.

Any hint would be helpful.

best regards

---

