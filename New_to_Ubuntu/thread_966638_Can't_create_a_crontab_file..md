---
title: "Can't create a crontab file."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by jerrydnj on 2008-11-01
I am a new user and trying to get the following to work.
sudo gedit /root/.crontab
to which I added the following...
12 40 * * * /usr/bin/apt-get update && /usr/bin/apt-get upgrade -y
After a saved it and waited until 12:40 it did not run and get updates.
 
I then looked to see if the .crontab file was really created.
I could not find this file on the system.  A search on the file system did not come back with it.
Also, when I tried ...  sudo cd /root ... I get.. command not found.  I just wanted to see if the .crontab file was there, 
I used UNIX back 25 years ago and do not remember anything.
Ubuntu veriona 8.04.
Jerry

---

### Post by taurus on 2008-11-01
The command to list "all" the files, even the hidden ones is

```
sudo ls -la /root
```
And if you plan to run something at a specific time and date, you need to add an entry in /etc/crontab.

```
gksudo gedit /etc/crontab
```

---

### Post by jerrydnj on 2008-11-01
> **taurus said:**
> The command to list "all" the files, even the hidden ones is

```
sudo ls -la /root
```
And if you plan to run something at a specific time and date, you need to add an entry in /etc/crontab.

```
gksudo gedit /etc/crontab
```
Thanks, the ls -la /root works. The .crontab file is there.
But,  do I put this "12 40 * * * /usr/bin/apt-get update && /usr/bin/apt-get upgrade -y" in /etc/crontab and not into /root/crontab ?
Jerry

---

### Post by taurus on 2008-11-01
Yes, put whatever you want to run in /etc/crontab, _not_ /root/crontab.

---

### Post by redbob on 2008-11-01
JerryDN, your crontab doesn't worked because you inverted hour and minute. The correct syntax is:
> **40 12** * * * /usr/bin/apt-get update && /usr/bin/apt-get upgrade -y
The minute is written before the hour

---

