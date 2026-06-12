---
title: "Antivirus?"
date: 2024-10-18
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-18
Heyo!!

What is the best AV for ubuntu?

---

### Post by Quarkrad on 2024-10-18
Essentially there isn't one.  Search for AV in this (wider - not just New to Ubuntu) and you can read pages and pages of why AV is not relevant to Ubuntu/Linux as it is per MS.  Read especially threads where 'false positives' can be obtained with some software(s) that claim to be a linux AV product.

---

### Post by shadowtabby on 2024-10-18
Heyo,

Thank you for the reply and advice.  I have installed clam AV.  What about firewalls?  Do we need one on ubuntu?

All i do really is gaming, testing out streaming on Monday with OBS.  Vid editing I have to relearn on here, but I have been told that shotcut is pretty good and should be easy to learn.  And with web broswing I just use brave.  I trust that.

---

### Post by Rubi1200 on 2024-10-18
Best place to start is with the Ubuntu Security sticky:
[https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

In general, unless you are sharing files with Windows users there is no need for antivirus on Linux.

---

### Post by Autodave on 2024-10-18
I have never run an antivirus program in the 15 years of using Linux.  This is across multiple machines.....some of which were open to the public.  Not a single virus ever.

---

### Post by TheFu on 2024-10-18
Start with the sticky threads and move onto the [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) Basic Security.  Much of what you've learned from MSFT doesn't apply anymore.

There are times when AV is required, but that is more about contracts for insurance coverage than anything too useful for Linux.  The most important security thing you can do for your Linux system (actually, any computer), is to have automatic, daily, versioned, backups that are pulled (not pushed).  Do that first, then worry about contractual mandates for AV and firewalls.

There's only 1 firewall in Linux. It is built-into the kernel already.  We just need to enable it by picking an interface tool into it.  There are about 5 different interfaces into the kernel firewall.  Most end users will be fine using **GUFW**.  If you are running a server and need more control and advanced options, there are **nft** (nftables) and **iptables** interfaces.  I tend to use GUFW on my laptop and UFW on servers, until I outgrow them an need the added power that iptables provides.  I seldom need to use iptables directly, only when some extra complex packet forwarding is required, which is outside the ufw capabilities.

---

### Post by shadowtabby on 2024-10-18
Heyo,

Thank you for you're reply.  Okies, this is going to take a lot of getting used to.

---

### Post by Perfect Storm on 2024-10-18
I haven't run a an Antivirus app in 20+ years. I did it for the first 5 years as I shared files with Windows users.

---

