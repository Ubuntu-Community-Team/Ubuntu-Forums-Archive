---
title: "Do I need a Firewall/Ant-ivirus?"
date: 2008-06-20
forum: Recurring Discussions
---

### Post by LMD1990 on 2008-06-20
So, people tell me that Ubuntu and it's variants are safe to run without a firewall or anti-virus. This concept is kinda alien to me, and I'm also slightly paranoid- so, do I really need a Firewall/Anti-virus?

I'd like to be sure that Ubuntu is as secure as I've heard people say it is.

EDIT: And yeah, I put the hyphon in the wrong place in the title :p

---

### Post by alexandremrj on 2008-06-20
The anti-virus part is an open issue so i wont't tell about it, although i prefer to be paranoid than to be sorry.

Ubuntu already has a firewall but it's not enabled by default. It's called uwf - uncomplicated firewall - and works from the command line.

I recommend you read about it here:
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

Any questions just ask

---

### Post by Dori02 on 2008-06-20
I personally use Firestarter as Firewall, KlamAV as Antivirus for my Kubuntu (Or ClamAV for Ubuntu)

Love to hear other Firewall/ Antivirus configurations, though.:rolleyes:

---

### Post by hyper_ch on 2008-06-20
(1) you don't need av

(2) very likely you don't need to twinker with iptables either...

---

### Post by barbedsaber on 2008-06-20
> **hyper_ch said:**
> (1) you don't need av

(2) very likely you don't need to twinker with iptables either...

nuff said

---

### Post by fatality_uk on 2008-06-20
Actually, Ubuntu's firewall, iptables is part of the system and **IS** installed by default.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
The packages mentioned are front end GUI configs. Unless you specifically open up ports by say installing a web server like apache, it's closed off.

As for the Anti-Virus. You do not need it for most situations. Do a quick google check as to why Linux is safer but essentially, for a Virus to propogate, it needs admin rights and they can only be given by you. 

If however you share files over a Windows network, or swap files with a Windows user, you could take the option to install an AV app. But you, as a Linux user, would not need to run an AV app. The protection given by the AV apps will only apply to the Windows users you swap files with, NOT your system.

---

### Post by attari on 2008-06-20
> **LMD1990 said:**
> So, people tell me that Ubuntu and it's variants are safe to run without a firewall or anti-virus. This concept is kinda alien to me, and I'm also slightly paranoid- so, do I really need a Firewall/Anti-virus?

I'd like to be sure that Ubuntu is as secure as I've heard people say it is.

EDIT: And yeah, I put the hyphon in the wrong place in the title :p


You would need neither for desktop. And just the firewall for the server. However you need Anti-rootkit. Get rkhunter.

---

### Post by rockinlinux on 2008-06-20
I never use a AV and never have problems. as for the firewall its secure as it stands from what i know. I have been using for years and have never had any problems with security.

---

### Post by LMD1990 on 2008-06-20
Okay, so I got Firestarter, but now i think it's stopping me downloading stuff using Add/Remove... how do I configure a rule to let the Add/Remove function through?

EDIT: False Alarm, it works.

---

### Post by Zeotronic on 2008-06-20
I've never had problems with Firestarter and Add/Remove... Now I HAVE had problems with firestarter blocking other things, but you might want to consider that it may be something else... obviously, to check if it is, you should try turning it off momentarily. Just have it open when it blocks it if its blocking it... I think it gives you some options but I don't mess with it regularly enough to know for sure.

---

### Post by wpshooter on 2008-06-20
> **LMD1990 said:**
> Okay, so I got Firestarter, but now i think it's stopping me downloading stuff using Add/Remove... how do I configure a rule to let the Add/Remove function through?

LMD1990:

   Whether you use any of this "protection" software sort of depends on how critical the information on your computer is.

   If you are runnng some type of business and the loss of the information would create a financial loss then you might consider using some of the addition protection programs, otherwise IMO you do not need it.  I have been running various versions of Ubuntu for about 3 years now on my home computers with only the security that is built into the O/S and to my knowledge I have not had the 1st virus and/or security issue.

   Good luck.

