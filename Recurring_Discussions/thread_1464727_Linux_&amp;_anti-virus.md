---
title: "Linux &amp; anti-virus"
date: 2010-04-28
forum: Recurring Discussions
---

### Post by flyfishingphil on 2010-04-28
This is just an FYI for those wondering about which anti-virus they should use for Linux/Ubuntu.

I spent a little time emailing with a tech at Avast! about what was available, what they offered and what it really needs to be protected using any of the Linux based programs. The answer I got back was both very interesting and very reassuring.

According to the tech I "talked" to there they don't worry about building an anti-virus for the Linux based systems for a couple of reasons. The first is because of the continuous changes in the kernel it makes it nearly impossible for "hackers" to get in to the system. The second, for the same reason, is that they know of no viruses, etc, written to work against Linux and, since there is not threat, they don't see the need to build an anti-virus program specifically for Linux. He said that the one that is included with the Ubuntu covers everything we might need when running Ubuntu only. The other forms of anti-virus are needed only if you run Windough$.

Hope this helps those wondering what they need for anti-virus with Ubuntu.

---

### Post by arrrghhh on 2010-04-28
Yes, I was pretty surprised at first coming from a Windows-only background.

However, if you run a server that shares files with Windows clients, or if you run a mail server, etc it is a good idea to run ClamAV for the sake of their machines.  The server won't get infected, but it may save a client PC :D

---

### Post by lisati on 2010-04-28
Moved to "Recurring Discussions"

---

### Post by Chrysantine on 2010-04-29
> **flyfishingphil said:**
> The first is because of the continuous changes in the kernel it makes it nearly impossible for "hackers" to get in to the system.
The tech is completely clueless - building virii for Linux is trivial as anyone who has ever had to clear rootkits from a server can tell you. 

There is no innate protection that makes the system hard or even moderately difficult to write viruses for - spreading such beliefs is an extremely dangerous thing because it'll come back to haunt you in the long run. 

Yes, there are no viruses for Linux because there's very little profit to be gained from writing them - look at Macs, there were no viruses for them either. Popularity was gained, now virus and malware writers are eyeing OSX because it's starting to become profitable for writing malware for it.

---

### Post by Viva on 2010-04-29
> **Chrysantine said:**
> The tech is completely clueless - building virii for Linux is trivial as anyone who has ever had to clear rootkits from a server can tell you. 

There is no innate protection that makes the system hard or even moderately difficult to write viruses for - spreading such beliefs is an extremely dangerous thing because it'll come back to haunt you in the long run. 

Yes, there are no viruses for Linux because there's very little profit to be gained from writing them - look at Macs, there were no viruses for them either. Popularity was gained, now virus and malware writers are eyeing OSX because it's starting to become profitable for writing malware for it.

I think that tech is talking about the regular bug fixes.

---

### Post by MarcusW on 2010-04-29
> **Chrysantine said:**
> The tech is completely clueless - building virii for Linux is trivial as anyone who has ever had to clear rootkits from a server can tell you. 

There is no innate protection that makes the system hard or even moderately difficult to write viruses for - spreading such beliefs is an extremely dangerous thing because it'll come back to haunt you in the long run. 

Yes, there are no viruses for Linux because there's very little profit to be gained from writing them - look at Macs, there were no viruses for them either. Popularity was gained, now virus and malware writers are eyeing OSX because it's starting to become profitable for writing malware for it.

I'm pretty sure that if it wasn't even moderately difficult to write viruses for Linux, there would be a lot of viruses for Linux. Since Linux has a large share in the server market, it is a target as well. Viruses for Linux do exist, but since those security holes have been plugged, they don't do any harm. Not having security holes is the "innate protection" that makes it hard to write effective viruses.

---

### Post by Chrysantine on 2010-04-29
> **MarcusW said:**
> Since Linux has a large share in the server market, it is a target as well
Servers get hacked all the time - most of the time they just don't get many mentions in the press.

> **MarcusW said:**
> Not having security holes is the "innate protection" that makes it hard to write effective viruses.
If you look at some of the most prevalent 'viruses' today, they aren't exploited through security vulnerabilities but rather by tricking a user to clicking a link or accepting an executable - trojans are much more effective tools than just random viruses.

Also if you take a look (for example) at the Firefox patches for the last 12 months, there have been tons of examples where a Linux system could have easily been exploited through them and there's lots of similar examples from a wide range of different software - even a few days of unpatched software could cause massive damage. 

What I'm trying to say is don't get lulled into the "Linux is invulnerable lololol at you Windows users!" -mentality.

---

### Post by Dayofswords on 2010-04-29
> Windough$
this is a new one :P

---

### Post by Meep3D on 2010-04-29
Viruses have not really existed anywhere since floppy disks stopped being the main source of transfer of software.  There are a few examples but they are pretty limited.

Worms got Windows a bad reputation in the early 2000's with things such as Code Red and Nimda.  The prevalence of NAT and default firewalls have largely mitigated this threat now.

Malware is the main thread to modern day systems and it comes in two varieties and is almost entirely distributed by people with a financial motive:

1: Drive by + exploit.  Using code execution bugs and privilege elevation bugs this code tries to gain access to your system to either spam you with popups or turn it into a zombie as part of a botnet.  Notable examples are Flash and PDF problems which have affected Linux users.  This is multiplied by people refusing to run system updates and sticking with outdated browsers.

2: Social Engineering.  In truth the bulk of malware (and what is considered viruses) is on peoples Windows machines because they click on anything they are told to click and run anything they are told to run.  If a website launches a popup that says 'Your computer is infected, run this to save it!' and you run it then there is pretty much nothing that can be done about it.

In short it's largely a user education issue rather than a technical issue.  The primary reason Linux isn't targeted is it is too small a target and the average user is far more educated in security matters and good practices.

---

### Post by del_diablo on 2010-04-29
> 1: Drive by + exploit. Using code execution bugs and privilege elevation bugs this code tries to gain access to your system to either spam you with popups or turn it into a zombie as part of a botnet. Notable examples are Flash and PDF problems which have affected Linux users. This is multiplied by people refusing to run system updates and sticking with outdated browsers.

2: Social Engineering. In truth the bulk of malware (and what is considered viruses) is on peoples Windows machines because they click on anything they are told to click and run anything they are told to run. If a website launches a popup that says 'Your computer is infected, run this to save it!' and you run it then there is pretty much nothing that can be done about it.

I disagree, trojans are not viruses.

---

### Post by MarcusW on 2010-04-29
> **Chrysantine said:**
> Servers get hacked all the time - most of the time they just don't get many mentions in the press.


If you look at some of the most prevalent 'viruses' today, they aren't exploited through security vulnerabilities but rather by tricking a user to clicking a link or accepting an executable - trojans are much more effective tools than just random viruses.

Also if you take a look (for example) at the Firefox patches for the last 12 months, there have been tons of examples where a Linux system could have easily been exploited through them and there's lots of similar examples from a wide range of different software - even a few days of unpatched software could cause massive damage. 

What I'm trying to say is don't get lulled into the "Linux is invulnerable lololol at you Windows users!" -mentality.

Hacked, sure. Virus? Not really. Just as you're saying though, social engineering is as easy to implement on Linux as on Windows.

Still. In Ubuntu you have a repository that gives you almost all software you need, signed so you know it's "the real thing", and all the software gets security updates automatically. It's alot harder to trick someone into installing some random thing on the internet if you don't install software "the windows way".

---

### Post by Meep3D on 2010-04-29
> **del_diablo said:**
> I disagree, trojans are not viruses.

I never said they were.

---

