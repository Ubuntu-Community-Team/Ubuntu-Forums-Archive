---
title: "patches and viruses"
date: 2008-09-09
forum: Recurring Discussions
---

### Post by uberdonkey5 on 2008-09-09
ok, I know ubuntu requires security patches, but are they as bad as this?

[http://www.vnunet.com/vnunet/news/2225710/microsoft-issues-four-patches](http://www.vnunet.com/vnunet/news/2225710/microsoft-issues-four-patches)

I don't like to update regularly and I don't have virus protection in ubuntu. Am I taking a risk? Basically, one of the things I increasingly hate, is that you get a system as you want, then you increasingly fill it with updates, security patches etc etc etc. I wanna just have a working system. My last works computer had double the RAM I started with, but ran at half the speed. I'm presuming it was all the junk that accumulated over 4 years from this type of thing and fragmentation (it was windows).

So, OK ubuntu is a pain to load and get working just right, but after that its pretty perfect, right? Just how secure is ubuntu? Has ANYONE here had a virus?

---

### Post by LaRoza on 2008-09-09
> **uberdonkey5 said:**
> Just how secure is ubuntu? Has ANYONE here had a virus?

For home use, it is perfectly safe. There are no services listening on ports (like Windows) and even if you did get a virus, you'd have to run it as root to get it to do anything, and running something as root is not something that can be done by accident, and running it at all would require explicitly running it.

---

### Post by mrsteveman1 on 2008-09-09
> **LaRoza said:**
> For home use, it is perfectly safe. There are no services listening on ports (like Windows) and even if you did get a virus, you'd have to run it as root to get it to do anything, and running something as root is not something that can be done by accident, and running it at all would require explicitly running it.

There can be privilege escalation exploits in certain things that would allow an exploit in some piece of software running as an unprivileged user to get into other areas of the system. For instance, an exploit in Firefox allowing someone to execute code as the UID Firefox is running under, and then another exploit in something else allowing the attacker to escalate to super user and then do whatever they want to. This is what AppArmor was designed to protect against, and SElinux as well (though SEL is insane).

But in general, Linux leaves a much smaller attack surface than Windows does. I think even XP SP2 left a bunch of ports listening by default with highly vulnerable services behind them, which is why a firewall was absolutely essential.

[QUOTE=uberdonkey5]
My last works computer had double the RAM I started with, but ran at half the speed. I'm presuming it was all the junk that accumulated over 4 years from this type of thing and fragmentation (it was windows).[/quote]

Windows slows down over time with use because it is architecturally flawed (understatement). I find i have to reinstall XP (when i was using it, and Vista as well to some extent even now) almost once a month to keep it working correctly.

[quote=uberdonkey5]
So, OK ubuntu is a pain to load and get working just right, but after that its pretty perfect, right? Just how secure is ubuntu? Has ANYONE here had a virus?[/quote]

Depends on what you mean. Worms are unlikely because as was stated, nothing is by default listening and wide open on the public net with Linux. There is in fact malware written to target Linux but it tends to be targeted at servers, for a specific exploit and for specific use cases, like attacking a high profile target. I don't think random viruses and worms are ever going to be a real problem on Linux. Trojans MIGHT be, but every Linux distro in current use relies on signed software coming from a trusted repository. Rarely if ever does a Linux user download and install anything from any website as you do with Windows, so most users are never going to be faced with a situation where a random app from a chinese website, calling itself a nifty toolbar or screensaver, is asking for permission to do something.

---

### Post by uberdonkey5 on 2008-09-10
thanks fellas (or fella/lady) ;)

thats reassuring and makes me feel better about my switch to linux which was mainly due to reasons of security against viruses and speed.

---

### Post by SunnyRabbiera on 2008-09-10
trust me linux is almost fort knox compared to windows when concerning security, antivirus isnt a concern as the viruses for linux need root accounts to work and ubuntu disables root accounts.

---

### Post by cardinals_fan on 2008-09-10
> **SunnyRabbiera said:**
> trust me linux is almost fort knox compared to windows when concerning security, antivirus isnt a concern as the viruses for linux need root accounts to work and ubuntu disables root accounts.
Viruses for Linux require root **permissions** to work, not the root account.  A virus executing a sudo command could impact Ubuntu just like any other Linux distro, if the user entered their password.  Actually, a distro like Slackware, which has a root account but doesn't activate it by default, is more secure (in my opinion) than a distro using sudo.  A malicious script could use sudo to acquire root permissions, while a system with the root account could only be compromised from within the shell using the root account (accessed with su).

---

### Post by SunnyRabbiera on 2008-09-11
Lets scare him away now shall we...

---

### Post by cardinals_fan on 2008-09-11
> **SunnyRabbiera said:**
> Lets scare him away now shall we...
What?  My position is **the truth** - disabling the root account doesn't magically prevent malicious scripts from obtaining root permissions.

---

### Post by Twitch6000 on 2008-09-12
> **cardinals_fan said:**
> What?  My position is **the truth** - disabling the root account doesn't magically prevent malicious scripts from obtaining root permissions.

At least someone else around here knows the dang truth lol.

to the OP yes there have been viruses around Linux.Has anyone gotten one on Linux,well I myself do not know.I have heard stories though.

Here is a list of Linux viruses and trojans that somehow made a impact.

The List-

Trojans

    * Kaiten - Linux.Backdoor.Kaiten trojan horse[6]
    * Rexob - Linux.Backdoor.Rexob trojan[7]

[edit] Viruses

    * Alaeda - Virus.Linux.Alaeda[8]
    * Bad Bunny - Perl.Badbunny[5][9]
    * Binom - Linux/Binom[10]
    * Bliss
    * Brundle[11]
    * Bukowski[12]
    * Diesel - Virus.Linux.Diesel.962[13]
    * Kagob a - Virus.Linux.Kagob.a[14]
    * Kagob b - Virus.Linux.Kagob.b[15]
    * MetaPHOR (also known as Simile)[16]
    * Nuxbee - Virus.Linux.Nuxbee.1403[17]
    * OSF.8759
    * Podloso - Linux.Podloso (The iPod virus)[18][19]
    * Rike - Virus.Linux.Rike.1627[20]
    * RST - Virus.Linux.RST.a[21]
    * Satyr - Virus.Linux.Satyr.a[22]
    * Staog
    * Vit - Virus.Linux.Vit.4096[23]
    * Winter - Virus.Linux.Winter.341[24]
    * Winux (also known as Lindose and PEElf[25]
    * ZipWorm - Virus.Linux.ZipWorm[26]

[edit] Worms

    * Adm - Net-Worm.Linux.Adm[27]
    * Adore[28]
    * Cheese - Net-Worm.Linux.Cheese[29]
    * Devnull
    * Kork[30]
    * Linux/Lion (also known as Ramen)
    * Mighty - Net-Worm.Linux.Mighty[31]
    * Millen - Linux.Millen.Worm[32]
    * Slapper[33]
    * SSH Bruteforce[34]

Source the wiki

---

### Post by uberdonkey5 on 2008-09-15
> **SunnyRabbiera said:**
> Lets scare him away now shall we...

he he, no need to worry... I'm using linux so much now I find it frustrating to log into windows and try things. Indeed, every time I have booted up into windows (dual boot) in the last couple of months I've quit out of annoyance and gone back into ubuntu. Now I have my system running well I don't wanna change it. Obviously I prefer the truth (having buddhist tendancies, he he) but nice to see that its pretty easy to list the viruses that have been on linux. Be amused to see the same for windows.

Pretty much understand the account vs. permissions also. With my eee pc I'm actually using my main computer less for internet now as well, which should help.

---

