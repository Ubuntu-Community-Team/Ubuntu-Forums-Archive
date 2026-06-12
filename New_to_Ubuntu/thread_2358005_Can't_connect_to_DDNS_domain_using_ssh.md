---
title: "Can't connect to DDNS domain using ssh"
date: 2017-04-08
forum: New to Ubuntu
---

### Post by baigergi on 2017-04-08
I have a remote Raspberry Pi with set up DDNS, so I can access it behind NAT using SSH. The thing is that I can't access it from my home's ISP.
When I ssh it from another network(e.g my phone's internet):
```
$ ssh -vvv pi@XX.XX.XX.XX
OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "XX.XX.XX.XX" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to XX.XX.XX.XX [XX.XX.XX.XX] port 22.
debug1: Connection established.

```

When I ssh it from my homes' network:
 ```
$ ssh -vvv pi@XX.XX.XX.XX
OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "XX.XX.XX.XX" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to XX.XX.XX.XX [XX.XX.XX.XX] port 22.
ssh: connect to host XX.XX.XX.XX port 22: Connection timed out

```

I am using Ubuntu 16.04 LTS.
Any idea what might be the problem?

---

### Post by papibe on 2017-04-08
Hi baigergi

By XX.XX.XX.XX I gues you mean a public IP or a dynamic dns domain (like from dyndns or no-ip)?

When you are in your network, e.g., home or office, you can't use a public address or IP to access a LAN machine unless your router supports NAT loopback. Look in your router if that option is available, but note that most consumer router don't have it.

To make things simpler, you may assign the Pi a short name that matches your XX.XX.XX.XX. For instance:

From outside:
```
 ssh -vvv pi@myserver.adomain.org
```
From your LAN:
```
 ssh -vvv pi@myserver
```
That would require to setup your local DNS server (router or home server).

Does that help? Let us know how it goes.
Regards.

---

### Post by baigergi on 2017-04-09
HI papibe,

I tried with both IP of the DDNS and with the domain name.
No, I am not trying to access it on my local local network - raspberry is  remotely located in another network(in another pat of the town, no VPN's are used or something like that). 
I am starting to wonder if my home router could be the problem or my ISP. I checked the security options of my home router, but I don't see any restrictions for outgoing SSH requests.

---

### Post by HermanAB on 2017-04-09
Give the Pi two IP addresses - one for the LAN.

---

### Post by SeijiSensei on 2017-04-09
If you followed Herman's advice and used "-vvv" in your ssh request, do so again and post the results inside [noparse]```

```[/noparse] tags.

---

