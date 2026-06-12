---
title: "[SOLVED] To Firewall or not to Firewall:that is the question!"
date: 2008-05-25
forum: Other OS Talk
---

### Post by Google Spider on 2008-05-25
I am running Windows XP in virtual box, host OS Linux Mint. Does windows need a 3rd party firewall?

First I was going to install zone alarm in XP but then I thought if XP is running on top of Linux, ipTables will probably block all the naughty hackers out.(Am I right?) An extra layer of security is good but I don't want too many processes running coz that will slow down the virtual machine :-/

Will windows somehow make a direct connection to the internet or all traffic has to pass through Linux firewall first? (I mean how does Virtual Box implement it?)

What do you think? 

ps: BTW, I'm not installing the firewall unless someone tells me that its absolutely necessary.

---

### Post by cdtech on 2008-05-25
I'm thinking a port is a port is a port. You access anything using XP, you've allowed access to your XP OS. Linux iptables is a port configuration utility. I don't know...........

---

### Post by miggols99 on 2008-05-25
The virtual machine gets the internet through the host OS (which in this case is Linux) so whatever is protecting the host is protecting the guest.

In other words, no. You won't need an extra firewall.

---

