---
title: "Linux Virus: A False Sense Of Security"
date: 2008-12-02
forum: Recurring Discussions
---

### Post by halovivek on 2008-12-02
Linux Virus: A False Sense Of Security
i read this in this [link]("http://www.linuxhaxor.net/2008/11/26/linux-virus-a-false-sense-of-security/")

Need more information on this...):P

---

### Post by Skripka on 2008-12-02
> **halovivek said:**
> Linux Virus: A False Sense Of Security
i read this in this [link]("http://www.linuxhaxor.net/2008/11/26/linux-virus-a-false-sense-of-security/")

Need more information on this...):P



***_"Why GNU/Linux Viruses are fairly uncommon" from Charlie Harvey_***
evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1)

---

### Post by bashveank on 2008-12-02
Or just run the .bin

---

### Post by Sealbhach on 2008-12-02
What about a .deb that looks harmless and adds itself to startup sessions?


.

---

### Post by Dragonbite on 2008-12-02
Where does AppArmor and SELinux fall?

---

### Post by Skripka on 2008-12-02
> **Sealbhach said:**
> What about a .deb that looks harmless and adds itself to startup sessions?


.

The weakest link in computer security, usually, ends up being the user.

---

### Post by Sub101 on 2008-12-02
There is a similar situation arising with mac:
[http://news.bbc.co.uk/1/hi/technology/7760344.stm]("http://news.bbc.co.uk/1/hi/technology/7760344.stm")

---

### Post by sydbat on 2008-12-02
> **Sub101 said:**
> There is a similar situation arising with mac:
[http://news.bbc.co.uk/1/hi/technology/7760344.stm]("http://news.bbc.co.uk/1/hi/technology/7760344.stm")Not sure how...seeing as it is a Unix OS...unless Apple set it up similar to the way Windows is, with everything root/admin...

---

### Post by bodhi.zazen on 2008-12-02
> **halovivek said:**
> Linux Virus: A False Sense Of Security
i read this in this [link]("http://www.linuxhaxor.net/2008/11/26/linux-virus-a-false-sense-of-security/")

Need more information on this...):P

As you might imagine this is a recurring issue. I have tow thoughts on this issue.

First, Linux is not windows. As such security is different and neither worms or viruses are major issues (on Linux) at this time. Viruses and worms take advantage of holes in the code and while there have been viruses and worms written, the open source community has long since patched the code and the known viruses will not run on an up to date system. This is not the case in Windows where know holes remain unpatched for dare I say decades ?

The solution to viruses on Linux is to keep your system up to date, including security patches / updates. The solution on Windows is to run antiviurs. Different OS, different solutions.

Now it may be that in the future Linux users may need to run antivirus software, that is a matter of speculation.

Second, yes I agree Linux users take security for granted. I suggest you read the stickies on this forum, both security and intrusion detection.

---

### Post by Kinstonian on 2008-12-02
After skimming over the article I agree with it.  Contrary to popular belief, there is nothing special about Linux that prevents it from being a target of malware.  In fact Windows Vista has many more built in security measures than Linux such as [Windows Resource Protection](http://en.wikipedia.org/wiki/Windows_Resource_Protection), [Mandatory Integrity Control](http://en.wikipedia.org/wiki/Mandatory_Integrity_Control), [Services Hardening](http://technet.microsoft.com/en-us/magazine/cc162523.aspx), [Volume Snapshot Service](http://en.wikipedia.org/wiki/Shadow_Copy), [Windows Defender](http://en.wikipedia.org/wiki/Windows_Defender), etc.

**The reason why Linux doesn't have much malware isn't because of the operating system itself, it's because of the environment it's in and the culture that surrounds it.**  For example, Linux accounts for only around 1% of the desktop market compared with around 90% for Windows.  If someone is going to write malware to make money (which is the most common motive now) then they are going to write it to work on Windows.  It's simple economics.

Also, the average Linux user is far more tech savvy than the average Windows user.  Most Linux users aren't going to run mobile code from shady web sites, or run attachments in email, etc.  They are also more likely to get software from trusted sources such as repositories or straight from the software vendors site, and then use cryptography to make sure it hasn't been modified before they install it.

Historically *nix has been known for being stable and secure while not being user friendly.  On the other hand, Windows has been known for being user friendly, but not stable or secure.  However, over time both OS's have improved dramatically on their weaknesses.  Windows Vista is much more stable and secure, where *nix with distributions like Ubuntu are much more user friendly.  The lack of usability has been a huge problem for *nix.  As it improves, I expect it will gain more market share, and at the same time, become more of a target.

---

### Post by HermanAB on 2008-12-02
Security has nothing to do with market share.  There are far more Linux devices online than any other OS, more than 2 billion.  Therefore, if your 'market share' argument held, then Linux has to be the most insecure OS with the most viruses and crapware.

There is a good reason why every Windows machine is installed behind a dinky little Linksys/Netgear Linux firewall box.  One day, when it is the other way around, with Linux desktops installed behind dinky little Windows firewall boxes, *then* you should get worried.

---

### Post by Kinstonian on 2008-12-02
> **HermanAB said:**
> Security has nothing to do with market share.  There are far more Linux devices online than any other OS, more than 2 billion.  Therefore, if your 'market share' argument held, then Linux has to be the most insecure OS with the most viruses and crapware.

There is a good reason why every Windows machine is installed behind a dinky little Linksys/Netgear Linux firewall box.  One day, when it is the other way around, with Linux desktops installed behind dinky little Windows firewall boxes, *then* you should get worried.

And how much functionality do those devices have?  It's not like a full blown **desktop** installation of Windows or Linux, which is what malware authors are focused on, and what I was talking about.

---

### Post by lukjad on 2008-12-02
Subscribing.

---

### Post by Sub101 on 2008-12-02
> **Kinstonian said:**
> And how much functionality do those devices have?  It's not like a full blown **desktop** installation of Windows or Linux, which is what malware authors are focused on, and what I was talking about.

I agree. It is far more visual and threatening to attack a home pc rather than a server etc. Yes it may well effect more people but the personal effect is still greater. There is also the fact that many people do not like Windows and Microsoft and take pleasure in 'embarrassing' these large companies.

---

### Post by lisati on 2008-12-02
I'm no security expert or *nix guru but....

<rant begins>
Much of it boils down to what the malware needs to happen (and in what environment that it'll work best) in order for it to do its mischief.

What kind of mischief? It could be anything from a simple practical joke like popping up a message like "Your computer is stoned", through surreptitiously sending emails or running up a big phone bill, to destroying data on the infected machine.
<end of rant>

---

### Post by www.google.com on 2008-12-02
There are a quite a few linux virii/malware out there. But from what I'm reading there havent been any major panics over a *nix virus since 2005.

---

### Post by johnkzin on 2008-12-03
> **bodhi.zazen said:**
> As you might imagine this is a recurring issue. I have tow thoughts on this issue.

First, Linux is not windows. As such security is different and neither worms or viruses are major issues (on Linux) at this time. 

At this time.  It's not impossible.  The first major worm waas a UNIX worm, not a windows/dos worm.

> Viruses and worms take advantage of holes in the code and while there have been viruses and worms written, the open source community has long since patched the code and the known viruses will not run on an up to date system. This is not the case in Windows where know holes remain unpatched for dare I say decades ?

Whether or not Windows is worse or not is irrelevant.  What's relevant is "can an adversary every find such a hole in Linux faster than the linux white-hats can find it?"  ... the answer is, without question: eventually, yes, they will.


> The solution to viruses on Linux is to keep your system up to date, including security patches / updates.

How will that prevent you from being infected by an Office Macro Virus?


The solution to viruses and worms on ALL platforms is:

1) don't be stupid: close services that shouldn't be open, don't open services you don't need, use things like tcpwrappers or your firewall of choice to keep access restricted, and don't open files you haven't scanned.  Don't leave an open port, for the latest malware, that MIGHT be vulnerable to an exploit you're not yet aware of, unless you absolutely need that port open.

2) keep up to date on patches/updates, both recommended and security.

3) scan your system for malware.  scan files you download against known malware (ClamAV is a good start, along with their 3rd party optional sigs, like SaneSecurity, MBL, and MSBL).  Even malware that might not be native to your platform(s) (because it might be left behind by an adversary that using you as a repository or something, and because you want to be a responsible netizen and be sure your system isn't passing on viruses ... even ones you yourself are immune to).

4) use tripwire, IDS, and similar tools to monitor access and changes to your system, reading your security logs and such. (and be proactive: when you see some idiot probing your SSH port every so often, don't wait for him to get lucky, block him now with your tcpwrapper or firewall config)

5) when it comes to "convenience vs security" always be aware of what you're doing when you choose convenience, and be diligent about the consequences of that decision.


Those 5 rules apply no matter whether you're talking about Linux, Solaris, Mac OS X, AIX, HP/UX, Windows, or any other OS that's still alive out there.

