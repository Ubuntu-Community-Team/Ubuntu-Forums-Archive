---
title: "Firewall preventing lots of connections outbound"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by MaxVK on 2008-07-01
Hi, Iv just checked my logs and noticed that the firewall is constantly preventing outbound connections, but I'm lost as to where they are going or what is trying to connect.

A (very) partial list of the connections is shown below. Could anyone help me out a little to try and work out what is trying to connect. I'm using 7.10.

Cheers

Max


```

Jul  1 16:35:47 max-desktop kernel: [  786.794177] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=70.71.40.188 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=30301 PROTO=ICMP TYPE=3 CODE=3 [SRC=70.71.40.188 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=24245 PROTO=UDP SPT=55590 DPT=64333 LEN=71 ] 
Jul  1 16:35:47 max-desktop kernel: [  787.180216] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=96.244.206.7 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=39271 PROTO=ICMP TYPE=3 CODE=3 [SRC=96.244.206.7 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=10065 PROTO=UDP SPT=51893 DPT=64333 LEN=71 ] 
Jul  1 16:35:49 max-desktop kernel: [  788.657088] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=211.120.206.236 LEN=113 TOS=0x00 PREC=0xC0 TTL=64 ID=15650 PROTO=ICMP TYPE=3 CODE=3 [SRC=211.120.206.236 DST=192.168.0.72 LEN=85 TOS=0x00 PREC=0x00 TTL=111 ID=21365 PROTO=UDP SPT=6881 DPT=64333 LEN=65 ] 
Jul  1 16:35:49 max-desktop kernel: [  788.751590] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=84.136.236.47 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=36798 PROTO=ICMP TYPE=3 CODE=3 [SRC=84.136.236.47 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=42864 PROTO=UDP SPT=61365 DPT=64333 LEN=71 ] 
Jul  1 16:35:50 max-desktop kernel: [  789.845275] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=78.27.37.183 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=62243 PROTO=ICMP TYPE=3 CODE=3 [SRC=78.27.37.183 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=18396 PROTO=UDP SPT=65159 DPT=64333 LEN=71 ] 
Jul  1 16:35:50 max-desktop kernel: [  790.143960] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=79.41.241.111 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=11758 PROTO=ICMP TYPE=3 CODE=3 [SRC=79.41.241.111 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=888 PROTO=UDP SPT=36105 DPT=64333 LEN=71 ] 
Jul  1 16:35:51 max-desktop kernel: [  791.053304] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=116.15.78.31 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=2898 PROTO=ICMP TYPE=3 CODE=3 [SRC=116.15.78.31 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=36773 PROTO=UDP SPT=16002 DPT=64333 LEN=71 ] 
Jul  1 16:35:54 max-desktop kernel: [  793.967922] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=68.83.232.148 LEN=98 TOS=0x00 PREC=0xC0 TTL=64 ID=58413 PROTO=ICMP TYPE=3 CODE=3 [SRC=68.83.232.148 DST=192.168.0.72 LEN=70 TOS=0x00 PREC=0x00 TTL=48 ID=32073 PROTO=UDP SPT=36835 DPT=64333 LEN=50 ] 
Jul  1 16:35:54 max-desktop kernel: [  793.993721] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=68.83.232.148 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=58414 PROTO=ICMP TYPE=3 CODE=3 [SRC=68.83.232.148 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=48 ID=32075 PROTO=UDP SPT=36835 DPT=64333 LEN=71 ] 
Jul  1 16:35:55 max-desktop kernel: [  795.011720] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=80.30.218.184 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=30029 PROTO=ICMP TYPE=3 CODE=3 [SRC=80.30.218.184 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=50 ID=43133 PROTO=UDP SPT=54789 DPT=64333 LEN=71 ] 
Jul  1 16:35:56 max-desktop kernel: [  795.596139] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=78.146.207.9 LEN=121 TOS=0x00 PREC=0xC0 TTL=64 ID=48175 PROTO=ICMP TYPE=3 CODE=3 [SRC=78.146.207.9 DST=192.168.0.72 LEN=93 TOS=0x00 PREC=0x00 TTL=117 ID=21087 PROTO=UDP SPT=27151 DPT=64333 LEN=73 ] 
Jul  1 16:35:58 max-desktop kernel: [  798.069705] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=220.236.126.137 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=37888 PROTO=ICMP TYPE=3 CODE=3 [SRC=220.236.126.137 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=292 PROTO=UDP SPT=39506 DPT=64333 LEN=71 ] 
Jul  1 16:35:58 max-desktop kernel: [  798.319933] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=24.37.243.220 LEN=99 TOS=0x00 PREC=0xC0 TTL=64 ID=39980 PROTO=ICMP TYPE=3 CODE=3 [SRC=24.37.243.220 DST=192.168.0.72 LEN=71 TOS=0x00 PREC=0x00 TTL=114 ID=51606 PROTO=UDP SPT=32257 DPT=64333 LEN=51 ] 
Jul  1 16:35:59 max-desktop kernel: [  798.649406] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=81.248.179.184 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=32095 PROTO=ICMP TYPE=3 CODE=3 [SRC=81.248.179.184 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=44 ID=26234 PROTO=UDP SPT=62487 DPT=64333 LEN=71 ] 
Jul  1 16:35:59 max-desktop kernel: [  799.440089] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=24.155.244.250 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=32022 PROTO=ICMP TYPE=3 CODE=3 [SRC=24.155.244.250 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=36841 PROTO=UDP SPT=46191 DPT=64333 LEN=71 ] 
Jul  1 16:36:00 max-desktop kernel: [  800.483612] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=201.9.105.193 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=28781 PROTO=ICMP TYPE=3 CODE=3 [SRC=201.9.105.193 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=52303 PROTO=UDP SPT=8100 DPT=64333 LEN=71 ] 
Jul  1 16:36:01 max-desktop kernel: [  801.211892] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=90.208.228.248 LEN=98 TOS=0x00 PREC=0xC0 TTL=64 ID=12834 PROTO=ICMP TYPE=3 CODE=3 [SRC=90.208.228.248 DST=192.168.0.72 LEN=70 TOS=0x00 PREC=0x00 TTL=37 ID=3908 PROTO=UDP SPT=17105 DPT=64333 LEN=50 ] 
Jul  1 16:36:02 max-desktop kernel: [  802.351793] [IPTABLES DROP] : IN= OUT=eth0 SRC=192.168.0.72 DST=212.122.214.3 LEN=119 TOS=0x00 PREC=0xC0 TTL=64 ID=64567 PROTO=ICMP TYPE=3 CODE=3 [SRC=212.122.214.3 DST=192.168.0.72 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=60977 PROTO=UDP SPT=56029 DPT=64333 LEN=71 ] 

```

