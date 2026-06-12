---
title: "Squid3 configuration help"
date: 2020-04-13
forum: New to Ubuntu
---

### Post by rrmv1970 on 2020-04-13
Hi everyone

I am trying to configure squid3 in ubuntu 16.04.  Recently updated from 12.04.  I can't getting up and running.  I start with this when checking the status of the service.  I have no idea and no experience on this, so any help is appreciated.  I had it working on ubuntu 12.04.

:~$ squid status
2020/04/13 12:10:16| ALERT: setgid: (1) Operation not permitted
WARNING: Cannot write log file: /home/precise/cache/cache.log
/home/precise/cache/cache.log: Permission denied
         messages will be sent to 'stderr'.
2020/04/13 12:10:16| ALERT: setgid: (1) Operation not permitted
2020/04/13 12:10:16| ALERT: setgid: (1) Operation not permitted
FATAL: Ipc::Mem::Segment::create failed to shm_open(/squid-cf__metadata.shm): (13) Permission denied


Squid Cache (Version 3.5.12): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.004 user + 0.004 sys
Maximum Resident Size: 47616 KB
Page faults with physical i/o: 0
:~$ 

All help is welcome

---

### Post by lvm on 2020-04-14
Apparently you are running squid with insufficient rights, probably under your own user account. Standard configuration sets up 'squid' user for squid and creates necessary files and folders accessible by that user, but judging by a very non-standard log location you changed a lot. Running as root will also work but should be discouraged.  

Why squid? Nowadays when only a small fraction of web traffic is unencrypted, it is mostly useless.

---