---

### Post by hyper_ch on 2008-12-03
> **Kinstonian said:**
> **The reason why Linux doesn't have much malware isn't because of the operating system itself, it's because of the environment it's in and the culture that surrounds it.**  For example, Linux accounts for only around 1% of the desktop market compared with around 90% for Windows.
Number of base installs has no direct measureable effect of the number of attacks. If it would have then apache would be the most targetted and hacked webserver out there... yet it is not although there are a lot more apache than IIS servers out there...

Why is that so? You answered it yourself already:
> **Kinstonian said:**
> If someone is going to write malware to make money (which is the most common motive now) then they are going to write it to work on Windows.  It's simple economics.
It's simple economics. Where do I get the best ROI.
On a Windows machine verything is tightly integrated. Lets say if you can hijack the browser you own the machine. So applying this to the IIS/Apache example: If you can hijack the IIS server you have full control over the whole machine. If you can hijack Apache however, you are very limited as to what you can do.

While number of base installs may play a partial role it is by far not the only one. An attacker will consider:
(1) How easy it is to hack the computer: As linus is opensource, it should be a lot easier to find a weakness and exploit it.

(2) If I can hijack somethign, what can I do with it: On Windows, where just about everything is run as admin and where things are so tightly knotted together, you will normally be the master of that machine if you can hijack just one thing. On linux you will normally be very limited and restricted of what you can do.

(3) Number of base installs: How many potential targets can I actually affect with it? As said, there are far more linux devices out there. You say it may not be worthwhile hijacking a router? I disagree. All the network traffic goes through there... unencrypted emails, unencrypted passwords, ..... if you can hijack the router you can get a lot of information. So this numbers does speak for Windows but not entirely.
With regard to the number of base installs you also have to consider that Linux is not a monolithic culture. On Windows you have like Windows 98, Windows 2000, Windows XP, Windows VISTA all running the same architecture. There's not a lot of diversity there.
On linux you have i386, you have sparc you have this and that... furthermore you have hundreds of different distro all being different from each other. While the total number of linux devices is bigger, the diversity makes it less attractive anymore.

As a practical example:

Google runs all servers on linux. The linux source code is available, so hijacking it should be "fairly simple".
Now, assuming you can manipulate google search engine results you can generate a lot of cash. This means google would be a prime target - so I wonder why not everbody tries to hack google... just get in stealthy, manipulate the ranking algorithms so that yuor sites are on top, get all the cash... the possible ROI would be very high yet has anyone achieved that yet?

---

### Post by Kinstonian on 2008-12-03
hyper_ch, we're talking about malware, not vulnerabilities in servers.  There is no doubt IIS has been buggy in the past, although it has improved a lot since then.  There's no doubt Microsoft screwed up on that. :)  Just like Sendmail was probably buggier than Exchange in the past.  But those are vulnerabilities, not malware.  Vulnerabilities and malware happen for different reasons.  Not only that, but **vendors/users** create vulnerabilities, **crackers/script kiddies** create malware.  Apples and oranges...

I agree compromising a router would be useful for an attacker.  In fact, I think attacks on them will increase, and they have already started-- for example IOS rootkits.

However, I don't think it's right to compare a full desktop OS, which has tons of resources, functionality, and attack vectors to a highly specialized device that is also *rarely interacted with by the user*.  There obviously aren't going to be many viruses for my Linksys router as there are for my desktop.  Including devices like that when talking about desktops is like including a Ferrari (Linksys router) in a group of BMWs (Desktop OS).

You raised a good point about monolithic culture in Windows vs diversity in Linux, which fits in to what I was saying about how the environment and culture around Linux is beneficial in preventing malware.  That we can agree on. :)

---

### Post by renaldoandrews on 2008-12-03
I may be wrong. But the best way to catch a virus is by running Wine on your computer. I run Wine currently. But I about to try Linux Alternative so I can take advantage of Linux best feature security.

---

### Post by johnkzin on 2008-12-03
> **Kinstonian said:**
> hyper_ch, we're talking about malware, not vulnerabilities in (hosts).

You can't talk about one without talking about the other.  Many forms of malware rely upon vulnerabilities in the host, whether it's poorly implemented software (OS, App, etc.), poorly administrated software, or common "worst practices" (ex: the internet worm relied upon a common "worst practice").

---

### Post by Dragonbite on 2008-12-03
> **renaldoandrews said:**
> I may be wrong. But the best way to catch a virus is by running Wine on your computer. I run Wine currently. But I about to try Linux Alternative so I can take advantage of Linux best feature security.

Best way to avoid a virus is to run from a LiveCD and reboot often.

---

### Post by Kinstonian on 2008-12-03
> **johnkzin said:**
> You can't talk about one without talking about the other.  Many forms of malware rely upon vulnerabilities in the host, whether it's poorly implemented software (OS, App, etc.), poorly administrated software, or common "worst practices" (ex: the internet worm relied upon a common "worst practice").

Yes, some malware exploits software/configuration vulnerabilities.  That is **one** possible attack vector for malware.  However, there is much more to vulnerabilities than malware, and much more to malware than vulnerabilities.  It appears as though hyper_ch was talking about vulnerabilities in Apache/IIS outside of malware, such as targeted attacks to deface a web server or something.

---

### Post by johnkzin on 2008-12-03
> **Kinstonian said:**
> However, there is much more to vulnerabilities than malware, and much more to malware than vulnerabilities.

Ok, fine.  I'll rephrase my first sentence from that quote:

You can't have a COMPLETE discussion about one without discussing the other.


And, if you're not going to make a complete discussion of a topic that NEEDS to be covered thoroughly and rigorously, then why bother?

---

### Post by aysiu on 2008-12-03
I fully agree that many Linux users are complacent.

But I also think that some new Linux users are misguided in thinking that complacency = not running antivirus and running antivirus = lack of complacency.

The two are wholly unrelated. Antivirus is not effective protection against malware, especially in Linux. Effective protection involves installing security updates, using strong passwords, not bypassing a proper permissions system by always running as root, and not enabling network services you don't know how to properly lock down.

Maybe someone should write a blog post called *Running antivirus: a false sense of security*

---

### Post by bodhi.zazen on 2008-12-03
> **johnkzin said:**
> At this time.  It's not impossible.  The first major worm waas a UNIX worm, not a windows/dos worm.

I never claimed Linux was invulnerable to worms or viruses. The Linux solution, however, is to keep your system up to date. An up to date system is not vulnerable to known viruses or worms.

> Whether or not Windows is worse or not is irrelevant.  What's relevant is "can an adversary every find such a hole in Linux faster than the linux white-hats can find it?"  ... the answer is, without question: eventually, yes, they will.

Security will always be a cat and mouse game.

> How will that prevent you from being infected by an Office Macro Virus?

Not sure what you are asking here. Personally I do not run OOO or Microsoft word so I do not see myself vulnerable to a Macro Virus.

> The solution to viruses and worms on ALL platforms is:

1) don't be stupid: close services that shouldn't be open, don't open services you don't need, use things like tcpwrappers or your firewall of choice to keep access restricted, and don't open files you haven't scanned.  Don't leave an open port, for the latest malware, that MIGHT be vulnerable to an exploit you're not yet aware of, unless you absolutely need that port open.

Unlike Windows, there are no open services with a default Ubuntu installation.

> 2) keep up to date on patches/updates, both recommended and security.

+1

> 3) scan your system for malware.  scan files you download against known malware (ClamAV is a good start, along with their 3rd party optional sigs, like SaneSecurity, MBL, and MSBL).  Even malware that might not be native to your platform(s) (because it might be left behind by an adversary that using you as a repository or something, and because you want to be a responsible netizen and be sure your system isn't passing on viruses ... even ones you yourself are immune to).

I agree, but only to a point. Scanning for known viruses/worms does not protect you from the next virus/worm to be released and if your system is up to date you should not be vulnerable to known viruses.

Although there have been Linux viruses/worms, unlike windows, the OpenSource community actually patches the code, thus the solution is to keep your system up to date. Microsoft, as far as I can tell, has no intention of patching their code, thus scanning for viruses is necessary.

Thus, although both *nix and Windows are vulnerable to worms/viruses, the solution to the problem is not the same.

I do not see how "it might be left behind by an adversary that using you as a repository or something" is realistic though. This is a circular argument in that if someone can do these things you are implying more then a virus or worm, now you are talking about a root kit or escalation of privileges. In that case you need more then a virus scanner, you need to image the HD for forensics and re-install.

I also disagree with your "netzen" concept. Although I would not knowingly pass on a virus or worm, IMO it is not my responsibility to scan for windows viruses or protect windows computers. If someone wishes to use windows it is his or her responsibility to secure his or her box. Now if I were to run a mail server or a file server with windows clients I would run a virus scanner on the server, but I disagree with you when running a Linux Desktop.

Along those lines, since when is Microsoft interested in stopping or screening for Linux viruses or worms ? IMO Microsoft needs to become a "netzen", in more ways then 1.

> 4) use tripwire, IDS, and similar tools to monitor access and changes to your system, reading your security logs and such. (and be proactive: when you see some idiot probing your SSH port every so often, don't wait for him to get lucky, block him now with your tcpwrapper or firewall config)

+1 I agree with proactive security.

If you run a server, take the time to learn to secure it. tcpwrapper does not apply to every service and sometimes you do not know the ip address you consider valid.

In my experience Snort and OSSEC are much more informative and are quite effective.

> 5) when it comes to "convenience vs security" always be aware of what you're doing when you choose convenience, and be diligent about the consequences of that decision.

