---
title: "Missing pop-before-smtp Package -- hash:/var/lib/pop-before-smtp/hosts is unavailable"
date: 2014-05-03
forum: Packaging and Compiling Programs
---

### Post by own3mall on 2014-05-03
Hey Guys,

I'm a developer for open source software, and I just now noticed that Ubuntu versions greater than 12.04 do not have a pop-before-smtp package.  So, I tried using the compiled deb package from Ubuntu 12.04 on my Ubuntu 14.04 server.  Unfortunately, it didn't work, and the daemon would not start.  It complained about this error:

> 
Insecure dependency in open while running with -T switch


 Realizing it was a basic perl issue, I downloaded the source, made a change with the pid file logic, compiled, created a deb package, and tried it on Ubuntu 14.04.  It appears to be working properly and is running as a daemon as happy as can be (as far as I can tell... at least my mysql integration into postfix is working again and emails are being sent and received).

Decided to share the love with you all in case you need this package in Ubuntu 13.04 - Ubuntu 14.04 for whatever reason.  To install it, run the following commands:

```

sudo apt-get install gdebi-core
cd ~/Downloads
wget -N -O "pop-before-smtp.deb" "http://www.dinofly.com/files/linux/pop-before-smtp.deb"
sudo gdebi --n "pop-before-smtp.deb"

```

Let me know if you have any problems!

---

