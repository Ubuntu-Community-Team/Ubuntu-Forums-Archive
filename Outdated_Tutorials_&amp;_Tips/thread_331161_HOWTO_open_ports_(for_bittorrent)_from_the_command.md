---
title: "HOWTO: open ports (for bittorrent?) from the command line"
date: 2007-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Choad on 2007-01-04
By default, ubuntu is totally locked down, and will not allow incoming connections. To rectify this, its very simple - just 1 command

```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```

this is the port that the built in ubuntu bittorrent client uses, so this is the example i give. just issue that 1 command and you're good to go. 

if you want to revert back to how it was before

```
sudo iptables -A INPUT -p tcp --dport 6881 -j DROP
```

i cant believe this hasnt already been posted :D

---

### Post by &amp;wi*m#~10+q on 2007-01-11
thanx for the tip :)

---

### Post by Draje on 2007-01-14
Thanks, I also used it for ports 4662 & 4672 (aMule) and now KAD isn't firewalled anymore. :D

---

### Post by stevieb on 2007-01-21
holy crap! i've been trying for months to get this stuff (amule) working!  you get my vote for 'post of the year'!

-steve=D> :guitar: :biggrin: 8-)

---

### Post by jake3988 on 2007-01-22
Thanks.

By the way, its good to hear that linux is completely shut-down by default.  Most linux distros now-a-days are trying to open things up to make things 'easier' like windows does.

Glad this sticks to security!

Granted, my bittorrent by default worked before but had trouble uploading /well/, this might rectify this problem.  Too bad the darned university won't let me torrent.

---

### Post by amgeex on 2007-02-16
Ok, I've done everything! I have forwarded the relevant ports in my router, I've opened the ports on ubuntu with the command above, and I added it to my iptables, so its permanent. When Deluge still insisted on reporting no incoming connections I decided to upgrade my router's firmware, but it didn't fix a thing. Right now I've got my computer on the DMZ Host of my router, and it STILL shows no incoming connections. What is happening?

---

### Post by Choad on 2007-02-18
> **amgeex said:**
> Ok, I've done everything! I have forwarded the relevant ports in my router, I've opened the ports on ubuntu with the command above, and I added it to my iptables, so its permanent. When Deluge still insisted on reporting no incoming connections I decided to upgrade my router's firmware, but it didn't fix a thing. Right now I've got my computer on the DMZ Host of my router, and it STILL shows no incoming connections. What is happening?
trying to download a poorly seeded torrent?

---

### Post by amgeex on 2007-02-18
No, in fact, the torrent has 300+ seeds and 500+ peers, so no, its not poorly seeded.

---

### Post by 0MG on 2007-02-19
Run a port scan on your self to see if the port is actually open. Also maybe try taking a look at the packets as they are trying to pass with wireshark or tshark. You might be able to find out what is stopping the packets that way.

---

### Post by amgeex on 2007-02-19
Thanks. I have scanned myself already, and the port is open. I will try to see the packets, which is something I haven't done. I'll post back to let you know.

---

### Post by Choad on 2007-02-20
also, the bittorrent client you are using may not be using port 6881... you probably know this but thought i'd mention it any way just in case

---

### Post by amgeex on 2007-02-20
Well, I switched to azureus, and it doesn't show any NAT error, so I guess the other clients are just blind. The only thing is that it still thinks my udp port is not open, as it notifies me that DHT is firewalled. I really don't know what else to use. And yes, azureus is using the correct port.

---

### Post by Timaaaaaaay on 2007-02-21
is there anyway i can open multiple ports at once?  bit tornado uses 6889-6999

---

### Post by nonewmsgs on 2007-02-24
can we sticky this?

---

### Post by ince on 2007-02-25
Does this work for ports under 1024, i need to open port 113.

---

### Post by odzx on 2007-02-27
i'm using deluge. opened the ports and tested them.
i'm still getting a "no incoming connection" message allthogh it seems to go away after awhile. anyway download seems to be slow while upload is at full capacity. my share ratio with the current download is at about 200% wich is wierd considering my line capacities are D/L 190 U/L 35.

---

### Post by amgeex on 2007-02-27
Same behavior here. No incoming connections message always popping up, but it won't go away. And my download speed is crap, but my upload speed is quite good. I wonder, if there are no incoming connections, how come I've uploaded so much stuff? Deluge is starting to get on my nerves.

---

### Post by Maverickprowls on 2007-05-19
This was very useful, particularly as Firestarter doesn't seem to work terribly well when it comes to allowing specific serives through the ports.  

Does anyone know how to cure the Azureus issue that makes the program insist it is still DHT firewalled?  I put in the command above.

```
sudo iptables -A INPUT -p tcp --dport <my azureus port> -j ACCEPT
```

But I also added

```
sudo iptables -A INPUT -p udp --dport <my azureus port> -j ACCEPT
```

to open ports for UDP connections.  Was I correct in doing this?

---

### Post by adza on 2007-05-20
allright, this is doing my head in now.... same problem here... opened ports in my hardware device (easy), opened ports in iptables as per above through command line (again, easy i guess... no confirmation on if this worked????)... still getting NAT error when net test in azureus...? anyone? There seems to be plenty of people experiencing this...


******EDIT***********
Problem fixed, after some more reading... found a solution.. the code for the iptables....
```
iptables -I INPUT -p tcp --dport < your_port_number > -j ACCEPT
iptables -I INPUT -p udp --dport < your_port_number > -j ACCEPT
```