+1 on that as well.

---

### Post by Kinstonian on 2008-12-03
> **johnkzin said:**
> Ok, fine.  I'll rephrase my first sentence from that quote:

You can't have a COMPLETE discussion about one without discussing the other.


And, if you're not going to make a complete discussion of a topic that NEEDS to be covered thoroughly and rigorously, then why bother?

You only responded to part of what I said.  "*It appears as though hyper_ch was talking about vulnerabilities in Apache/IIS outside of malware, such as targeted attacks to deface a web server or something.*"  I'm just trying to keep things relevant and on topic.

With that said, back to my original point I was making...  I haven't heard of anyone who thinks a monoculture and the monopoly like Microsoft has is a good thing for security.  In fact, the experts who have done research on the effects monoculture has on security have concluded it's bad.  I still stand by my original comment that Windows gets the most attacks and malware because of its monopoly, and Linux's small market share.

---

### Post by bodhi.zazen on 2008-12-03
> **Kinstonian said:**
> I still stand by my original comment that Windows gets the most attacks and malware because of its monopoly, and Linux's small market share.

The Microsoft propaganda machine would certainly agree,

"we only get attacked because:
[list][*]We are the best.
[*]We are the biggest.
[*]No one uses any other OS."[/list]

*nix servers / Apache is as big, or dare I say bigger targets as any Windows Server. And Microsoft certainly does NOT dominate the server market.

With your reasoning, Apache would have far, far more issues. If you grant IIS has 50% market share, it would follow from your reasoning, that 50% of the (web server) malware would target IIS. But since this is not the case ...

Security comes in design of the OS, from the ground up, not market share.

---

### Post by Kinstonian on 2008-12-03
> **bodhi.zazen said:**
> The Microsoft propaganda machine would certainly agree,

"we only get attacked because:
[list][*]We are the best.
[*]We are the biggest.
[*]No one uses any other OS."[/list]

*nix servers / Apache is as big, or dare I say bigger targets as any Windows Server. And Microsoft certainly does NOT dominate the server market.

With your reasoning, Apache would have far, far more issues. If you grant IIS has 50% market share, it would follow from your reasoning, that 50% of the (web server) malware would target IIS. But since this is not the case ...

Security comes in design of the OS, from the ground up, not market share.

