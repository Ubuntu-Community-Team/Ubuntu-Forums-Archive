---
title: "change script permission"
date: 2018-07-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2018-07-21
my script works when i run in terminal
#!/bin/bash
echo xxxx | sudo -S sudo  rtcwake -m mem -s 28800 
however not in crontab
i am the owner not root.
read that root must be owner for crontab
how to fix
script is in my home folder 
using scheduled task application
./tks

---

### Post by rburkartjo on 2018-07-21
path /home/ray/sleep


runs in terminal
ray@nightmare:~$ ./sleep

---

### Post by rburkartjo on 2018-07-21
0 22 * * * /home/ray/sleep # JOB_ID_4

---

