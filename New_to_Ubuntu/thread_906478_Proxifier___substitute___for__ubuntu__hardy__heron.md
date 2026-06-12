---
title: "Proxifier   substitute   for  ubuntu  hardy  heron"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by leo21tollstoy on 2008-08-31
Hello,

My college servers do not support bit-torrent protocol.

So we have to use Proxifier in windows to transform bit-torrent requests to HTTP requests.

I am running Ubuntu 8.04 and **wine** makes my system very slow.

Is there any alternative to Proxifier in UBUNTU 8.04 ??

I tried Proxychains but it was giving errors.


I also tried HTTP tunnel.  But failed to make it run.

Did not understand what htc and hts mean.

Please Help.:(

---

### Post by Sycron on 2008-08-31
If it's a HTTP proxy you may try System-->Preferences-->Network Proxy .

---

### Post by leo21tollstoy on 2008-09-01
well ok but I mean only bittorrent clients like transmission do not work

Firefox works fine through http proxy

System --> Preferences --> Network

But bittorrent clients do not .

---

### Post by t0p on 2008-09-01
There's an app called **Your Freedom** that enables you to get round local rules like your college server's ban on file sharing.  Unfortunately it's not in the repos.  You can download it from [www.your-freedom.net]("http://www.your-freedom.net").  You'll also need to install **OpenVPN** -

```
sudo apt-get install openvpn
```

At the Your Freedom site, you'll also find a user's guide in pdf format.  Download that too, as it'll help in setting up Your Freedom.

---

