---
title: "Virius or Firewall?"
date: 2008-05-21
forum: Recurring Discussions
---

### Post by jras20 on 2008-05-21
Do you need a Virus or Firewall protection using Ubuntu?  I heard you dont.
Thanks

---

### Post by danwood76 on 2008-05-21
No virus protection required, though you can still pass windows viruses on so some people get AVG for that sort of stuff or if you share files over a LAN to windows machines.

Firewall is optional, I dont use one but I am behind a router which gives some degrees of protection naturally from hackers. (most routers are linux based these days)

---

### Post by Anduu on 2008-05-21
You should use antivirus to protect any Windows computers you may come in contact with.

As for a firewall you are running one right now(It is built into linux...).Go to [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and check for yourself ;)

---

### Post by p_quarles on 2008-05-21
Moved to Recurring Discussions, where you can all find numerous other threads on this topic.

---

### Post by latna on 2008-05-21
I'm pretty sure ubuntu doesn't enable the firewall on installation. That test will show a clean system on a fresh install because ubuntu has no open ports by default. As soon as you install any servers that will change.

If you install samba to do file sharing you should enable the firewall or configure samba to not listen on the interface facing the Internet. Samba by default will listen on all available interfaces.

iptables is the low level program to configure the firewall. You would probably want a gui frontend for that though. Firestarter is program that I've seen mentioned the most. Of course you don't really need to if you don't install any servers.

---

### Post by jras20 on 2008-05-21
Ok I found firestarter I installed it.  How can I get it to bootup when Ubuntu starts up instead of having to load it manully?
Thanks

---

### Post by Frak on 2008-05-21
IPTables is the default firewall, it is very low level and only accepts input in the form of configuration files. [Firestarter ]("apt:firestarter")manages them.

There is no need for an anti-virus. Since all the software comes from a trusted source or sources, the software is known to be safe and there is no need to protect yourself from anything foriegn.

---

### Post by lisati on 2008-05-23
> **Frak said:**
> IPTables is the default firewall, it is very low level and only accepts input in the form of configuration files. [Firestarter ]("apt:firestarter")manages them.

There is no need for an anti-virus. Since all the software comes from a trusted source or sources, the software is known to be safe and there is no need to protect yourself from anything foriegn.

There might not be a specific need for anti-virus protection specifically for Ubuntu (since most viruses aren't directed at Linux) but it would be a nice touch for Windows users to be reassured that they're not going to get one from you, even if it can't hurt you.

---

### Post by Trail on 2008-05-23
Who cares about them Microsoft (R) Windows (R) users, let them swarm in virii for all I care :) I want my system lightning fast.

---

### Post by smoker on 2008-05-23
> **Trail said:**
> Who cares about them Microsoft (R) Windows (R) users, let them swarm in virii for all I care :) I want my system lightning fast.

exactly, windows users should take their own precautions to ensure the safety of their own machines. if they can't be bothered to protect themselves then why should i care?

---

### Post by lisati on 2008-05-23
> **smoker said:**
> exactly, windows users should take their own precautions to ensure the safety of their own machines. if they can't be bothered to protect themselves then why should i care?

But is the need to protect machines limited to Windows users? True, Windows users should take some responsibility for their machines. But don't we have a moral responsibility not to pass on nasty stuff to others, even when it can't hurt our own machines?

Edit: Back to the original post: there isn't normally any need for extra protection of the anti-virus and anti-spyware kind, but a good firewall and a good dose of good sense is always useful.

---

### Post by danwood76 on 2008-05-23
Is it not Mr Gates' moral duty to fix the bugs in his OS that lead to the viri that attack it?

Microsoft fix a small % of the bugs that lead to the viruses, why do they not do more?

---

### Post by gamont on 2008-05-24
I think the AV is needed even if you dont communicate with Windows.

> 
Assuming you're safe from viruses and other malware
just because you are on a non-Windows platform is a big
mistake, as the number of Linux-based malware doubled
in 2005, according to a report from Kaspersky Labs.

In a report titled "2005: *nix Malware Evolution," the
Russian antivirus software developer pointed out that the
number of Linux-based malicious programs -- viruses,
Trojans, back-doors, exploits, and whatnot -- doubled
from 422 to 863.

