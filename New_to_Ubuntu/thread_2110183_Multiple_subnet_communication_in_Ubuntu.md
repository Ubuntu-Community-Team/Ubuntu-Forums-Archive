---
title: "Multiple subnet communication in Ubuntu"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Lordhowe on 2013-01-29
Hi all,
 
I have a question about communication across subnets using Ubuntu. 
 
In windows, I can set the default gateway for a pc to be on a separate subnet if I choose. In my router, I have a setting for multiple subnets enabled, which allows my systems on the two subnets to communicate. My problem with the Ubuntu server though is that will not allow me to choose a default gateway on a different subnet.
 
We are using Ubuntu as our vpn server, so when employees connect via vpn, they can not access shares on the main subnet (which they could before when it was setup on a Windows server). 
 
How can I enable communication between the Ubuntu box, and the other subnet? 
 
example: 
Main subnet = 192.168.101.0
Secondary subnet = 192.168.104.0
 
PC1 (Windows PC): 192.168.104.2 
DFG: 192.168.101.1
No issues communicating
 
PC2 (Ubuntu): 192.168.104.3
DFG: 192.168.104.1
Can't communicate with the .101.0 subnet, and it will not allow me to choose the 101.1 router as my default gateway.
 
Thanks,
LH

---

### Post by aromo on 2013-01-29
> **Lordhowe said:**
> Hi all,
 
In windows, I can set the default gateway for a pc to be on a separate subnet if I choose. 



Are you sure?  If your default gateway is in a different subnet how are you going to reach it?

Your gateway may have multiple IP addresses, one for each subnet, and machines in each segment have to point the corresponding gateway interface as the default gateway AFAIK.

---

### Post by SeijiSensei on 2013-01-29
Have you enabled IP forwarding in /etc/sysctl.conf?  Read the comments in that file and remove the hash mark from the line "net.ipv4.ip_forward=1".  Then reboot.

For a quick test without rebooting run the command:
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

If that solves the connection problem, you've found the culprit.

IP forwarding is disabled by default for security reasons.

---

### Post by Lordhowe on 2013-02-06
> **aromo said:**
> Are you sure? If your default gateway is in a different subnet how are you going to reach it?
 
Your gateway may have multiple IP addresses, one for each subnet, and machines in each segment have to point the corresponding gateway interface as the default gateway AFAIK.
 
My gateway has a setting that allows multiple subnets to connect through it. In Win server, I can set the DFG to point to that router (but be on either subnet), and it works fine. Ubuntu won't allow me to do that.

---

### Post by Lordhowe on 2013-02-06
> **SeijiSensei said:**
> Have you enabled IP forwarding in /etc/sysctl.conf? Read the comments in that file and remove the hash mark from the line "net.ipv4.ip_forward=1". Then reboot.
 
For a quick test without rebooting run the command:
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```
 
If that solves the connection problem, you've found the culprit.
 
IP forwarding is disabled by default for security reasons.
 
Thanks, but I've checked that IP forwarding is enabled, and it is. 
 
I played around with this some more tonight. I was able to add some routes using the following command:
 
sudo route add -net 192.168.101.0 netmask 255.255.255.0 gw 192.168.104.253 dev eth1
 
It allowed me to add the route, but still no dice as the issue is coming from users connecting to the ppp0 interface (via vpn connection). I also tried the same command substituting 'eth1' with 'ppp0', but that basically broke the vpn connection entirely :rolleyes:
 
So, I'm still back at the drawing board and trying to figure out how to allow users connecting via vpn on one subnet to connect to another subnet. It should be noted that the users connecting have the 'use default gateway of remote network' setting disabled (this was done to not tie up their local traffic). So, when they connect and do an ipconfig (again, these are all windows clients), it does not show a default gateway for the ppp connection.

---

