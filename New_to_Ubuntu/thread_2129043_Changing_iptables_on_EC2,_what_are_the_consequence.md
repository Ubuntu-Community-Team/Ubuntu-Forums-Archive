---
title: "Changing iptables on EC2, what are the consequences?"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by Houmie on 2013-03-25
I was just going through some tutorials how to setup openvpn on ec2 and came across this iprouting:

```
sudo modprobe iptable_nat
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
sudo iptables-save > /some/place/you/can/recall
sudo iptables -t nat -A POSTROUTING -s 10.4.0.1/2 -o eth0 -j MASQUERADE
```

Since I also run an Apache2 Webserver on the Ec2 instance, what is the consequence of messing around with iptables as above? Would I still be able to access the webserver?

Many Thanks

---

