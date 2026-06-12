---
title: "Low Disk Space"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by rajivt on 2013-02-24
I have an 8-GB USB with plenty of disk space. I tried to install MP3 and received the following message. My Ubuntu version is 12.10. Please help.

ubuntu@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: error: failed to write status database record about 'python3-aptdaemon.pkcompat' to '/var/lib/dpkg/status': No space left on device
ubuntu@ubuntu:~$

---

### Post by sanderj on 2013-02-24
what is the output of


```
df -h

```
Post it here

---

