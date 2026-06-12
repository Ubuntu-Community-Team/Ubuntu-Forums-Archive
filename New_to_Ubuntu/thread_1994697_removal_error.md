---
title: "removal error"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-06-03
trying to remove virtual box -i tried to update to new version. now cant remove it using spm get this error message

E: virtualbox-4.1: subprocess installed pre-removal script returned error exit status 1

any ideas
tks

---

### Post by rburkartjo on 2012-06-03
and got this reply when i tried to remove using the software center


installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 267289 files and directories currently installed.)
Removing virtualbox-4.1 ...
dpkg: error processing virtualbox-4.1 (--remove):
 subprocess installed pre-removal script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 virtualbox-4.1
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rburkartjo on 2012-06-03
or if someone could suggest a command to remove. had this problem a few weeks ago when tried to update orcale but solved it by just removing virtual box with spm of course now that wont work.

---

### Post by mapes12 on 2012-06-03
Google search **uninstall virtualbox ubuntu** brought back loads of stuff about how to uninstall.

---

### Post by rburkartjo on 2012-06-03
searches didnt offer any insight and didnt work here is how i fixed

first empty cache
then opened spm and tried to uninstall oracle
still got error message
somehow virtual box would not shutdown  so opened system monitor and forced killed virtual box two processes were running. 
was able to remove and then reinstall newest version
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

working fine now never had a problem like this before

---

