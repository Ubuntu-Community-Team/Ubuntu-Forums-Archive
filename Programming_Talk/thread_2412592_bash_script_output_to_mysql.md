---
title: "bash script output to mysql"
date: 2019-02-14
forum: Programming Talk
---

### Post by barroncm on 2019-02-14
I have the following bash script 

```
#!/bin/bash
#speed.sh
echo $(date) >> /var/log/speed.log


/usr/bin/speedtest-cli --simple --server 2391 >> /var/log/speed.log


echo $(date) "*Speed.sh Ran*" >> /var/log/ran.log

```~
that produces a log file like whats below


```
Thu Feb 14 17:22:02 CST 2019
Ping: 37.052 ms
Download: 89.61 Mbit/s
Upload: 11.84 Mbit/s
Thu Feb 14 18:22:01 CST 2019
Ping: 32.904 ms
Download: 92.29 Mbit/s
Upload: 11.58 Mbit/s
Thu Feb 14 19:22:01 CST 2019
Ping: 63.462 ms
Download: 85.73 Mbit/s
Upload: 11.98 Mbit/s
Thu Feb 14 20:22:02 CST 2019
Ping: 38.098 ms
Download: 71.64 Mbit/s
Upload: 11.89 Mbit/s
Thu Feb 14 21:22:01 CST 2019
Ping: 33.685 ms
Download: 86.39 Mbit/s
Upload: 11.80 Mbit/s

```
I would like to parse the info into a mysql db, everything I find says to use python, unfortunately I know zero about python.
is there a way to do this in bash or am I completely out of line with how Im doing this?

---

