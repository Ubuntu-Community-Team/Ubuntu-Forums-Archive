---
title: "how open port in ubuntu"
date: 2015-11-01
forum: New to Ubuntu
---

### Post by rony19812 on 2015-11-01
Hi there
I am very new to this forum and i hope you could understand my poor english..
I have ubuntu 14.04 desktop with 2 network card in it 
1- eth0 is connected to the router which is wan connect
2- eth1 connect to another ubuntu desktop and i get this 
eth1      Link encap:Ethernet  HWaddr 00:02:b3:d1:69:43  
            inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
my quastion is how i open port 34422 to the second desktop to get remotly in it .

please do not forget i am new to ubuntu ..

---

### Post by Frogs Hair on 2015-11-01
Hello and Welcome

Linked is some documentation for using UFW- Uncomplicated Firewall. 

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

   
Remote SSH if applicable: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by sandyd on 2015-11-01
> **rony19812 said:**
> Hi there
I am very new to this forum and i hope you could understand my poor english..
I have ubuntu 14.04 desktop with 2 network card in it 
1- eth0 is connected to the router which is wan connect
2- eth1 connect to another ubuntu desktop and i get this 
eth1      Link encap:Ethernet  HWaddr 00:02:b3:d1:69:43  
            inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
my quastion is how i open port 34422 to the second desktop to get remotly in it .

please do not forget i am new to ubuntu ..

By default, Ubuntu does not have any firewall rules enabled and automatically closes and opens ports.

If you do not have any custom firewall rules, both computers can ping each other, and the application (not sure what application you are using) is bound to port 34422, you should be able to access the first computer remotely from the second.

**Checking for firewall rules**

Run the following command to show firewall rules in the filter table.
```

sudo iptables -L
```
It should list all of your IPTables rules. If there are any, post them here.
Here is what an empty (no rules) output looks like:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

**Testing Ping**
Run the following to test the ping from the second computer. It should not return any errors or blank output.
```

ping -c10 10.42.0.1

```
A sample no-errors output:
```

PING 10.2.1.1 (10.2.1.1) 56(84) bytes of data.
64 bytes from 10.2.1.1: icmp_seq=1 ttl=63 time=28.1 ms
64 bytes from 10.2.1.1: icmp_seq=2 ttl=63 time=27.7 ms
64 bytes from 10.2.1.1: icmp_seq=3 ttl=63 time=28.1 ms
64 bytes from 10.2.1.1: icmp_seq=4 ttl=63 time=27.5 ms
64 bytes from 10.2.1.1: icmp_seq=5 ttl=63 time=27.4 ms
64 bytes from 10.2.1.1: icmp_seq=6 ttl=63 time=27.6 ms
64 bytes from 10.2.1.1: icmp_seq=7 ttl=63 time=27.3 ms
64 bytes from 10.2.1.1: icmp_seq=8 ttl=63 time=27.4 ms
64 bytes from 10.2.1.1: icmp_seq=9 ttl=63 time=27.7 ms
64 bytes from 10.2.1.1: icmp_seq=10 ttl=63 time=27.6 ms

--- 10.2.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 27.321/27.691/28.189/0.321 ms
```

**Check application binding**
If you want to check whether the the application is binding correctly, you can run
```

sudo lsof -i :34422
```
It should give output similar to
```

dhclient 651 root   20u  IPv4  10325      0t0  UDP *:6380
```

The name of the application "dhclient" and the port "6380" are obviously different, this is just an example.

When you get the output, there is one main thing you are looking for, which is the last column of output (the NAME column). This column indicates how the application is binding to the port.

A star in front of the port ```
*:*portnumber*
``` indicates that that it is binding to all IP Addresses on the system.
Anything else, such as ```
127.0.0.1:*portnumber*
``` indicates that this is bound to a port.
If there is an arrow (->), ```
10.5.1.100:4506->111.111.111.111:111 (ESTABLISHED)
```this indicates a connection between two IP Addresses. The ip/port on the left the arrow is the local ip/port on the system, while the ip/port on the right of the arrow is the remote ip/port on the system. The part in the quotes shows the current status of the connection if the connection is TCP.

Note that you will find that sometimes, instead of an IP address, there is a set of words; that is just the reverse DNS of the IP Address.

In this case, you either want to have a star in front of the port, or it should be bound to the IP of 10.42.0.1. If there is no output, nothing is listening on the port.

---

### Post by rony19812 on 2015-11-08
Thank you for your replay , but i did not succeed . so i tried another connecting
i have ubuntu 14.04 in desktop with 2 network card 
the first one (eth0) connect to router with WIRE and i get ip 192.168.1.5
the second network (eth1) i connect dreambox and get ip 10.42.0.40 . i can open the dreambox web in this desktop by 
10.42.0.40 but how i can get into dreambox web from another pc ??

---