---

### Post by DC@DR on 2007-05-20
@adza: I guess you were missing the [rulenum] for the -I insert switch in iptables code...That's why we'd better use -A append switch then -I insert switch, IMHO :-)

---

### Post by benx009 on 2007-07-20
> **Choad said:**
> By default, ubuntu is totally locked down, and will not allow incoming connections. To rectify this, its very simple - just 1 command

```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```

this is the port that the built in ubuntu bittorrent client uses, so this is the example i give. just issue that 1 command and you're good to go. 

if you want to revert back to how it was before

```
sudo iptables -A INPUT -p tcp --dport 6881 -j DROP
```

i cant believe this hasnt already been posted :D

thanx, helped me out a lot:)

---

### Post by jocheem67 on 2007-07-21
I was wondering about this when I stumbeled cross this thread.....
I'm using mtorrent with wine, amule and nicotine...I just used some custom ports and openend them in my router. Actually it seems that these ports are open now. 
Where is iptables then? I think it is just accepting these ports to be open? Didn't configure anything.....

---

### Post by aen on 2007-07-26
> **Timaaaaaaay said:**
> is there anyway i can open multiple ports at once?  bit tornado uses 6889-6999

Use:

```
sudo iptables -A INPUT -p tcp --dport 6889:6999 -j ACCEPT
```

---

### Post by sunilmk on 2008-09-27
I know the thread is more than a year old, still...


I have system running 8.04 Hardy Heron,
& I'm using Rp-PPoE to connect to the net
(using pppoe-start)

When it was getting installed it asked me about the
firewall level
0, 1 or 2
selected 1 (for desktops used for browsing etc)

now, even if i use the above mentioned command
  sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

deluge still tells me that the ports are closed
& I do get terrible speeds

---

### Post by Choad on 2008-09-29
> **sunilmk said:**
> I know the thread is more than a year old, still...


I have system running 8.04 Hardy Heron,
& I'm using Rp-PPoE to connect to the net
(using pppoe-start)

When it was getting installed it asked me about the
firewall level
0, 1 or 2
selected 1 (for desktops used for browsing etc)

now, even if i use the above mentioned command
  sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

deluge still tells me that the ports are closed
& I do get terrible speeds
ubuntu is now completely open by default

it's probably your router. gotta set up port forwarding

---

### Post by drsubhadip on 2008-10-01
> **sunilmk said:**
> I know the thread is more than a year old, still...


I have system running 8.04 Hardy Heron,
& I'm using Rp-PPoE to connect to the net
(using pppoe-start)

When it was getting installed it asked me about the
firewall level
0, 1 or 2
selected 1 (for desktops used for browsing etc)

now, even if i use the above mentioned command
  sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

deluge still tells me that the ports are closed
& I do get terrible speeds

i m living in india
 and before the code applied my ktorrent speed was bad..
but after applying the code
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
the speed increases greatly
thank everybody for this great thread

---

### Post by sunilmk on 2008-10-01
> **Choad said:**
> ubuntu is now completely open by default

it's probably your router. gotta set up port forwarding


Heres what i did

after a clean install of ubuntu 8.04
i connected to the net using rp-pppoe
(as pppoeconf doesnt let me choose my
access concentrater, service name from
multiple entries)

then i uninstalled transmission (too basic)
& installed deluge (somehow reminds me of
utorrent)

used the command:
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

changed the port range in deluge to
6881 to 6881,
so that it will use a single port

here, if i "test for active port"
firefox pops up saying
"TCP port 6881 closed on <ip>"

I even tested azureus, & the same thing


So where did I go wrong?


btw, i dont even hv a router since its ethernet
cable all the way to my local cable operator

---

### Post by kevdog on 2008-10-02
I didnt read every post in this thread, however the default netfilter firewall policy is ACCEPT and not REJECT.  So why do you need to open up a specific port in the first place if you haven't messed with the firewall settings?  All incoming ports are ACCEPTED -- at least that is what I thought.

---

### Post by ProNux on 2008-11-16
> **Choad said:**
> By default, ubuntu is totally locked down, and will not allow incoming connections. To rectify this, its very simple - just 1 command

```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```

this is the port that the built in ubuntu bittorrent client uses, so this is the example i give. just issue that 1 command and you're good to go. 

if you want to revert back to how it was before

```
sudo iptables -A INPUT -p tcp --dport 6881 -j DROP
```

i cant believe this hasnt already been posted :D

VERY GREAT HELP FOR MY TRANSMISSION PROBLEMS!!!!  Thanks... :guitar:

---

### Post by jfluet on 2009-01-24
this seems to shut down my web browser after about 30 seconds?

---

### Post by Baby Boy on 2009-01-30
This seems to have helped, thanks.

---

### Post by qualified on 2009-03-28
I know this is an old thread but I need help. I am using transmission and have slow speeds my router is allowing traffic on port 51413, and when I ran sudo iptables -I INPUT -p tcp --dport 51413 -j ACCEPT I got a good speed for about one minute then it dropped. Any ideas? I am using ubunt 8.10

---

### Post by jokei on 2010-05-10
Hi, I tried this and it still says (In Transmission) port 6881 is closed???

I'm using Lucid Lynx.

Any help much appreciated.

---

### Post by evencoil on 2010-12-07
> **jokei said:**
> Hi, I tried this and it still says (In Transmission) port 6881 is closed???

I'm using Lucid Lynx.

Any help much appreciated.

I also have this problem for Deluge. Anybody?

---

