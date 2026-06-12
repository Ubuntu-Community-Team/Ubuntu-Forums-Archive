---
title: "xl2tpd and openswan is not working on Ubuntu 12.04 &amp; 14.04 LTS"
date: 2014-10-02
forum: New to Ubuntu
---

### Post by cktan on 2014-10-02
Hi all,

I need to set up a L2TP server on AWS by using Ubuntu 14.04LTS. I and my colleague are going to China to work so I set up that VPN server for us to bypass from the censorship.

I followed the tutorial from [here]("https://vpsboard.com/topic/4095-ipsecl2tp-vpn-on-ubuntu-1404/") ([https://vpsboard.com/topic/4095-ipsecl2tp-vpn-on-ubuntu-1404/](https://vpsboard.com/topic/4095-ipsecl2tp-vpn-on-ubuntu-1404/)) to set up xl2tpd, openswan and ppp on my Ubuntu 14.04LTS running t1.micro instance. I followed step-by-step exactly.

However, none of my computers (Windows / Mac OS X) can connect to the L2TP/IPSec VPN server on AWS. I want to connect using a Pre-shared key. On Windows, I was given Error 789 while the connecting to the server.

> Error: 789 "The L2TP connection 		  attempt failed because the security layer encountered a processing error during 		  initial negotiations with the remote computer"

Therefore, I assume 14.04LTS is not compatible with Openswan yet so I tried using 12.04LTS. I got the same error.

Can anyone give me some clues what should I do to solve this ? I appreciate your help a lot. Thank you.

---

### Post by Vladlenin5000 on 2014-10-02
Hi, welcome.

Here's some reading materials:
[https://help.ubuntu.com/community/L2TPServer](https://help.ubuntu.com/community/L2TPServer)
[http://blog.jameskyle.org/2012/07/configuring-openswan-ipsec-server/](http://blog.jameskyle.org/2012/07/configuring-openswan-ipsec-server/)

---

### Post by cktan on 2014-10-02
Hi Vladlenin5000,

Thanks for your help. I am wondering is the guide can be applied on Ubuntu 14.04LTS?

---

### Post by Vladlenin5000 on 2014-10-02
Yes, it should.

---

