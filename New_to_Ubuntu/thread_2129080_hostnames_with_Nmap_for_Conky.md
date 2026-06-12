---
title: "hostnames with Nmap for Conky?"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by salmonsm on 2013-03-25
I'm not sure if this is the right forum for this, but seeing how I am a beginner with awk, nmap AND conky, i think this might be the place.

I'm trying to setup a really basic security system for our open wireless channel. I've decided to try to use Nmap to detect new hosts and Conky to report it. I've got something simple that works ok:

${execi 100 nmap -sn 192.168.1.0/24 | awk -F " |/" '/report/ {print $5;}'}

However, I tested it by firing up a Windows 7 machine that doesn't have anything more exotic than Windows Security Essentials, but it does not show up in my host list. I read a suggestion that perhaps it's rejecting pings,  I am able to find it with nmap -Pn, but that doesn't work for a subnet scan- it never reports back. 

I can get an IP report with all hosts, but I'd rather grab the hostname because the system relies on me identifying hostnames by sight.
I am considering dumping this periodically to a table, but if I did that, at minimum I would want both the IP and the hostname, which is a whole other kettle of fish.

Is anyone else doing anything like this, or could point me in the right direction to get more comprehensive scan results? I don't need to be told the exact thing, but pointing out something obvious I missed would be much appreciated.

Thanks in advance.

---

### Post by schragge on 2013-03-25
I probably would do something like
```

sudo arp-scan -I wlan0 192.168.1.0/24|grep -o $'^[0-9.]*\t'|xargs -d\\n -I@ sh -c 'echo "$0\c"; host -i $0|awk "{print \$NF}"' @

```

---

### Post by salmonsm on 2013-03-25
> **schragge said:**
> I probably would do something like
```

sudo arp-scan 192.168.1.0/24|grep -o $'^[0-9.]*\t'|xargs -d\\n -I@ sh -c 'echo "$0\c"; host -i $0|awk "{print \$NF}"' @

```

Thanks, I will tweak it and see if I can get something going for wlan0. Much appreciated for the direction.

---

