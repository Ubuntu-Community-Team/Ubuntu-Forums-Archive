---
title: "Viruses"
date: 2008-12-19
forum: Recurring Discussions
---

### Post by joker243 on 2008-12-19
I am a complete newb when it comes to Linux. I Was wondering what is a good OPEN SOURCE Virus protection suite and Spyware suite for Ubuntu 8.10. 

Also I was wondering how do you install programs on Ubuntu. Please don't laugh I am just a newb and I like to learn from the best - the best refering to the user(s)

---

### Post by binbash on 2008-12-19
you dont worry about spywares and viruses at linux.Just forget it

---

### Post by nordmichael29 on 2008-12-19
in Ubuntu t is virtually Impossibvle to get a virus, and thus no protection is needed, or even offered as far as I know, there's one program called clamwin antivirus that may support linux. but that's only if you want to find windows bugs.

---

### Post by click4851 on 2008-12-19
I keep hearing about ClamAV, and Avast....take a look?

---

### Post by SunnyRabbiera on 2008-12-19
You really dont need antivirus for linux as really linux has no viruses, or at least any that really work.
Most linux viruses are conceptual and windows viruses have no effect on linux.
As for installing software, there are many ways to do it, but typically we use something called apt to download and install packages.
Both synaptic (found under system, administration, synaptic package manager)
and add/remove are front ends for it.
Software installation is easy, just open one of those up, click on a box, hit apply and the process is painless from there on in :D

> **click4851 said:**
> I keep hearing about ClamAV, and Avast....take a look?
Clam is more for windows viruses, its only needed if you run a mailserver, have a microsoft share or other.
Linux has no working viruses.

---

### Post by cdtech on 2008-12-19
By using the repositories to install packages, md5 checksums and using root privileges only when necessary are just a few ways to to guard against an intrusion or a system wide infection. SSH is often the first point of entry to a Linux machine, so using strong passwords could guard against an SSH intrusion. Antiviral software should **ALWAYS** be common practice for any OS and could potentially limit the risk of a system catastrophe.

There is a method to infect a system wide Linux OS without the need to become root, it's known as &#8220;Privilege escalation&#8221; --

> &#8220;Privilege escalation is the act of exploiting a bug or design fault in a software application to gain access to resources which normally would have been protected from an application or user. The result is that the application performs actions with more privileges than intended by the application developer or system administrator&#8221; (wiki, Privilege escalation). 

This is just my two cents and everyone has their own methods to protect their own systems......

**UPDATE::.**
Running "clamscan" on my system display's:
```
----------- SCAN SUMMARY -----------
**Known viruses: 175983**
Engine version: 0.92
Scanned directories: 1
Scanned files: 144
Infected files: 0
Data scanned: 653.43 MB
Time: 124.086 sec (2 m 4 s)
```

---

