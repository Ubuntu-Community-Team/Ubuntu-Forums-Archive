---
title: "Should there be Virus Scanning in Linux?"
date: 2009-09-07
forum: Recurring Discussions
---

### Post by chessnerd on 2009-09-07
Many people in the Linux world claim that there are no Linux viruses in the wild and, therefore, you never need to scan your computer for viruses. However, since almost no one ever scans for viruses on Linux how would anyone know they've been infected?

Most Windows viruses aren't the super obvious "You have a virus!" types that crash programs or cause RAM usage to go through the roof. They usually are trojans and backdoor bots that are hard to notice without running a regular virus/malware scan. Therefore, if there was a Linux virus in the wild, it would make sense that it would act the same way: It wouldn't cause terminal windows to spontaneously open or make the mouse jump randomly on the screen, it would just sit as a background process and most users wouldn't be able to tell.

Yes, I know that the file system of Linux is incredibly immune to viruses compared to Windows, but sometimes people make a careless download or two and the home folder doesn't require sudo privileges to get at. If a user stored important information in their home folder it could be copied by a virus and uploaded to the Internet.

While this is all hypothetical it does raise a question in my mind: Should Linux users scan their computers for viruses? Not daily or weekly like Windows scanners, but maybe a monthly scan just to make sure that they haven't been infected.

What do you think?

EDIT: By "virus" I mean "malware" or "malicious software" not just viruses in particular...

---

### Post by Whiffle on 2009-09-07
Thing is, if nobody knows what these viruses are, then how does the scanner know what to look for?  I'd say that whatever virus scanner we might use now, against whatever viruses might be out there for linux, will be useless against any virus that does manage to get into a Linux system.

---

### Post by madjr on 2009-09-07
yea a scanner for windows partition, but that already exists is called Clam

---

### Post by lisati on 2009-09-07
It's up to the user. I wouldn't want to have to take on an ISP or email provider to reactivate an account when they reckon I've violated their terms and conditions by propogating malware.

---

### Post by chessnerd on 2009-09-07
> **Whiffle said:**
> Thing is, if nobody knows what these viruses are, then how does the scanner know what to look for?  I'd say that whatever virus scanner we might use now, against whatever viruses might be out there for linux, will be useless against any virus that does manage to get into a Linux system.

Good point... 
What about a heuristics scan? I know those aren't as reliable as a definitions scan, but that would probably be the only way to check for it.

---

### Post by NormanFLinux on 2009-09-07
Its not needed. I have never had to install AV in either Linux or Mac OSX.

---

### Post by MikeTheC on 2009-09-07
> **madjr said:**
> yea a scanner for windows partition, but that already exists is called Clam

I believe you misunderstood (or failed to read) the OP's post.

---

### Post by Whiffle on 2009-09-07
> **chessnerd said:**
> Good point... 
What about a heuristics scan? I know those aren't as reliable as a definitions scan, but that would probably be the only way to check for it.

Maybe maybe not. I don't know much about that kind of thing, but I have no idea how I would write a program to find viruses that don't exist yet, especially without tons of false indicators.

---

### Post by gn2 on 2009-09-07
> **chessnerd said:**
> ~ maybe a monthly scan just to make sure that they haven't been infected.

What do you think?


Whatever floats your boat.
Not for me until such time as there are Linux viruses in the wild.
That'll be the day after a squadron of pigs fly past your window, so keep watching the sky......

---

### Post by chessnerd on 2009-09-07
> **Whiffle said:**
> Maybe maybe not. I don't know much about that kind of thing, but I have no idea how I would write a program to find viruses that don't exist yet, especially without tons of false indicators.

The false positives are the main flaw in heuristics scanning. Some programs (Malwarebytes for instance) use a weak heuristics scan in addition to their definitions scan and those work okay. A powerful heuristics scan, however, often is wrong more than it is right.

A Linux heuristics scan would only be useful if the person doing the scanning could, after an alleged virus was found, distinguish it from a program that was supposed to be there, which is something that even I might have a hard time doing...

---

### Post by cariboo on 2009-09-07
Ubuntu's security model only allows you to install programs to your home directory. For malware to do it's job properly, it has to be installed by root, and the only way that's going to happens is by social engineering.

As far as I know, clamav is the only virus scanner that claims to scan for Linux malware.

---

### Post by Warpnow on 2009-09-07
...Do you not realize a decent portion of linux users know exactly what processes are running at all times and what they do, and they monitor their processes?

