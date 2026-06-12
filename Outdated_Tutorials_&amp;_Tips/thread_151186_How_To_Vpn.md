---
title: "How To Vpn"
date: 2006-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by int on 2006-03-27
**[SIZE="5"]To connect with a VPN:[/SIZE]**


**Install VPN:**
```
sudo apt-get install pptp-linux 
```
[B]
Create a File for VPN:[/B]
```
sudo gedit /etc/ppp/peers/VPN
```

**Paste this:**
Change this 2 words with yours configurations (this are mine)
_VPNSERVER_ = vpnserver.e-u
_LOGIN_= name @alunos.estg.ipleiria.pt

> # profile: VPN

# name of tunnel, used to select lines in secrets files
remotename VPN

# name of tunnel, used to name /var/run pid file
linkname VPN

# name of tunnel, passed to ip-up scripts
ipparam VPN
# data stream for pppd to use
pty "pptp  _VPNSERVER_  --nolaunchpppd"

# domain and username, used to select lines in secrets files
name _LOGIN_

# retrieve DNS server from peer
usepeerdns

# use MPPE compression
nomppe-40
require-mppe

# do not require the server to authenticate to our client
noauth

# we want to see what happen
nodetach

# lock the device
lock

# Dont use BSD compression
nobsdcomp

# Dont use deflate method
nodeflate

defaultroute


**Edit this file to put or password:**

Paste this at the end of the file.. 

Change this 2 words with yours configurations (this are mine)
_LOGIN_=name @alunos.estg.ipleiria.pt
_PASSWORD_= mine
> #  tunnel VPN
_LOGIN_ VPN _PASSWORD_ *
#  tunnel VPN


[B]
Create a script to connect to wireless and vpn:[/B]
```
gedit ~/ligar_vpn
```

**Paste this:**
Change this 3 words with yours configurations (this are mine)
_VPNSERVER_ = vpnserver.e-u
_ESSID_ = guest-e-U
_ETHX_= eth1
> #!/bin/bash
echo "A configurar Wireless"
modprobe ppp-mppe
iwconfig _ethx_ essid guest-e-U
iwconfig _ethx_ mode managed
dhclient _ethx_
echo "A adicionar o servidor vpn a _ethx_"
route add -host '_VPNSERVER_' dev '_ethx_'
echo "A activar a ligação n"
pon VPN &
echo "Esperar 10 Segundos"
sleep 10
echo "A definir eth1 como disp. principal"
echo "route del default"
route del default '_ethx_'
echo "route add default"
route add default 'ppp0'

**Make and executable script:**
```
chmod 777 ~/ligar_vpn
```

**Execute**:)
```
sudo ~/ligar_vpn
```

---

### Post by dbw on 2006-08-16
What is the purpose of the `sleep 10` command in your script?  Is that just for fun?

---

### Post by simosx on 2006-08-17
> **dbw said:**
> What is the purpose of the `sleep 10` command in your script?  Is that just for fun?

No, it's not for fun.

It takes several seconds for the new interface to come up, so 10 seconds is a good compromise.
The ideal solution is to have a loop that would check every second if the interface is up, saving the wasted time. Would you like to code this loop?

---

### Post by codedmin on 2007-10-26
Don't work in gutsy...

---

