---
title: "[SOLVED] please read"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by kennster on 2008-07-08
i dont know much about networking with linux so bare with me plz but i left internet worked fine i came home 2days later "and a thunder stomr or too" and now i cant connect to the internet last time this happend i took the battery outta the mobo to restart the bios and it fixed it this time nuttin any ideas or need me to post any info? and im useing the 64bit hardy version of ubuntu

ps i put please read because for some reasion when i post people dont hardly read or respond

---

### Post by chetan.89 on 2008-07-08
Hi kennster !

I don't know what your exact problem is and removing your battery and putting it again won't help you in any way if you have problems with connecting to the internet.

Please describe more about your problem. Ex: How you are connected to the i'net ?

Try - System-->Help and Support to connect and if you still have problems come here and post. 

Regards,
Chetan.

---

### Post by webofunni on 2008-07-08
Hi,

  What is the result of following commands : 

```
sudo ifconfig

sudo cat /etc/resolv.conf
```

---

### Post by kennster on 2008-07-08
```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:73:ca:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:248 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:18:f3:73:d7:eb  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe73:d7eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37842 (36.9 KB)  TX bytes:110107 (107.5 KB)
          Interrupt:249 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89910 (87.8 KB)  TX bytes:89910 (87.8 KB)

```sudo cat /etc/resolv.conf```


### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5179
#
### END INFO

search tampabay.rr.com





nameserver 65.32.5.111
nameserver 65.32.5.112


```

btw it is from a router to a wireless rougter but i have a wire from the wirless router to the computer im on mylaptop atm

---

### Post by lisati on 2008-07-08
I'm wondering if we're talking literal or metaphorical thunder storms here.

Sometimes bad weather can affect a telco's wiring on the street. Last year, water getting into the underground cables between my place and the telco's local exchange messed with my phone connection. Funny thing, though was, at one point the phone was out but ADSL was working but no phone, and at other times it was no ADSL but a noisy phone line.

---

### Post by kennster on 2008-07-08
> **lisati said:**
> I'm wondering if we're talking literal or metaphorical thunder storms here.

Sometimes bad weather can affect a telco's wiring on the street. Last year, water getting into the underground cables between my place and the telco's local exchange messed with my phone connection. Funny thing, though was, at one point the phone was out but ADSL was working but no phone, and at other times it was no ADSL but a noisy phone line.

real thunderstorms cuz i live in FL and its been raining and well everone sed it rainded pretty bad and that the power might have went out while they were at work... i wasnt home so i dont know but eather way its strange... that the wirless works the olny computer that donst work fine is my desktop running ubuntu 64bit hardy... and the olny problem is it will not get online

---

### Post by webofunni on 2008-07-08
Are you able to ping the nameservers ? 

```
ping 65.32.5.112
ping 65.32.5.111

```

---

### Post by kennster on 2008-07-08
> **webofunni said:**
> Are you able to ping the nameservers ? 

```
ping 65.32.5.112
ping 65.32.5.111

```
ima guess yes because it ses "from 192.168.1.101 icmp_seq=1 destination host unreachable" and the olny thing that chagne's is icmp_seq=1-200+

both say ping 65.32.5.111 (65.32.5.111) 56 (84) bytes of data 
ping 65.32.5.112 (65.32.5.112) 56 (84) bytes of data

---

### Post by kennster on 2008-07-08
humf...

---

### Post by hyper_ch on 2008-07-08
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by crazyness003 on 2008-07-08
Theres a whole bunch of things that coulda gone wrong. The probelm is that all (if not, most) are hardware related.
1. Modem died (probably not since your on the net)
2. Router(s) died (same as above)
3. Your service died (again same as above)
4. Infrastructure failure (wires form your comp to the isp)
5. You have a windows machine in the house (im serious...it happens :roll:)
or
6. Your NIC died or got fried.

Again, i dont fully understand your problem tho. How are you currenly connected?
According to your previous posts, it seems like the actual machine is ok.

---

### Post by kennster on 2008-07-08
> **crazyness003 said:**
> Theres a whole bunch of things that coulda gone wrong. The probelm is that all (if not, most) are hardware related.
1. Modem died (probably not since your on the net)
2. Router(s) died (same as above)
3. Your service died (again same as above)
4. Infrastructure failure (wires form your comp to the isp)
5. You have a windows machine in the house (im serious...it happens :roll:)
or
6. Your NIC died or got fried.

