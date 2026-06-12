---
title: "Server getting DHCP although Static ip is configured"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by llewellynpienaar on 2014-03-31
Good day Ubuntu Community. 

I set up my one server, lets call it server1 to have a static ip. 

Here is my config file

/etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 dsl-provider
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 10.0.0.11
        netmask 255.255.255.0
        broadcast 10.0.0.254
        gateway 10.0.0.11
        hostname = gondor



pre-up /sbin/ip link set dev eth0 up # line maintained by pppoeconf

iface dsl-provider inet ppp
provider dsl-provider

```
Am I missing a config to edit for static? or is there something I need to disable?

Best Regards
Llewellyn Pienaar

---

### Post by apohal9 on 2014-03-31
Do you use Network-Manager on server1? I think it's default behavior is to ignore /etc/network/interfaces and therefor the setting for static IP.

---

### Post by llewellynpienaar on 2014-03-31
Hi apohal9, 

I am not sure. How can I check this?

Best regards

---

### Post by apohal9 on 2014-03-31
Hi llewellynpienaar,

check with > sudo pkg --list '*network*manager*' and if installed. If yes, run > sudo ps -A|grep -i network

---

### Post by steeldriver on 2014-03-31
What is your actual network type? if you are using a PPPoE (DSL) connection, then I don't think you will be able to set your own private LAN IP address - PPP means that you are a 'peer' on someone else's network so you must use whatever IP they allocate to you. 

The static eth0 setup would only apply if you have your own private LAN that is separated from the DSL connection via a router.

---

### Post by llewellynpienaar on 2014-03-31
Hi apohal9

is it pkg or dkpg?

I ran dpkg --list *network*manager* and got this result

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                               Description
+++-=====================================================-=====================================================-==========================================================================================================================
un  network-manager                                       <none>                                                (no description available)
un  network-manager-pptp                                  <none>                                                (no description available)

@steeldriver. I run pppoe via router that is in bridge mode. The server dails out. I dont think it is the pppoe connection or ppp connection that gives out the ip since they are on different ip ranges. 10.0.0.0/24 is my local network range and the pppoe connection gives a dynamic ip that changes frequently and the range always start with 196.x.x.x

Best regards

---

### Post by SeijiSensei on 2014-03-31
Isn't this the problem?
```
# The loopback network interface
auto lo eth0 dsl-provider
iface lo inet loopback
```
I don't know what "dsl-provider" refers to, but you should certainly remove eth0 from this directive.  If you don't know why "dsl-provider" is there either, I'd remove it too.
```

auto lo
iface lo inet loopback

```

---

### Post by llewellynpienaar on 2014-03-31
Hi SeijiSensei

I removed dsl-provider from line to look like

auto lo eth0
iface lo inet loopback

At first I removed oth0 aswell but then eth0 did not reveive an ip. 

I added eth0 back to 
auto lo eth0

I will monitor if removing dsl-provider resolved the problem or if the problem continues. 

Kudos

Llewellyn

---

### Post by apohal9 on 2014-04-01
Hi Llewellyn

did the behavior change?

---

### Post by llewellynpienaar on 2014-04-01
Hi apohal9

It seems it stays on the static ip now. 

Thanks for the help

---

### Post by apohal9 on 2014-04-01
So SeijiSensei solved your problem ;)

---

