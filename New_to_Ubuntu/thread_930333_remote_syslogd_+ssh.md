---
title: "remote syslogd +ssh?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by iason on 2008-09-25
I am trying to find a good howto for setting up syslogd over ssh?  I haven't been able to search and find anything, can someone point me in the right direction?

---

### Post by paultag on 2008-09-25
am I wrong in assuming that it is already installed by default on Ubuntu? if you are looking to view files try

cat `syslogd-listfiles`

---

### Post by iason on 2008-09-25
hmm so by default syslogm clients communicate to the syslogd server through an ssh tunnel?  I just assumed it was not encrypted.

---

### Post by paultag on 2008-09-25
> **iason said:**
> hmm so by default syslogm clients communicate to the syslogd server through an ssh tunnel?  I just assumed it was not encrypted.

I don't think I understand the question.

Syslogd is a Daemon ( background process ) that enables processes to write to it. You can then view the files ( as a log )

You can view these over an ssh connection ( and yes, SSH is encrypted, unlike Telnet or other socket based connections ) 

you need to view the logs on the remote computer. If you can not do that in bash, be sure to forward the X11 connection as well. You might also want to compress it if you are doing that.

---

### Post by iason on 2008-09-26
well not exactly.  I am trying to setup two computers one being the syslog client, one being the server.  the client will send and store its logs (remotely) on the server.  I have read the howto's on getting that all setup.  However i feel uneasy having the traffic between the two servers unencrypted.  I would like the two servers communication to run over ssh.

this all being done so when looking at logs, i just need to view them from the main server.

---