---

### Post by athowell on 2008-06-20
If you don't use AV/Firewall/RK scanner, how would you know if you had a problem in the first place?  I'm trying to find tools to use that alert me in the event a problem is detected.

---

### Post by wpshooter on 2008-06-20
> **athowell said:**
> If you don't use AV/Firewall/RK scanner, how would you know if you had a problem in the first place?  I'm trying to find tools to use that alert me in the event a problem is detected.

Because things would start not working like they are supposed to and I have had no such in 3 years !!!

Personally, I think you are wasting your time and if you install any of this you are going to be wasting CPU cycles.  But to each their own.  Please remember that this is NOT M/S windows.

---

### Post by JordanH on 2008-06-20
I'm reading through the above and it seems to be the same question asked but far different responses than I would have expected.

I do agree that anitvirus on a home linux desktop system is presently not really needed, you may consider installing one if it's acting as a file server for Windows machine.  In that case, the purpose is not to protect your system but protect your users who may be running another OS.  Linux systems are not impervious to viruses, trojans etc.  Perhaps more bang for your buck would be something like Tripwire - it's NOT antivirus but protects the integrity of your system files.

The real reason I'm posting this is that you really should enable the firewall rules on your machine.  Failing to do so is hubris and it would be negligent of you because you can not guarantee that all linux applications will be secure.  For example, maybe you have a local daemon running as root and there is a security flaw, perhaps that is now exposed to the internet.  Why keep those ports open for potential attackers to attempt to gain access?  There are many simple firewalls available either GUI or scripts.  IPTables scripts take practically no CPU cycles so there is no reason NOT to have them enabled - only benefits.

For the practical home system; antivirus is not needed. integrity tools (like Tripwire) might be desired.  A few firewall rules are a must.

---

### Post by snappy46 on 2008-06-20
I have been running Ubuntu for a few years now without any virus checker or firewall other than what might already be enable through the ip-routes on default.

I never had a virus or security issues that I know of.  I do use a router (hardware) that do act like a firewall and once in a while go to the grc (shieldup) site to do a scan of my ports.  It always come back telling me that all my ports are sthealh which is a good thing.

I feel pretty secure without an anti-virus or firewall for now.  As Ubuntu and other linux distribution gain more and more popularity things might be different.  Although I agree that Linux is way more secure than MS windows will ever be I also believe that if human make it; human can break it!!!  :)

---

### Post by philinux on 2008-06-20
According to this test.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

I've only 2 ports stealthed. "True Stealth Analysis Failed".

The other common ports are list as "Your computer has responded that this port exists but is currently closed to connections"

I'm installing firestarter to get full stealth.

---

### Post by hyper_ch on 2008-06-20
> **JordanH said:**
> For example, maybe you have a local daemon running as root and there is a security flaw, perhaps that is now exposed to the internet.
By default you have no daemon running

> **JordanH said:**
> Why keep those ports open for potential attackers to attempt to gain access?
Well, in most cases you want to have an open daemon when you install one... 

> **JordanH said:**
> There are many simple firewalls available either GUI or scripts.  IPTables scripts take practically no CPU cycles so there is no reason NOT to have them enabled - only benefits.
No, you block things where you don't need to block anything. And practically no CPU cycles != 0 CPU cycles. And according to those forums here there are many people that just install firestarter which adds rules and those people then complain something does not work...

> **JordanH said:**
> A few firewall rules are a must.
No, by default ubuntu is as secure as it can be for a large number of different installs. Linux treats you like a human. You make choices what you install and hence it should be you to know what you're doing. Mindless zombies that listen to the virus/firewall/... boogeyman belong to Windoze.

---

