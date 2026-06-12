---
title: "Share Internet Connection (Ubuntu Server)"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by mikemhz on 2012-11-17
I have turned an old laptop into a linux server. It uses wi-fi to connect to the internet (eth1) and I have a desktop connected to it via ethernet that I want to share the internet with (eth0).

Easy enough with the ubuntu GUI, but something to do with 'iptables' by command line, from what I've read. Can anybody help?

---

### Post by mikemhz on 2012-11-18
One thing I keep coming accross is this:

```

iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o eth1 -j MASQUERADE
```

Say I can browse to my router settings on 192.168.1.254 and my server IP is 192.168.1.69. But eth1's default gateway is 192.168.1.255.

After telling eth1 to masquerade, how do I configure eth0 on the server and the ipv4 settings on the (windows 8) desktop?

---

### Post by Cheesemill on 2012-11-18
I've used this tutorial in the past:
[http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/](http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/)

---

### Post by mikemhz on 2012-11-18
So I followed the tutorial and my Windows desktop recognizes a DHCP through the Ethernet but tells me DHCP is not enabled. Also, my DNS suffix is blank or has example.org.

My setup differs from that tutorial in the first step.

in /etc/network/interfaces i have:

```


auto eth1
iface eth1 inet dhcp
    wpa-ssid <ESSID>
    wpa-psk <password>


```

will this make a difference?

---

### Post by mikemhz on 2012-11-18
So I've wasted a weekend doing this. Please help lol. Just want this to be over. Do I need to enter my ISPs DNS details into /etc/dhcp/dhcpd.conf?

---

### Post by Cheesemill on 2012-11-18
If you don't mind setting up the IP settings on your Windows box manually you can skip the DHCP part of that tutorial altogether.

---

