---
title: "[SOLVED] Hostname issues &amp;quot;hostname: Unknown host&amp;quot;"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Blue Sassley on 2008-11-02
Ok, I have searched this land far and wide, and I can't not figure out what I am doing wrong no madder how I write my /etc/hosts file I can't get my FQDN to work:

```
blue@PleskUbuntu:~$ hostname -f
hostname: Unknown host
blue@PleskUbuntu:~$ hostname -a
hostname: Unknown host
blue@PleskUbuntu:~$ hostname -d
hostname: Unknown host
```

Here is my hosts file;
```
127.0.0.1       localhost
127.0.1.1       server.PleskUbuntu.local server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Any ideas on what I have screwed up?

Thanks,
Blue

---

### Post by racmar on 2008-11-03
from man hostname:

>    SET NAME
       When called with one argument or with the --file option, the commands set the host name or the NIS/YP domain name.  Note that this is effective only until  the  next
       reboot.  Edit /etc/hostname for permanent change.


so, just do
```
sudo nano /etc/hostname
```
and change it to what you want

---