---

### Post by Fire_Chief on 2008-07-01
All of the blocked packets in that list are ICMP packets (pings). Probably not much to worry about there. Aside from the logs, are you experiencing any problems on your connection?

---

### Post by MaxVK on 2008-07-01
Thanks for replying. No, I'm having no issues at all and my connection seems to be fine. I just happened to check the logs and saw all these connections and got a bit panicked (Horror images from Windows came back to haunt me!).

If they are all pings, what could be doing the pinging? I'm (pretty) sure Iv not set anything up to do such a thing.

Cheers

Max

---

### Post by MaxVK on 2008-07-02
Okay, a bump by way of a new question:

How can I find out what is doing all these pings? Surely it cant be correct that my machine is trying to do all these pings all the time, right?

---

### Post by Fire_Chief on 2008-07-03
That's a little more difficult if you're not running any intentional Internet applications (bittorrent, other P2P app, network scanner, etc.). You might be able to get more information using a packet sniffer such as Wireshark to capture the data and examine it.

Cheers!

---

### Post by wolfen69 on 2008-07-03
actually, blocking ICMP is a good thing. if you have no problems with your internet connections, i would not worry about it. it just means the firewall is doing its job.

---

### Post by MaxVK on 2008-07-04
Hmm, thanks for the replies. I'm not using any P2P, just Firefox and Thunderbird.

But it sounds as if I'm safe enough and I don't have any issues with my connection so Ill let sleeping dogs lie I think.

Thanks all

Regards

Max

---

### Post by txcrackers on 2008-07-04
Assuming you're "safe" is not necessarily a good idea. Most well-behaved systems don't just randomly send out PINGs - there's some software in your system or network that's doing that and should be investigated, especially since it's once per second. Whatever computer is assigned the IP address 192.168.0.72 is the one involved.

---

### Post by MaxVK on 2008-07-05
Okay, that does make a lot of sense (and it appeals to the old window user in me), but I'm still stuck to work out *what* software is causing the pings. Can anyone suggest a way to do this please?

Cheers

