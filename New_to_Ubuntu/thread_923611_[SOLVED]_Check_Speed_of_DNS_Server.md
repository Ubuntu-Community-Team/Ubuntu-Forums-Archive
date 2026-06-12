---
title: "[SOLVED] Check Speed of DNS Server"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by EarloftheWest on 2008-09-18
I've been using OpenDNS and ScrubIT dns servers lately for their filtering capacity but it seems that these are slower than Comcast's DNS Servers.

I found this [article]("http://www.labnol.org/software/tutorials/check-isp-dns-server-speed-compare-opendns-ip-address/2614/") which tells me how to determine the speed of various DNS Servers but when I try something similar in Terminal, it doesn't give me the time it takes to resolve the DNS lookup.

Can anyone help?

- EarloftheWest

---

### Post by MegaJim on 2008-09-18
In linux you can prefix any command with "time" which will tell you how long it took for the command to execute, for instance:

```
james@megathron:~$ time ls
bin  Desktop  Documents  Fitness-App  mkdev.sh~  project

real	0m0.005s
user	0m0.000s
sys	0m0.004s

```

---

### Post by EarloftheWest on 2008-09-18
Worked great. Thanks!

Here's the results in case anyone is curious:

```
x@ubuntu:~$ time nslookup www.google.com
Server:		192.168.0.100
Address:	192.168.0.100#53

Non-authoritative answer:
www.google.com	canonical name = www.l.google.com.
Name:	www.l.google.com
Address: 209.85.173.147
Name:	www.l.google.com
Address: 209.85.173.103
Name:	www.l.google.com
Address: 209.85.173.104
Name:	www.l.google.com
Address: 209.85.173.99


real	0m0.021s
user	0m0.008s
sys	0m0.004s
x@ubuntu:~$ time nslookup www.google.com 208.67.222.222
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
www.google.com	canonical name = google.navigation.opendns.com.
Name:	google.navigation.opendns.com
Address: 208.67.216.230
Name:	google.navigation.opendns.com
Address: 208.67.216.231


real	0m0.025s
user	0m0.000s
sys	0m0.012s
```

It looks like Comcast is faster than OpenDNS.

---

### Post by Buntumatic on 2012-07-22
Sorry for necromancy, but this thread popped up on top of Google search.
First, the time command as used above gives meaningless results. Because time command really does not measure the lookup time, it measures how long it took in your box to execute the whole command. More importantly comparing lookup time between local caching router (192.168.0.100) and a remote server will always show the remote one is slower.
Second, there are better tools than nslookup. Below I'm using dig instead. It prints out the actual query time.

```
$ dig @8.8.8.8 www.google.com

; <<>> DiG 9.8.3-P1 <<>> @8.8.8.8 www.google.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30652
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         43199   IN      CNAME   www.l.google.com.
www.l.google.com.       299     IN      A       74.125.227.115
www.l.google.com.       299     IN      A       74.125.227.113
www.l.google.com.       299     IN      A       74.125.227.114
www.l.google.com.       299     IN      A       74.125.227.112
www.l.google.com.       299     IN      A       74.125.227.116

;; Query time: 29 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Jul 22 05:40:30 2012
;; MSG SIZE  rcvd: 132
```

---

