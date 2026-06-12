---
title: "[SOLVED] Linux security"
date: 2008-02-22
forum: Recurring Discussions
---

### Post by Rytron on 2008-02-22
Hi,
I am new to Linux. I really want to get into it.
Recently I installed these distros on various machines(ubuntu,xubuntu,pclinuxos 2007,kubuntu).
What I find to be strange after so many years using Xp Pro is this:

does linux need firewall
does linux need antispyware
does linux need anti virus software

I know that the security of Linux is renowned for being superior to Windows but are the above applications required?

I read somewhere that a firewall is only required if you run a Linux mail server-is this true?

Are all Linux distros in general extremely secure thus not requiring firewall / antimalware software?

I'd be delighted on some input to my question. Thank you.

---

### Post by JimBuntu on 2008-02-22
BUMP. 

There is a Linux Firewall called Firestarter that seems to be well liked. I do have it installed and running, but do I need it?

---

### Post by Crafty Kisses on 2008-02-22
You don't need Firewalls, Ubuntu has someting called **"iptables"**

---

### Post by PeterJS on 2008-02-22
Here's the cliff notes:
-Smaller user baser == smaller target == less incentive for attack
-Real separation of the idea of admin and user, even as an admin you have to explicitly request admin rights when you want them
-File permissions, by default files can not be executed, so even if you do get a nasty file on your system some how, you have to explicitly allow it to run
-Currently there are 0 know viruses in the wild, the last major security flaw in the OS was patched in under 48 hours, and there have only been a couple hundred viruses ever as compared to a couple hundred of thousands for windows
-Linux by extension of it's Unix heritage, is more hardened simply because it assumes hostile intentions of users towards one and other, and the system. It's built to be secure in a hostile environment, rather than having security as a bolted on after thought
-No need for passive scanning tools as their is nothing to scan for.

And a more expanded guide:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HermanAB on 2008-02-23
Common fallacy:
"-Smaller user baser == smaller target == less incentive for attack"

There are about 1 billion more Linux machines out there than Windows machines.  So if your statement was true, then Linux should be crawling with viruses and malware and Windows should be working perfectly.

The difference is in the design.

You don't believe me?  Go to Linuxdevices.com.  You'll quickly find information that there are about 300 million Linux devices sold each year.  Linux is the most popular OS ever.

---

### Post by m4mb4 24 on 2008-02-23
bump...I noticed a pop up something trying to clean my computer...do i need to worry about it..i stopped it...thinking it was spyware

---

### Post by tubezninja on 2008-02-23
Did the popup appear while you were browsing a web page?  If so, it might've been an ad.

---

### Post by m4mb4 24 on 2008-02-23
Yeah i ignored it

---

### Post by euler_fan on 2008-02-23
What you'll find most saying is that unless you run a server, there's not much need for any of those products, especially if you use a desktop behind a router with a built-in firewall which is properly configured.

Firestarter will let you easily configure your firewall on your box. It's not as powerful as something like Firewall Builder, but great for the home user. You may investigate a restrictive outbound policy with white listed services.

As for spyware/AV ClamAV is fine if you feel like being bothered. RKhunter and chkrootkit are the same way. I'm having some problems with OSSEC-HIDS right now or I'd suggest that too. Samhain looks interesting, however, as does AIDE and a few other products for more advanced users.

There is also a great thread stickied at the top of this forum.

---

### Post by ChaosParser on 2008-02-24
> **HermanAB said:**
> Common fallacy:
"-Smaller user baser == smaller target == less incentive for attack"

There are about 1 billion more Linux machines out there than Windows machines.  So if your statement was true, then Linux should be crawling with viruses and malware and Windows should be working perfectly.

The difference is in the design.

You don't believe me?  Go to Linuxdevices.com.  You'll quickly find information that there are about 300 million Linux devices sold each year.  Linux is the most popular OS ever.

More like.. 

Smaller HOME user base = smaller targert = less incentive for script kiddies

---

### Post by bodhi.zazen on 2008-02-25
> **m4mb4 24 said:**
> bump...I noticed a pop up something trying to clean my computer...do i need to worry about it..i stopped it...thinking it was spyware

You need to secure your browser :

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

