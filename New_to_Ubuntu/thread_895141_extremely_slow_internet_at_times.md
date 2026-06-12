---
title: "extremely slow internet at times"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-08-19
it seems every night my ubuntu firefox runs slow as can be, like dial up and i have cable. i disabled ipv6 in firefox 3.1 and blacklisted ipv6 in ubuntu and still no improvement. im not sure if this problem is from my internet provider or the system ? it's driving me crazy and i just checked my vista install and it's ok there. i need some advice here guys. :confused:

---

### Post by nicedude on 2008-08-19
Well I doubt it is your provider if you say that when it happens you can boot into Vista and it is fine. Normally vista should be the slow one ( all those nazi like checks to make sure you didn't steal anything from MS :-) ). I have a few questions that would help me or others figure this out.

1. Is this the only PC hooked up to your internet connection?

2. Are you using Wifi or Wired connection to your router or modem?

3. Does your Ubuntu computer ever have fast internet like it should be or is this just at certain times and at others it is normal ?

4. When you are having slow speeds do you have any kind of downloading going on such as frostwire or a bit torrent program ?

Also the following commands output might help someone see something that is wrong. So run these and paste the outputs here in your thread.

ifconfig

lshw -C Network

Please answer those and post the commands above outputs and I will look at it for you. You might also run an internet speed test and see what speed you are getting and whether it is close to what you are paying for. To do a speed test just google "speed test" and the first 3 or 4 will be free internet speed tests just use one and tell us the result of that too.

---

### Post by smooth3006 on 2008-08-20
> **nicedude said:**
> Well I doubt it is your provider if you say that when it happens you can boot into Vista and it is fine. Normally vista should be the slow one ( all those nazi like checks to make sure you didn't steal anything from MS :-) ). I have a few questions that would help me or others figure this out.

1. Is this the only PC hooked up to your internet connection?

2. Are you using Wifi or Wired connection to your router or modem?

3. Does your Ubuntu computer ever have fast internet like it should be or is this just at certain times and at others it is normal ?

4. When you are having slow speeds do you have any kind of downloading going on such as frostwire or a bit torrent program ?

Also the following commands output might help someone see something that is wrong. So run these and paste the outputs here in your thread.

ifconfig

lshw -C Network

Please answer those and post the commands above outputs and I will look at it for you. You might also run an internet speed test and see what speed you are getting and whether it is close to what you are paying for. To do a speed test just google "speed test" and the first 3 or 4 will be free internet speed tests just use one and tell us the result of that too.

1. yes its the only pc
2. wired connection to my cable modem
3. it seems to be really slow every evening and at certain parts of the day.
4. its just slow all of the sudden, im not downloading anything or running any p2p at the time.
5. i also made sure i disabled ipv6 and it seemed to help a bit. i just don't feel this should happen. 


eth0      Link encap:Ethernet  HWaddr 00:01:29:a4:5b:13  
          inet addr:71.205.142.250  Bcast:255.255.255.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2714500 (2.5 MB)  TX bytes:503365 (491.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2700 (2.6 KB)  TX bytes:2700 (2.6 KB)


WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 22
       serial: 00:01:29:a4:5b:13
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=71.205.142.250 latency=0 module=sky2 multicast=yes


heres my speed test results :

[IMG]http://www.speedtest.net/result/311496088.png[/IMG]

---

### Post by vikramaditya on 2008-08-20
hmmm...wonder if comcast is up to their "network management" tricks again.

---

### Post by smooth3006 on 2008-08-20
> **vikramaditya said:**
> hmmm...wonder if comcast is up to their "network management" tricks again.

i dunno but it drives me nuts at times.

---

### Post by smooth3006 on 2008-08-20
has anybody had a chance to look at the requested outputs i posted ? i just want to make sure everything looks ok ?

---

### Post by LowSky on 2008-08-20
everything seems fine

It looks as if Comcast is throttling your connection through out the day. When you speed slows down, unplug the modem and plug it back in. I bet the speed will come back up. Thats why its fine when you switch to Vista, you getting a new MAC adress for each OS.

---

### Post by pi.boy.travis on 2008-08-20
I had the same problem here with an old cable modem used with Road Runner.  Only every couple of days though. . .

---

### Post by nicedude on 2008-08-20
Man everything looks fine in your post of output commands. You show zero errors or dropped packets. Your speed test results make me jealous as you have 20MB a second Internet and are actually getting most of that promised speed but I am assuming at the time of that scan you were not experiencing any slowdowns? There is nothing to suggest any problems at all and your adapter looks like it is using a IPv4 address as well. I would suggest that the next time you experience the slowdown to run the commands I will give you at the end of this message and PM them to me so I can tell you where your connection is slowing down as I believe it will be discovered that it lies either on Comcast or their backbone provider to the Internet. If so though there isn't much you can do since all the cable companies I know of have a clause of "such and such speed or best effort" in their contracts and will usually blame such slowdowns on their networks being overloaded and hence the slowdown. You see their network isn't built to support all the people they sell services to for the maximum download rate all at the same time ( BS to me but hey they get away with it, kinda like banks as if everyone goes in and wants their money out on the same day the bank doesn't have it ) 

Here are some commands I would like you to run the next time it slows down and PM to me ( if ping isn't installed by default then install it, I think it is but I don't remember for sure but you will have to install traceroute and I give the command to do that easily )

sudo apt-get install traceroute

ping -c 3 [www.google.com](www.google.com)

traceroute [www.google.com](www.google.com)

Please don't post those outputs here but send to me via PM.

---

### Post by drubin on 2008-08-20
This thread makes me want to cry living in South Africa.  :(

---

### Post by LowSky on 2008-08-20
This is mine at work, direct T1 gotta love it

[IMG]http://www.speedtest.net/result/311586922.png[/IMG]

---

### Post by nicedude on 2008-08-20
Ok lowsky I officially hate you :-) Just kiddin but that does make me extremely jealous but hey who can seed torrents to me at 30MB a sec not many so I will continue to think of downloading as fishing with a net, you put the net out at night with lots of fish in mind. Then in the morning you check your nets and see what has been caught in the net :-)

---

### Post by smooth3006 on 2008-08-20
thanks guys i appreciate the advice. ill send you a pm when or if it occurs again. what do you mean by comcast must be throttling my connection ? can they do that ?

---

### Post by nicedude on 2008-08-20
Throttling is when they on purpose slow down your internet connection, I doubt however that this problem is due to throttling as that is used against people they think are downloading large amounts of data. If you are not downloading anything and instead are experiencing slow Internet speed when just browsing then I would bet this is due to their equipment not being able to handle the load of all the users trying to use their system. This would further make sense because you say this behavior occurs in the evening which is when there would be peak traffic. By using traceroute you can at least see at what point the data is getting poor throughput and if it is on a Comcast server you can call and complain. It might get you a few bucks off your bill or promises to fix the situation but irregardless of what they say the more calls they get with complaints the more likely they are to try and do something about it ( sqeaky wheel does get the grease sometimes ). Also there is a small chance that they have some problem with their equipment in your immediate area or neighborhood and this might spur them to at least check it out. Also as far as I know I thought they were supposed to cease throttling in the USA at least ( not for my friends in Briton though ) and so they should not be doing this ( but hey they are a big corporation and might just break the law as I doubt Bush Jr cares if they say they are throttling downloaders etc ).

There are stories all over the net about Comcast's throttling but as I just looked at one it said that the FCC has said what they are doing is against net neutrality rules but that they probably can't police it ( our government is the best that money can buy :-) ).

[http://news.cnet.com/8301-13578_3-10000821-38.html?hhTest=1](http://news.cnet.com/8301-13578_3-10000821-38.html?hhTest=1)

Hope that clears up what throttling means.

---