### Post by aysiu on 2008-06-20
Antivirus works in one or both of two ways:
1. Keep a list of known viruses and scan for those
2. Look for signs that the executable exhibits alarming behavior (self-replication, for example)

In light of this understanding of antivirus, this whole idea that "Linux isn't impervious, so we need antivirus" makes no sense.

1. If the antivirus kept a list of known virus threats to Linux, the list would be virtually empty right now. And if a new threat appeared, people would be able to install antivirus or avoid it faster than the definitions could be added to the list of known viruses.

2. Guessing what might be a threat or not just leads to a lot of false positives (which you see often when you run antivirus in Windows), which leads to people getting excessively paranoid about completely harmless files or just desensitized to antivirus warnings in general, both of which defeat the purpose of antivirus.

In other words, antivirus is essentially useless unless you are running a mail server.

Be smart. A self-replicating virus is not going to be the biggest threat to your Linux installation.

---

### Post by brian_p on 2008-06-20
> **JordanH said:**
> The real reason I'm posting this is that you really should enable the firewall rules on your machine.  Failing to do so is hubris and it would be negligent . . . .

No, it would not be. It makes perfect sense not to have one.

>  . . . . of you because you can not guarantee that all linux applications will be secure.

All installed services on Ubuntu are safe by default. Guaranteed.

> For example, maybe you have a local daemon running as root and there is a security flaw, perhaps that is now exposed to the internet.

Ubuntu installs a service running as root? Which one? And how would an iptables rule help? An example would clarify your claim.

> Why keep those ports open for potential attackers to attempt to gain access?

If you do not want to run the service close it down or uninstall it.

> A few firewall rules are a must.

Zero is the ideal number to have.

---

### Post by ComputerGeek31618 on 2008-06-20
Now hold on.  There is no way *anything* can be totally secure.  There is always a potential, if only due to a bug or a really wierd set of circumstances, that something could be compromised.  Granted, Linux is nearly impossible to get your nose around, but the word is "nearly."  Just because Linux runs in a completely different way than windows...
You can't be too safe.

---

### Post by hyper_ch on 2008-06-20
> **ComputerGeek31618 said:**
> You can't be too safe.

That's true... unplug your computer, take it your yuor bank's vault and enclose it there... that's probably as safe as you can manage to make it... but then, what about usability?

---

### Post by brian_p on 2008-06-20
> **ComputerGeek31618 said:**
> Now hold on.  There is no way *anything* can be totally secure.  There is always a potential, if only due to a bug or a really wierd set of circumstances, that something could be compromised.

'Potential' implies a set of circumstances which lie in the future and whose exact nature is unknown. Being unknown makes it impossible to defend against. Firewalls don't possess precognition.

Also, I did not say Ubuntu is totally secure.

---

### Post by aysiu on 2008-06-20
> **ComputerGeek31618 said:**
> Now hold on.  There is no way *anything* can be totally secure.  There is always a potential, if only due to a bug or a really wierd set of circumstances, that something could be compromised.  Granted, Linux is nearly impossible to get your nose around, but the word is "nearly."  Just because Linux runs in a completely different way than windows...
You can't be too safe.
Agreed. Nothing is totally secure, and you can't be too safe.

But pretending running antivirus in Linux or adding extraneous firewall rules in Ubuntu makes you safer doesn't make you totally secure either.

---

### Post by fonsi2099 on 2008-06-21
And now! for beginners like me:
one thing is clear we don't need an anti-virus, that's very very fine! many thanks.

The second point isn't clear: are we needing a firewall or not? 
If yes i.e. Firestarter is the default configuration OK for home and small office applications. 

Thanks for help:guitar:

---

### Post by hyper_ch on 2008-06-21
> **fonsi2099 said:**
> The second point isn't clear: are we needing a firewall or not?
You have one already called iptables

> **fonsi2099 said:**
> If yes i.e. Firestarter is the default configuration OK for home and small office applications.
Default configuration that firestarter applies to iptables will block just about everything... which is not necessary and makes lots of people come here and complain... If you don't install services, you don't need to configure a firewall... if you install services like p2p, apache, mysql, ssh server, ..... then you might need one...

