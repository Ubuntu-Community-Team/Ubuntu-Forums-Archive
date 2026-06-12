---
title: "ip address question"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by macstl on 2013-08-18
What command do I use to find addresses for DNS Gateway DHCP local ipaddress? Like in windows when you use ipconfig -all it shows all this stuff.

---

### Post by uRock on 2013-08-18
```
ifconfig
```will show the local IP, but not the DNS.

---

### Post by deadflowr on 2013-08-18
I know if you install curl you can run
```
curl ifconfig.me
```
And get the Internet ip address you're using.

There are other elaborate ways such as the site checkip.

But, yes as per the thread ifconfig is the linux equivalent of ipconfig.

---

### Post by macstl on 2013-08-18
Curl worked for me ok. what shows the ip for dhcp server and gateway ip?

---

### Post by deadflowr on 2013-08-18
You can try
```
nm-tool
```
Which should at least list the gateway address.

---

### Post by steeldriver on 2013-08-18
With recent version of the network-manager package, you also get 'nmcli' - which goes a bit deeper than nm-tool e.g.

```

nmcli dev list

nmcli dev list iface wlan0

nmcli dev list | grep '^IP\|^DHCP'

```

---

### Post by macstl on 2013-08-18
curl ifcongfig.me yields XX.XX.XX.XX
ifconfig is 192.168..1.70
is the XX.XX.XX.XX my external gatway ip address?

---

### Post by tripp98 on 2013-08-18
yes that is your external IP.

if you are using ubuntu(unity) at the clock at top right click on network icon at the bottom 2nd from bottom is the connection information.  will show you the gateway and dns servers.

---

### Post by lisati on 2013-08-18
> **macstl said:**
> curl ifcongfig.me yields XX.XX.XX.XX
ifconfig is 192.168..1.70
is the XX.XX.XX.XX my external gatway ip address?

You're on the right track. I've edited out the public IP address to help avoid attacks by bots.

---