Max

---

### Post by nowshining on 2008-07-05
it's iptables blocking incoming, etc... not firefox - iptables is a firewall for linux. :) and everything else is either a GUI for it or script.

---

### Post by MaxVK on 2008-07-06
> **nowshining said:**
> it's iptables blocking incoming, etc... not firefox - iptables is a firewall for linux. :) and everything else is either a GUI for it or script.

Yes. I know what iptables is and what it does, but these look like outgoing connections, not incoming ones, which is why I was concerned in the first place. Firefox has nothing (apparently) to do with it and I don't use any GUI to configure iptables.

What I need to do is find out what is sending these erroneous connections attempts and why. I would imagine that being able to accurately decipher the log entries would help, but Iv not been able to find anything that adequately explains what all the information means.

---

### Post by nowshining on 2008-07-06
router?

---

### Post by MaxVK on 2008-07-06
Yes, I'm running through a router but I'm not sure I see how that could be registering outgoing connections on my system logs. Incoming perhaps, but not outgoing.

---

### Post by MaxVK on 2008-07-06
Well Iv found some information at least. The outgoing packets are all ICMP type 3, code 3, which translates to "Destination Unreachable, Port Unreachable". Now then, what could be sending such a packet? Remember that these are *outgoing* connections, which suggests that (possibly) a connection has been requested on a specific port and the system is trying to reply with an error message that the port is unreachable.

I'm afraid thats all as far as my research goes for now, so if anyone has any further ideas or information Id be glad to hear it because these outgoing messages are making me more than a little paranoid!

BTW: For those interested, I found the information on the ICMP codes here:
[http://www.iana.org/assignments/icmp-parameters](http://www.iana.org/assignments/icmp-parameters)

---

### Post by ChildOfMana on 2008-07-06
MaxVK,

Sorry to hijack your thread but, just out of curiosity, where do you find the logs where this info is held?

---

### Post by MaxVK on 2008-07-07
> **ChildOfMana said:**
> MaxVK,

Sorry to hijack your thread but, just out of curiosity, where do you find the logs where this info is held?

No worries - It bumps the thread anyway! ;)

The logs are found on the main menu system under:

System->Administration->System Log

Regards

Max

---

### Post by ChildOfMana on 2008-07-07
Thanks man.

---

### Post by Fire_Chief on 2008-07-07
Max,

Check your router to make sure you don't have rules permitting inbound traffic to your PC (NAT or port mappings). On a random side note, you may want to glance at the startup items and services you have configured to see if there are any that look unusual or suspicious.

Cheers!

---

### Post by MaxVK on 2008-07-08
> **Fire_Chief said:**
> Max,

Check your router to make sure you don't have rules permitting inbound traffic to your PC (NAT or port mappings). On a random side note, you may want to glance at the startup items and services you have configured to see if there are any that look unusual or suspicious.

Cheers!

My router seems to be okay - Its been set in the same way for a long time now but this problem has only just come to my attention. In any case, if I use an online port scan I show up as not being there, so inbound ports are still closed properly.

As for the startup services, there is only one that seems a little odd, but thats only because I don't really know what it does and Iv not had time to hunt down the info yet. Thats the "*Multicast DNS service discovery (avahi-daemon)*".

Everything else seems fine and Iv already been in here turning off things such as the braille display service.

Thanks for your reply. I'm still trying to hunt these connections down, but so far I'm not having much luck. The fact that the firewall is blocking them is satisfying, but its still a worry that something is trying to connect, and I don't know what it is.

Regards

Max

---

### Post by nowshining on 2008-07-10
```
"Multicast DNS service discovery (avahi-daemon)".
```

It's normal:

try disabling that and removing avahi.

What it does it simply tries to find other computers on ur network, etc..

if u don't have a network of computers, etc.. - just disable it or remove it as suggested above.

As for the icmp, multicast shouldn't send out icmps tho..hmmmm

I'm wondering, do u has a file sharing program like gtk or frostwire, etc..?? or any p2p program such transmission, etc..

or

do u use wine?

alas

when u read this,

screenshot us ur processes in system monitor or install htop and screenshot us the output in the terminal. - put cursor over the terminal and press alt+printscreen after typing htop in the terminal.

---

### Post by MaxVK on 2008-07-11
> I'm wondering, do u has a file sharing program

I do *have* Azureus installed but Iv not used it since I downloaded Hardy64 with it for a friend. Its not running now, so I doubt that it could be responsible. I also have Wine installed, although it is only used directly when I need to use a specific program.