Actually the monoculture point is against Microsoft, not in defense of it.  [Here](http://www.ccianet.org/papers/cyberinsecurity.pdf) is one research paper on monoculture and why Microsoft's monopoly is **bad**.  I can understand if you don't want to believe me, but you can believe the authors of that report including Dan Geer, Bruce Schneier, and Peter Gutmann. In the paper they are talking about breaking up Microsoft's monopoly, so it's definitely not part of Microsoft's propaganda.

---

### Post by damis648 on 2008-12-03
Maybe I am wrong... but there AFAIK NOT 800 some malwares for *nix (In the wild at least)

---

### Post by bodhi.zazen on 2008-12-04
> **Kinstonian said:**
> Actually the monoculture point is against Microsoft, not in defense of it.  [Here](http://www.ccianet.org/papers/cyberinsecurity.pdf) is one research paper on monoculture and why Microsoft's monopoly is **bad**.  I can understand if you don't want to believe me, but you can believe the authors of that report including Dan Geer, Bruce Schneier, and Peter Gutmann. In the paper they are talking about breaking up Microsoft's monopoly, so it's definitely not part of Microsoft's propaganda.

Thanks for the links :)

---

### Post by magmon on 2008-12-05
If anyone else posted this, I second your opinion xD.

Solution: Synaptic search "clam"
Download clam AV
Done.

---

### Post by CholericKoala on 2008-12-05
Many have already stated antivirus programs are not the solution to Linux viruses.  However, neither are they the solution to Windows viruses.  If a user is willing to install something on their system, they are hosed no matter what.  Sure, an antivirus program might help against an old, depreciated virus, but new ones come out every day.  Linux is not superior to Windows because it is immune to viruses, but I would argue that it can be if Linux communities, like this one educated its users on what is safe and unsafe, what is good practice and what is folly.  Using a program in place of your own discernment just seems like bad practice to me.  Programs can help us discern between good and bad things, but it does not look like people are using programs for that purpose, rather, throwing their discernment out the window and letting the brain-less program determine their destiny.

---

### Post by SunnyRabbiera on 2008-12-05
> **Kinstonian said:**
> After skimming over the article I agree with it.  Contrary to popular belief, there is nothing special about Linux that prevents it from being a target of malware.  In fact Windows Vista has many more built in security measures than Linux such as [Windows Resource Protection](http://en.wikipedia.org/wiki/Windows_Resource_Protection), [Mandatory Integrity Control](http://en.wikipedia.org/wiki/Mandatory_Integrity_Control), [Services Hardening](http://technet.microsoft.com/en-us/magazine/cc162523.aspx), [Volume Snapshot Service](http://en.wikipedia.org/wiki/Shadow_Copy), [Windows Defender](http://en.wikipedia.org/wiki/Windows_Defender), etc.
Well the reason why vista is so bogged down with all those tools is because of the model that MS has about security.
There are so many issues with the windows security model its ridiculous.
Now its not like linux wont become vulnerable, quite the contrary as it becomes more popular the more of a target it will become.
There will probably be something that will make linux vulnerable but as long as we patch and keep up to date these vulnerabilities could be canceled out quite soon unlike windows.

---

### Post by tsali on 2008-12-05
> Also, the average Linux user is far more tech savvy than the average Windows user. Most Linux users aren't going to run mobile code from shady web sites, or run attachments in email, etc.

I don't agree.

Here's why: 

The large majority of Ubuntu users in these forums who have used Windows complain about virus/malware having been a problem for them. In my admittedly short foray into using Windows (3 years), I have never experienced a virus/malware or even encountered one that I know of. I spend an inordinate amount of time web surfing.

Therefore, I counter that a lot of linux users were engaging in high risk activities and defected to linux to reduce that risk. The ONLY virus I've had to clean off my daughter's computer was because she tried to download a "cracked copy of Photoshop" from a warez site.

I tend to agree that authors of truly destructive or criminal malware want the highest ROI, so they target the most prevalent systems. 

I also agree that the user is the easiest link in the security chain to break. It is INCREDIBLY easy to get a consumer user to give you their root password...you only have to ask them for it! Besides, isn't most valuable information on a consumer desktop kept in their home folder anyway?

And, to be clear, I don't care about the server arguments...servers are typically administered by professional people who's priority is keep them safe. I am amazed they are infected at all and would tend to think that would be more the fault of the sysadmins than anything else.

---

### Post by billgoldberg on 2008-12-05
> **Kinstonian said:**
> After skimming over the article I agree with it.  Contrary to popular belief, there is nothing special about Linux that prevents it from being a target of malware.  In fact Windows Vista has many more built in security measures than Linux such as [Windows Resource Protection](http://en.wikipedia.org/wiki/Windows_Resource_Protection), [Mandatory Integrity Control](http://en.wikipedia.org/wiki/Mandatory_Integrity_Control), [Services Hardening](http://technet.microsoft.com/en-us/magazine/cc162523.aspx), [Volume Snapshot Service](http://en.wikipedia.org/wiki/Shadow_Copy), [Windows Defender](http://en.wikipedia.org/wiki/Windows_Defender), etc.

**The reason why Linux doesn't have much malware isn't because of the operating system itself, it's because of the environment it's in and the culture that surrounds it.**  For example, Linux accounts for only around 1% of the desktop market compared with around 90% for Windows.  If someone is going to write malware to make money (which is the most common motive now) then they are going to write it to work on Windows.  It's simple economics.

Also, the average Linux user is far more tech savvy than the average Windows user.  Most Linux users aren't going to run mobile code from shady web sites, or run attachments in email, etc.  They are also more likely to get software from trusted sources such as repositories or straight from the software vendors site, and then use cryptography to make sure it hasn't been modified before they install it.

Historically *nix has been known for being stable and secure while not being user friendly.  On the other hand, Windows has been known for being user friendly, but not stable or secure.  However, over time both OS's have improved dramatically on their weaknesses.  Windows Vista is much more stable and secure, where *nix with distributions like Ubuntu are much more user friendly.  The lack of usability has been a huge problem for *nix.  As it improves, I expect it will gain more market share, and at the same time, become more of a target.

I have to disagree with you here, big time.

Linux is a HUGE market to write viruses for (the interet= linux :p).

Ubuntu, by default is is very secure.

I'm not going to go into details why, I'm sure others will have already responded to this.

---

### Post by collinp on 2008-12-05
> **tsali said:**
> I don't agree.

Here's why: 

The large majority of Ubuntu users in these forums who have used Windows complain about virus/malware having been a problem for them. In my admittedly short foray into using Windows (3 years), I have never experienced a virus/malware or even encountered one that I know of. I spend an inordinate amount of time web surfing.

Therefore, I counter that a lot of linux users were engaging in high risk activities and defected to linux to reduce that risk. The ONLY virus I've had to clean off my daughter's computer was because she tried to download a "cracked copy of Photoshop" from a warez site.

I tend to agree that authors of truly destructive or criminal malware want the highest ROI, so they target the most prevalent systems. 

I also agree that the user is the easiest link in the security chain to break. It is INCREDIBLY easy to get a consumer user to give you their root password...you only have to ask them for it! Besides, isn't most valuable information on a consumer desktop kept in their home folder anyway?

And, to be clear, I don't care about the server arguments...servers are typically administered by professional people who's priority is keep them safe. I am amazed they are infected at all and would tend to think that would be more the fault of the sysadmins than anything else.

That is Ubuntu. Not Gentoo, Fedora, Red Hat, SuSe, Debian, Arch, or any of the others. There is very few Linux viruses wrote, and none run on a modern system, partially because of Linux not being like windows with popularity, and partially because of the strong security model Linux has. There is way too much variety in the Linux operating system to code a virus that could affect all computers, unless it was a massive security hole in something like bash.

---

### Post by billgoldberg on 2008-12-05
> **renaldoandrews said:**
> I may be wrong. But the best way to catch a virus is by running Wine on your computer. I run Wine currently. But I about to try Linux Alternative so I can take advantage of Linux best feature security.

I don't think a lot of viruses will actually run on wine, but if your wine install should get infected, it can only infect the data on the Wine drive itself.

Your OS will not be harmed, nor will your personal data in /home.

---

### Post by billgoldberg on 2008-12-05
> **damis648 said:**
> Maybe I am wrong... but there AFAIK NOT 800 some malwares for *nix (In the wild at least)

That could be the case, but as of today I don't know of any malware that can infect an UP-TO-DATE Ubuntu install.

So if there is malware, it's not harmful for me and most likely not for you either.

--

I have been following the discussion, and I agree with just about anything Bodhi.Zazen has said on this issue.

---

### Post by Liunx on 2008-12-05
fine , we had to be familiar with our linux system deeper than the virus, is not it?
So, let virus ran after us more than we follow the boring Mr virus.):P

---

### Post by bodhi.zazen on 2008-12-05
I would like to point out that, on linux, virus scanners are of very very limited utility.

Virus scanners do NOTHING for zero day exploits.

The solution is, besides security upgrades, using selinux or in ubuntu apparmor.

I will be writing a how-to on apparmor soon but Linux security is moving away from a monolithic superuser account (ie sudo rather then su for example) and putting restrictions on users and processes. Both aparmor and selinux, for example, will restrict even root.

I suggest if you are interested in securing your Linux box you look into either selinux, or on Ubuntu apparmor (amongst other tools).

---

### Post by tsali on 2008-12-05
> **Hellow said:**
> That is Ubuntu. Not Gentoo, Fedora, Red Hat, SuSe, Debian, Arch, or any of the others. There is very few Linux viruses wrote, and none run on a modern system, partially because of Linux not being like windows with popularity, and partially because of the strong security model Linux has. There is way too much variety in the Linux operating system to code a virus that could affect all computers, unless it was a massive security hole in something like bash.

What exactly are you saying? If I write malware that cajoles the root password out of the user, I don't care what distro you're using...it's mine.

---

### Post by bodhi.zazen on 2008-12-05
> **tsali said:**
> What exactly are you saying? If I write malware that cajoles the root password out of the user, I don't care what distro you're using...it's mine.

That is what selinux and apparmor are for ;)

Are they perfect, no, but they are an improvement. In Engarde Linux, even if you log in as root, you are treated as a normal user, and can not change system files (or even do a simple wget).

---

### Post by Grant A. on 2008-12-05
> **Kinstonian said:**
> 

**The reason why Linux doesn't have much malware isn't because of the operating system itself, it's because of the environment it's in and the culture that surrounds it.**  For example, Linux accounts for only around 1% of the desktop market compared with around 90% for Windows.  If someone is going to write malware to make money (which is the most common motive now) then they are going to write it to work on Windows.  It's simple economics.

Then why do Macs with an 8% market share only have 2 viruses compared to Linux's 34?

---

### Post by CholericKoala on 2008-12-05
The population of linux hackers compared to mac hackers are higher?  I dunno, take a guess, I'm sure it wouldnt be too far off from a combination of reasons.

---

### Post by magmon on 2008-12-06
> **Grant A. said:**
> Then why do Macs with an 8% market share only have 2 viruses compared to Linux's 34?

LOL! Buddy, you may want to check your sources. I am willing to bet that mac has considerably more viruses than 2, and Ive read that linux has over 800

---

### Post by Grant A. on 2008-12-06
> **magmon said:**
> LOL! Buddy, you may want to check your sources. I am willing to bet that mac has considerably more viruses than 2, and Ive read that linux has over 800

Read Apple's Mac OS X section of their site. Linux only has 32 non-proof-of-concept viruses, of which only 4 or so still work and are very rare to get without compiling it yourself. All the others were made to expose bugs in the kernel and programs so they could be fixed.

---

### Post by Giant Speck on 2008-12-06
> **magmon said:**
> LOL! Buddy, you may want to check your sources. I am willing to bet that mac has considerably more viruses than 2, and Ive read that linux has over 800

You are confusing definitions. There are over 800 specific malware programs for Linux, but only 34 fit the true definition of "virus."

---

### Post by magmon on 2008-12-06
> **Giant Speck said:**
> You are confusing definitions. There are over 800 specific malware programs for Linux, but only 34 fit the true definition of "virus."

Ah, ok. Why is there a distiction?? Dont they both do essentially the same things?

---

### Post by CraigPaleo on 2008-12-06
> **bodhi.zazen said:**
> I would like to point out that, on linux, virus scanners are of very very limited utility.

Virus scanners do NOTHING for zero day exploits.

The solution is, besides security upgrades, using selinux or in ubuntu apparmor.

I will be writing a how-to on apparmor soon but Linux security is moving away from a monolithic superuser account (ie sudo rather then su for example) and putting restrictions on users and processes. Both aparmor and selinux, for example, will restrict even root.

I suggest if you are interested in securing your Linux box you look into either selinux, or on Ubuntu apparmor (amongst other tools).

I just checked Synaptic and Apparmor is apparently installed by default, at least in Ubuntu Intrepid. Will your how-to explain how to configure it beyond the default configuration?

---

### Post by hyper_ch on 2008-12-06
> **magmon said:**
> Dont they both do essentially the same things?
No

---

### Post by hyper_ch on 2008-12-06
> **CraigPaleo said:**
> I just checked Synaptic and Apparmor is apparently installed by default, at least in Ubuntu Intrepid. Will your how-to explain how to configure it beyond the default configuration?

jdong startet a "howto" on AppArmor:  [http://digg.com/linux_unix/Advanced_Linux_Security_Introduction_to_AppArmor](http://digg.com/linux_unix/Advanced_Linux_Security_Introduction_to_AppArmor)

---

### Post by Giant Speck on 2008-12-06
> **magmon said:**
> Ah, ok. Why is there a distiction?? Dont they both do essentially the same things?

No.  Malware is software that infiltrates and destroys computer systems without the owner's consent.

Viruses are a type of malware (specifically "infectious malware") that self-replicate and spread themselves.

In a nutshell, all viruses are malware, but not all malware are viruses.

---

### Post by johnkzin on 2008-12-06
> **magmon said:**
> Ah, ok. Why is there a distiction?? Dont they both do essentially the same things?

There are distinctions, but for the purpose of "should you use a virus scanner or not", they're the same -- a good virus scanner can detect both viruses proper, and malware in general (and phishing messages when applied to email).

For example, clamav has malware based 3rd party signatures.

---

### Post by mdsmedia on 2008-12-06
While I agree that Linux is not invulnerable to malware, I also say that the theory that it's all to do with market-share is almost as inaccurate as saying that Linux is invulnerable.

While I'm no expert, isn't one of the biggest problems with viruses their ability to propagate or spread? That's where Linux, from what I've read, can hold its own. Sure, your system may be infected, but passing it on to other systems is another story. But that's just what I've read.

---

### Post by tsali on 2008-12-06
> **bodhi.zazen said:**
> That is what selinux and apparmor are for ;)

Are they perfect, no, but they are an improvement. In Engarde Linux, even if you log in as root, you are treated as a normal user, and can not change system files (or even do a simple wget).

How well do think Engarde and similar systems would fare on a consumer desktop?

How hard do you think it would be to get consumer users to download my linux native version of Photoshop? Or perhaps connect to a repo that contains blu-ray player software?

Making a system hard is one thing...making it user proof is another entirely.

If you are administering enterprise systems or servers, this is relatively straight-forward. You simply limit the user's activities. Authorized users should not engage in high risk operations.

However, when the user is also the owner and sysadmin, as most home users are, they won't tolerate the inconvenience of having excessively limited access to their system.

In scenarios where the assailant must "break" into the guarded facility, hardening facilities works...but I stand by my ealier premise that it all too easy to turn the user into an inside man.

Both Apparmor and SELinux are tools designed to limit privileges of KNOW INSTALLED software to prevent exploiting vulnerabilities in useful applications. However, I can write a self contained binary that may not depend on apps or services with an existing profile.

---

### Post by mdsmedia on 2008-12-06
> **tsali said:**
> How well do think Engarde and similar systems would fare on a consumer desktop?

How hard do you think it would be to get consumer users to download my linux native version of Photoshop? Or perhaps connect to a repo that contains blu-ray player software?

Making a system hard is one thing...making it user proof is another entirely.

If you are administering enterprise systems or servers, this is relatively straight-forward. You simply limit the user's activities. Authorized users should not engage in high risk operations.

However, when the user is also the owner and sysadmin, as most home users are, they won't tolerate the inconvenience of having excessively limited access to their system.

In scenarios where the assailant must "break" into the guarded facility, hardening facilities works...but I stand by my ealier premise that it all too easy to turn the user into an inside man.

Both Apparmor and SELinux are tools designed to limit privileges of KNOW INSTALLED software to prevent exploiting vulnerabilities in useful applications. However, I can write a self contained binary that may not depend on apps or services with an existing profile.That's true, but how far will the malware get, having been installed by the "inside man"?

---

### Post by tsali on 2008-12-06
> **mdsmedia said:**
> That's true, but how far will the malware get, having been installed by the "inside man"?

Good question. Once it has been installed by the "inside man", it's pretty easy to hi-jack all of the user's personal information (it is HIS app after all)

Seems to me that once the user has given the program the root password, it can go as far as I want it to.

Anyway, the linux using population doesn't represent enough ROI...or enough payback to take the risk of writing and sending it out.

Suffice to say that good structure (which *nix has) is a very good foundation for a secure system. It reduces opportunities for exploitation but does not eliminate them.

The same rule apply IRL. Hardcore *nix users/programmers KNOW how to get into your system. If you have something they really want, they will find a way to take it. Know that government and law enforcement have these skills at their disposal also. 

The point of the thread is that Linux users should not make the mistake of assuming they are invulnerable and drop their guard.

---

### Post by bodhi.zazen on 2008-12-06
> **tsali said:**
> How well do think Engarde and similar systems would fare on a consumer desktop?

Engarde is not designed for a desktop, it is designed as a very secure server.

SELinux has a steep learning curve. Right now, I am running Fedora 10 as a desktop with SeLInux (Targeted). It took less then 10 minutes for me to lock down (resolve all the policies) for Virtualbox, which is fairly complex. SELinux (targeted) and the ease of management has come a long way in even the last year.

Apparmor is easier to configure and is already installed on Ubuntu by default.

There is a HUGE difference, in terms of ease of use, between Apparmor, SELinux (targeted) and SELinux Strict.

Are these tools perfect, no, but look at the alternate ... Firewalls and Antiviurus and Security updates all leave you vulerable to zero day exploits. 

Now I happen to know a few people who have been victems of identity theft (through compromise of their computers) and I can guarentee you, it is easer to learn Apparmor then reclaim your identity.

I offer you a choice, you can have the red pill or the blue pill.

---

### Post by cardinals_fan on 2008-12-07
> **Giant Speck said:**
> No.  Malware is software that infiltrates and destroys computer systems without the owner's **_informed_** consent.

Viruses are a type of malware (specifically "infectious malware") that self-replicate and spread themselves.

In a nutshell, all viruses are malware, but not all malware are viruses.
Fixed that for you ;)

