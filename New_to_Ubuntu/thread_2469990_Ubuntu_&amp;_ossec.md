---
title: "Ubuntu &amp; ossec"
date: 2021-12-16
forum: New to Ubuntu
---

### Post by kaltoum2021 on 2021-12-16
hello everyone ,
I want to ask you about OSSEC TOOL , I found that it is one of the most tools used for monitoring , but when I want to install on my ubuntu 20.04 with nginx , it forced me to install apache2 which I cannot to have two webservers in the same time , I need nginx alone.
Any solution with thanks

---

### Post by schragge on 2021-12-17
Nowhere in [their documentation]("https://www.ossec.net/docs/docs/manual/installation/index.html") do I see Apache 2 (or any web server for that measure) mentioned as a requirement. Nor is it listed in the **Depends:** field of the DEB package:
```
[COLOR=green]$[/COLOR] dpkg-deb -f ossec-hids-server_3.6.0-16569focal_amd64.deb Depends|sed 's/, /\n/g'[COLOR=green]
libc6 (>= 2.27)
libevent-2.1-7 (>= 2.1.8-stable)
libgeoip1 (>= 1.6.12)
libmysqlclient21 (>= 8.0.11)
libpcre2-8-0 (>= 10.22)
libssl1.1 (>= 1.1.0)
zlib1g (>= 1:1.2.3.3)
expect
debconf[/COLOR]
```
The agent has even fewer dependencies:
```
[COLOR=green]$[/COLOR] dpkg-deb -f ossec-hids-agent_3.6.0-16569focal_amd64.deb Depends|sed 's/, /\n/g'[COLOR=green]
libc6 (>= 2.27)
libevent-2.1-7 (>= 2.1.8-stable)
libpcre2-8-0 (>= 10.22)
libssl1.1 (>= 1.1.0)
zlib1g (>= 1:1.1.4)
debconf[/COLOR]
```

---

### Post by kaltoum2021 on 2021-12-24
No I mean , when I want to install the ossec web-ui , the interface it must be an apache2, which I don't want it , I want only nginx , If you have any alternative for ossec web-ui for nginx , I ll be grateful.
THANK YOU

---

### Post by QIII on 2021-12-24
You might have a look through [ these]("https://linuxsecurity.expert/tools/ossec/alternatives/") alternatives, but you will have to look through them to see if any are compatible with NGINX

---

### Post by Holger_Gehrke on 2021-12-24
Take a look at the github for ossec wui [https://github.com/ossec/ossec-wui](https://github.com/ossec/ossec-wui). Read the first Sentence of the README. Take a look at the dates of the last check ins. This is **unmaintained** software and has been that way **for 6 years**. Personally I wouldn't touch it with a six-foot pole.

On the other hand, it's all in php and doesn't use any functions to directly interface with the web-server, so there's no good reason why it shouldn't work with nginx if you've got PHP working on that.

Holger

---

