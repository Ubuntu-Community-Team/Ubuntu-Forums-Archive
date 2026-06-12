---
title: "/var/log/ error message"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-01-05
any idea how to fix i used gksudo nautilus and just deleted the logs and then the error message comes up when i try to use sudo freshclam
output:

ray@ray-Latitude-D630:~$ sudo freshclam
[sudo] password for ray: 
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

tks

---

### Post by rburkartjo on 2014-01-05
note i can run a scan: sudo clamscan -r  '/'  .just fine. sure it is something dumb i overlooked.

---

### Post by Iowan on 2014-01-05
I've no idea if this will work...
```
touch /var/log/clamav/freshclam.log
```

---

### Post by rburkartjo on 2014-01-05
lo, that was worth a short but didnt work here is output:
ray@ray-Latitude-D630:~$ touch /var/log/clamav/freshclam.log
touch: cannot touch ‘/var/log/clamav/freshclam.log’: No such file or directory
ray@ray-Latitude-D630:~$

---

### Post by rburkartjo on 2014-01-05
even if i remove running sudo apt-get purge clamav and reisntall sudo apt-get install clamav i have the same problem. no big deal but bugs me when i cant figure out the problem.

---

### Post by rburkartjo on 2014-01-05
fixed it new it was something stupid. just opened the spm and reinstalled clamav-freshclam. tks

---

### Post by Dave_L on 2014-01-05
Just for reference (freshclam works properly for me without errors):

```
$ ll -h /var/log/clamav/freshclam.log
-rw-r----- 1 clamav adm 2.3K Jan  5 08:33 /var/log/clamav/freshclam.log
```

---

### Post by Iowan on 2014-01-05
> **rburkartjo said:**
> lo, that was worth a short but didnt work here is output:
ray@ray-Latitude-D630:~$ touch /var/log/clamav/freshclam.log
touch: cannot touch &#8216;/var/log/clamav/freshclam.log&#8217;: No such file or directory
ray@ray-Latitude-D630:~$Wonder if it needed **sudo**?
Moot point now - glad you got it.

---

