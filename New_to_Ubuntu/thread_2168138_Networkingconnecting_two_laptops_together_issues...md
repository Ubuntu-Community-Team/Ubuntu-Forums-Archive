---
title: "Networking/connecting two laptops together issues..."
date: 2013-08-16
forum: New to Ubuntu
---

### Post by grouchyolddude on 2013-08-16
I've been running ubuntu for a few years, but this is the first time I've tried to do ANY networking on my own. So I may appear ignorant.
  I have my Dell vostro 1000 connected to the internet via wireless. I have a Sharp Note book connected via ethernet cable to the Dell. 
I can't seem to get the Sharp to connect to the internet so I can seek help here getting the wireless card  (broadcom card) to work. I can't DL drivers etc. 
The Sharp has ubuntu 9.01 (I believe) installed on it. 
When I click on the network connections icon, it shows Wired connection Auto etho as available. But won't connect. 
  I probably need step-by step setup instructions. Do I need to set ip's  net mask etc? I searched but failed to find a link/thread that dealt with it specifically.

---

### Post by sandyd on 2013-08-16
> **grouchyolddude said:**
> I've been running ubuntu for a few years, but this is the first time I've tried to do ANY networking on my own. So I may appear ignorant.
  I have my Dell vostro 1000 connected to the internet via wireless. I have a Sharp Note book connected via ethernet cable to the Dell. 
I can't seem to get the Sharp to connect to the internet so I can seek help here getting the wireless card  (broadcom card) to work. I can't DL drivers etc. 
The Sharp has ubuntu 9.01 (I believe) installed on it. 
When I click on the network connections icon, it shows Wired connection Auto etho as available. But won't connect. 
  I probably need step-by step setup instructions. Do I need to set ip's  net mask etc? I searched but failed to find a link/thread that dealt with it specifically.

You will need to set a static IP for each computer

For example, you can try using this
On each computer, change the networking settings from DHCP (Automatic) to manual. Enter the below in the ipv4 tab

Computer 1:
IP Address: 192.168.10.3
Netmask: 255.255.255.0

Computer 2:
IP Address: 192.168.10.4
Netmask: 255.255.255.0

Save it, and computer 1 should be able to ping 192.168.10.4 and computer 2 should be able to ping 192.168.10.3

Caveat:Some ethernet cards dont do MDI/MDIX (autodetecting if its a straight through or crossover cable). All gigabit cards do. If you are not using a crossover cable, and its not working, make sure you have MDI/MDIX on both computer's ethernet cards. Most computers produced within the last few years or so should have them.

---

### Post by grouchyolddude on 2013-08-16
hmmm.. I added 192.168.1.113 and 255.255.255.0 to the ipv4 tab hit 'apply' it saved it it appears. Still can't ping each other?? 
ip of the Dell is 192.168.1.112 and mask 255.255.255.0 Should I need to reboot the Sharp? It tries to connect, but fails.

---

### Post by sandyd on 2013-08-16
> **grouchyolddude said:**
> hmmm.. I added 192.168.1.113 and 255.255.255.0 to the ipv4 tab hit 'apply' it saved it it appears. Still can't ping each other?? 
ip of the Dell is 192.168.1.112 and mask 255.255.255.0 Should I need to reboot the Sharp? It tries to connect, but fails.

Can you post the output of
```

ifconfig
```
on each computer?

---

