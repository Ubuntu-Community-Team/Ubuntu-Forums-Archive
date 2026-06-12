---
title: "thin client fail to login to Ubuntu LTSP server, the client requests to disconnect"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by dvks on 2014-02-24
I installed LTSP thin client server on UBUNTU 12.04.4, but can't get a client to login to the server.
When I power-on the client it manage to go all the way to the login screen.
I enter the user name and password
I get a message: "verifying password, please wait" , but after 2-3 seconds it pops up again the login screen.


The /var/log/auth.log file on the UBUNTU LTSP server have the following line:
[B][COLOR=black][FONT=Courier New]Feb 24 11:38:40 ksnas61 sshd[5863]: Accepted keyboard-interactive/pam for dov1 from 192.168.0.20 port 50204 ssh2
Feb 24 11:38:40 ksnas61 sshd[5863]: pam_unix(sshd:session): session opened for user dov1 by (uid=0)
Feb 24 11:38:44 ksnas61 sshd[6014]: Received disconnect from 192.168.0.20: 11: disconnected by user
Feb 24 11:38:44 ksnas61 sshd[5863]: pam_unix(sshd:session): session closed for user dov1

It suggests that the client disconnect itself before or after the authentication, any idea how to resolve it, I have wasted already a whole day and searched for solutions, nothing seams to work.
I appreciate any help
Thanks[/FONT][/COLOR][/B]

---