But setting up firewall rules, just to have them, does not benefit you at all.

---

### Post by imjscn on 2008-06-22
I just started downloading Xubuntu, will install a XP+Xubuntu dual OS. I have emule(P to P file sharing) and ZoneAlarm Security Suit(Antivirus/Antispy/Firewall) installed in WinXP. I probably sometimes need to share a file between WinXP and Linux. Also, If WinXp opened a port, will that port still be open when boot into Linux? In my case, do I need the security things in Linux?
Another question is...I heard that Linux does need an Anti-Rootkid...Which real time Anti-Rootkid protection is the best for Xubuntu? 
Thanks!

---

### Post by hyper_ch on 2008-06-22
> **imjscn said:**
> lso, If WinXp opened a port, will that port still be open when boot into Linux?
No, it's two independant OSes


> **imjscn said:**
> In my case, do I need the security things in Linux?
Not really... however if you download stuff that you want to use then in Windows, you might want to av check that stuff...

> **imjscn said:**
> Another question is...I heard that Linux does need an Anti-Rootkid...Which real time Anti-Rootkid protection is the best for Xubuntu?
Best thing is to know what you do on the system... there are scanners, but not real time ones. Check out   chkrootkit   and   rkhunter

---

### Post by snappy46 on 2008-06-23
I just love those debate about Firewall and anti-virus on Linux.  Thankfully Linux does not have all the problem that ms window has.  Just has an example a few days ago I had to run a window application ( I use virtual box) and since the process was taking a lot of time I decided to go on the internet.  I must say that I usually never go on the internet using windows but for some strange reason I click the internet explorer on the bar (I normally just use firefox in Linux).  Well, within minutes (about 10 minutes) I manage to pickup enough adware/spyware/malware and viruses to last a life time.  Now my guest ms window is acting all weird and nice ads are poping up all over the place (nice!!!).  I endup downloading adware from lavasoft to try to get rid of some of those pesty popup.

Unfortunately one of the trojan still seem to want to hang on.  Look like I will have to format and reinstall window under virtual box again; man what a pain.

All that just to say that this was a good reminder of just how secure Linux is compare to window: 2 years+ with Linux and zlicht, nada, nothing to report about adware/spyware etc...; 10 minutes with windows and well I don't want to repeat myself but I think you got the point.

Linux (Ubuntu) rocks.  I do not believe that a virus checker or firewall is required on linux but if it makes you feel better than go ahead and install them.  Just be aware that the firewall might complicate things for you when using certain piece of software that uses the internet (torrent client, skype etc...) and you will probably endup having to open up ports using the firewall configuration system to make the software(s) work.

Happy computing!!!:)

---

### Post by JordanH on 2008-06-23
> **brian_p said:**
> No, it would not be. It makes perfect sense not to have one.
I disagree with you but since you don't add any reasons to justify your "perfect sense not to have [a firewall]" then I won't argue with you.

> **brian_p said:**
> All installed services on Ubuntu are safe by default. Guaranteed.  :-)  Guaranteed.  You don't speak officially for the Ubuntu folks, do you?  This might be news worthy.


> **brian_p said:**
> Ubuntu installs a service running as root? Which one? And how would an iptables rule help? An example would clarify your claim. Many daemons run as root including typical services like SSH and FTP.  It wasn't too long ago when OpenSSH had a security vulnerability ([http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)).  With a few simple rules, for example allowing only certain hosts/mac addresses to connect to ssh, this would have reduced the risk without worrying a sysadmin.

Other attacks I see quite frequently are dictionary attacks trying to login as root to my ssh server as well as DOS attacks pounding away at a specific service.  Using IPTables, you can limit the rate at which these people can attempt to connect to your machine - in the case of ssh, you can ignore connections after several failed attempts.  For DOS attacks, you can recognize a flood of syn packets and drop them silently.

