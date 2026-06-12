---
title: "Need help with internet connection"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-18
I am a bit confuse right now. In my understanding, whenever we switch on wireless, ethernet connection will be suspended and our system will automatically switch to wireless connection. If we disconnect wireless, our connection will use ethernet automatically so we would not experience connection intermission during the process. Is that correct? 
However in my case, if I turn on the wireless (without unplugging the Ethernet cable), I will lose internet connectivity because wireless fail to take over. In my conky, I can see my ESSID and IP address (mean wireless is working), but internet is still disconnected.

How do I made automatic switching between wireless and ethernet without bother to open Network Manager. Hope someone can assist me

---

### Post by wariskampar on 2008-08-18
Does anyone has something to offer me

---

### Post by wariskampar on 2008-08-18
Hello, really hope someone will come to the rescue. I check into my /etc/network/interfaces:

auto lo
iface lo inet loopback

That are the only lines. Is it normal or do I need to add anything to achieve my objective

---

### Post by wariskampar on 2008-08-18
I hope someone will be kindly enough to help me sort out my problem. I notice after one successfully wireless session, new line appear in /etc/networking/interfaces:

```
auto lo
iface lo inet loopback











iface eth1 inet dhcp
wpa-psk xxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid xxxxxxxxxx (my ESSID)

auto eth1
```

However, wpa-psk key is different than my actual WPA password. Can that be the problem. can I just manually alter it.

---

### Post by john test on 2008-08-18
Looks like you are about to work your way into a solution with no help from the regulars. :-)
The wpa key/passphrase on the local machine has to match the passphrase on the wireless router.
Can you post your ifconfig?
The inet lines shold show the ipv4 addresses for lo, eth0 and eth1,  and it should which interface is up and which is down.

You might usse a script to do the switch using ifup and ifdn

---

### Post by wariskampar on 2008-08-18
At last someone return my call. Thanks john. I tried to change the wpa-psk manually according to my router but when I fire up wireless, the key will change. I am not sure whetehr the key is similar to the one before though. This is my ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:d2:f0:44  
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fed2:f044/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:18405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16846657 (16.0 MB)  TX bytes:1788505 (1.7 MB)
          Interrupt:18 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:01:b5:1c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe01:b51c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:3 dropped:3 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1408811 (1.3 MB)  TX bytes:217342 (212.2 KB)
          Interrupt:18 Base address:0xc000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:166859 (162.9 KB)  TX bytes:166859 (162.9 KB)
```

My wireless is eth1. As for /etc/network/interfaces, there is no entry for eth0. Maybe lo handles wired connection. 

Now, my ethernet will automatically re-connect when I plug in the cable (some improvement).

---

### Post by john test on 2008-08-18
No lo is your loopback address 
eth0 and eth1 both show as "UP" and both have ip addresses in the same subnet and both are pointing toward the same default gateway.
That leaves the WPA encryption as an issue.
I don't know enough about wireless encryption to advise you but I have never seen a wireless passphrase change except when manually changed.
Are you saying that the wpa passphrase matches the passphrase on the router while wireless isturned off and then changes to something else when you turn wireless on?
How are you viewing the passphrase?
What process do you use to switch between wireless and ethernet?

---

### Post by wariskampar on 2008-08-18
I use default Ubuntu Network Manager to manage internet connection. If I want to use wireless, I will 'Manual Configure..' and disable Wireless roaming (after providing ESSID and passphrase in the respective column). Even though, it is already disable, I still need to re-do it otherwise wireless will fail. 

Like you say, probably WPA is the issue. Once I get it to fix the problem will solved. DO I need to add anything in /etc/network/interfaces

---

### Post by john test on 2008-08-19
Are there other computers on your network that successfully connect wirelessly?
Can this computer successfully connect wirelessly to another router?

---

