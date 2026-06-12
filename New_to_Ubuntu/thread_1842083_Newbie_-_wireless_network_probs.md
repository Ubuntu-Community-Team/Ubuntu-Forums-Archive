---
title: "Newbie - wireless network probs"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by krisb60 on 2011-09-10
Installed ubuntu 3-days ago via Windows. Install completed and several updates applied. All great and working via my wireless router. Next day would not connect to the Belkin router (router log says "sending", ubuntu says "getting IP configuration"). So I set the IP configuration in ubuntu manually and presto it now works with the IP address as already known to the router.
Next day (now) connects to the router but has not internet. Severla reboots etc, still not internet. The router working fine for everyone else. PING won't return anything.
So 2 issues:
1. Why is ubuntu refusing to accept the wireless connection via DHCP, having previously worked?
2. Why is ubunbu failing to reach the internet having previously worked?
Anticipating plenty of useful help before I contemplate giving up completely :-(

---

### Post by snip3r8 on 2011-09-10
Welcome to the forum.

Firstly ,what version of ubuntu are you runniing?

---

### Post by krisb60 on 2011-09-11
11.04
build 2.6.38.11

---

### Post by gandaran on 2011-09-11
> **krisb60 said:**
> Installed ubuntu 3-days ago via Windows. Install completed and several updates applied. All great and working via my wireless router. Next day would not connect to the Belkin router (router log says "sending", ubuntu says "getting IP configuration"). So I set the IP configuration in ubuntu manually and presto it now works with the IP address as already known to the router.
Next day (now) connects to the router but has not internet. Severla reboots etc, still not internet. The router working fine for everyone else. PING won't return anything.
So 2 issues:
1. Why is ubuntu refusing to accept the wireless connection via DHCP, having previously worked?
2. Why is ubunbu failing to reach the internet having previously worked?
Anticipating plenty of useful help before I contemplate giving up completely :-(
when I have network problems like yours I just remove every setup connection in network manager and maybe reboot then wait for the connection to automatically setup and ask for the wireless wpa password, as worked for me every time.

---

### Post by krisb60 on 2011-09-11
Nope that hasn't worked.
So need to manually set IP..
Internet doesn't work
Oh and Windows network not seeing anything on my Windows Home PC share (despite working fine a couple of days ago

---

### Post by gandaran on 2011-09-11
> So need to manually set IP
DHCP server is enabled on the router?

---

### Post by krisb60 on 2011-09-12
Yes, DHCP originally allocated the IP address that I must now load manually.

---

### Post by krisb60 on 2011-09-13
So no-one got any words of wisdom and my installation completely unusable?

---

### Post by gandaran on 2011-09-13
okay, one more question, which brand of wireless chipset on the computer?
```
lspci
```
or
```
lsusb
```
shows the answer
if it happens to be an Intel device try changing the wireless security (wep, wpa and wpa2 and try open too) see if that fixes the problem.

---

### Post by krisb60 on 2011-09-14
I will check but add that I can access the router control panel without issue.....It has internet connectivity but Firefox in ubuntu does not

---

### Post by krisb60 on 2011-09-14
Update for anyone watching - internet still not working, Windows network access now working, Skype working. PING works to the router but not to the internet. Still won't DHCP without applying settings manually.
HELP ?

---

### Post by krisb60 on 2011-09-25
In the bin it goes :cry:

---

