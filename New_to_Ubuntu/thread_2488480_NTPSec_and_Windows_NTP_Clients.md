---
title: "NTPSec and Windows NTP Clients"
date: 2023-07-05
forum: New to Ubuntu
---

### Post by danebriggs on 2023-07-05
I have a Ubuntu 23.04 that I am setting up as an NTP server.   I ran the "sudo apt-get install ntp" to install but it installs ntpsec instead. (See below)  I went ahead and configured ntpsec instead of ntp with mostly default settings.  I've connected multiple devices (VMWare, Cisco Switches, etc) to use the new ntpsec server with no issues.  However, when I point my Windows Primary Domain Controller emulator at the new ntpsec server I get "The computer did not resync because no time data was available."  Upon further investigation is seems "Unlike NTP, NTPsec doesn’t support Windows". Any ideas on how to get Windows to use ntpsec, how to install classic ntp or an alternative ntp package to ntp/ntpsec?  

sudo apt-get install ntp
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  ntpsec
Suggested packages:
  certbot ntpsec-doc ntpsec-ntpviz
The following NEW packages will be installed:
  ntp ntpsec
0 upgraded, 2 newly installed, 0 to remove and 12 not upgraded.
Need to get 0 B/361 kB of archives.
After this operation, 957 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y

I'm new to Linux and I know enough to be dangerous!  So please be patient

---

### Post by TheFu on 2023-07-05
NTP is deprecated. Attacks against the protocol have happened for the last 10 yrs.  I know nothing about MSFT time except that when I opened a bug with MSFT support engineers through work, they said that ±5 min was close enough to be called accurate time. We had multiple MSFT SEs at this job because we were a huge customer.

I use chrony, but don't know how it works for MSFT systems. Sorry.  When I had MS-Windows computers before, Linux NTP was my time server and worked fine ... though the MS-Windows systems were constantly wrong on time, until I forced sync every 15 minutes.  The funny thing is that my network time server running Linux was losing over 15 minutes a day when it had WinXP and Win7 running on it.  With Linux, it is sub-second accurate and all the other systems on my LAN get their time from it. For example, 
```
$ chronyc sourcestats 
Name/IP Address            NP  NR  Span  Frequency  Freq Skew  Offset  Std Dev
==============================================================================
romulus                    11   8   647     +0.000      0.045     +1ns  6117ns
```
It keeps time quite well.

---

### Post by ActionParsnip on 2023-07-06
[https://www.server-world.info/en/note?os=Ubuntu_22.04&p=ntp&f=2](https://www.server-world.info/en/note?os=Ubuntu_22.04&p=ntp&f=2)

Chrony can be a time server

---