Why 'Alas'? Is there some issue with having Wine or Azureus installed (Even when they are not currently being used)?

Ill sort out a screen shot when I'm back on my own machine (I'm at work right now).

Very many thanks for your help and persistence with this thread.

Regards

Max

---

### Post by nowshining on 2008-07-11
i'll be waiting..

---

### Post by MaxVK on 2008-07-12
Hmm. First time Iv tried to attach a file, so here goes. Iv trimmed it a bit because it was quite a large image. Naturally Ill edit this post and try again if it fails.

Very many thanks for your efforts

regards

Max

---

### Post by MaxVK on 2008-07-21
Okay, a shameless bump - Can anyone shed any light on these outgoing connection attempts please?

Cheers

Max

---

### Post by barney385 on 2008-07-21
Sounds like a loopback to me...but don't hold me to that.

---

### Post by Fire_Chief on 2008-07-21
Hi Max,

Just to be thorough, would you please post the output of```
sudo iptables -L
```

Cheers!

---

### Post by MaxVK on 2008-07-22
Thanks for the reply - iptables -L:

This firewall script has been adapted from one found on these forums ([http://ubuntuforums.org/showthread.php?p=4152863#post4152863](http://ubuntuforums.org/showthread.php?p=4152863#post4152863))

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
LOG_DROP   0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   0    --  anywhere             anywhere            

Chain FIREWALL (2 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
TRUSTED    0    --  anywhere             anywhere            
LOG_DROP   0    --  anywhere             anywhere            

Chain LOG_DROP (2 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning prefix `[IPTABLES DROP] : ' 
DROP       0    --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www state NEW,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webcache state NEW,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ircd 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ircd 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:pop3 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3s 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nntp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:2082 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssmtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp state NEW,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp-data state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:54123:54683 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:54123:54683 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:64333 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:64333 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:64333 
ACCEPT     udp  --  anywhere             anywhere            udp spt:64333
``` 


thanks

Max

---

### Post by Fire_Chief on 2008-07-22
Ok, I'm betting the application that is generating the ping attempts is definitely a bittorrent app. I looked up the destination IPs from your first post and they are all over the globe (UK, Japan, US, Italy, Germany, Netherlands, Poland, South America, Australia, France).

It is attempting to ping out from your machine to the various destinations so it's not someone attacking or trying to get to you. 

If you just want to see what app is causing the pings, you'll need to do some testing where you monitor the running processes (possibly via top) and the log file. I recommend using tail to view the last lines of the log file and get the latest recorded info in it frequently. Kill or stop all bittorrent applications and processes that you can find and then check to see if you get any new log entries of the same info. It is a bit tedious but will relatively quickly help you see what app is generating the pings.

There is another way to determine the source app. If you check the log file and see current blocked packets happening, then run ```
sudo netstat -anp | grep raw
```It should return only a little bit of information about the ping connections being attempted (assuming attempts blocked by the firewall still appear here but they may not). This will also list the PID and application name of the source. If nothing is appearing, then disable iptables for a few minutes and check again. Since you are behind a router with no port openings and NAT, you should be okay for those few minutes.

Cheers!

---

### Post by MaxVK on 2008-07-23
Thanks for that information. As soon as Im on my own machine again Ill give that a try and report back here if I have any joy, just in case others have a similar problem.

Many thanks

Max

---

### Post by MaxVK on 2008-08-01
Sorry for the delay - been a busy bee.

The 'sudo netstat -anp | grep raw' command doesn't show anything at all, with or without IPTables enabled, however, Iv a feeling that I found the culprit.

It looks as though this may be caused by Azureus: I opened it again yesterday to continue a download of the Fedora DVD and the rejected packets started again almost instantly.

The thing is that the ports are all set okay, and the download seems to be working fine, so while I seem to have found the program sending these packets out, doing so has raised even more questions:

1) Why is Azureus still trying to send out packets when its not even open, and, possible more to the point, HOW?

2) How come the firewall is blocking these packets, but the download works anyway? What are they if they are not part of the download process and why should they continue for a time, even when the program that generates them has been closed?

BTW: The little face in Azureus turns green almost straight away, supposedly indicating that I have full connection with no firewall problems.

Thanks for your time,

regards

Max

---

### Post by The Cog on 2008-08-01
Those outgoing messages being blocked are indeed Port Unreachable messages. Here's another reference site that says so:
[http://www.networksorcery.com/enp/protocol/icmp/msg3.htm](http://www.networksorcery.com/enp/protocol/icmp/msg3.htm)

What those packets actually are then, is responses to incoming connection requests from other machines. They basically say "No you can't connect to that port, there is no application taking connections on that port number". 

Which is fine, except for the question: Why are incoming connect requests arriving at all? The incoming connections are to UDP port 64333, which means nothing to me. Byt why is your firewall allowing the packets in? Your posted iptables listing above suggests that the FIREWALL chain permits all packets regardless of source or destination address, which isn't good. It doesnt explain why the ICMP responses outgoing are being logged and dropped though, so there is info missing (interface names perhaps)? using the -v flag will get you the interface names too.

I notice that port 64333 is explicitly permitted in the rules in the TRUSTED chain, so maybe you know what protocol/application they are trying to contact.

---

### Post by MaxVK on 2008-08-02
Hmm. Okay, lets try and clear things up in order:

> Which is fine, except for the question: Why are incoming connect requests arriving at all? The incoming connections are to UDP port 64333, which means nothing to me. Byt why is your firewall allowing the packets in?

Port 64333 is the one assigned for use with Azureus. This was added manually to the IPTables configuration by myself, so no major surprises if Iv got it wrong!

> Your posted iptables listing above suggests that the FIREWALL chain permits all packets regardless of source or destination address, which isn't good.

The IPTables configuration was taken from a thread in these forums ([Here]("http://ubuntuforums.org/showthread.php?t=159661") and also on the link in that thread to the more advanced version). As far as I can tell everything is permitted and then passed to the TRUSTED or FIREWALL chains and is allowed or dropped from there. Editing (In other words 'allowing') something else is a matter of adding the required ports to the configuration, which is what I have (tried) done in the case of Azureus, which seems to be the culprit in this case.

> It doesnt explain why the ICMP responses outgoing are being logged and dropped though, so there is info missing (interface names perhaps)? using the -v flag will get you the interface names too.

Its looking as though I have made some kind of major cock-up when I tried to edit the IPTables configuration file - I have tried to allow the Azureus port but it seems that it is blocking the information going out, which means (I suppose) that others trying to connect to my Azureus are not getting the message telling them that I'm not available, and therefore they keep trying for a time, which generates more items in the log.

I have tried to understand more about IPTables, but unfortunately it hasn't come at all easily, and I'm now convinced that this problem has been caused by my lack of understanding.

Aside from the obvious 'Learn more about IPTables', do you have any suggestions about how to clear this up? 

Iv tried to use Firestarter to sort the firewall settings before, but it kept closing itself while I was using it, which is why I used the script from the other thread instead.

Basically I want everything locked unless I say otherwise (Yes, I'm an old Windows user), but I obviously need to be able to open (or close) things depending on what I want to do. I thought that was what I was doing!

Very many thanks for your efforts, and I apologise for my (apparently) complete lack of understanding about IPTables.

Regards

Max

---

### Post by mcduck on 2008-08-02
> **MaxVK said:**
> Well Iv found some information at least. The outgoing packets are all ICMP type 3, code 3, which translates to "Destination Unreachable, Port Unreachable". Now then, what could be sending such a packet? Remember that these are *outgoing* connections, which suggests that (possibly) a connection has been requested on a specific port and the system is trying to reply with an error message that the port is unreachable.

I'm afraid thats all as far as my research goes for now, so if anyone has any further ideas or information Id be glad to hear it because these outgoing messages are making me more than a little paranoid!

BTW: For those interested, I found the information on the ICMP codes here:
[http://www.iana.org/assignments/icmp-parameters](http://www.iana.org/assignments/icmp-parameters)

Then sending those packages is what really should be happening. Probably your firewall configuaration is not actually optimal as it's allowing some incoming connections that cause the system to respond with the "destination unreachable"-message, which is then blocked by the firewall.

So you should try to block the incoming message, not the outgoing response to it..

(if the firewall would be working correctly the incoming connection would be blocked (and would show in logs instead of this one) or it would be allowed (and you wouldn't get any message about blocked connection, incoming or outgoing).

---

### Post by MaxVK on 2008-08-04
Thanks for your help everyone. I'm still very lost so I think I'm going to have to open a new question and ask for some major help in preparing or repairing an IPTables script.

Many thanks

Max

---