> **brian_p said:**
> If you do not want to run the service close it down or uninstall it.

Following this logic, you'd suggest I don't connect my computer to the Internet.  I do want ssh services to be provided, I'm just going to allow only specific machines to be able to access it though.

There are quite a few different types of attacks out there from spoof'd IP addresses, DOS, brute-force dictionary attacks, etc.  Having no firewall is an invitation for trouble.

For the other readers out there, I strongly suspect that Ubuntu, nor developers of packages provided on Ubuntu, "guarantee" safety and security of your system.  Bugs happen.  Your home machines are attacked more often than you'd think.  A simple firewall can help.

---

### Post by aysiu on 2008-06-23
Ubuntu does not install an SSH or FTP server by default. If you decide to install and run those services, you should know how to keep those secure and set up appropriate firewall rules for them.

---

### Post by brian_p on 2008-06-23
> **JordanH said:**
> I disagree with you but since you don't add any reasons to justify your "perfect sense not to have [a firewall]" then I won't argue with you.

That was a response to your guilt inducing reference to it being 'negligent' not to install a firewall. As for giving reasons - they came later and you have responded to them.

> :-)  Guaranteed.  You don't speak officially for the Ubuntu folks, do you?  This might be news worthy.


No, but I can read and so can any user. Look at the default configuration for a service. Anything unsafe there? If so, report a bug. By the way, 'not safe by default', 'almost safe by default' or 'can give no assurance daemaons are safe by default' as a guarantee are all reasons to look to use another OS.

So, install exim or mysql or samba with the confidence of getting a secure service. And all without the need to touch a firewall.

> Many daemons run as root including typical services like SSH and FTP.  . . . . 

You're employing a very broad brush to make a case for such daemon being inherently insecure. ssh has privilege separation and proftpd has limited use for root privileges, working mainly as the user given in the configuration file. The situation varies from daemon to daemon and is more complex than a simple 'runs as root'.

> It wasn't too long ago when OpenSSH had a security vulnerability ([http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)).  With a few simple rules, for example allowing only certain hosts/mac addresses to connect to ssh, this would have reduced the risk without worrying a sysadmin.

In that particular case a few iptables rules might have come in useful. There again, denyhosts or a suitable /etc/hosts.allow or (gasp) configuring sshd.conf would have been just as effective.

The code confusion in libssl was never exploited but had it been only a hundred or so machines out of 100,000,000 would have been accessed. Yours wouldn't have been one of them.

> Other attacks I see quite frequently are dictionary attacks trying to login as root to my ssh server as well as DOS attacks pounding away at a specific service.  Using IPTables, you can limit the rate at which these people can attempt to connect to your machine - in the case of ssh, you can ignore connections after several failed attempts.  For DOS attacks, you can recognize a flood of syn packets and drop them silently.

Dictionary attacks are sidesplitting; they cannot even get a valid username. If by some miracle they did there is still a 16 character password or 2048 bit key to crack. Forget about them. They are of no danger.

DOS attacks and SYN floods (not exactly common, are they) do not threaten the basic security of the service. I assume they do not just suddenly stop and go away because the limit module is used so service efficiency may still be impaired.


> Following this logic, you'd suggest I don't connect my computer to the Internet.  I do want ssh services to be provided, I'm just going to allow only specific machines to be able to access it though.

You said:

> Why keep those ports open for potential attackers to attempt to gain access?

I replied:

> If you do not want to run the service close it down or uninstall it.

Offering a service is an open port in WindowsSpeak. The logic is obvious.

> There are quite a few different types of attacks out there from spoof'd IP addresses, DOS, brute-force dictionary attacks, etc.  Having no firewall is an invitation for trouble.

If one of the trusted IPs you have mentioned a few times is spoofed how does your firewall help?

And having no firewall is sensible if you accept services are safe by default, If you do not you have the wrong OS.