---

### Post by Giant Speck on 2008-12-07
> **cardinals_fan said:**
> Fixed that for you ;)

:lolflag:

Thanks.

---

### Post by nvteighen on 2008-12-07
No OS is 100% invulnerable to malware, but GNU/Linux systems have some design features that may harden the creation of critically dangerous malware.

**1. Diversity**: You don't have "GNU/Linux", but Gentoo, Ubuntu, Fedora, Red Hat, Slackware, Debian, gNewSense, etc. and who knows how many lots of homebread distros. Each distro using a different packaging system, having different software installed by default, etc. Of course there's a bunch of stuff that's common to all distros: mainly the GNU utilities and obviously the Linux kernel, so maybe there you could have a more succesful exploit.

**2. Repository system**: The repository system makes sure you're using "certified" software and not just random stuff (as you'd do at Windows). Of course, you could start adding non-trustworthy repos to your configuration, but that's not a system's flaw. And if you restrict yourself to Free Software, you'll be even safer... Those distros without repository servers usually deal with compiling stuff by hand, so they tend to be used by real experts who probably read the source first.

**3. The multiuser environment**: Specially on those distros that disable root's login at console, the fact that users only have user-access is vital to reduce the risk of a virus attack to be succesful. Here sudo might even be proved unsafer than su, as the time gap that leaves sudo before timing out could be used by some latent virus to gain root privileges (piping periodically to some terminal device expecting that some sudo session in it hadn't timed out yet?... of course the logs would show the attempts).

All known possible attacks to a GNU/Linux system need user interaction. So, as in Windows (I never had any malware using Windows since 3.1...), education is the first defense: even an armored tank would be vulnerable if you don't know what you're doing.

But there are strong reasons to say that GNU/Linux is a *more* robust system by design, not just "unexplored" by chance. Of course, to keep on this track, developers are needed to keep an eye on the source and detect any security hole.

Other malware depends on application-security. There you need to use trusted applications.

---

### Post by finalmacpro on 2008-12-07
> **sydbat said:**
> Not sure how...seeing as it is a Unix OS...unless Apple set it up similar to the way Windows is, with everything root/admin...

No the only time you can log in as Admin in Mac OS X is if you have just installed the OS and are setting up the User accounts and installing the iLife suite that is on Disk 2. You can do that on the setup process. In the setup assistant you do connect to the internet, not long enough for a Virus though. You can log in as root later by going to the Utilities folder going to the "Directory Utility" put your username and password in to unlock go edit Enable Root User. Then Log out and then click "sign in as another user" then in the username box type "root" and type the password it told you to set up! Then you are a bit less secure of viruses! Although most mac users don't know how to do this it's a good job though some n00b might think he knows everything about computers and explore the root.

---

### Post by halovivek on 2008-12-08
Since Linux is open source. why cant a virus can be created or run by using the loop holes. windows os is closed programs for that itself virus is created. but what is the major thing in linux it prevents all... malwares, spywares and virus? since you can see all the codes from security to desktop..

---

### Post by CraigPaleo on 2008-12-08
> **halovivek said:**
> Since Linux is open source. why cant a virus can be created or run by using the loop holes. windows os is closed programs for that itself virus is created. but what is the major thing in linux it prevents all... malwares, spywares and virus? since you can see all the codes from security to desktop..

Because anyone can look at the source code, holes are found and closed before anyone really has a chance to exploit them.

---

### Post by nvteighen on 2008-12-08
> **halovivek said:**
> Since Linux is open source. why cant a virus can be created or run by using the loop holes. windows os is closed programs for that itself virus is created. but what is the major thing in linux it prevents all... malwares, spywares and virus? since you can see all the codes from security to desktop..
Again, it's its design.