Ubuntu has far too many going, especially with all my current crap, but when I was running on my old pentium 2, I had to conserve resources. I was running a very light system, and new exactly what processes were running, and I knew what they did...mostly through trial and error of the kill command (hehe) and man pages...

---

### Post by Georgesl on 2009-09-07
Considering that one of the main reasons I'm running ubuntu is to avoid wasting a significant portion of my resources (both machine and $) on anti-virus software.

If someone comes up with a viable Linux virus it won't be long until some script-kiddie makes a painfully obvious "look at what I can do!" version.  There is little worry about more subtle versions going undetected for long.

---

### Post by misfitpierce on 2009-09-07
It can be seen by server admins running linux, if they had a virus they would have a process running using excessive CPU that was not supposed to be running. A destructive app would be trying to mess with root files and would also need super user privleges so it would be seen and published all over the net... No virus scanning should not be included inside linux but it is avail in the repos aka App Center for download to make sure if computing with windows networks on your network to make sure a file you download does not have a windows virus attached so you don't send to windows computer by mistake. I think it is fine as is.

---

### Post by lisati on 2009-09-07
I'm more worried about accidentally passing on malware to the Windows portions of my network and/or doing something stupid myself than malware being in with a serious chance of hurting the Ubuntu portions of my machines.

---

### Post by samjh on 2009-09-07
Viruses are inevitable as Linux gains popularity.  Right now, Linux is not really a worthy prey for virus or malware writers.  Windows has the big bounty on its head, and had it for a very long time.

When I was at university, the internal CS/IT/SE mailing lists used to feature very long and toxic debates about the pros and cons of Windows and Linux systems, including security.  The general opinion of those with expert knowledge seems to be that neither are more or less vulnerable than the other, if the systems are properly administered.

The problem with Windows is that you've got a much larger portion of users who know nothing about security or system administration, and generally don't give such issues much consideration.  That goes for both home computer users as well as small business server operators.  And that means, unfortunately, Windows systems are often more vulnerable than they should be.

Just because we have an apparent security edge now, doesn't mean that it will be everlasting.  Be vigilant.

---

### Post by gn2 on 2009-09-07
> **samjh said:**
> Viruses are inevitable as Linux gains popularity. ~

Sorry, but this is simply incorrect.
Windows doesn't have viruses because it's popular, it has them because of poor design.
Linux doesn't have them because of good design.
Increasing the popularity of desktop Linux won't affect the design.

---

### Post by aysiu on 2009-09-07
> **samjh said:**
> Viruses are inevitable as Linux gains popularity.  Right now, Linux is not really a worthy prey for virus or malware writers.  Windows has the big bounty on its head, and had it for a very long time. So the Linux servers Google and the NSA use aren't worthy enough targets?

---

### Post by speedwell68 on 2009-09-07
I do run periodic virus scans on my Ubuntu PCs as I do not want to inadvertantly pass a virus or any other form of malicious software to anyone I know that uses Windows, namely my employer.  I run Avast Free Edition and from time to time there has been the odd thing in my email, normally in the Junk folder.  Whilst we ourselves are more or less immune to malicious software it still pays to operate a good house-keeping policy.

---

### Post by Vaeil on 2009-09-07
> **aysiu said:**
> So the Linux servers Google and the NSA use aren't worthy enough targets?

Yes, but they are harder targets.

The argument of 'less linux users' is viable to a degree. Mainly because a lot of virusses require a PEBKAC (stupid user), which isn't all that common in Linux as in Windows.

---

### Post by aysiu on 2009-09-07
> **Vaeil said:**
> Yes, but they are harder targets.

The argument of 'less linux users' is viable to a degree. Mainly because a lot of virusses require a PEBKAC (stupid user), which isn't all that common in Linux as in Windows.
That's a trojan, then, not a virus.

A trojan can work on any operating system. It's not the operating system, then, that's insecure--it's the user.

---

### Post by speedwell68 on 2009-09-07
> **aysiu said:**
> That's a trojan, then, not a virus.

A trojan can work on any operating system. It's not the operating system, then, that's insecure--it's the user.

The user is always the weakest link.

[img]http://blogs.coventrytelegraph.net/passtheremote/annerob.jpg[/img]

---

### Post by juancarlospaco on 2009-09-07
AntiVirus are a poor bad security system it only work with well know malware,
Linux Kernel got proactive strong security built-in in itself.

---

### Post by samjh on 2009-09-07
[quote=gn2]Windows doesn't have viruses because it's popular, it has them because of poor design.
Linux doesn't have them because of good design.[/quote]Please explain why the system security model of the current Windows Server 2008, Vista, and 7, make them more vulnerable to viruses than Linux if properly administered?

