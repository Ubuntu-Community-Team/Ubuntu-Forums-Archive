---
title: "iptables exception for streaming audio"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by rsa137 on 2013-02-03
Hi all,

I have a user profile (called "work") on my computer that  I've intentionally disabled internet access for by adding the line

```
pre-up  iptables -A OUTPUT -p tcp -m owner --uid-owner work -j DROP 
```to  the /etc/network/interfaces folder. This works well for disabling all internet access for the user, but I would like to allow a handful of exceptions for streaming audio (to be accessed by Banshee). Does anyone know of a way to tweak iptables to deny all internet access for this user except for these streaming audio sources (which are of the form [http://www.*.com/*.pls](http://www.*.com/*.pls)).

Thanks very much

---

### Post by SeijiSensei on 2013-02-03
If the list of acceptable sites is reasonbly limited, just gather their IP addresses and add lines like this above the one you presented above:

```

iptables -A OUTPUT -d 10.10.10.10 -j ACCEPT
iptables -A OUTPUT -d 10.10.10.11 -j ACCEPT
[etc.]
iptables -A OUTPUT -p tcp -m owner --uid-owner work -j DROP

```

Filtering by something like a file extension is pretty difficult with iptables.  If you have enough users to make running a Squid proxy justifiable, you can write rules for Squid that allow or block URLs using regular expressions.

---

### Post by kevdog on 2013-02-03
If you knew the port you connect to, you could also filter by port number or a port range and/or combine that with a uid (user id) or group id.

---

### Post by rsa137 on 2013-02-03
Thanks for the replies!

SeijiSensei: Thanks for the suggestion. I tried this, but was unable to get it to work. The first problem I had is that I don't know what the ip addresses of my stations are (for example,  [http://listen.di.fm/public3/chillout.pls](http://listen.di.fm/public3/chillout.pls) -- how do I determine the ip corresponding to this?). The second problem I encountered is that I was unable to get this method to work even when I'm using the ip for an ordinary website (let alone streaming audio). So I suspect that even if I could find the ip for my audio streams, it may not work.

kevdog: This sounds like a good idea, but I'm not sure what the right port is. If I open the above .pls in gedit I see 6 entries of the form "http://pub[1-6].di.fm:80/di_ambient". Does this mean that the stream uses port 80? (I don't know...)

Maybe I'll look into squid, but that's new to me.

---

### Post by Doug S on 2013-02-03
> (for example, [http://listen.di.fm/public3/chillout.pls](http://listen.di.fm/public3/chillout.pls) -- how do I determine the ip corresponding to this?). You look it up. Example:```
doug@doug-64:~$ [COLOR=red]nslookup listen.di.fm[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53
Non-authoritative answer:
Name:   listen.di.fm
Address: [COLOR=red]173.231.147.50[/COLOR]

```

---

### Post by rsa137 on 2013-02-03
> **Doug S said:**
> You look it up. Example:```
doug@doug-64:~$ [COLOR=red]nslookup listen.di.fm[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53
Non-authoritative answer:
Name:   listen.di.fm
Address: [COLOR=red]173.231.147.50[/COLOR]

```

Ah, neat! I didn't know that. Thanks.

---

### Post by Doug S on 2013-02-03
> The second problem I encountered is that I was unable to get this method to work even when I'm using the ip for an ordinary website (let alone streaming audio). So I suspect that even if I could find the ip for my audio streams, it may not work.
What Seiji said should work. If you continue to have problems, then post your entire iptables rules set, as something else must be blocking it. Post the output from this command:```
sudo iptables -v -x -n -L
```

---

### Post by rsa137 on 2013-02-03
I'm not having much luck here, despite the good suggestions that you've offered. Here's the output:

```
computer usr # sudo iptables -v -x -n -L
Chain INPUT (policy ACCEPT 91 packets, 32229 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 50 packets, 7856 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            173.231.147.50      
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            owner UID match 1000
```And here's my /etc/iptables.rules file:

```
 *filter
:INPUT ACCEPT [2001:1048219]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [1412:131292]
-A OUTPUT -d 173.231.147.50/32 -j ACCEPT
-A OUTPUT -p tcp -m owner --uid-owner 1000 -j DROP 
COMMIT 
```The ip there is associated with listen.di.fm, but I've tried several other ips with no success. 

Finally, here is my etc/network/interfaces file:

```
 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
     pre-up iptables-restore < /etc/iptables.rules  
```As it stands now, the user "work" has no internet access (which is mostly good) but can't access the streaming audio that I want (which is not so good). Any other suggestions would be helpful.

---

### Post by Doug S on 2013-02-04
O.K., it is true that there are not any packets accepted via the special rule for the desired IP address. However, the listing also shows that there were no packets DROPPED by the "owner" rule. Something isn't right, but it isn't the iptables rules, as far as I can see. Continue to experiment with it, watching the packet counters as you do. I'll set up the same senario on my test computer in the morning, if this still isn't resolved (it's getting late in my time zone).

---

### Post by rsa137 on 2013-02-04
Thanks for the help Doug. I've played around with the iptables rules a bit, but I haven't had any success. The good news is that I'm learning a lot about iptables in the process. 

My guess (and this is just a guess) is that something somewhere else is causing a problem. I may do a fresh install on a spare machine later today and try this over from scratch to see if I can get it to work.

Thanks again for the help.

---

### Post by Doug S on 2013-02-04
For reference, I tried what you are trying to do on my test computer. First, with just the blocking rule, I tried to access my own web site:```
doug@s15:~/temp1$ sudo iptables -v -x -n -L
Chain INPUT (policy ACCEPT 165 packets, 16117 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain OUTPUT (policy ACCEPT 91 packets, 13121 bytes) [COLOR=red]<<< These are me (UID 1000) and my SSH session)[/COLOR]
    pkts      bytes target     prot opt in     out     source               destination
      [COLOR=red]42     2520[/COLOR] DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            owner UID match 1001
```Second with an added rule to allow access to my web site, as per Seiji's suggestion:```
doug@s15:~/temp1$ sudo iptables -v -x -n -L
Chain INPUT (policy ACCEPT 24 packets, 11377 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain OUTPUT (policy ACCEPT 11 packets, 1860 bytes) [COLOR=red]<<< These are me again[/COLOR]
    pkts      bytes target     prot opt in     out     source               destination
       [COLOR=red]9      619[/COLOR] ACCEPT     all  --  *      *       0.0.0.0/0            192.168.111.1
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            owner UID match 1001
```Let us know how you make out.

---

### Post by rsa137 on 2013-02-04
Thanks Doug. It's good to know that the iprules that I'm using are correct. I'll try things again later today and let you know how it goes.

---

### Post by rsa137 on 2013-02-04
No dice. I tried the same iptables settings on a machine with a fresh install, and ran into the same problems. There must be something wrong with the way that I'm configuring iptables.

Unfortunately I don't have much time to devote to solving this problem now, so I may have to put it aside for a while. Thanks for the help though -- especially Doug. Thanks!

---

