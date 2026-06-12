---
title: "Am I under some kind of attack?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Tylazene on 2008-06-24
Watching Firestarter (paranoid) I all of sudden keep getting UDP hits on port 6261. None of them are red entrys but I get one or two every couple seconds and are from 5 or 6 different IPs. I noticed too that my internet is much slower. Is this one of those DOS attacks?

I'm not really good yet with firewall settings but Firestarter shows that everything is set on stealth (drop). I checked with ShieldsUp and it said everything was stealth but it could ping me with ICMP. Checking IP tables with command prompt is very confusing  and I'm not really sure what all this UDP ICMP and SSH stuff means. What can I do?

---

### Post by Cadmus on 2008-06-24
6261 isn't on the [IANA allocated port list]("http://www.iana.org/assignments/port-numbers") so I wouldn't be able to tell you what they're trying to do.

However if it's always the same port and it's only once a second or so then it doesn't feel like a DoS attack.

---

### Post by the_doc on 2008-06-24
Do you use some kind of torrent?

---

### Post by Tylazene on 2008-06-24
I did download a couple torrents about a month ago but my IP has changed at least a couple times since then. I can't get a new one for a couple three days now. I can usually get assigned a new IP if I unplug my modem overnight. 

I looked up one of the offending IP's and it's from gavlegardarna.gavle.to ever that is.

---

### Post by the_doc on 2008-06-24
Can you provide some kind of log output?

---

### Post by benfindlay on 2008-06-24
It may well be that the previous owner of your IP address was using torrents. If the peers he/she was connected to haven't updated they will still be looking for him/her on your IP address. Give it some time and see if it keeps up

With regards to your ICMP problem, just go into your router, enable the DMZ and set the IP address to a non-existent internal IP address, e.g. 192.168.1.222

THat way any ping requests will be forwarded by your router to the address 222, which is non existent, so they will be dropped!

Hope this helps!

Ben

---

### Post by ukripper on 2008-06-24
can you do ```
nmap localhost 
```in termianl to check if this port is being used and it will tell you what application/service is using it.


you need to install nmap first.

---

### Post by Joeb454 on 2008-06-24
I thought nmap was considered illegal in some places :confused:

---

### Post by the_doc on 2008-06-24
I don't think it is if you use it to analyse your own systems.

---

### Post by ukripper on 2008-06-24
> **Joeb454 said:**
> I thought nmap was considered illegal in some places :confused:

not sure where but not in uk. You are scanning localhost then it is not illegal. Scanning outside your network can be considered malicious. 

and also for UDP ports scan you need to do:
```
sudo nmap -sU localhost
```

---

### Post by Tylazene on 2008-06-24
Tried nmap but it was command not found. I always meant to figure out how to log in to my cable modem but never got around to it. I'll work on that. 

Here's an update: I unplugged that HD and plugged in another with Hardy on it and that port only gets hit once every 5 to 10 minutes now. Why would this change anything?

---

### Post by benfindlay on 2008-06-24
Are you plugged direct into the modem without a router? Usually the login involves typing an IP address into your browser, and its usually either 192.168.1.1 or 192.168.0.1

That will display the configuration options. If you're directly plugged into a modem, then you're likely being hit by packets that a router would drop for you.

Anyways, try those 2 IP addresses to get into the modem

Hope this helps

Ben

---

### Post by ukripper on 2008-06-24
> **Tylazene said:**
> Tried nmap but it was command not found. I always meant to figure out how to log in to my cable modem but never got around to it. I'll work on that. 

Here's an update: I unplugged that HD and plugged in another with Hardy on it and that port only gets hit once every 5 to 10 minutes now. Why would this change anything?

install nmap first :
```
sudo apt-get install nmap
```

---

### Post by dca on 2008-06-24
Isn't the Network Tool (gnome-nettool) in the 'System -> Administration' menu similar?

---

### Post by ukripper on 2008-06-24
> **dca said:**
> Isn't the Network Tool (gnome-nettool) in the 'System -> Administration' menu similar?

never used it gui way, perhaps may be the same.

---

### Post by Tylazene on 2008-06-24
Ok, I switched back to the first HD and the hits on that port are totally gone now. I just get my usual occasional hits on 1026 1027 and 1028 now.

I did nmap and got this:

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-06-24 12:49 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1694 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
631/tcp  open  ipp
3306/tcp open  mysql

and this:

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-06-24 12:50 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1485 closed ports
PORT      STATE         SERVICE
68/udp    open|filtered dhcpc
5353/udp  open|filtered zeroconf
32768/udp open|filtered omad


Not sure what this all means though.

---

### Post by the_doc on 2008-06-24
Can you run nmap against one specific port i.e. 6261, the one you were blocking traffic on?

---

### Post by Tylazene on 2008-06-24
nmap -sU -p 6261 127.0.0.1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-06-24 13:26 EDT
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
6261/udp closed unknown

Nmap finished: 1 IP address (1 host up) scanned in 0.046 seconds



Did I do that right?

---

### Post by the_doc on 2008-06-24
Yeah, it looks as if you did it right.  

At any rate you have that port closed so whatever was trying to get in won&#8217;t be able to, I think it may have been torrent traffic anyway.

A lot of blocks on that port by your firewall may look like a lot of attacks but AFAIK as UDP is connectionless you'll get a block per packet, with TCP you only get one block with each connection attempt.

---

### Post by Tylazene on 2008-06-24
Ok, thanks for your help guys.

---

