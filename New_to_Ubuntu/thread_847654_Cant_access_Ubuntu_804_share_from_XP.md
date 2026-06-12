---
title: "Cant access Ubuntu 804 share from XP"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Joe325 on 2008-07-02
We have setup an Ubuntu 8 server at work just to fill in times of boredom. There are 2 of us who access it. The problem is that when my collegue enters \\linuxbox\share\ in the RUN command of a win XP laptop, he connects successfully after entering his username and password. When I try the same command with my credentials, I get the resource is not available.
Im guessing the smb.conf file is fine - as he connects. Allowed users are the both of us - according to the file.
If i create another share thru a webmin GUI, and try to access the new folder -adding myself to the right groups, i still cant access. Yet locally on the server, i can read/write without issues.
I can connect to it for CUPS admin & obviously the webmin GUI :10000. I have run smbpasswd -a username and still nothing.
The funny thing is: my collegue didnt do the smbpasswd cmd and he is happily logged in.

Any ideas?

Any ideas?

---

### Post by superprash2003 on 2008-07-02
is there something blocking it?? some firewall etc?? usually restarting the pc solves the problem

---

### Post by Joe325 on 2008-07-02
Dam Windows !!!  It worked! Restarted the laptop and the share accepted my credentials. Thanks:)

---