The only major vulnerability you may have in GNU/Linux systems are those related to servers (so, if you don't run one... forget this, unless you do something silly like opening your ports): rootkits, crackers, etc. That cases won't need any user interaction to harm your system... There you'll need to have a robustly set up firewall, keep your server software up-to-date and constantly be checking logs.

About privilege escalation: that's mainly because of faulty programming... It's hard to explain how this works without recurring to programming concepts, but believe me it's not that easy to exploit that and are fairly easy to detect (usually always related to some user input mechanism and certain programming languages).

---

### Post by johnkzin on 2008-12-08
> **CraigPaleo said:**
> Because anyone can look at the source code, holes are found and closed before anyone really has a chance to exploit them.

not "are", "can be".  It's a race.  So far, open source *nix'es have been pretty successful in this regard, but it only takes one creative black hat to upset the record by figuring out a place to look that hasn't been given attention by the white hats.

(and, for the most part, the things being given as the strengths of Linux are not the strengths of Linux, they're the strenghts of all Unix-like platforms, including *BSD and Mac OS X)

---

### Post by blazercist on 2008-12-08
I'm going to have to disagree with the OP's argument, not in principal, but in practice.

1.  Linux is far too unstandardized for a wide spread security problem to exist.  Simply put, each distro has its own filesystem structure, services, programs, kernel/patches.  This makes it extremely difficult to write a virus or some kind of malware that will effectively procreate in the wild.

2.  The default in most Linux distro's is to run as user and not as root, although "privilege escalation" exists its much more difficult than the article makes it sound and theoretically exploits code in a program that is not present of all systems like lets say for example explorer.exe is on windows.

3.  If the article is correct and there are ~800 known malwares for Linux at ~1% market share then we can extrapolate to Windows market share by multiplying by 90 and we get 72000 malwares, still far less virus' in total than were written for Windows in this year alone.  Not to mention that of those 800 "known" viruses for Linux claimed in the article 95% of them were created in a lab type environment as proof of concepts and have never been found in the wild.

4.  Linux changes CONSTANTLY, even if all the distro used a standard kernel and filesystem with standard programs and services, we get so many updates so often that even if someone were to write an effect virus for Linux it would be obsolete in a day, possibly a week or two at most.

5.  Again, the filesystem and permissions scheme makes it so that you would have to be almost completely brain dead........ no forget that, you would have to actually WANT to install the virus on your system in order to install it.


</end rant>

---

### Post by aysiu on 2008-12-08
If a new "hole" is found, I still don't see how having anti-virus installed protects you.

Imagining Linux is invincible is definitely evidence of a false sense of security, but so is imagining having anti-fill-in-the-blank gives you protection against future threats.

The only "false sense of security" I've seen is from people running anti-virus.

---

### Post by aysiu on 2008-12-08
If a new "hole" is found, I still don't see how having anti-virus installed protects you.

Imagining Linux is invincible is definitely evidence of a false sense of security, but so is imagining having anti-fill-in-the-blank gives you protection against future threats.

The only "false sense of security" I've seen is from people running anti-virus.

---

### Post by Giant Speck on 2008-12-08
If some kind of malware was to successfully infiltrate Linux, I don't think we'd see it coming.  An anti-virus program is not going to catch it, because it has never seen it before.  It's just like Windows. 

You can't fight off problems that haven't occurred yet.  You can only fight off problems that currently exist.

---

### Post by bodhi.zazen on 2008-12-08
Linux is vulnerable to exploits, and I have seen several cracked systems.

There are several "problems" in this thread :

1. False Sense of Security. I tend to agree, that attitude on many linux forums is that users do not need to be concerned with security, or worse, people believe (falsely I might point out) that they are the "only user who uses the system". These are unhealthy attitudes.

While it is true, IMO, Ubuntu is relatively secure out of the box, this does not alleviate the need for all users to learn security, regardless of OS.


2. The discussion of "Viruses" is very much off topic. The term is being thrown around as a general term to mean "Malware" or "Exploits". In general viruses are a non-issue on Linux systems. This is not the same as saying Linux is invulnerable.

3. Zero day exploits. This is the Elephant in the room so to speak. How to manage zero day, or new exploits ? The problem is these exploits can not, by definition, be managed with virus or root kit scanners.

There are essentially 3 tools:

NIDS - Network Intrusion Detection is snort or wireshark. These tools monitor network traffic.

HIDS - Host based intrusion detection. OSSEC, tripwire, tiger, etc (antivirus scanning world also be an example).

AC or access control. This is a security system that limits users or applications access to system files and, IMO, is like standard permissions on steroids. Examples include Apparmor (which is default on Ubuntu) and SELinux.

These tools are very interesting and if you have not seen them in action, you will have a cow the first time you see "permission denied" when you run an application as root:

> bodhi@jaunty:~$ gksu firefox
**[COLOR=darkred]No protocol specifiedError: cannot open display: :0[/COLOR]****[COLOR=darkred]Although the above error "appears" to be a problem with X, the error is generated because the (apparmor) firefox profile does not allow root to access my X session.[/COLOR]**

If I run firefox as a user it works.  I put the firefox profile into the complain mode (sudo aa-complain firefox) then gksu firefox works as well.

This is the power of apparmor and SELinux.

Rather then endless discussion I suggest we shift the conversation to how to use these tools. 

Security is like an onion, it has layers and it stinks. No single layer is fool proof, but it you are running say Snort, OSSEC, and SELinux, or if you configure apparmor, you are pretty solid.

So please let us stop having these endless, mindless debates, and start talking security, security tools, and how to use them.

---

### Post by aysiu on 2008-12-08
I agree with bodhi.zazen.

Discussions about viruses and anti-viruses distract from discussions about *real security measures* and *real security threats*.

---

### Post by sydbat on 2008-12-08
OK. Where do I find AppArmor (it is installed by default, I checked)? How do I open it? Is it GUI or Terminal? 

I am asking in all seriousness because it is one of the things talked about through this thread, yet no mention of how to use it or where to go to find out more.

---

### Post by bodhi.zazen on 2008-12-08
I am working on an apparmor sticky for the forums.

for now :

[Novell AppArmor Quickstart](http://www.novell.com/documentation/apparmor/book_opensuse_aaquick21_start/index.html?page=/documentation/apparmor/book_opensuse_aaquick21_start/data/article_book_book_opensuse_aaquick_start.html)

---

### Post by sydbat on 2008-12-08
Thanks.

---

### Post by drubin on 2008-12-08
> **aysiu said:**
> I agree with bodhi.zazen.

Discussions about viruses and anti-viruses distract from discussions about *real security measures* and *real security threats*.

I agree. Users are the biggest cause of Security issues... :(

---

### Post by Yownanymous on 2008-12-08
> **Grant A. said:**
> Then why do Macs with an 8% market share only have 2 viruses compared to Linux's 34?

Cause they couldn't even get viruses to work on Macs, let alone many apps!:p

---

### Post by sportscrazed2 on 2008-12-08
i don't think you really have to worry about viruses if you are just using add/remove programs to get programs

---

### Post by tsali on 2008-12-08
> There are essentially 3 tools:

NIDS - Network Intrusion Detection is snort or wireshark. These tools monitor network traffic.

HIDS - Host based intrusion detection. OSSEC, tripwire, tiger, etc (antivirus scanning world also be an example).

AC or access control. This is a security system that limits users or applications access to system files and, IMO, is like standard permissions on steroids. Examples include Apparmor (which is default on Ubuntu) and SELinux.


Ok, so now you have to make these tools Suzy Soccermom simple...how do we do that? Otherwise, your exhortation is lost on the vast majority of desktop users...

Having seen the guts of these, I can assure you that Joe Dirt will lose interest in about 45 seconds...

You've gotta put a nice face on it with comprehensible indicators and controls. Can you make it effective yet completely transparent to users?

As far as Apparmor goes...from what I can tell, a program's installer can also install an associated Apparmor profile.

I suppose you really have to trust whoever wrote that installer.

---

### Post by bodhi.zazen on 2008-12-08
> **tsali said:**
> Ok, so now you have to make these tools Suzy Soccermom simple...how do we do that? Otherwise, your exhortation is lost on the vast majority of desktop users...

Why does everyone think security needs to be dumbed down ?

Everyone, including Suzy Soccermom, can run their machine they way she sees fit.

If you, Suzy Soccermom, or anyone else wishes to learn security, then they need to be committed to exactly that.

Security is a process and will remain so for the foreseeable future. The question is not how can we dumb down security, but rather how can we encourage and teach it's use.

If noting else, Windows has shown us what happens when we dumb things down.

---

### Post by tsali on 2008-12-08
> Why does everyone think security needs to be dumbed down ?

Everyone, including Suzy Soccermom, can run their machine they way she sees fit.

If you, Suzy Soccermom, or anyone else wishes to learn security, then they need to be committed to exactly that.

Security is a process and will remain so for the foreseeable future. The question is not how can we dumb down security, but rather how can we encourage and teach it's use.

If noting else, Windows has shown us what happens when we dumb things down.


It needs to made simple...that's quite different from being "dumbed down".

I suppose we'd all still be driving cars with manual transmissions, hand-crank starters and manual spark advance if we approached driving automobiles this way. Next time you get in your car, I want you to think real hard about EXACTLY what that ignition control computer is doing for you before you ever turn the key...and if you have to admit that you don't know everything it's doing, GET OUT AND WALK because you aren't qualified to drive that car. YOU AREN'T COMMITTED to learning how to drive your car.

Using your argument, all drivers would demonstrate their commitment to safety by going to F1 school...why should we be wasting our time with anti-lock brakes, stability control and air-bags?

You can keep security in your basement if you want to...but I'm glad there are others out there who will have the vision to make security available to everyone on terms they are able to manage...just as they have done with so many other computer capabilities.

---

### Post by bodhi.zazen on 2008-12-09
> **tsali said:**
> It needs to made simple...that's quite different from being "dumbed down".

I suppose we'd all still be driving cars with manual transmissions, hand-crank starters and manual spark advance if we approached driving automobiles this way. Next time you get in your car, I want you to think real hard about EXACTLY what that ignition control computer is doing for you before you ever turn the key...and if you have to admit that you don't know everything it's doing, GET OUT AND WALK because you aren't qualified to drive that car. YOU AREN'T COMMITTED to learning how to drive your car.

Using your argument, all drivers would demonstrate their commitment to safety by going to F1 school...why should we be wasting our time with anti-lock brakes, stability control and air-bags?

You can keep security in your basement if you want to...but I'm glad there are others out there who will have the vision to make security available to everyone on terms they are able to manage...just as they have done with so many other computer capabilities.

First, why are you so hostile ? All of the security tools I have mentioned are under development and all are improving.

Starting with a "default installation" of any OS, security is improving, and will likely continue to improve.

But along with these improvements, crackers have also become more sophisticated.

Security will always be a game of "cat and mouse" this way.

Starting with SELinux, yes SELinux is a very advanced and sophisticated tool. If you install Fedora 10 it is all pre-installed and pre-configured. How much easier is that ? If you have not used or looked at using SELinux, or try Fedora 10, you will see the tools to manage SELinux have also become more user friendly.

If SELinux is "too hard", well that is why apparmor was designed. Apparmor is also a fairly advanced tool, but it is easier to use then SELinux.

OSSEC is also easy to install and it pretty much runs itself with very little input from the user.

Snort is a little harder.

I do not know why you are talking about cars, but keeping the conversation to the current state of affairs:

1. Default installations of all OS are increasing security. If you feel a default installation is "secure enough" for your needs, more power to you.

2. If you wish to increase security further, with any OS, it takes some effort. There is no "turn key" solution to security as of yet. Install it and forget it security technology does not yet exist. So the questions are how much time do you wish to spend increasing security and what are the available tools? This is what I am here to assist with, helping people learn to use some of the available tools.

3. SELinux, Apparmor, OSSEC, etc are all under development and are all becoming easier and easier to use.

So if you choose to stay with a default installation and feel it is secure enough for your needs, that is fine with me. If you wish to learn some additional tips and tricks, I will help if I can.

Either way, there is no need for you to rant.

I suggest you implement what you feel are simple, "turn key" solutions. This might include encryption (now default on Ubuntu), improving the quality of your passwords, adding a router (if you do not have one), using ufw (gufw if you do not wish to use a command line tool).

If you wish to put in a little more effort take a look at OSSEC and or appramor. Both tools are relatively easy to install and use.

Increasing security is a spectrum of activity and a trade off between convenience and security. Security is different on servers then desktops, wireless vs wired, etc. Decide where you are personally on the spectrum and go with it (again no need to rant).

If you need assistance, you know where to look.

---

### Post by aysiu on 2008-12-09
The car analogy is faulty.

The car starting has one ideal path to achievement.

There is no one ideal path to computer security. If there were, then it would make sense for it to be out of the user's hands. As it is now, whether you're using Windows, Mac, or Linux, you as the user are the main security hole or strength of your computer.

If you do want to talk about car *security*, think about theft instead of collision safety. No one worries about a computer crashing into another computer. People do, however, worry about their cars being broken into or stolen.

The way many computer users run their computers from a "security" standpoint is the equivalent of handing your car keys and title over to anyone who asks (not even a bonafide valet).

---

### Post by sydbat on 2008-12-09
A great sentiment bodhi.zazen. However, I agree a *bit* more with tsali - simplifying may not be what you and I expect (or most people who use GNU/Linux), but Joe Average has no clue and education only works if people are willing to learn.

Case in point - our new church secretary called me this morning asking about computer related things (the pastor knows I work with computers). When I asked her what operating system she was using, she asked 'what is that?". People really have no clue how things work...especially computers! I then asked what version of Windows. She actually thought the OS I asked about first was a program of some sort. She was willing to hear what I told her and understood a bit more, but I deal with people everyday who do not listen, who do not want to learn. They just want their computer to work without knowing anything. This is the reality. 

The pastor asked me if I could build a box for the church 2 years ago, and by the time I quoted a price (not even a day later) someone who "knew better" had already decided to go out and buy one pre-configured with Vista, which cost almost 3 times as much as the one I would have built...and they have had nothing but problems with it (I do not support their computers anymore).

Sorry for the rant, but most people *think* they know what their computer does and how secure it is, when the reality is they have very little knowledge. And, as I stated, most people do not want to learn because they already think they know and see input as either arrogant interference or that they simply know better. I mean, look at all the "Linux is not ready" or "Why windows is better for users" threads on this forum.

And aysiu is correct about the car analogy being a bit off. Securing the car would have worked batter for this discussion.

---

### Post by aysiu on 2008-12-09
It's true many people don't want to learn how to secure their computers, but I think that actually supports bodhi.zazen's point. The software programming and defaults can secure the computer only to a certain degree. After that, it's up to an educated user to keep things secure through good practice.

If people don't want to learn good practices, they can't expect their computers to remain secure.

---

### Post by sydbat on 2008-12-09
> **aysiu said:**
> It's true many people don't want to learn how to secure their computers, but I think that actually supports bodhi.zazen's point. The software programming and defaults can secure the computer only to a certain degree. After that, it's up to an educated user to keep things secure through good practice.

If people don't want to learn good practices, they can't expect their computers to remain secure.Absolutely. That was (I hope) where I was going.

So the question then becomes - at what point do we begin educating people about proper security? I think it should start in school, as soon as kids sit down in front of their first computer. It should be continued throughout their school years, but not too heavy handed or they might rebel against it...just enough, like spelling or math. Then there might be hope.

---

### Post by aysiu on 2008-12-09
> **sydbat said:**
> Absolutely. That was (I hope) where I was going.

So the question then becomes - at what point do we begin educating people about proper security? I think it should start in school, as soon as kids sit down in front of their first computer. It should be continued throughout their school years, but not too heavy handed or they might rebel against it...just enough, like spelling or math. Then there might be hope.
That's a very good question. I'm not sure where it should begin. I think the whole culture needs to change. Right now there's definitely a widespread culture of "computer are these mysterious things, and I don't really need to know how to secure them or keep them running well." That culture needs to shift. Schooling can be one part of that shift.

---

### Post by nvteighen on 2008-12-10
> **aysiu said:**
> That's a very good question. I'm not sure where it should begin. I think the whole culture needs to change. Right now there's definitely a widespread culture of "computer are these mysterious things, and I don't really need to know how to secure them or keep them running well." That culture needs to shift. Schooling can be one part of that shift.
That's a bit because of the (in a historical sense) recent massification of computers... At the beginning these problems didn't exist because only computer scientists had computers... now it's different and only time will give people consciousness on what a computer is and how it works (at least conceptually).

---

### Post by hyper_ch on 2008-12-10
don't forget that there's also a massive industry telling john doe that they will never ever have a chance of comprehend what's actually going on and that they shouldn't even try to because they will fail epicly.

---

### Post by aysiu on 2008-12-10
> **hyper_ch said:**
> don't forget that there's also a massive industry telling john doe that they will never ever have a chance of comprehend what's actually going on and that they shouldn't even try to because they will fail epicly.
And if you just buy this anti-malware product and that one, you'll be secure.

---

### Post by tsali on 2008-12-10
What I tend to get a bit testy about is a general sense of "elitism" demonstrated by a lot of linux users.

1) Linux is great and it's a lazy user who has issues with it.

2) Users who choose other options, e.g. Windows or Mac are just too stupid or too lazy to know better and deserve what they get.

I won't mind saying that I absolutely HATE this attitude and I think it demonstrates ignorance on the part of the person who holds it.

It would be like a bunch of pro footballers sitting around complaining that the sandlot team they keep smashing is just too lazy and too stupid to do better.

Most people have REAL LIVES that don't revolved around screwing with a computer. I actually envy these folks because I spend WAY too much time messing with mine.

Those people are neither stupid not lazy. They are great doctors, lawyers and teachers.

I respect what they do so much that I think attitudes that want to subjugate them to someone else's idea of "intelligence" and "industriousness" is an absolute sin.

My heroes are those developers that work to find a way for regular people to be able to enjoy technology in a SAFE and SECURE way that lets them be the better people THEY choose to be. I think those developers who insist on molding everyone to serve their beloved software have a serious inversion problem.

Don't try to tell me that configuring SELinux will "build character" when I could be using that time to help kids at church.

This is why I am a fan of Microsoft and Apple. They brought computing to people who would never have been able to leverage its power otherwise. That is happening with Ubuntu.

---

### Post by BGFG on 2008-12-10
> **Skripka said:**
> ***_"Why GNU/Linux Viruses are fairly uncommon" from Charlie Harvey_***
evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1)

Will always be funny as ever! :) And people still don't get why we use the OS for geeks :lolflag:
May someone have mercy on their system32

