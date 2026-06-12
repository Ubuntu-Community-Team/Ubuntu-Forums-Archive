---
title: "VirtualBox and Connections"
date: 2009-08-06
forum: Programming Talk
---

### Post by ooobooontooo on 2009-08-06
Hi,

I have ubuntu 8.10 server set up as the guest on my box. Right now, port forwarding is enabled to reach the server. However, I realised that when I try to connect via telnet to the port that is forward to the vm, it never refuses the connection even when the service is not running. Instead it just sort of errors out. My question is why, and how I can make it so that the connections to the forwarded ports are refused when the service is not running? (I have python scripts which expect refusal...because that's how non vm boxes usually act in my experience.)

---