> For the other readers out there, I strongly suspect that Ubuntu, nor developers of packages provided on Ubuntu, "guarantee" safety and security of your system.  Bugs happen.  Your home machines are attacked more often than you'd think.  A simple firewall can help.

I suspect you have some concept of the word 'guarantee' over and above that of giving an assurance. The Debian view on security is at

[http://www.debian.org/security/](http://www.debian.org/security/)

Now there's a guarantee against bugs! Let the attacks commence. The OS and regular updates are your assurance - not the firewall.

---

### Post by lisati on 2008-06-23
Do we need antivirus on Ubuntu (or other *nix based distros) or not?

**For the OP and other interested parties:** I've said elsewhere that it's usually a matter of courtesy to Windows users and sometimes as an aid to making sure you don't violate your email provider's terms of service.

**For the technically competant readers of this thread:** It occurred to me last night that *just because an executable file is designed for a different platform, it is no guarantee that a piece of malware can't do some mischief or cause some grief. *What would happen if you run a program compiled for MS-DOS or Windows on Linux? Best case scenario: It just wouldn't run without help, no damage done. Worst case scenario (assuming necessary permissions were in place to let it run without the help of something like Wine or DOSemu): the answer is in the "unpredictable" category.

---

### Post by hyper_ch on 2008-06-23
as linux and windows is completely different from core I don't see how a (real/pure) windows/dos program could be run without wine or similar stuff as compatibility layer...

Java applications are different...

---

### Post by aysiu on 2008-06-23
> **lisati said:**
> 
**For the technically competant readers of this thread:** It occurred to me last night that *just because an executable file is designed for a different platform, it is no guarantee that a piece of malware can't do some mischief or cause some grief. *What would happen if you run a program compiled for MS-DOS or Windows on Linux? Best case scenario: It just wouldn't run without help, no damage done. Worst case scenario (assuming necessary permissions were in place to let it run without the help of something like Wine or DOSemu): the answer is in the "unpredictable" category. How would antivirus help in this scenario?

---

### Post by lisati on 2008-06-23
> **hyper_ch said:**
> as linux and windows is completely different from core I don't see how a (real/pure) windows/dos program could be run without wine or similar stuff as compatibility layer...

Java applications are different...

> **aysiu said:**
> How would antivirus help in this scenario?

The best defense is to be alert and aware of what's going on.

What I had in mind was a  major muck-up on my part many years ago developing a program for someone else: I had assumed that doing things a particular way would work on the other person's computer because it worked perfectly on mine. To cut a long story short, their machine was sufficiently different that their database ended up being scrambled.

The application in this context is that we can't afford to assume that malware designed for Windows won't be able to make a nuisance of itself with Linux, even with its protection: if the malware can somehow get past the security measures and get a binary file running (**most likely through carelessness and/or ignorance and/or someone doing something "dumb")**, the 'x86 under the hood won't care, and will try to plow on regardless.

---

### Post by imjscn on 2008-06-24
I installed vmware player, WinXP guest on Ubuntu host. Now I want to add share folder service in Ubuntu. Is it safe or risky?

---

### Post by imjscn on 2008-06-30
???

---

### Post by lisati on 2008-06-30
> **imjscn said:**
> I installed vmware player, WinXP guest on Ubuntu host. Now I want to add share folder service in Ubuntu. Is it safe or risky?
If it's data only: fairly safe.

---

### Post by imjscn on 2008-06-30
that's great! thanks!!

---

### Post by Mr Fat Bat on 2008-11-20
The concern for me is that I connect to my work network over SSH and use port forwarding to connect to our mail server.  As I'm sending/receiving mail directly from work our internal server I don't want to (in the rare case the on server AV fails) forward any emails containing either a malicious attachment(s) or embedded scripts to M$ users.

So can anybody recommend a good AV to scan through Thunderbird traffic (or monitor the emails through the port I connecting through)?

Cheers!

---

