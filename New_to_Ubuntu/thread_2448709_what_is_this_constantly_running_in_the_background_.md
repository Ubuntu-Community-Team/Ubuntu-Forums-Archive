---
title: "what is this constantly running in the background update-secureboot-policy"
date: 2020-08-12
forum: New to Ubuntu
---

### Post by khan3 on 2020-08-12
Hi

Im monitoring my CPU usage using `glances` and i notice that the following is using 50% of my cpu

49.3   0.1   43.0M 23.2M    6253 root        2h23:05 1     0 S    ? ?    /usr/bin/perl -w /usr/share/debconf/frontend /sbin/update-secureboot-policy --enroll-key
14.5   0.0   2.55M 1.87M    6275 root          41:58 1     0 S    ? ?    /bin/sh /sbin/update-secureboot-policy --enroll-key
2.0    2.4   3.38G 377M  2754177 kay            0:59 76    0 S    0 0    /usr/lib/firefox/firefox -new-window

Does anyone know what this is and why its always on


System: (Ubuntu 20.04 64bit / Linux 5.4.0-42-generic)

---

### Post by CelticWarrior on 2020-08-12
This is among the first Google results I got:

[https://superuser.com/questions/1493050/update-secureboot-policy-enroll-key-running-on-every-new-startup-eating-reso](https://superuser.com/questions/1493050/update-secureboot-policy-enroll-key-running-on-every-new-startup-eating-reso)

---

