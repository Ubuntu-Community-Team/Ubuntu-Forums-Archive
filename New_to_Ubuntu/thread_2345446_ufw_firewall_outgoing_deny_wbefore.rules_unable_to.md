---
title: "ufw firewall outgoing deny w/before.rules unable to outgoing traceroute"
date: 2016-12-04
forum: New to Ubuntu
---

### Post by jesse27 on 2016-12-04
I am trying to harden my Ubuntu and use UFW incl "ufw default deny outgoing", however, when I do this I am unable to traceroute out.

```
Relevant part of the UFW config:
ufw allow out to any port 33434:33523 proto tcp
ufw allow out to any port 33434:33523 proto udp
ufw allow in from any port 33434:33523 proto tcp
ufw allow in from any port 33434:33523 proto udp
ufw allow in from any to any port 33434:33523 proto tcp
ufw allow in from any to any port 33434:33523 proto udp
```

I have also made entries in before.rules
```
# allow outbound icmp
-A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
#Outbound UDP traffic Policy
-A ufw-before-output -p udp --dport 33434:33524 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-input -p udp --dport 33434:33524 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-input -p udp --sport 33434:33524 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```

I am able to make outgoing pings but not traceroutes. Some examples from the error logs while attempting to run the traceroute to 8.8.8.8:
```
Dec 4 21:00:42 Orion vmunix: [574251.174438] [UFW BLOCK] IN=eth0 OUT= MAC=e0:8f:ec:00:2f:25:00:50:7f:38:8d:85:08:00 SRC=216.xxx.56.87 DST=192.168.11.108 LEN=65 TOS=0x00 PREC=0xC0 TTL=52 ID=61883 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.11.108 DST=8.8.8.8 LEN=37 TOS=0x00 PREC=0x80 TTL=1 ID=49031 DF PROTO=UDP SPT=44567 DPT=33439 LEN=17 ] 
Dec 4 21:00:45 Orion vmunix: [574254.176261] [UFW BLOCK] IN=eth0 OUT= MAC=e0:8f:ec:00:2f:25:00:50:7f:38:8d:85:08:00 SRC=216.xxx.56.87 DST=192.168.11.108 LEN=65 TOS=0x00 PREC=0xC0 TTL=52 ID=61884 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.11.108 DST=8.8.8.8 LEN=37 TOS=0x00 PREC=0x80 TTL=1 ID=51185 DF PROTO=UDP SPT=44567 DPT=33439 LEN=17 ] 
Dec 4 21:00:48 Orion vmunix: [574257.179600] [UFW BLOCK] IN=eth0 OUT= MAC=e0:8f:ec:00:2f:25:00:50:7f:38:8d:85:08:00 SRC=216.xxx.56.87 DST=192.168.11.108 LEN=65 TOS=0x00 PREC=0xC0 TTL=52 ID=61885 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.11.108 DST=8.8.8.8 LEN=37 TOS=0x00 PREC=0x80 TTL=1 ID=53169 DF PROTO=UDP SPT=44567 DPT=33439 LEN=17 ] 
Dec 4 21:00:54 Orion vmunix: [574263.189267] [UFW BLOCK] IN=eth0 OUT= MAC=e0:8f:ec:00:2f:25:00:50:7f:38:8d:85:08:00 SRC=216.xxx.41.79 DST=192.168.11.108 LEN=65 TOS=0x00 PREC=0xC0 TTL=52 ID=12809 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.11.108 DST=8.8.8.8 LEN=37 TOS=0x00 PREC=0x80 TTL=1 ID=57635 DF PROTO=UDP SPT=44567 DPT=33440 LEN=17 ] 
Dec 4 21:00:57 Orion vmunix: [574266.192366] [UFW BLOCK] IN=eth0 OUT= MAC=e0:8f:ec:00:2f:25:00:50:7f:38:8d:85:08:00 SRC=216.xxx.41.79 DST=192.168.11.108 LEN=65 TOS=0x00 PREC=0xC0 TTL=52 ID=12810 PROTO=ICMP TYPE=11 CODE=0 [SRC=192.168.11.108 DST=8.8.8.8 LEN=37 TOS=0x00 PREC=0x80 TTL=1 ID=58729 DF PROTO=UDP SPT=44567 DPT=33440 LEN=17 ] 
Dec 4 21:01:37 Orion vmunix: [574306.219055] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.11.108 DST=192.168.11.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=58555 DF PROTO=UDP SPT=138 DPT=138 LEN=241 
Dec 4 21:04:37 Orion vmunix: [574486.393908] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.11.108 DST=192.168.11.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=6017 DF PROTO=UDP SPT=137 DPT=137 LEN=58
```



I have looked through some posts and the only people that seem to have been able to do traceroutes through ufw/iptables that I could find gave up and tried tcp traceroutes.
Surely such a work around is not necessary?

Could someone please let me know where I am going wrong with this?

Thanks

---

### Post by jesse27 on 2016-12-05
Is there any more information that someone needs to be able to reply to this?

---

### Post by jesse27 on 2016-12-05
Thankyou deadflowr for the editing

---

### Post by kevdog on 2016-12-06
Although traceroute usually runs over ICMP if you look at your log it also shows trying to run over UDP from specific source port:
PROTO=UDP SPT=44567

Perhaps opening up this outgoing port would help.

In terms of your firewall -- I'm not sure. I don't use ufw rather I usually just write a script that contains the iptables rulesets.  On looking at your setup, I'd make sure that the table you have setup ufw-before-output is really what you want to do. It could be correct -- I'm just not sure.

---

### Post by jesse27 on 2016-12-06
Hi Kevdog
Thanks for your reply.
The SPT (in that log 44567) although constant for that particular traceroute, is a dynamic ip that changes from one traceroute to another.
I cannot work out exactly why UFW blocks what should be open.
I actually want to work out how the default Ubuntu UFW works and use it, but if no-one can help I think I might have to trash it and just go back to good ole iptables too.

---

### Post by jesse27 on 2016-12-06
In case anyone finds this thread and has the same problem I think I have found the issues so I will explain below:

By default UFW seems to put "ufw default deny" close to the start of the ufw config. In mine at least.
So when I changed it to
```
sudo ufw default deny outgoing
sudo ufw default deny incoming
```
this policy seems to take precedence over some but not all other rules. Its a bit bizarre to me, but regardless I made a bash file and put this as the last commands prior to "ufw enable".

It took a few restarts of the service, however, then the traceroutes started to work.
Finally these are the succinct adjustments required

/etc/ufw/before.rules:```

# allow outbound icmp
-A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```

ufw commands (after all other commands and before "ufw enable")
```
ufw allow out to any port 33434:33523 proto tcp
ufw allow out to any port 33434:33523 proto udp
```

I hope this helps someone as there does not seem to be much helpful contribution on this issue regarding UFW that I can find.

Jesse

---

