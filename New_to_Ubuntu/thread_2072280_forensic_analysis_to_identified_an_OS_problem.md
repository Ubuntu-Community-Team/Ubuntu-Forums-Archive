---
title: "forensic analysis to identified an OS problem"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-10-17
Hi, I'm using ubuntu precise in my laptop, this day to startup it I could not acquire ip addressing, using my ethernet card or wireless, I check if those devices were up and everything was ok, just I could not get Ip, so I tried to restart the networking service but the process was hang up, then I tried to reboot but still I could not get the ip address, so I tried to startup the pc using debian and I got these error:

```

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Unable to resolve 'UUID=f233e543-abb4-4cba-9071-8b490a239bbd'
fsck died with exit status 8

```

also from debian i could not get ip address. obviously the dhcp service is working excellent with other .

after that i decided to reboot into ubuntu and suddenly the problem has gone I got ip address at first.

so what happened? I've already both syslog -debian and ubuntu- and nothing weird, just that i could not bind address.

my questions are:
1. what should i recheck in my syslog files that could help me?
2. is there another log file related to networking service | network devices?
3. what else should i check?

---

### Post by herbert tamayo on 2012-10-17
I want to add this comment: my network is a mixed environment, in the IT department all pcs work with ubuntu, it's a weird thing that all these machines have the same problem: can't get ip address; one of these has ubuntu/windows installation, so booting into windows the same pc got ip but after reboot into ubuntu could not get ip address, also checking in the syslog there is nothing weird, so my new questions are:

4. how can do some test to figured it out what is the problem, the DHCP service? the switch?

5. the network admin said that there is no extra changes in the network, how can I check this?

regards

---

### Post by Bashing-om on 2012-10-17
herbert tamayo;

As several workstations are affected, indicates a network problem. Look to your gateway access.

I would be pinging the various equipments in the network: (routers, switches, hubs)
```
man ifconfig
man ping
```With information in hand-> talk to your system administrator.
[INDENT]hth <==BDQ

[/INDENT]

---