### Post by jerome1232 on 2008-12-19
I think this is a good sticky to take a look at when it comes to security [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Really if you keep you system patched and updated there is no known malware or virus that can infect your system, so I don't see the good in having a piece of software that scans for threats your already patched against. But that's my two cents.

---

### Post by thane1 on 2008-12-19
You may be relatively safe yourself using linux.  But if you forward emails from your windoze friends to other winduh friends, you won't be on the end of the line recipient's 10 list if you forward them a virus (especially if it doesn't get you personally).  If you don't do a lot of mail (such as jokes) forwarding, maybe this is not a concern.  However if you forward emails frequently, you might want to consider an antivirus program such as clamav available through the (safe) repositories of Synaptic.  It works with a number of email programs easily, although if you're using Thunderbird, you would have to get a mozilla thunderbird add-ons registration to install clamdrib in thunderbird for clamav to work with tbird.  Not sure about evolution email - haven't used that in some time personally.  Cheers.

---

### Post by handydan918 on 2008-12-19
> **cdtech said:**
> By using the repositories to install packages, md5 checksums and using root privileges only when necessary are just a few ways to to guard against an intrusion or a system wide infection. SSH is often the first point of entry to a Linux machine, so using strong passwords could guard against an SSH intrusion. Antiviral software should **ALWAYS** be common practice for any OS and could potentially limit the risk of a system catastrophe.
Silly. First, only the SSH client is installed by default, on Ubu and most other distros. You are not going to exploit SSH if the server isn't installed. 
Second,  > Antiviral software should **ALWAYS** be common practice for any OSis double-silly. If there are NO KNOWN viruses in the wild, why waste time, money and system resources on "anti-virus" programs of dubious value?> 
There is a method to infect a system wide Linux OS without the need to become root, it's known as “Privilege escalation” --
What this wiki reference describes is the concept of escalating user privileges to root  in an unauthorized fashion, not some magick invocation that renders impotent all the decades of Unix permissions experience that goes into a Linux distro. IOW, it is not a de facto ecploit, it's a genereal description of a class of exploits that may or may not even exist in the real world. To try to scare noobs into using AV unnecessarily is just --- dare I say it again?--- 
Silly!

:lolflag:

---

### Post by prabhakaran1989 on 2008-12-19
[https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus")

just see this link where they discussed y we need a antivirus software for UBUNTU r anyother linux versions:KS

---

### Post by samden on 2008-12-19
Just to be clearer how to install software:

Go to the Applications menu.

Select "Add/Remove".

Pick what you want.

That was far, far simpler than under Windows, wasn't it!

---

### Post by cdtech on 2008-12-19
> **handydan918 said:**
> Silly. First, only the SSH client is installed by default, on Ubu and most other distros. You are not going to exploit SSH if the server isn't installed. 

For basic users such as yourself this may be the case but for some of us advanced users that require an SSH server this is the most vulnerable access point to a GNU/Linux OS.
> Second,  is double-silly. If there are NO KNOWN viruses in the wild, why waste time, money and system resources on "anti-virus" programs of dubious value?

I suppose you have first hand knowledge of the known viruses in the wild? As far as wasted time, money and system resources on an "anti-virus" program, most companies agree this to be top priority.
> What this wiki reference describes is the concept of escalating user privileges to root  in an unauthorized fashion, not some magick invocation that renders impotent all the decades of Unix permissions experience that goes into a Linux distro. IOW, it is not a de facto ecploit, it's a genereal description of a class of exploits that may or may not even exist in the real world. To try to scare noobs into using AV unnecessarily is just --- dare I say it again?--- 
Silly!


This just proves the possibilities to escalate user privileges, right?

All of your replies are totally silly and only try to rule out the possibilities of an attack. If you, as an administrator, told me that there is no need for protection against an intrusion, or even protection against viruses (that don't exist), you would not be working for me.

---

### Post by vikramaditya on 2008-12-19
I _do_ run the iptables firewall with firestarter frontend, but it's almost anticlimactic as so few "events" get logged. :)

---

### Post by jerome1232 on 2008-12-19
> **vikramaditya said:**
> I _do_ run the iptables firewall with firestarter frontend, but it's almost anticlimactic as so few "events" get logged. :)

Turn on an active ssh server, and watch your /var/log/auth log after a week or so of having it up, you'll get enough hits to make your eyes water.


I think it's kind of a "duh" that ssh get's attacked, ssh allows remote control of a computer there and is almost certain to be running on a Linux server. Fortunatly it's a very secure protocol and exploits are few and far between, and patched very quickly when found. Not to mention that has nothing to do with anti-virus.... intrusion detection systems, good administration, and configuration yes.

My argument against anti-virus isn't that there's no viruses for linux.
It's that here when exploits are found they are patched quickly. If a virus (or malware) has it's route of infection patched it does nothing.

So if this anti-virus program can only detect known viruses that I'm already patched against what is the point?

Now I haven't done extensive research or anything but I'm pretty sure there's no viruses any linux virus scanner can detect that can still infect a patched and up to date system.

---

### Post by bapoumba on 2008-12-20
Moved to Recurring.

---

### Post by Prasius on 2008-12-20
As a newb to Linux of only a few months, but with computer experience dating back to BBC Acorns*, this old favourite topic (also popular with Apple users, Firefox users, Opera users and a whole bundle of other system essential software thats, frankly, niche in the scale of things that have giant MICROSOFT labels over them)makes me laugh in a slightly uncomfortable way.  

Do we think that Linux (OSX,Firefox,Opera,etc) have very few/no viruses/trojans/malware/adware that they're vunerable to because they're super-duper-fantastic?  Or is it that the fact is that the majority of home computer users use Internet Explorer and Windows, and because the huge majority of these "viruses" are designed to make money in one way or another, it makes far more financial sense to hit the 90% of users than the 10%?  Why are more vulnerabilities identified in Windows and IE than in other software?  Lazy coding might have something to do with it.. but the fact there is at least 20 times the user base against these other "invulnerable" programs must make bug hunting a little easier too.

You don't go fishing in an empty lake.

You might find that the rapid growth in the netbook sector that is bringing many new people to Linux (myself included), might also eventually make you all wish we had a virus checker after all (although admittedly its kinda hard to check for something that doesn't exist, but people should always be encouraged to be weary and carry out safe browsing and downloading.)


(..the Brits will understand the joys of Chucky Egg when you're 7 years old!)

---

### Post by SunnyRabbiera on 2008-12-20
> **Prasius said:**
> As a newb to Linux of only a few months, but with computer experience dating back to BBC Acorns*, this old favourite topic (also popular with Apple users, Firefox users, Opera users and a whole bundle of other system essential software thats, frankly, niche in the scale of things that have giant MICROSOFT labels over them)makes me laugh in a slightly uncomfortable way.  

Do we think that Linux (OSX,Firefox,Opera,etc) have very few/no viruses/trojans/malware/adware that they're vunerable to because they're super-duper-fantastic?  Or is it that the fact is that the majority of home computer users use Internet Explorer and Windows, and because the huge majority of these "viruses" are designed to make money in one way or another, it makes far more financial sense to hit the 90% of users than the 10%?  Why are more vulnerabilities identified in Windows and IE than in other software?  Lazy coding might have something to do with it.. but the fact there is at least 20 times the user base against these other "invulnerable" programs must make bug hunting a little easier too.

You don't go fishing in an empty lake.

You might find that the rapid growth in the netbook sector that is bringing many new people to Linux (myself included), might also eventually make you all wish we had a virus checker after all (although admittedly its kinda hard to check for something that doesn't exist, but people should always be encouraged to be weary and carry out safe browsing and downloading.)


(..the Brits will understand the joys of Chucky Egg when you're 7 years old!)

Well no matter how popular linux becomes I still dont think many will exploit it as those who exploit windows often use linux because if its great diversity.
As long as linux remains open source I dont think as many people would take advantage of it, most hackers and crackers hack MS because it is MS.

---

### Post by jrusso2 on 2008-12-20
> **cdtech said:**
> For basic users such as yourself this may be the case but for some of us advanced users that require an SSH server this is the most vulnerable access point to a GNU/Linux OS.

I suppose you have first hand knowledge of the known viruses in the wild? As far as wasted time, money and system resources on an "anti-virus" program, most companies agree this to be top priority.


This just proves the possibilities to escalate user privileges, right?

All of your replies are totally silly and only try to rule out the possibilities of an attack. If you, as an administrator, told me that there is no need for protection against an intrusion, or even protection against viruses (that don't exist), you would not be working for me.

What good is it to run an Anti virus to protect Linux when they only protect against WIndows viri.  If a new Virus was to come out that could infect Linux your avast and clamav would be worthless for protection.

---

### Post by edd07 on 2008-12-20
> **jrusso2 said:**
> What good is it to run an Anti virus to protect Linux when they only protect against WIndows viri.  If a new Virus was to come out that could infect Linux your avast and clamav would be worthless for protection.
Agreed. You'd only need them if you forward e-mail or other files to Windows machines very often. But that's only for being kind to those Windows machines, yours won't get infected.

BTW, the plural for "virus" is "viruses". "Viri" (Actually it should be "virii") is plural for "man".

---

### Post by ranch hand on 2008-12-22
Virus protection is just part of security.  Most viruses are transmitted by email and ISPs filter very well for that.  All others require the active participation of the user in clicking on something stuped.

I am the biggest threat to the security of my box.

The security issue will become more important over time in linux.  It is true that the system of permissions is tough to crack but not impossible.  If you are file sharing it is a good idea to password protect your recovery mode log in.  This is the only real hole in Ubuntu and easy to fix with Start up Manager, available at your local Synaptic.

---

