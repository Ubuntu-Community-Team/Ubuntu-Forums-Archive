---
title: "Ubuntu server 16.04 not forwarding correctly to internal webserver (ubuntu serv14.04)"
date: 2018-10-03
forum: New to Ubuntu
---

### Post by cwup on 2018-10-03
Hello,
  I'm trying to ping the eth0 on my firewall(16.04) (192.168.1.210) and have  it route to eth1 on my internal server(14.04) (192.168.21.129). I've followed  all the steps and it should be working, but it will timeout the request.  Below are my ip tables.

  Firewall: eth0 - 192.168.1.210 eth1 192.168.21.128

  LAMP - eth1 - 192.168.21.129
  Initial IP tables:[INDENT] iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
  iptables -A FORWARD -i eth0 &#8211;o eth1 &#8211;m state &#8211;-state  RELATED,ESTABLISHED -j ACCEPT
  Iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
 [/INDENT]
Below is the pre/postrouting I've done[INDENT] iptables &#8211;t nat -A PREROUTING -i eth0 &#8211;p tcp &#8211;-dport 80 &#8211;j DNAT &#8211;-to-destination 192.168.21.129:80
  iptables &#8211;t nat -A POSTROUTING &#8211;p tcp &#8211;o eth0 &#8211;-dport 80 &#8211;d  192.168.21.129 &#8211;j SNAT &#8211;-to-source 192.168.21.128
 [/INDENT]
This is all on a private network using VMware 14.
  Expected Outcome: Access firewall eth0 (192.168.1.210) and have it route to internal websever (192.168.21.129)
  Actual Outcome: Access and it will timeout the request after attempting for awhile.

I should add that these are all dhcp, and not static.

  I've configured the /etc/sysctl.conf file on the firewall after activating echo 1 > /proc/sys/net/ipv4/ip_forward 
  Pings from the firewall to the internal server work fine. Pings from Internal server to firewall work fine


  I'm not understanding why this is not working, is there a service or something I need to enable or unblock?


  [http://prntscr.com/l1wp1q](http://prntscr.com/l1wp1q)  - Here is the iptables -t nat -L
  [http://prntscr.com/l1wp8s](http://prntscr.com/l1wp8s) - Here is the iptables -S


  Thank you

Edit: Going to see if there's any difference with static ip's
Edit2: No difference in static, can still ping but not connect. Going to make sure third vm (windows domain) can ping to firewall.
edit3: Can ping to firewall from both host and vm, assuming I must have gotten an iptables command wrong, going to try to flush and re-enter information.

---

