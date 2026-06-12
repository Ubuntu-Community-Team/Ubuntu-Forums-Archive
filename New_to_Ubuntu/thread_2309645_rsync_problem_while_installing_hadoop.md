---
title: "rsync problem while installing hadoop"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by Sara__Alizadeh on 2016-01-12
hello guys,
i have a windows8.1 on my laptop. and a VMware on it. which has 2 ubuntu 14.04 on intself.
i try to install hadoop on them. i have a problem running this code on my slave node:
sudo rsync -avxP /usr/local/hadoop/ hduser@HadoopSlave1:/usr/local/hadoop/the answer i get is:

ssh: connect to host hadoopslave1 port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(226) [sender=3.1.0]

before i explain what i did to solve it, i should mention that i have set these ip addresses by this code in both VMs:
# Edit the /etc/hosts file with following command
sudo gedit /etc/hosts

# Add following hostname and their ip in host table
192.168.2.14    HadoopMaster
192.168.2.15    HadoopSlave1
and my laptop is connected to internet via a wifi connection.

so i took these steps:
made sure port 22 in listening(it was not before)
made sure my firewall is inactive(it was)
made sure my ssl is installed and running on both VMs(it was)
changed network setting of my VMs to bridged mode(it was NAT)
then i tried to ping:
   on VM with 192.168.2.14 ip address: ping 192.168.2.14 --->got reply
                                                     ping 192.168.2.15 --->got nothing,even timeout. so i had to terminate the process
   on VM with 192.168.2.15 ip address: ping 192.168.2.14 --->got reply
                                                     ping 192.168.2.15 --->got nothing,even timeout. so i had to terminate the process

these are what i get from ifconfig:
saralinux@HadoopSlave1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:b1:20:6b  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feb1:206b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67099572 (67.0 MB)  TX bytes:721269 (721.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80871 (80.8 KB)  TX bytes:80871 (80.8 KB)

saralinux@HadoopMaster:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:0e:c0:c8  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe0e:c0c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:464953 (464.9 KB)  TX bytes:919067 (919.0 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146334 (146.3 KB)  TX bytes:146334 (146.3 KB)




despite doing all these...the problem is unsolved :(

---

### Post by nerdtron on 2016-01-12
192.168.2.14    HadoopMaster
192.168.2.15    HadoopSlave1

and 

saralinux@HadoopMaster:~$ ifconfig
inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0

saralinux@HadoopSlave1:~$ ifconfig
inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0


These are two different network blocks.
Can you try to ping each IP address as listed on ifconfig? these are the real IP addresses of the VMs. Is that successful?

---

### Post by Sara__Alizadeh on 2016-01-12
yes,i got reply from these ip addresses

---

### Post by nerdtron on 2016-01-12
If you have reply using the ip addresses, 192.168.1.115 and 192.168.1.116, then those are the correct IP addresses you should use on the rsync command.

Also, change the /etc/hosts to update the correct IP addreses:
```

192.168.1.116 HadoopMaster
192.168.1.115 HadoopSlave1

```

---

### Post by Sara__Alizadeh on 2016-01-13
yes!this worked!
thanks a lot!=d>=d>=d>=d>
and to those who might have the same problem...the IP addresses change everytime i change my network.so i have to reset them to new values respectively!

---

