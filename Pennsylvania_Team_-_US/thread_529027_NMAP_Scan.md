---
title: "NMAP Scan"
date: 2007-08-18
forum: Pennsylvania Team - US
---

### Post by jpr13 on 2007-08-18
I scanned and got this result:

Starting Nmap 4.11 ( [http://www.insecure.org/nmap](http://www.insecure.org/nmap) ) at 2007-08-18 22:36 Central Europe Daylight Time
Interesting ports on (censored).res-cmts.mtp.ptd.net (censored):
Not shown: 1238 filtered ports
PORT STATE SERVICE
1025/tcp closed NFS-or-IIS

I assume all my ports are closed from the last line...?

                           Jason

---

### Post by jedijf on 2007-08-18
Yep, you are all hunkered down. 

You could also check grc.com and the shield's up tool to verify if you are still in shock.

---

### Post by theox26 on 2007-08-22
ok, mine shows this

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-08-22 09:56 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1691 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
935/tcp  open  unknown
2049/tcp open  nfs


i assume 445 is open for samba, which is cool. NFS i get too.  I recently opened 631 trying to get a network printer working but don't need that anymore.

So my question is, how do i close these ports that don't need to be open?

I did an iptables -h and couldn't really tell what was supposed to be used to close a port.

Any help would be appreciated (or I'll probably find an answer anyway so don't feel to pressured to help if your busy, this is just me being lazy :)

---

### Post by andrewPCT on 2007-08-22
Don't forget that some of those ports that you are seeing as open, are only open to localhost.  For a better determination, try scanning it from another computer on the network.

---

### Post by cox377 on 2007-09-06
Hello Guys

I'm just wondering, should i be worried about these filters ports as this is a WAN scan for a webserver behind a router



Not shown: 1685 closed ports
PORT     STATE    SERVICE
21/tcp   filtered ftp
22/tcp   open     ssh
23/tcp   filtered telnet
80/tcp   open     http
85/tcp   filtered mit-ml-dev
135/tcp  filtered msrpc
139/tcp  filtered netbios-ssn
161/tcp  filtered snmp
179/tcp  filtered bgp
445/tcp  filtered microsoft-ds
593/tcp  filtered http-rpc-epmap
1720/tcp filtered H.323/Q.931
No OS matches for host


Much appreciated

CoXen

---