Again, i dont fully understand your problem tho. How are you currenly connected?
According to your previous posts, it seems like the actual machine is ok.

i am on my mac book at the moment i have my desktop up and running with no internet next to me. so 1-3 are not the problem 4 i dont think is the problem and yes i have 2 outher windows computers running atm and 1 mac. but what do you mean my NIC fried?

---

### Post by crazyness003 on 2008-07-08
> **kennster said:**
> i am on my mac book at the moment i have my desktop up and running with no internet next to me. so 1-3 are not the problem 4 i dont think is the problem and yes i have 2 outher windows computers running atm and 1 mac. but what do you mean my NIC fried?

Your ethernet card (network interface card aka NIC). I say this because back in the day when dialup was the way, a t-storm fried my modem (and powersupply and tv, and phone)
You guessed it, I too live in Florida

---

### Post by kennster on 2008-07-08
my Etho card is in my mobo and it still works cuz i can ping my router... at least i think its pining idk what to look for good old fl what part polk county here

---

### Post by crazyness003 on 2008-07-08
> **kennster said:**
> my Etho card is in my mobo and it still works cuz i can ping my router... at least i think its pining idk what to look for good old fl what part polk county here

Ok. well, thet rules out any hardware failures. I still cant see how an electric storm can directly affect software and not cause any hardware failures. Anything can happen.

All i can say is check for MAC filtering on you router and see if your network interface is configured correctly.

/etc/network/interfaces
/etc/udev/rules.d/70-persistent-net.rules

you need root privelages to modify (so be careful)

---

### Post by kennster on 2008-07-08
> **crazyness003 said:**
> Ok. well, thet rules out any hardware failures. I still cant see how an electric storm can directly affect software and not cause any hardware failures. Anything can happen.

All i can say is check for MAC filtering on you router and see if your network interface is configured correctly.

/etc/network/interfaces
/etc/udev/rules.d/70-persistent-net.rules

you need root privelages to modify (so be careful)

 i dont think your understanding im on my MAC at the momment and it works fine so do the PC (windows) just the computer in my room running linux dosent seem to work for some reasion it seems to be when the internet get's shut off all of a sudden it will not reconnect , last time it was a bios error frineds dad figuered that one out told me to take the bat outta the mobo and put it back in to reset it that worked tryed it again and nuttin... but u think it could be the router never had that problem befor?

---

### Post by kennster on 2008-07-08
> **crazyness003 said:**
> Ok. well, thet rules out any hardware failures. I still cant see how an electric storm can directly affect software and not cause any hardware failures. Anything can happen.

All i can say is check for MAC filtering on you router and see if your network interface is configured correctly.

/etc/network/interfaces
/etc/udev/rules.d/70-persistent-net.rules

you need root privelages to modify (so be careful)

Solved it is a router / software ishue <--spell check but i had did the unplug the routher plug it back in thing was looking at it and saw a restart button and that fixed it idk how but it did
any idea on a good router to use? cuz it seems any time this one drops signal or loses power it messes up and being in FL losing power is quite common :D lol but ty yalls help

---

### Post by crazyness003 on 2008-07-09
> **kennster said:**
> Solved it is a router / software ishue <--spell check but i had did the unplug the routher plug it back in thing was looking at it and saw a restart button and that fixed it idk how but it did
any idea on a good router to use? cuz it seems any time this one drops signal or loses power it messes up and being in FL losing power is quite common :D lol but ty yalls help

Iv had the best luck with d-link, but when i was away for a while (i was in Europe...w00t), it got fried by the swell Florida Storms (Volusia). 
Now im using a Belkin and im not happy with it. Also, i read that belkins have issues with apple macs. 
Dont even get me started on linksys...the wrt54g i had was a bust, but i got the one right after they switched from the linux firmware to the propriatary one (go figure, huh). 
Never actually used Netgear, i had one that someone gave me, but i accidently broke the anntena off, so i was getting extremely bad reception, so i diched it immediately. 
All in all, iv had the best luck with D-Link (not 100% tho, dont get me wrong)

those are the major ones, and im talking about the wireless G era, so i know nothing about the N ones (be careful N still hasent been finalized, as far as i know, even tho they say theres gonna be compatability)

Happy hunting, and good to hear your problem is (semi)solved

---

