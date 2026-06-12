---
title: "Why does msmtp fail with Gmail?"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Bushflyr on 2012-04-28
OK, I've been searching and reading threads for weeks and nothing has solved my problem. 

I'm trying to use msmtp to send system notification emails to my Gmail account. It worked initially, but somewhere along the line it stopped. Not exactly sure when because I only recently started going through the log files to check for unseen errors. My msmtp.log is full of:

```
Apr 28 06:42:53 host=smtp.gmail.com tls=on auth=on user=me@gmail.com from=me@gmail.com recipients=anotherme@gmail.com errormsg='cannot connect to smtp.gmail.com, port 587: Connection timed out' exitcode=EX_TEMPFAIL
```
my msmtprc file is:

```

defaults
tls on
tls_starttls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
 
account default
host smtp.gmail.com
port 587
auth on
user me@gmail.com
password mypass
from me@gmail.com
logfile /var/log/msmtp.log

```I have port 587 and 53 (among others) opened up in UFW and can ping smtp.gmail.com no problem.

Anybody have any ideas? TIA.

---

### Post by Bushflyr on 2012-04-28
Messing with more things and it now works if I disable UFW. So, then the question is why is UFW blocking my outbound messages?

```

Status: active

To                         Action      From
--                         ------      ----
68                         ALLOW       192.168.1.0/24
548/tcp                    ALLOW       192.168.1.0/24
427/tcp                    ALLOW       192.168.1.0/24
4700/tcp                   ALLOW       192.168.1.0/24
4700/tcp                   ALLOW       127.0.0.1
5353/udp                   ALLOW       192.168.1.0/24
56794/udp                  ALLOW       192.168.1.0/24
42826/udp                  ALLOW       192.168.1.0/24
67                         ALLOW       192.168.1.0/24
4040/tcp                   ALLOW       Anywhere
123                        ALLOW       Anywhere
4040/tcp                   ALLOW       Anywhere (v6)
123                        ALLOW       Anywhere (v6)

25                         ALLOW OUT   Anywhere
68                         ALLOW OUT   192.168.1.0/24
548/tcp                    ALLOW OUT   192.168.1.0/24
427/tcp                    ALLOW OUT   192.168.1.0/24
4700/tcp                   ALLOW OUT   192.168.1.0/24
4700/tcp                   ALLOW OUT   127.0.0.1
5353/udp                   ALLOW OUT   192.168.1.0/24
56794/udp                  ALLOW OUT   192.168.1.0/24
42826/udp                  ALLOW OUT   192.168.1.0/24
67                         ALLOW OUT   192.168.1.0/24
80/tcp                     ALLOW OUT   Anywhere
123                        ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere
25                         ALLOW OUT   Anywhere (v6)
80/tcp                     ALLOW OUT   Anywhere (v6)
587                        ALLOW OUT   Anywhere (v6)
123                        ALLOW OUT   Anywhere (v6)
53/udp                     ALLOW OUT   Anywhere (v6)

```

---

### Post by DocHoss on 2012-05-02
Same problem here.  It was working before, but I must have changed something in UFW.  Any ideas on this one, guys?

EDIT: Figured it out.  I needed to add incoming and outgoing UFW rules on port 587.  I did tcp and udp, but I may tinker with that and figure out which it needs and kill the other.

EDIT 2: Deleted the udp rules and it still works.  Looks like you just need 587/tcp in and out.

```

sudo ufw allow in 587/tcp
sudo ufw allow in 587/udp
sudo ufw allow out 587/tcp
sudo ufw allow out 587/udp

```

---

### Post by Bushflyr on 2012-05-03
Glad you got it working, unfortunately mine is still TU. :mad: Can you post your msmtprc file? Maybe my issue is in there somewhere.

---