---

### Post by BGFG on 2008-12-10
> **tsali said:**
> What I tend to get a bit testy about is a general sense of "elitism" demonstrated by a lot of linux users.

1) Linux is great and it's a lazy user who has issues with it.

2) Users who choose other options, e.g. Windows or Mac are just too stupid or too lazy to know better and deserve what they get.

I won't mind saying that I absolutely HATE this attitude and I think it demonstrates ignorance on the part of the person who holds it.

It would be like a bunch of pro footballers sitting around complaining that the sandlot team they keep smashing is just too lazy and too stupid to do better.

Most people have REAL LIVES that don't revolved around screwing with a computer. I actually envy these folks because I spend WAY too much time messing with mine.

Those people are neither stupid not lazy. They are great doctors, lawyers and teachers.

I respect what they do so much that I think attitudes that want to subjugate them to someone else's idea of "intelligence" and "industriousness" is an absolute sin.

My heroes are those developers that work to find a way for regular people to be able to enjoy technology in a SAFE and SECURE way that lets them be the better people THEY choose to be. I think those developers who insist on molding everyone to serve their beloved software have a serious inversion problem.

Don't try to tell me that configuring SELinux will "build character" when I could be using that time to help kids at church.

This is why I am a fan of Microsoft and Apple. They brought computing to people who would never have been able to leverage its power otherwise. That is happening with Ubuntu.

