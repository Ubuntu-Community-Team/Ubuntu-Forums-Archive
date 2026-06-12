---
title: "How many known Linux Viruses are there?"
date: 2011-11-11
forum: Recurring Discussions
---

### Post by JayKay3OOO on 2011-11-11
I'd also like to know how dangerous these viruses have been as I know many users don't use protection (uhm).

Cheers

P.S Dunno where all these windows viruses are either as I've never gotten one. Although I use protection on Windows (:oops:)

---

### Post by haqking on 2011-11-11
> **JayKay3OOO said:**
> I'd also like to know how dangerous these viruses have been as I know many users don't use protection (uhm).

Cheers

P.S Dunno where all these windows viruses are either as I've never gotten one. Although I use protection on Windows (:oops:)

none currently in the wild, however not because there couldnt be.

There are no currently good AV solutions either other than for scanning for file sharing with Windows.

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

But dont fall into the trap that Linux is secure so dont worry crowd.

read here [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) for a beginners.noob intro to security and some links to more information

and also how do you know you have never had one ? ;-)

most people dont know the different types of malware or if they have been infected, just because Norton or whatever doesnt tell you doesnt mean you havent been compromised at some point

---

### Post by overdrank on 2011-11-11
Moved to Recurring Discussions

---

### Post by 3rdalbum on 2011-11-13
> **JayKay3OOO said:**
> I'd also like to know how dangerous these viruses have been as I know many users don't use protection (uhm).

No danger; there haven't been any written for a while, and the old ones are no longer in the wild. Even if someone tried to infect your Linux system with an old virus I doubt it would work because today's Linux systems are very different to what we were running a couple of years ago.

---

### Post by Lucradia on 2011-11-13
Trojans can infect any system, no matter the OS, no matter the filesystem. It's the firewall that stops these, not anti-malware or anti-virus, though, if a trojan executes successfully after infecting, then the latters try to catch them.

The problem with trojans is not what they do immediately, but what they do later. For instance, a windows trojan can infect a linux system, but it can't execute itself, it just can latch onto windows files it finds, and then waits to be sent to a windows machine.

Similarly, never run browsers in wine, unless you purposely want to run keyloggers.

---

### Post by haqking on 2011-11-13
> **Lucradia said:**
> Trojans can infect any system, no matter the OS, no matter the filesystem. It's the firewall that stops these, not anti-malware or anti-virus, though, if a trojan executes successfully after infecting, then the latters try to catch them.

The problem with trojans is not what they do immediately, but what they do later. For instance, a windows trojan can infect a linux system, but it can't execute itself, it just can latch onto windows files it finds, and then waits to be sent to a windows machine.

Similarly, never run browsers in wine, unless you purposely want to run keyloggers.

That is incorrect.  AV solutions and Anti malware can detect trojans, trojans are not dealt with by firewalls.  What the trojan can or does do depends on what the trojan is designed to hide.  A firewall will not stop a keylogger being downloaded hidden inside another file.

If the trojan happens  to be an app that calls home then yes the firewall can deal with or prevent that action with outbound rules for example but a firewall is about traffic not whether you get the trojan in the first place.

Besides a virus and a trojan are 2 seperate things so we are off topic as the OP asked specifically about Viruses.

Cheers

---

### Post by JayKay3OOO on 2011-11-14
Thanks guys for the help on this. I was in some form trying to erase the idea that there are no viruses for Linux.

To clarify. I stated viruses, but I should have been a little more specific as I was using the Virus term to blanket anything that can do harm to your computer when using Linux.

Although probably the biggest danger to your computer is an incompetent user ;)

---

