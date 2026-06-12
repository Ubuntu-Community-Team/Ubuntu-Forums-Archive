---
title: "Linux Viruses?"
date: 2009-04-13
forum: Recurring Discussions
---

### Post by octobermagic on 2009-04-13
I recently made the switch from MS Vista to Ubuntu.  So far everything has been great and im loving my new OS.  But I was wondering how is it that there are now viruses or key loggers for linux based OS?  Is it that no one writes viruses for these OS?  And if not what would stop someone from making a virus that is targeted to linux based OS's.  
I really only asking this because I kind of feel naked without a virus scanner running on the bottom of my taskbar like I used to do with Microsoft products.

---

### Post by hwttdz on 2009-04-13
It's not an impossibility.  Read the wiki article for some background [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware) .  Because of design, linux is less prone to catastrophic wipeout from viruses, you have to give up the root password to the virus in order to be vulnerable.  However, if someone mails you an infected word document per se, you can pass the virus along to your windows comrades by sending it along.  For this reason some people run a virus scanner for windows viruses.  Anyways it's a commonly discussed question, you'll be able to find out lots about it.  In the end don't give up your root pass, and know what any commands you type at the terminal do.

---

### Post by lisati on 2009-04-13
Have a look here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

By the way, "[malware]("http://en.wikipedia.org/wiki/Malwa")" is often a better word to use than "virus" (which refers to only one kind of nasty beast)

---

### Post by memories on 2009-04-13
People can write malware for Linux easily. In fact, you should never run any script you get off this forum or anywhere else without actually looking at the code, and never run binary's (executable files which you cannot see the source of). 

Although in 99% of the cases above, you're safe. You're more likely to wipe out your entire HD by accident than you are to get a "virus" :P

Linux users are generally more competent, the market share is minimal, and the way the OS is designed - you aren't running as root, so a virus would only be able to toy with your own user account and home files unless you run it sudo - make it unprofitable or just undesirable to target. 

Most WindowzZz malware is actually for-profit, no matter how deceiving and evil it feels. It's backed up by A LOT of money. We're talking 15 year olds being able to make $10k a day by altering a user's cookies to add their own affiliate links and getting the user's machine to sign up under their own affiliate offers for money, etc ... 

It's also **very cool** (like smoking) to see your name go up on the anti-virus sites and databases.

edit: something like Adobe AIR is potentially insecure as well. I don't trust anything not on the repositories unless it has some merit for being reputable. There's a paper on Adobe AIR's security if you're interested.

---

### Post by tommynz1975 on 2009-04-13
like windows, some people are their own worst enemy. running scripts from an un trusted source could contain nasties. 

Welcome to the world of Ubuntu.

---

### Post by antikristian on 2009-04-13
Just don't use a simple password and run an openssh server, I've seen an old unpatched linux server beeing hacked by someone using brute force password guessing and using voulnerablilities to get a root shell once they were in.

I guess their plan was to install a rootkit once they were inside, but they screwed it up by using binarys built for the wrong architecture, which in turn screwed up the server.

Linux computers are attractive to hackers since they often are emailservers, and make great candidates for spam servers. There's also a possibility that they contain email addresses and crunchy secrets.

---

### Post by hwttdz on 2009-04-13
Yeah, I think I've done "rm *" a few times over the last 5 years or so.  Of course for me usually it's accomplished by making a typo in some sort of a command that should do something useful, like remove all crash dump files older than a week old.

---

### Post by octobermagic on 2009-04-13
O OK I see.  I kind of had the feeling that might have been the case.  Just wanted to be sure, new OS and all, it's a whole new world.  Windows is pretty much what I only knew.  Definitely going to read up on those links you guys posted.  TY.

---

### Post by cmay on 2009-04-13
problem today is that you can get a fake virus warning such as the one i posted a screenshot of. i know this is a scam but i also know lots of people running a windows machine which this is targeted at would maybe fall for it. that loophole in any system will never be patched. but linux being not so popular as windows has in my honest opinion nothing to do wiht the fact that linux has virually no known virus and windows has. however rootkits and keyloggers exist for linux.

 but we are pretty secure if only we follow the golden rule that if it is not included in synaptic and can be fetched trough the terminal via apt-get then it could be a security risc. and this is just how it is. stick wiht using only software from apt-get and your safe. 

there is so many packages in the respotories that no one really should need anyting else than this. if you are just a casual computer user. some people do add other things to their souces list than what the distribution official support and i recommend not to do that unless you know exactly what you are doing and trust the unofficial sources. 

there is lots of information on this subject in the forums that you can search on.

---

### Post by octobermagic on 2009-04-13
So pretty much anything in Synaptic and anything in terminal that I can get with "sudo apt-get" is safe?

---

### Post by hwttdz on 2009-04-13
By default anything you can get through synaptic is safe.  Synaptic looks in a file to find its repositories though, so if you edit this file then install something from one of the added repositories you are not as assured.  If you trust the repository then all is well though.

---

### Post by lisati on 2009-04-13
> **octobermagic said:**
> So pretty much anything in Synaptic and anything in terminal that I can get with "sudo apt-get" is safe?

Pretty much: and the Add/Remove software menu even gives you a choice of whether you trust a source or not

---

### Post by SunnyRabbiera on 2009-04-13
> **octobermagic said:**
> So pretty much anything in Synaptic and anything in terminal that I can get with "sudo apt-get" is safe?

Pretty much, and some extra sources such as getdeb and medibuntu are also trustworthy...
The launchpad PPA repos are also safe too

---

### Post by mb_webguy on 2009-04-13
It would probably be a good idea to read the links on security in my signature.

Basically, Linux is a very secure OS as long as you use a little bit of common sense, and that security has very little to do with the greater popularity of Windows making it a bigger target for malware developers.  As long as you only install software from trusted sources (including the official Ubuntu repositories, the Medibuntu repository, and the repositories maintained by large software projects) you're extremely safe.  Open-source software in general tends to be safer than proprietary software, since anyone can look at the code to see exactly what it does.

---

### Post by 0per4t0r on 2009-04-14
Linux is not completely invulnerable, AV is not necessary, but it is recommended.

---

