---
title: "connection refused for socks5 on 11.10 ubuntu"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by PxDuck on 2013-06-07
I completed this command 


ssh -N -D 0.0.0.0:1080 localhostfrom
[URL="http://www.linuxexpert.ro/Linux-Tutorials/setup-ss5-socks-proxy.html"]
[http://www.catonmat.net/blog/linux-socks5-proxy/](http://www.catonmat.net/blog/linux-socks5-proxy/)


[/URL]and I get "channel 6 (other number as well) open failed: connect failed: connection refused"

So i started on this guide

[http://www.linuxexpert.ro/Linux-Tutorials/setup-ss5-socks-proxy.html](http://www.linuxexpert.ro/Linux-Tutorials/setup-ss5-socks-proxy.html)

I can get the download required and make it to step 2.

yum install rpm-build.x86_64 openldap-devel.x86_64 pam-devel.x86_64 openssl-devel.x86_64 libgssapi-devel.x86_64 -y (for 64 bit Linux)

and i get 

"
Setting up Install Process
No package rpm-build.x86_64 available
No package openldap-devel.x86_64 available
No package pam-devel.x86_64 available
No package openssl-devel.x86_64 available
No package libgssapi-devel.x86_64 available
Nothing to do
"

Any help on how to get these?

also 

sudo apt-get install yum

"yum is already the newest version"

sudo apt-get install rpm

"rpm is already the newest version"


I can get my chrome to use from the original command but i am needing it to be a socks5 proxy for another program to connect.

Help?

---

### Post by PxDuck on 2013-06-07
i have updated to 12.04 and included all software updates with same effect.

---