I agree and disagree with you . many times it's just user inexperience and many time is is in fact laziness. I believe that each case should be measured on it's own merit.

Something such as, "i downloaded the .deb now what do i do ?" , What is one to think ? You managed to download ubuntu, successfully navigate the install, figure out the need to find a .deb file for your program of choice, but are now in a quandary as to the way forward ? REALLY ?

And lets be rid of this 'real lives' thing. As i sit and post to you all, I am very real and have simply chosen to make linux and these forums an integral part of my life. That is it.

No one gets to tell me that chatting with people across the globe and learning with them and educating each other is not a worthwhile enterprise... 
I hike, play football, chase women, study, work, drink, live , love....etcetera, etcetera, etcetera.....and dude: I linux.

Anyways, i don't know what the tone of the thread was before, i just read your post and though i'd say hello :)

---

### Post by ranch hand on 2008-12-10
BGFG  thanks for that.

I know the biggest threat to my box and I am not going to quit using it to make it more secure.

As a ranch hand, I feel that my life is just about as real as it gets.  I also need to know the general principles that a wide variety of machines and animals run on.

I am new to linux and I need to learn it too.

I am not interested in a simple solution.  Simple solutions is what has ruined MS as a viable OS builder.  I don't have the time to give myself authorization to authorize myself to do something.  This is silly.  It may make people feel secure but  it does not make them so.

Education on how to secure your machine, as I see it, is no for the linux user than the user of any other OS.  It is up to the user.  The job that MAC and MS have done is only good to a point because they have fostered the idea that security comes as a magic package frome the internet or on a CD.

We are remote here and if there is a wild fire or medical emergency WE are the first responders, ahead of anyone else by at  least an hour if not 2 or 3.  This may give me a little different veiw.

---

### Post by Dragonbite on 2008-12-11
> **tsali said:**
> What I tend to get a bit testy about is a general sense of "elitism" demonstrated by a lot of linux users.

1) Linux is great and it's a lazy user who has issues with it.

2) Users who choose other options, e.g. Windows or Mac are just too stupid or too lazy to know better and deserve what they get.

I won't mind saying that I absolutely HATE this attitude and I think it demonstrates ignorance on the part of the person who holds it.

It **is** annoying to run across this, and I find this attitude shows up in all camps in one form or another.

> **tsali said:**
> Most people have REAL LIVES that don't revolved around screwing with a computer. I actually envy these folks because I spend WAY too much time messing with mine.

That's why I decided upon Ubuntu (out of all of the Linux distributions and Windows) for my home computers, so I can spend less time working ON the computer and more time working WITH the computer in various endeavors.

> **tsali said:**
> 

Those people are neither stupid not lazy. They are great doctors, lawyers and teachers.

I respect what they do so much that I think attitudes that want to subjugate them to someone else's idea of "intelligence" and "industriousness" is an absolute sin.

Everybody is intelligent but in their own interest or focus.  I don't fathom to know as much as a doctor does about Medicine but I can beat at least some of them on computers.

My wife is an artist who can draw circles around a LOT of people (pun intended) but on a computer ... well, let's just say she's mentioned she's lucky I'm into computers.  

She is very intelligent in many ways but nobody is intelligent in ALL ways.  So I try and respect that.

> **tsali said:**
> This is why I am a fan of Microsoft and Apple. They brought computing to people who would never have been able to leverage its power otherwise. That is happening with Ubuntu.

Personally, I do not have an issue with Microsoft or Apple, just not their desktop products and some of their philosophies/business models.

---

### Post by bodhi.zazen on 2008-12-11
> **aysiu said:**
> That's a very good question. I'm not sure where it should begin. I think the whole culture needs to change. Right now there's definitely a widespread culture of "computer are these mysterious things, and I don't really need to know how to secure them or keep them running well." That culture needs to shift. Schooling can be one part of that shift.

Along these lines I would like to make a clarification.

We are volunteers on these forums providing information and empowering people. As has been pointed out in this thread, security and security tools are not simple.

This is not the same as saying they are beyond understanding and we are here to promote education and awareness. By providing information I feel we are empowering people and I have a hard time viewing the process as elitism.

I would also like to point out that security does not need to be complex. Many of the suggestions in [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") are easy to understand and implement.

I also have to disagree with the idea that SELinux is difficult to implement. I suggest you install Fedora 10 if you would like to try it out. SELinux is installed and enabled by default and is for the most part invisible to end users.

It is true, in the past, SELinux was not so easy to use, and was often disabled, but it has improved greatly in the last year and again I suggest you try it. I think you would be surrised at how much has been accomplished with SELinux in Fedora, the GUI tools are much nicer.

Now if you are wanting to learn how to configure some of the more obtuse security tools such as wireshark, snort, iptables, SELinux, Apparmor, etc yes it will take some effort. This is where we, on the Ubutnu forums are here to help.

And really, that is all we can do. Raise the level of security awareness and educate.

If my willingness to educate makes me an elitist, then so be it. But really any kind of install it and forget it posture with security will lead to a false sense of security.

---

### Post by Changturkey on 2008-12-11
SElinux doesn't like VLC, Xine...

---

### Post by CholericKoala on 2008-12-11
Hmmmm.  Might this be compared to forms of government?  Before social security and welfare formed in the 1930's, people were not dying in the streets.  There were private organizations that helped out the poor, and people, for the most part, knew how to manage their own money.  The US is becoming more socialist (and this is not a political post, just an analogy) and the government is taking on more responsiblity for things that the average person has a brain for.

As a point that has been used many times in this thread already, computers are not terribly difficult things to manage, especially with all the gui candy we have nowadays.  The more operating systems regulate user activity, the more "socialist" they get in order to do what the users "can't" do.  The only problem with that is that the users can discern between a flashing virus and legitimate, widely-used program.

In other, more succinct words, the more regulated an operating system is, the less freedom and potential customability there is.  Users can keep themselves free from malware and it is silly to say that we *need* a corporation to do it for us.

---

### Post by halovivek on 2008-12-18
I really thanks all people for valuable reply.:guitar:  Thank you):P so much for all. I never expected i will get this much replies in this thread.:lolflag:

---

### Post by niponbharali on 2011-04-21
Whatever may be linux is more secure than other OS till now.But,we cannot say about future

---

### Post by brpylko on 2011-04-21
Linux TENDS to not have AS MANY viruses because it is not as widely used, smae reason for Mac, and also most hackers have experiencs with windoze and don't want to switch.

---

### Post by Elfy on 2011-04-21
Closed.

Necro'd thread.

---

### Post by Quadunit404 on 2011-04-21
Hmm, for a closed thread I still seem to be able to reply ;)

---

### Post by spook1980 on 2011-04-21
so this thread is closed right?

---

### Post by aysiu on 2011-04-21
> **spook1980 said:**
> so this thread is closed right?
Yes.

---

### Post by Elfy on 2011-04-21
Thank you aysiu - kettle boiled just at the wrong time.

---

