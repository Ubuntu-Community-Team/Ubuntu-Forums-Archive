---
title: "Why is UFW Blocking Port 587 When I Set it to Open?"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by Bushflyr on 2012-05-13
I've been having issues with this for a while, but have now definitively found the problem. I just need help fixing it. 

I have msmtp set up to send system messages through a dummy gmail account like so:

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
```

With UFW off the messages get through just fine.

```
May 12 19:06:07 host=smtp.gmail.com tls=on auth=on user=me@gmail.com from=me@gmail.com recipients=anotherme@gmail.com mailsize=355 smtpstatus=250 smtpmsg='250 2.0.0 OK 1336885566 rj10sm5606305obc.22' exitcode=EX_OK
```

However, when I turn UFW on the messages fail to get through:

```
May 12 20:12:20 host=smtp.gmail.com tls=on auth=on user=me@gmail.com from=me@gmail.com recipients=anotherme@gmail.com errormsg='cannot connect to smtp.gmail.com, port 587: Connection timed out' exitcode=EX_TEMPFAIL
```

All the gmail ports, 25, 465, and 587 are currently open with :

```
sudo ufw allow 587
```
(or whatever port)

Can anybody tell me why this is, or, at least point me in a direction to look further? I've searched and read everything I can find, but nothing explains why this isn't working.

TIA

---

### Post by The Cog on 2012-05-13
That's odd. ufw doesn't normally block outgoing connections, only incoming ones. Can you post the output of the command "sudo ufw status" so we can see what is configured?

---

### Post by Bushflyr on 2012-05-13
Thanks, I forgot. It's set up to default deny then I'm only allowing ports that I use.

```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 25                         ALLOW OUT   Anywhere (out)
[ 2] 68                         ALLOW IN    192.168.1.0/24
[ 3] 68                         ALLOW OUT   192.168.1.0/24 (out)
[ 4] 548/tcp                    ALLOW IN    192.168.1.0/24
[ 5] 548/tcp                    ALLOW OUT   192.168.1.0/24 (out)
[ 6] 427/tcp                    ALLOW IN    192.168.1.0/24
[ 7] 427/tcp                    ALLOW OUT   192.168.1.0/24 (out)
[ 8] 4700/tcp                   ALLOW IN    192.168.1.0/24
[ 9] 4700/tcp                   ALLOW OUT   192.168.1.0/24 (out)
[10] 4700/tcp                   ALLOW IN    127.0.0.1
[11] 4700/tcp                   ALLOW OUT   127.0.0.1 (out)
[12] 5353/udp                   ALLOW IN    192.168.1.0/24
[13] 5353/udp                   ALLOW OUT   192.168.1.0/24 (out)
[14] 56794/udp                  ALLOW IN    192.168.1.0/24
[15] 56794/udp                  ALLOW OUT   192.168.1.0/24 (out)
[16] 42826/udp                  ALLOW IN    192.168.1.0/24
[17] 42826/udp                  ALLOW OUT   192.168.1.0/24 (out)
[18] 67                         ALLOW IN    192.168.1.0/24
[19] 67                         ALLOW OUT   192.168.1.0/24 (out)
[20] 80/tcp                     ALLOW OUT   Anywhere (out)
[21] 4040/tcp                   ALLOW IN    Anywhere
[22] 123                        ALLOW IN    Anywhere
[23] 123                        ALLOW OUT   Anywhere (out)
[24] 53/udp                     ALLOW OUT   Anywhere (out)
[25] 587/tcp                    ALLOW IN    Anywhere
[26] 587                        ALLOW IN    Anywhere
[27] Anywhere                   ALLOW IN    192.168.1.10
[28] Anywhere                   ALLOW IN    224.0.0.22
[29] Anywhere                   ALLOW IN    239.255.255.250
[30] 25                         ALLOW OUT   Anywhere (v6) (out)
[31] 80/tcp                     ALLOW OUT   Anywhere (v6) (out)
[32] 4040/tcp                   ALLOW IN    Anywhere (v6)
[33] 123                        ALLOW IN    Anywhere (v6)
[34] 123                        ALLOW OUT   Anywhere (v6) (out)
[35] 53/udp                     ALLOW OUT   Anywhere (v6) (out)
[36] 587/tcp                    ALLOW IN    Anywhere (v6)
[37] 587                        ALLOW IN    Anywhere (v6)

```Also, and I may need to make another thread for it, does anybody know how to translate likes 12 & 13

```
[12] 5353/udp                   ALLOW IN    192.168.1.0/24
[13] 5353/udp                   ALLOW OUT   192.168.1.0/24 (out)
```into IPv6?

---

### Post by cryptotheslow on 2012-05-13
As far as I can see you are only allowing port 587 IN

```

[25] 587/tcp                    ALLOW IN    Anywhere
[26] 587                        ALLOW IN    Anywhere

[36] 587/tcp                    ALLOW IN    Anywhere (v6)
[37] 587                        ALLOW IN    Anywhere (v6)

```I'm not familiar with UFW but I think you need to add entries for 587 ALLOW OUT.

As for those line 12 & 13, 192.168.1.0/24 is a subnet declaration and basically means all IP addresses in the range 192.168.1.1 -> 192.168.1.254, presumably your LAN.

This may help with that [http://www.subnet-calculator.com/](http://www.subnet-calculator.com/) where 24 is the "Mask Bits".

*edit - *Sorry I didn't see your edit when posting. I've no idea about IPv6.

---

### Post by Old_Grey_Wolf on 2012-05-13
sudo ufw allow out 587

---

### Post by Bushflyr on 2012-05-13
](*,) Thanks, you guys rock. I can't believe I missed that.

I just ASSumed that "sudo ufw allow 587" allowed traffic in both directions. 

I'll mark this one solved and start a new thread for the IPv6 stuff if I can't figure it out in a few days.

---

### Post by Old_Grey_Wolf on 2012-05-13
> **Bushflyr said:**
> ](*,) Thanks, you guys rock. I can't believe I missed that.

I just ASSumed that "sudo ufw allow 587" allowed traffic in both directions. 

I'll mark this one solved and start a new thread for the IPv6 stuff if I can't figure it out in a few days.

I don't have IPv6 so I was curious what I would face once I got it. I found this thread [http://ubuntuforums.org/showthread.php?t=1371345](http://ubuntuforums.org/showthread.php?t=1371345) at the end are some things that may help.

---