While it's good to use and support Linux, let's not get down to the level of Microsoft at spreading FUD, especially old FUD like Windows security.

Virus vulnerability on Windows has less to do with system security and more to do with user complacency and improper system administration.

---

### Post by juancarlospaco on 2009-09-07
> **samjh said:**
> Please explain why the system security model of the current Windows Server 2008, Vista, and 7, make them more vulnerable to viruses than Linux

[LIST]
[*]Confiker
[*]ActiveX
[*]RDP Vulneravility never fixed
[/LIST]
*Random examples...*

---

### Post by Regenweald on 2009-09-07
Yes, i think there should be. just so this particular thread topic will not appear ever again.

---

### Post by lykwydchykyn on 2009-09-07
Every time this topic comes up, the discussion revolves hopelessly around the same basic semantic problem.

 - Person asking the question equates "virus" with "security problem"
 - Person answers saying "virus" (the specific type of malware) isn't an issue with Linux
 - Person asking assumes then that "security problems" are not an issue with Linux, when in fact it's only "viruses" in particular that aren't.

I'd bet the single biggest security threat to most Linux users these days is to have your SSH service brute-force hacked and have a rootkit dropped on your machine.  And, surprise surprise, we have software in spades to help mitigate both of those threats.

Common sense tells us to secure against existing threats.

I have spent time, effort, and money to secure and/or insure my home against a number of threats, including fire, flood, pests, burglars, and falling tree limbs.  I have not done anything to protect my house from Viking hordes, alien invasion, or zombies.  Is my house insecure?

---

### Post by Regenweald on 2009-09-08
> **lykwydchykyn said:**
> Every time this topic comes up, the discussion revolves hopelessly around the same basic semantic problem.

 - Person asking the question equates "virus" with "security problem"
 - Person answers saying "virus" (the specific type of malware) isn't an issue with Linux
 - Person asking assumes then that "security problems" are not an issue with Linux, when in fact it's only "viruses" in particular that aren't.

I'd bet the single biggest security threat to most Linux users these days is to have your SSH service brute-force hacked and have a rootkit dropped on your machine.  And, surprise surprise, we have software in spades to help mitigate both of those threats.

Common sense tells us to secure against existing threats.

I have spent time, effort, and money to secure and/or insure my home against a number of threats, including fire, flood, pests, burglars, and falling tree limbs.  I have not done anything to protect my house from Viking hordes, alien invasion, or zombies.  Is my house insecure?

Don't be daft man! what about ninjas! you did not mention ninjas! devil in the details....

---

### Post by chessnerd on 2009-09-08
> **lykwydchykyn said:**
> Every time this topic comes up, the discussion revolves hopelessly around the same basic semantic problem.

 - Person asking the question equates "virus" with "security problem"

