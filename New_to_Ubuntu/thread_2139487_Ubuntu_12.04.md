---
title: "Ubuntu 12.04"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by crashdogy on 2013-04-27
Ok followed this tutorial [http://ubuntuforums.org/showthread.php?t=1992469](http://ubuntuforums.org/showthread.php?t=1992469) and every thing works but my sons xbox cant connect to xbox live please help.

---

### Post by crashdogy on 2013-05-01
ok figured it out, need to add all these to my pintables and now it works with no Nat issues !!!!!                                                                                                                                                                                                                                                                                                                      iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.10.39    
iptables -t nat -A PREROUTING -i eth0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.10.39
iptables -A FORWARD -i eth0 -d 192.168.10.39 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i eth0 -d 192.168.10.39 -p udp -m multiport --dports 88,3074 -j ACCEPT
sudo /sbin/ifconfig eth1 mtu 1500
sudo /sbin/ifconfig eth0 mtu1500                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 and                                                                                                                                                                                                                                                                                               iptables -t nat -A POSTROUTING -o eth1 -s 192.168.10.0/24 -j MASQUERADE          as need for your network also add these in to the sbin root so they load all the time.  :):P

---