### Post by grouchyolddude on 2013-08-16
> o@o-Vostro-1000:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:80:d6:28  
          inet6 addr: fe80::219:b9ff:fe80:d628/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10872 (10.8 KB)  TX bytes:9509 (9.5 KB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1c:26:06:92:d8  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe06:92d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19261 errors:0 dropped:0 overruns:0 frame:6501
          TX packets:19103 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14621571 (14.6 MB)  TX bytes:3439681 (3.4 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4632 (4.6 KB)  TX bytes:4632 (4.6 KB)
on the Dell.. 
  ifconfig got no return/nothing from the Sharp. However ifconfig -a did. 
> Link encap:Ethernet HWaddr oo:40:d0:6c:63:87
inet6 addr: fe80::240:d0ff:fe6c:6387/64 Scope:link
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
RX packets: 18 errors:0 dropped:0 overruns:0 frame:0
TX packets: 36 errors: 0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:6228 (6.2KB) TX bytes: 10873 (10.8 KB)
Interrupt 16

Link encap:local loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 METRIC:1

RX PACKETS TX PACKETS collisions all show 0

sorry it took me a bit to type that all in

---

### Post by grouchyolddude on 2013-08-16
Okay.. I followed the instructions here .. [http://ubuntuforums.org/showthread.php?t=1192331&p=7490040#post7490040](http://ubuntuforums.org/showthread.php?t=1192331&p=7490040#post7490040) and no have a "wired connection" established. But still no internet access, nor will the machines ping on another. the Vostro won't even ping itself/ip. But the Sharp will w/ 100% success on 5 packages.  ???? I'm really lost on that

---

### Post by sandyd on 2013-08-16
> **grouchyolddude said:**
> Okay.. I followed the instructions here .. [http://ubuntuforums.org/showthread.php?t=1192331&p=7490040#post7490040](http://ubuntuforums.org/showthread.php?t=1192331&p=7490040#post7490040) and no have a "wired connection" established. But still no internet access, nor will the machines ping on another. the Vostro won't even ping itself/ip. But the Sharp will w/ 100% success on 5 packages.  ???? I'm really lost on that

Looks like networkmanager isnt setting your IPs properly
The above ifconfig output shows that both eth0 interfaces on both computers do not have an ip address

Try setting the IP manually with the commands below

Computer 1:
```

sudo ifconfig eth0 192.168.10.3 netmask 255.255.255.0 up
sudo ifconfig eth0

```

Computer 2:
```

sudo ifconfig eth0 192.168.10.4 netmask 255.255.255.0 up
sudo ifconfig eth0

```

---

### Post by grouchyolddude on 2013-08-16
> o@o-Vostro-1000:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:19:b9:80:d6:28  
          inet addr:192.168.10.3  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe80:d628/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71395 (71.3 KB)  TX bytes:12560 (12.5 KB)
          Interrupt:21 

the Sharp (computer 2) will now ping the vostro succesfully, but vostro computer 1) fails on packages sent to  computer 2
thanks so much for taking the time n effort to help me. THAT's what I love about linux :)

---

### Post by sandyd on 2013-08-16
> **grouchyolddude said:**
> the Sharp (computer 2) will now ping the vostro succesfully, but vostro computer 1) fails on packages sent to  computer 2
thanks so much for taking the time n effort to help me. THAT's what I love about linux :)
No problem :)

Lets check if the ip is in the arp table.

Run
```

arp -n
```

On the vostro

---

### Post by grouchyolddude on 2013-08-16
o@o-Vostro-1000:~$ arp-n
No command 'arp-n' found, did you mean:
 Command 'arpon' from package 'arpon' (universe)
arp-n: command not found
o@o-Vostro-1000:~$

---

### Post by sandyd on 2013-08-16
Thats a typo, should be ```
arp -n
```

Sorry about that

---

### Post by grouchyolddude on 2013-08-16
> o@o-Vostro-1000:~$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:23:69:a7:53:b4   C 

I shoulda know it needed a space in there

---

### Post by sandyd on 2013-08-16
> **grouchyolddude said:**
> I shoulda know it needed a space in there

So the IP isnt even in the arp cache....
[s]/me is stumped at the moment, and will take another look in the morning[/s]

Actually, can you post the output of
```

route -n
```

Since there are two interfaces, you need a route so that the system knows what interface to go out of

---

### Post by grouchyolddude on 2013-08-17
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by sandyd on 2013-08-17
Below command should add the route on the computer
```

sudo ip route add 192.168.10.0/24 dev eth0
```

---

### Post by grouchyolddude on 2013-08-17
o@o-Vostro-1000:~$ sudo ip route add 192.168.10.0/24 dev eth0
RTNETLINK answers: File exists

---

### Post by grouchyolddude on 2013-08-17
but the connection to the Sharp now keeps disconnecting ,connecting, disconnecting  .. uhg!

---

### Post by sandyd on 2013-08-17
> **grouchyolddude said:**
> but the connection to the Sharp now keeps disconnecting ,connecting, disconnecting  .. uhg!

so both computers can ping now?

---