No, not really. A security problem and malicious software aren't the same thing. A security problem is a flaw in the code of a program. Malicious software is software created to infiltrate someone's computer without their knowledge/permission. Malicious software may USE a security problem to do its job, but they are not the same thing. What I was doing was mistakenly equating "virus" with malware, I will admit this (and I'll correct it), but it feels like the whole "who" vs. "whom" thing to me. There's innocently correcting people's grammar and being a Grammar Nazi... 
In my defense, though, the malware page on Wikipedia does point out that: 
> The term "computer virus" is sometimes used as a catch-all phrase to include all types of malware, including true viruses.

> **lykwydchykyn said:**
>  - Person answers saying "virus" (the specific type of malware) isn't an issue with Linux
You're right about this one.

> **lykwydchykyn said:**
>  - Person asking assumes then that "security problems" are not an issue with Linux, when in fact it's only "viruses" in particular that aren't.
I know that security problems can be an issue with Linux, otherwise I wouldn't have gotten an update a few days ago that said "Security Update."

---

### Post by Regenweald on 2009-09-08
> **chessnerd said:**
> No, not really. A security problem and malicious software aren't the same thing. A security problem is a flaw in the code of a program. Malicious software is software created to infiltrate someone's computer without their knowledge/permission. Malicious software may USE a security problem to do its job, but they are not the same thing. What I was doing was mistakenly equating "virus" with malware, I will admit this (and I'll correct it), but it feels like the whole "who" vs. "whom" thing to me. There's innocently correcting people's grammar and being a Grammar Nazi... 
In my defense, though, the malware page on Wikipedia does point out that: 



You're right about this one.


I know that security problems can be an issue with Linux, otherwise I wouldn't have gotten an update a few days ago that said "Security Update."

Cool thing about our security updates though is that they are mostly if not all, proof of concept. You seem spot on with everything else....

---

### Post by lisati on 2009-09-08
> **Regenweald said:**
> Don't be daft man! what about ninjas! you did not mention ninjas! devil in the details....

What about the squirrels? Are we through with them yet? But we digress......

---

### Post by samjh on 2009-09-08
> **juancarlospaco said:**
> [LIST]
[*]Confiker
[*]ActiveX
[*]RDP Vulneravility never fixed
[/LIST]
*Random examples...*

Bad examples.

The vulnerability used by Conficker has been patched (MS08-67), and the worm itself can be stopped by making appropriate changes to access permissions and groups.  If anything, it actually shows the security model working, not failing.

ActiveX and RDP are not system security issues.  We don't blame Java plugins and RFB for Linux system vulnerabilities, so neither should we blame ActiveX and RDP for Windows system vulnerabilities.

While it's easy to just pick some random examples of security issues with Windows, be mindful of the embarrassments suffered by the Linux community.  Differences in the magnitude of vulnerability between Windows and Linux (and Mac, and Solaris, just to throw in some more) is now more a matter of proper administration and user vigilance, than underlying technical design.

---

### Post by gn2 on 2009-09-08
As predicted, thread moves away from discussion of *viruses*. :rolleyes:

---

### Post by sydbat on 2009-09-08
> **samjh said:**
> Bad examples.

The vulnerability used by Conficker has been patched (MS08-67), and the worm itself can be stopped by making appropriate changes to access permissions and groups.  If anything, it actually shows the security model working, not failing.

ActiveX and RDP are not system security issues.  We don't blame Java plugins and RFB for Linux system vulnerabilities, so neither should we blame ActiveX and RDP for Windows system vulnerabilities.

While it's easy to just pick some random examples of security issues with Windows, be mindful of the embarrassments suffered by the Linux community.  Differences in the magnitude of vulnerability between Windows and Linux (and Mac, and Solaris, just to throw in some more) is now more a matter of proper administration and user vigilance, than underlying technical design.Actually, I think you may have missed the point juancarlospaco was getting at (unless I misunderstood too)...those "vulnerabilities" mentioned all have to do with poor implementation of the default Windows system that virtually everyone uses (unless they are a sys admin, then your argument holds up nicely), which is...the default user IS the administrator (root). Because of this, any and all malware has free reign with the system. 

This is fundamentally different than a Unix or Linux system because, by default, the 'user' is not root. To get most malware to even run on a *nix system, you have to give it permission by becoming root via su/do.

---

### Post by lykwydchykyn on 2009-09-08
> **chessnerd said:**
>  There's innocently correcting people's grammar and being a Grammar Nazi... 

I'm not being a Grammar Nazi (godwin.invoke()), the point is not to criticize your use of colloquialism.  Even if you knew what you meant, other people get involved who respond with the misunderstanding I highlighted.

The point is that there's almost always a fundamental misunderstanding that happens in these threads that revolves around someone using "virus" colloquially, someone interpreting it literally, and subsequent respondents (either the OP or others) mixing literal and colloquial understandings of the word.

The basic points are:
 - We do have security issues to deal with on Linux
 - We do have software and practices in place to mitigate those threats
 - "Viruses" are not high on the list of threats
 - We therefore don't commonly use "anti-virus" (i.e. -- "scan system for known baddies") as such.

I don't care if people use words colloquially, but it will generate misunderstandings. If you read enough of these threads you'll see the same misunderstandings over and over again.  Just thought I'd attempt to head it off at the pass.

---

### Post by juancarlospaco on 2009-09-09
> **samjh said:**
> 
ActiveX and RDP are not system security issues.  We don't blame Java plugins and RFB for Linux system vulnerabilities,

While it's easy to just pick some random examples of security issues with Windows, be mindful of the embarrassments suffered by the Linux community.  Differences in the magnitude of vulnerability between Windows and Linux (and Mac, and Solaris, just to throw in some more) is now more a matter of proper administration and user vigilance, than underlying technical design.

Bad examples.

Because on Windows you don't have something like** AppArmor **or **SELinux**.
You can configure your selinux and even Kernel vulnerability or gained root can damage it.



More random examples:

[LIST]
[*]**RPC vulnerability, you simply can't set a login attempt limit.**
[*]**Memory Managment model, an specially crafted program can dump others.**
[*]**Pagefile vulnerability, is not cleaned on shutdown.**
[/LIST]

:)

---

