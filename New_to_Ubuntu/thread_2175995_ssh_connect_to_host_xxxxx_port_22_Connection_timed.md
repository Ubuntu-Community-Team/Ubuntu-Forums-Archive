---
title: "ssh: connect to host xxxxx port 22: Connection timed out"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by yaslinush on 2013-09-22
hi group
im try to connect to uni server with ssh but give time out error.im give this cammand:
ssh user@ip
ssh: connect to host 192.168.29.59 port 22: Connection timed out

---

### Post by Lars Noodén on 2013-09-22
There are several possible causes.  One is that you are pointing to the wrong server, maybe the address is different to the outside or there is a gateway.  Another could be that there is a firewall misconfigured to block incomming ssh connections.  A third possibility is that the ssh server is listening on another port than the standard port.  A fourth is that the ssh server wasn't started on that machine.  

Have you been able to connect to that server before via SSH on a different network?

---

### Post by yaslinush on 2013-09-22
im connect to server with this ip and ssh cammand .firewall mis configured?

---

### Post by Lars Noodén on 2013-09-22
The address you give is for a private subnet, 192.168.0.0/24  If you are outside that subnet, say at home while the machine is at school, then you cannot connect without using a gateway or a jump host or a (ugh) a VPN.

---

### Post by dhuckle3 on 2013-09-22
When i'm having connection issues I tend to go through a basic sanity check:

1) Can I ping the IP address of the machine that I'm trying to access?
```
pint HOSTNAME
```
2) Can I telnet to the port of the machine that I want to connect to? If yes, then the issue doesn't appear to be on the client side. Try connecting with the service. If I can cool, otherwise
```
telnet HOSTNAME PORT
```
3) Check/Ask someone to check the server. On the server check if anything is listening on the port the client is attempting to connect
```
ps -aux | grep "PORT_NUMBER"
```
If nothing is listening on that port the service probably isn't running try restarting it. In your case:
```
service sshd restart
```

Retry connecting, then if i'm still unsuccessful then I start digging into firewall issues or something else.

---

### Post by yaslinush on 2013-09-22
the server is located in the University., And I was connected to the server of the University.and now im connected to uni internal network.but ssh doesn't work for connect to server

---

### Post by Lars Noodén on 2013-09-22
Right.  But you are probably on a different network now than you were before.  In order to connect to a machine on a private subnet you generally have to either be on the same subnet or else use a jump host.  Have you moved to a different building or different facility?

What network are you on now?

```

ifconfig eth0

```

---

### Post by yaslinush on 2013-09-22
im connect to net with home adsl and create vpn with uni gateway.
eth0      Link encap:Ethernet  HWaddr 64:31:50:12:8f:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by yaslinush on 2013-09-22
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.20.160.150  P-t-P:10.10.10.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:6409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3789157 (3.7 MB)  TX bytes:1414691 (1.4 MB)

---

### Post by Lars Noodén on 2013-09-22
> **yaslinush said:**
> inet addr:172.20.160.150  P-t-P:10.10.10.5  Mask:255.255.255.255

You're on a different subnet and the network administrators appear to have not set up routing between the networks.  So I doubt you can even ping the server from the network you are on:

```

ping 192.168.29.59

```

If there are a lot of people connecting via SSH, the network administrators probably have arranged a solution.  Is there a jump host or gateway available that sits on both networks?

---

### Post by yaslinush on 2013-09-22
no one use it.just me now

---

### Post by Lars Noodén on 2013-09-23
Can your VPN be used to connect to a different network?  To reach the server you want, you have to have it connect to the same network as the server.

---

