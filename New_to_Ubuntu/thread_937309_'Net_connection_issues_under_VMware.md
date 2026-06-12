---
title: "'Net connection issues under VMware"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by bobdabuilda on 2008-10-03
Hi guys - yet another Windows pro turned 'nix noob. Looking at playing with Squid etc. for monitoring data usage across my home LAN to see who's chewing up all our bandwidth (yay for 12gb/month net connections).

I am running Ubuntu 8.04 on VMware workstation. Both the host PC (Server 2003) and Ubuntu are configured with static 192.168 addresses, I have both DNS servers configured for both PCs.

Tracert does actually resolve names etc. of websites - to a point, and then stops. ie. the Net *is* working - except for the fact I can't actually make any connections to anything, either in FireFox or when trying to install new packages (get the good ole 111 Connection Refused).

My VMware network adapter is configured in Bridged mode. I am able to browse my network fine, can connect to other machines on my LAN and pull files across. So the hardware and bridging etc. are working... just seems to me to be something in the config of Ubuntu, or a combination of Ubuntu and VMware that i'm missing somewhere ?

Any suggestions please on what else I can check/do to get this working ?

---

### Post by spiderbatdad on 2008-10-03
seems like a permissions and or owner/group issue. Or...are you running ufw?

---

### Post by bobdabuilda on 2008-10-03
Thanks for the response :)

I don't *think* it's a permissions thing... being able to PING external sites etc. says to me that DNS etc is all working fine. I've jsut done some more testing and found that I am also unable to connect to my gateway via FireFox - can still PING it and all that, just unable to make a http connection to it.

Get a "Failed to connect" error saying "Though the site seems valid, the browser was unable to establish a connection" - this happens immediately - no timeout delay or anything along those lines.

I'm thinking "ufw" is short for Ubuntu Firewall ?? If so, i'm fairly certain i've seen during startup a line saying it's not enabled... yup just confirmed that with a "sudo ufw status" = "Firewall not loaded".

I saw something on another thread where someone suggested ensuring the "VMware bridge Protocol" is enabled on the VMware NIC in Windows - so i've tried setting that on both interfaces, with no improvement.

Oh, I also saw another article which mentioned adding ipv6 to a blacklist, which i've also tried with no visible change to my situation.

I've double-checked my network settings under System > Administration > Network, and as far as I can tell that's all set fine (static IP, DNS, mask, etc).

I find it rather odd that PINGs etc. work fine, but i'm not able to make http connections locally ??

Any suggestions very much welcome (provided they're on-topic lol)

---

### Post by bobdabuilda on 2008-10-04
Ok - I think I may have sorted it. Not *exactly* sure what I did to fix it, but I changed a couple of things, and changed them all back (I think lol) and now it's working.

The majority of the issue was caused by Server 2003 - apparently it needs TWO reboots after the installation of VMware in order for the networking to sort itself out.

Thought that had fixed it entirely, as once i'd done that, browsing was fine... but then it stopped again. Have done some tweaking, and played with the VMware Workstation settings, and it appears to be behaving itself now. Rather odd.

Anyways... now to work out what's going wrong with the compile of my Squid install hehe... thanks for trying to help, Spider :)

---