Numerically, that pales compared to the 11,000
Kaspersky found for Windows in the second half of 2005
alone. However, it could be more devastating because
many non-Windows users assume malware is only a
Windows problem and don't take any precautions.
Kaspersky said Linux users are careful, but one security
expert disagrees.

"With Linux users, there's a very vigilant effort to make
sure the system is as secure as possible, mostly because
Linux people are very aware of security dangers and the
security that needs to be put in place," said Shane
Coursen, senior technical consultant with Kaspersky's
U.S. office in Woburn, Mass.

"The other thing is that there are people who have transi-
tioned from Windows to Linux, thinking Linux would pro-
vide them more security, and they make sure their new
Linux system is secured," he added.

But Tom Ferris, researcher with Security Protocols, a
computer security research firm in Mission Viejo, Calif.,
said the opposite. "In people's minds, if it's non-Windows,
it's secure, and that's not the case," he said. "They think
nobody writes malware for Linux or OS X. But that's not
necessarily true, as that report showed."

[B]The growth in Linux malware is simply due to its increas-
ing popularity, particularly as a desktop operating system[/B],
said Coursen.
"The use of an operating system is directly correlated to
the interest by the malware writers to develop malware
for that OS," he added.

The Kaspersky report said that the Unix picture mirrors
that on the Win32 front. The biggest problems are exploits
and back doors designed to steal information. There are
also sniffers, flooders and other hack tools. While rootkits
get all the headlines, Coursen said the biggest problems
will still be exploits and Trojans.

--Andy Patrizio, InternetNews.com


---

### Post by aysiu on 2008-05-24
Really. An anti-virus software developer is telling me I need to be worried about viruses? How surprising.

I wouldn't be surprised at all if trojans proliferated as desktop Linux became more popular, but trojans are based on social engineering. Education, and not anti-virus, will stop that.

Anti-virus is the biggest scam ever created, and it's rarely effective against malware anyway. It's just a cleverly-named way for people to gain a false sense of security.

---

### Post by p_quarles on 2008-05-24
> **aysiu said:**
> Really. A anti-virus software developer is telling me I need to be worried about viruses? How surprising.

I wouldn't be surprised at all if trojans proliferated as desktop Linux became more popular, but trojans are based on social engineering. Education and not anti-virus will stop that.

Anti-virus is the biggest scam ever created, and it's rarely effective against malware anyway. It's just a cleverly named way for people to gain a false sense of security.
Cisco (another not entirely neutral source of information) recently said much the same: the entire anti-virus industry has cost corporations and individuals massive amounts of money, and has returned benefits so small as to make it basically nil. 

The recurring discussion we seem to have around here is whether or not anti-virus is needed for Linux. The discussion we *should* be having is whether or not it is needed for Windows. I'd vote "no." Anti-virus software is simply a very passive and wasteful way of protecting against a small number of threats.

The "false sense of security" issue is very real. Running an anti-virus on Windows, while taking no other precautions regarding security, is sort of like installing a fingerprint scanner on your front door, and then leaving that door wide open and unlocked. The expensive piece of security equipment does no good whatsoever if it isn't part of a larger, secured environment.

---

### Post by Frak on 2008-05-24
> **aysiu said:**
> Really. An anti-virus software developer is telling me I need to be worried about viruses? How surprising.

I wouldn't be surprised at all if trojans proliferated as desktop Linux became more popular, but trojans are based on social engineering. Education, and not anti-virus, will stop that.

Anti-virus is the biggest scam ever created, and it's rarely effective against malware anyway. It's just a cleverly-named way for people to gain a false sense of security.
Even worse, AV software has the ability to delete **anything **it seems deemable to destroy.

ESET (the creator of NOD32), some time ago listed an Open Source project, known as Peerguardian2 as a high threat. Reason? PG2 blocked NOD32 updates from being downloaded. Why? Eset had their nose in peoples business in the P2P protection **and **ad markets. To stop their business from going down, ESET removed a FOSS project from everybodies computer that kept up with updates and used NOD32.

They have since just listed it as a minor threat after major criticism. Minor threats are notified of, but not removed. (They are considered as probable false-positives)

---

