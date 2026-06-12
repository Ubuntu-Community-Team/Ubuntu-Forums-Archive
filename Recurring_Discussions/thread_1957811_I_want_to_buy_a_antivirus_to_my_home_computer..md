---
title: "I want to buy a antivirus to my home computer."
date: 2012-04-13
forum: Recurring Discussions
---

### Post by jaho22 on 2012-04-13
I want to buy antivirus for av and email, to my java developing hobby, i want to try sell few copy of my games.

What antivirus you recommend for my java developing.

I know AVG F-PROT and F-SECURE is there any other.

What is the best choice for small business and why.

---

### Post by kc1di on 2012-04-13
a couple questions is this going to be a linux install or other O.S. platform?

Is it a network or single machine?

---

### Post by jaho22 on 2012-04-13
AV and EMail scanners will be set to my home developing computer, my home developing computer will be ssh connected to my server where my java games are no other ports other than email are allowed on iptables.

I will make myself a single computer with no browser or any other program use, just eclipse and gimp and inkscape for developing java games and an ssh hole to my server to update my games on net.

I will use Ubuntu 12.04 on my developing computer and Ubuntu 10.04 on server.

---

### Post by Lars Noodén on 2012-04-13
I would start with [ClamAV](http://www.clamav.net/lang/en/) and work from there.  It will detect all kinds of malware.

---

### Post by iisjman07 on 2012-04-13
I'd recommend ESET Antivirus; it's got very good detection rates and minimal computer performance impact. It's available on Linux (including an on-access scanner), OS X & Windows, so you can use any operating system you like for you development. It's also really easy to install in linux, all you do is mark the installer file as an executable and it'll give you a lovely GUI.

---

### Post by roelforg on 2012-04-13
Why pay?
 
DrWeb is good and free.

---

### Post by iisjman07 on 2012-04-13
> **roelforg said:**
> DrWeb is good and free.

[http://estore.drweb.com/linux/]("http://estore.drweb.com/linux/") - this says it costs 18,90 EURO...

---

### Post by kc1di on 2012-04-13
> **roelforg said:**
> Why pay?
 
DrWeb is good and free.

Not free for business machines which this would be. 

I think that I would go with bitdefender I've used it on my linux installs in the past and it's work very well clam AV is ok and avast makes a good one for linux also. Here's a review of various AV software for Linux;

[http://www.makeuseof.com/tag/free-linux-antivirus-programs/]("http://www.makeuseof.com/tag/free-linux-antivirus-programs/")

---

### Post by haqking on 2012-04-13
AV for linux is only any good for scanning for file sharing with Windows as there are no current viruses in the wild which effect Linux.

If there was (which there could easily be) the current solutions would not combat them anyways.

If you want a scanner for Linux then clamAV will do the job for the most part, its free, easy and fairly light on resources and will combat most infections which you may pass on.

Though as with all AV false positives and false negatives appear.

Best AV is user habits.

For security in general Good browsing habits, apparmor, strong inbound/outbound firewall rules, NOscript etc

The ubuntu security wiki link in my signature is a good start

Peace

---

### Post by Hungry Man on 2012-04-13
I agree with haqking. Set up a strong password for sudo and use apparmor. That should be fine. An AV isn't going to help much.

---

### Post by 0011235813 on 2012-04-13
AV is worthless FUD propagated by antivirus companies so that they can make money by ripping people off. Save your money! AV is a highly ineffective solution to combat modern threats. AV is pointless if you're installing from the repositories, and the threats you have to worry about are web based, which means WOT, NoScript, Apparmor, Adblock etc. Plus good browser settings, like disabling third party cookies. The world is moving towards the Internet, and ultimately, the Internet clients like browsers and email will be more important to security than the OS. Some people have tried to make malware for Linux, and they've all failed. It's all either proof of concept and harmless, or extinct. But I'm not so sure about our incompetent plug-in developers, like Adobe Flash (which HTML5 will hopefully replace, if not, Lightspark will probably gain attention) and Java (which you probably don't need) . My biggest worry is JavaScript, but zero day exploits using JS are actually quite rare, so that isn't as big a problem.

---

### Post by Ms. Daisy on 2012-04-13
>  Some people have tried to make malware for Linux, and they've all failed. 
 Please provide a source for that fact.

---

### Post by 0011235813 on 2012-04-13
> **Ms. Daisy said:**
> Please provide a source for that fact.

Let's put it the other way; can you cite any reliable sources that show the existence of any serious (not proof-of-concept and harmless) modern day (that is, not extinct 5 years ago) malware for Linux in the wild (not in a lab) ?


It's harder to prove a negative, but I'll give it a go...


[https://en.wikipedia.org/wiki/Linux_malware#Threats](https://en.wikipedia.org/wiki/Linux_malware#Threats) you will find all of them are proof of concept or extinct... And [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by haqking on 2012-04-13
> **0011235813 said:**
> Let's put it the other way; can you cite any reliable sources that show the existence of any serious (not proof-of-concept and harmless) modern day (that is, not extinct 5 years ago) malware for Linux in the wild (not in a lab) ?


It's harder to prove a negative, but I'll give it a go...


[https://en.wikipedia.org/wiki/Linux_malware#Threats](https://en.wikipedia.org/wiki/Linux_malware#Threats) you will find all of them are proof of concept or extinct... And [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

kbeast as a quick one, well known rootkit.

not to mention the various keyloggers out there.

I could dig out more but cant be bothered to go off and find links right now ;-)

oh there was the unreal IRC daemon trojan thing about a 2 years ago as another

Peace

---

### Post by 0011235813 on 2012-04-13
> **haqking said:**
> kbeast as a quick one, well known rootkit.

not to mention the various keyloggers out there.

I could dig out more but cant be bothered to go off and find links right now ;-)

oh there was the unreal IRC daemon trojan thing about a 2 years ago as another

Peace

LOL that is **also** a proof of concept rootkit that only effects kernel 2! [http://ipsecs.com/web/?p=277](http://ipsecs.com/web/?p=277)
And no it's not in the wild, since it requires you to manually download, and go through complex installation procedures to install, so it's not really a danger to anyone, failing to meet all of my criteria. Very interesting though, tell me if you find any more interesting stuff ;)


I'd be curious about the keyloggers, I haven't found any dangerous ones in the wild.


Also extinct [http://www.bit-tech.net/news/bits/2010/06/14/linux-irc-daemon-trojan/1](http://www.bit-tech.net/news/bits/2010/06/14/linux-irc-daemon-trojan/1), and the repositories nor the official site was infected, only an external mirror.

---

### Post by haqking on 2012-04-13
> **0011235813 said:**
> LOL that is **also** a proof of concept rootkit that only effects kernel 2! [http://ipsecs.com/web/?p=277](http://ipsecs.com/web/?p=277)
And no it's not in the wild, since it requires you to manually download, and go through complex installation procedures to install, so it's not really a danger to anyone, failing to meet all of my criteria. Very interesting though, tell me if you find any more interesting stuff ;)


I'd be curious about the keyloggers, I haven't found any dangerous ones in the wild.


Also extinct [http://www.bit-tech.net/news/bits/2010/06/14/linux-irc-daemon-trojan/1](http://www.bit-tech.net/news/bits/2010/06/14/linux-irc-daemon-trojan/1), and the repositories nor the official site was infected, only an external mirror.

well in the wild usually refers to viruses (due to propogation), keyloggers and rootkits and other malware can still effect a Linux box, i could go off and install a keylogger on a linux box right now, so still valid.

And many people are still using kernel 2x (I am on one laptop)

It sounds like you are saying Linux does not suffer from malware and by using Linux you are safe from malware, this isnt true.

Viruses yes (for the moment) but not all malware

---

### Post by 0011235813 on 2012-04-13
> **haqking said:**
> well in the wild usually refers to viruses (due to propogation), keyloggers and rootkits and other malware can still effect a Linux box, i could go off and install a keylogger on a linux box right now, so still valid.

And many people are still using kernel 2x (I am on one laptop)

It sounds like you are saying Linux does not suffer from malware and by using Linux you are safe from malware, this isnt true.

Viruses yes (for the moment) but not all malware
But I'm talking practically here, why on Earth would you go and deliberately install malware? It's really rather unrealistic. My definition of in the wild means that the malware is used as part of the social engineering scams people keep seeming to fall for, or worse still, embeded into web pages as plugins or JavaScript. Not on relatively obscure geek sites, where it clearly states "keylogger" or "rootkit" or whatever.  

I'm not saying Linux is immune to malware, and I'm only talking here in terms of executable programs and not web-based threats that could affect Linux.

PS: Saying a threat affects an old kernel version means the malware is extinct. That's like mentioning a piece of malware that only affects XP on a Windows 7 forum!

---

### Post by haqking on 2012-04-13
> **0011235813 said:**
> 

PS: Saying a threat affects an old kernel version means the malware is extinct. That's like mentioning a piece of malware that only affects XP on a Windows 7 forum!

yeah my bad i forgot everyone here was running the latest kernel, i mean nobody runs a 2.6x kernel anymore do they ;-)

Anyways im bowing out of this now and upgrading my kernel super quick so im safe....LOL

Peace

---

### Post by Ms. Daisy on 2012-04-13
It's like herding cats trying to argue with you. You originally said  that "Some people have tried to make malware for Linux, and they've all  failed. It's all either proof of concept and harmless, or extinct." and  that simply isn't true. Then you added the caveat "I'm not saying Linux  is immune to malware, and I'm only talking here in  terms of executable programs and not web-based threats that could affect  Linux."

I watched my pen testing instructor NOT fail to write Linux malware and  deliver it in an executable & through the browser.  It was in no way  harmless because it gave the attacker a shell on the victim.  It's  proof of concept but it's naive to believe that it's only the good guys  who can do it.  

It's one thing to say that it's unlikely to encounter malware targeting  Linux, because it is. I think that we actually agree on that point.   It's another thing to say that everyone failed at writing Linux malware,  because they did not.

I think I'm weary of this discussion as well. I'll let you have the last word, 0011235813.

---

### Post by Dangertux on 2012-04-13
> **0011235813 said:**
> But I'm talking practically here, why on Earth would you go and deliberately install malware? It's really rather unrealistic. My definition of in the wild means that the malware is used as part of the social engineering scams people keep seeming to fall for, or worse still, embeded into web pages as plugins or JavaScript. Not on relatively obscure geek sites, where it clearly states "keylogger" or "rootkit" or whatever.  

I'm not saying Linux is immune to malware, and I'm only talking here in terms of executable programs and not web-based threats that could affect Linux.

PS: Saying a threat affects an old kernel version means the malware is extinct. That's like mentioning a piece of malware that only affects XP on a Windows 7 forum!


Okay someone tagged me in on this one, and I can't resist these kinds of threads, so here we go.

First off, if you want to talk about "out of date kernels" you might want to check your facts. The 2.6 kernel is still the stable kernel for all enterprise class solutions, this includes RHEL , Ubuntu LTS (10.04) , Debian stable etc et al. That means that those systems would be vulnerable. Also -- most code that can be compiled on a 2.6.32x series kernel works just fine on a 3.3 series kernel. The kernel developers actually did something clever this time around and went for reverse compatibility.

Now that you want to talk about "recent" linux malware, let's talk about something that is not extinct.  Let's talk about phalanx and it's dozens of clones. You know the rootkit that was found on kernel.org's rig a few months ago? Here...Let me refresh your memory.

[http://www.theregister.co.uk/2011/08/31/linux_kernel_security_breach/](http://www.theregister.co.uk/2011/08/31/linux_kernel_security_breach/)

For the OP, if you want pay solutions for AV. McAfee makes some decent non-free solutions for linux. Otherwise bit-defender is pretty decent IMO.


Hope this helps.


P.S: A note on FUD since the poster I quoted it threw it around. FUD is the average level of ignorance of  the typical Linux desktop user multiplied by the incompetence of most OSS development groups divided by the potential that someone with absolutely no life will find a way to compromise either of the former two.

---

### Post by wacky_sung on 2012-04-13
[0011235813]("http://ubuntuforums.org/member.php?u=1505383")

---

### Post by Ms. Daisy on 2012-04-13
> **Dangertux said:**
> P.S: A note on FUD since the poster I quoted it threw it around. FUD is the average level of ignorance of  the typical Linux desktop user multiplied by the incompetence of most OSS development groups divided by the potential that someone with absolutely no life will find a way to compromise either of the former two.
I'm so glad to know the formula to calculate it :D

---

### Post by 0011235813 on 2012-04-14
> **haqking said:**
> yeah my bad i forgot everyone here was running the latest kernel, i mean nobody runs a 2.6x kernel anymore do they ;-)

Anyways im bowing out of this now and upgrading my kernel super quick so im safe....LOL

Peace
Of course people are still running 2.6, but it's a little unfair to name an exploit that has already been fixed as a current threat to the OS. Don't blame the kernel developers for not forcing people to upgrade the kernel!
> **Ms. Daisy said:**
> It's like herding cats trying to argue with you. You originally said  that "Some people have tried to make malware for Linux, and they've all  failed. It's all either proof of concept and harmless, or extinct." and  that simply isn't true. Then you added the caveat "I'm not saying Linux  is immune to malware, and I'm only talking here in  terms of executable programs and not web-based threats that could affect  Linux."

I watched my pen testing instructor NOT fail to write Linux malware and  deliver it in an executable & through the browser.  It was in no way  harmless because it gave the attacker a shell on the victim.  It's  proof of concept but it's naive to believe that it's only the good guys  who can do it.  

It's one thing to say that it's unlikely to encounter malware targeting  Linux, because it is. I think that we actually agree on that point.   It's another thing to say that everyone failed at writing Linux malware,  because they did not.

I think I'm weary of this discussion as well. I'll let you have the last word, 0011235813.
I think what I should have said was "Nobody has managed to create a Linux malware in the form of an executable file (.deb,.rpm,.sh,.tar.gz,.run etc) that has actively been used in social engineering scams". I never changed the criteria, that was what I meant to say in the first place. I clearly stated that web threats were a different matter, and anyway, why are we arguing over this? Social engineering scams are a trivial threat to the majority of users here, only naivete fall for them, but web-based threats that compromise systems without user interaction and with no warning are a completely different matter. The OP is wasting time and money on AV, as all of us have clearly stated, OP should be more concerned about hardening the browser and email client, not buying into AV company FUD.
> **Dangertux said:**
> Okay someone tagged me in on this one, and I can't resist these kinds of threads, so here we go.

First off, if you want to talk about "out of date kernels" you might want to check your facts. The 2.6 kernel is still the stable kernel for all enterprise class solutions, this includes RHEL , Ubuntu LTS (10.04) , Debian stable etc et al. That means that those systems would be vulnerable. Also -- most code that can be compiled on a 2.6.32x series kernel works just fine on a 3.3 series kernel. The kernel developers actually did something clever this time around and went for reverse compatibility.

Now that you want to talk about "recent" linux malware, let's talk about something that is not extinct.  Let's talk about phalanx and it's dozens of clones. You know the rootkit that was found on kernel.org's rig a few months ago? Here...Let me refresh your memory.

[http://www.theregister.co.uk/2011/08/31/linux_kernel_security_breach/](http://www.theregister.co.uk/2011/08/31/linux_kernel_security_breach/)

For the OP, if you want pay solutions for AV. McAfee makes some decent non-free solutions for linux. Otherwise bit-defender is pretty decent IMO.


Hope this helps.


P.S: A note on FUD since the poster I quoted it threw it around. FUD is the average level of ignorance of  the typical Linux desktop user multiplied by the incompetence of most OSS development groups divided by the potential that someone with absolutely no life will find a way to compromise either of the former two.
Many people are still running XP, and WIndows 7 Ultimate has an XP function in it. The distro makers are responsible, the kernel developers have done everything they can, they can't force people to use their kernel. Oh and that attack was a compromise on the kernels website, and has nothing to do with the OPs desktop client that we're talking about. I never said the Linux kernel was unbreakable, that would just be silly, what I meant to say, is that in a world where people get their software from screened repositories, it wouldn't make sense for a malware writer to target that platform through a non web-based threat, as how would he or she be able to distribute the malware?

---

### Post by wacky_sung on 2012-04-14
> **0011235813 said:**
> I think what I should have said was "Nobody has managed to create a Linux malware in the form of an executable file (.deb,.rpm,.sh,.tar.gz,.run etc) that has actively been used in social engineering scams".

What make you think it has never happened? You can never come to light till someone leak the cat out of the bag. Openbsd is a good example for a case study.

[FBI 'planted backdoor' in OpenBSD]("http://www.theregister.co.uk/2010/12/15/openbsd_backdoor_claim/")

---

### Post by 0011235813 on 2012-04-14
> **wacky_sung said:**
> What make you think it has never happened? You can never come to light till someone leak the cat out of the bag. Openbsd is a good example for a case study.

[FBI 'planted backdoor' in OpenBSD]("http://www.theregister.co.uk/2010/12/15/openbsd_backdoor_claim/")

And you managed to find an article that clearly states they have no evidence...
> Perry said he had waited until his ten year NDA with the FBI had expired before coming forward with the claims, which remain unsupported by secondary sources.
> Perry's allegations are being taken seriously even though they don't come alongside anything substantial by way of evidence.
Which was finally concluded by the fact that this alleged attack happened 10 years ago, which is extinct by anyone's measure;
> Former government contractor Gregory Perry, who helped develop the OpenBSD crypto framework a decade ago, claims that contractors were paid to insert backdoors into OpenBSD's IPSec stack around 10 years ago.

---

### Post by Dangertux on 2012-04-14
> **0011235813 said:**
> Of course people are still running 2.6, but it's a little unfair to name an exploit that has already been fixed as a current threat to the OS. Don't blame the kernel developers for not forcing people to upgrade the kernel!

I think what I should have said was "Nobody has managed to create a Linux malware in the form of an executable file (.deb,.rpm,.sh,.tar.gz,.run etc) that has actively been used in social engineering scams". I never changed the criteria, that was what I meant to say in the first place. I clearly stated that web threats were a different matter, and anyway, why are we arguing over this? Social engineering scams are a trivial threat to the majority of users here, only naivete fall for them, but web-based threats that compromise systems without user interaction and with no warning are a completely different matter. The OP is wasting time and money on AV, as all of us have clearly stated, OP should be more concerned about hardening the browser and email client, not buying into AV company FUD.

Many people are still running XP, and WIndows 7 Ultimate has an XP function in it. The distro makers are responsible, the kernel developers have done everything they can, they can't force people to use their kernel. Oh and that attack was a compromise on the kernels website, and has nothing to do with the OPs desktop client that we're talking about. I never said the Linux kernel was unbreakable, that would just be silly, what I meant to say, is that in a world where people get their software from screened repositories, it wouldn't make sense for a malware writer to target that platform through a non web-based threat, as how would he or she be able to distribute the malware?

Okay -- Let's take this another way, and this is all I'm going to say about this because you're being stubborn. 

First point of contention : executable file (.deb,.rpm,.sh,.tar.gz,.run etc)

- extensions mean NOTHING in linux, these are just for ease of use for the human aspect of the process. That being said, neither .deb's , .rpm's or .tar.gz's are actually exectuable. They are simply compression formats that contain executables (or source code, your homework, family photos, whatever...) They require something else to "unpack them" for instance dpkg, rpm , gzip etc..

- In terms of executables, like .exe in Windows you're wanting to talk about ELF files.

Now back to what you're talking about with the kernel. No you're wrong, I'm sorry. Most people , and businesses will want to run the latest STABLE kernel. Then again, from the popularity of this forum I assume they don't. So your point has some validity in this case. Still a threat to the current stable release would be considered more serious then a threat to the current development release. The reason being if you're fast-tracking with dev releases, you'll probably have a new kernel in a few weeks anyway. Which would limit your exposure.

Also : No kernel developers will not force those needing high stability to update to an unstable kernel. They would lose the little bit of market share that they do have, and Linux would no longer be taken very seriously in most enterprise circles (let's not forget Linux is a server OS ok?)

My point is you're advocating the right ideas but you're doing it in a silly way. I've said it many times AV is NOT security.

However, the OP wants to purchase an AV solution. We should recommend one. Whether or not Apparmor, and certain browser addons would be more beneficial then that are an irrellevancy. 

If you treat AV as the reactive measure that it is, it can still be incredibly effective (even on Linux boxes.)

Besides, the OP never said they weren't going to do those other things, just that they wanted AV.

Also -- You should update your signature : to not read this way "Want Security? Use the two browsers with the most vulnerabilities at the latest pwn2own"

Hope this helps.

P.S : This thread should make its way into recurring, it hasn't been on topic in two pages ;-)

---

### Post by wacky_sung on 2012-04-14
> **0011235813 said:**
> And you managed to find an article that clearly states they have no evidence...


Which was finally concluded by the fact that this alleged attack happened 10 years ago, which is extinct by anyone's measure;

Come and think about those that went unreported. 

Find out for yourself that even firefox addon and Google Chrome extension has removed those malicious addon/extension.

Nobody will write on their forehead and telling people his code is malicious.:lolflag::lolflag::lolflag:

---

### Post by 0011235813 on 2012-04-14
> **Dangertux said:**
> Okay -- Let's take this another way, and this is all I'm going to say about this because you're being stubborn. 

First point of contention : executable file (.deb,.rpm,.sh,.tar.gz,.run etc)

- extensions mean NOTHING in linux, these are just for ease of use for the human aspect of the process. That being said, neither .deb's , .rpm's or .tar.gz's are actually exectuable. They are simply compression formats that contain executables (or source code, your homework, family photos, whatever...) They require something else to "unpack them" for instance dpkg, rpm , gzip etc..

- In terms of executables, like .exe in Windows you're wanting to talk about ELF files.

Now back to what you're talking about with the kernel. No you're wrong, I'm sorry. Most people , and businesses will want to run the latest STABLE kernel. Then again, from the popularity of this forum I assume they don't. So your point has some validity in this case. Still a threat to the current stable release would be considered more serious then a threat to the current development release. The reason being if you're fast-tracking with dev releases, you'll probably have a new kernel in a few weeks anyway. Which would limit your exposure.

Also : No kernel developers will not force those needing high stability to update to an unstable kernel. They would lose the little bit of market share that they do have, and Linux would no longer be taken very seriously in most enterprise circles (let's not forget Linux is a server OS ok?)

My point is you're advocating the right ideas but you're doing it in a silly way. I've said it many times AV is NOT security.

However, the OP wants to purchase an AV solution. We should recommend one. Whether or not Apparmor, and certain browser addons would be more beneficial then that are an irrellevancy. 

If you treat AV as the reactive measure that it is, it can still be incredibly effective (even on Linux boxes.)

Besides, the OP never said they weren't going to do those other things, just that they wanted AV.

Also -- You should update your signature : to not read this way "Want Security? Use the two browsers with the most vulnerabilities at the latest pwn2own"

Hope this helps.

P.S : This thread should make its way into recurring, it hasn't been on topic in two pages ;-)
 As far as I'm aware, the only browsers that sandbox plugins effectively are Chrome and Opera. Firefox does not sandbox anything, Opera sandboxes plugins and extensions, and Chrome sandboxes just about everything. From a security perspective, these two make the most sense. You can clearly see they sandbox their processes by opening the system monitor. 
Oh and what you mean, by saying that .debs etc are compressed files, is really quite irrelevant. If a scam site wanted a Linux user to install malware, they would put it in the form of a .deb or .rpm or .aux etc. 

Also, can you cite the last point? I'm curious...

---

### Post by Dangertux on 2012-04-14
[http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own](http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own)

Yeah as you can see sandboxing and standard memory protections are trivial to bypass.

---

### Post by wacky_sung on 2012-04-14
> **0011235813 said:**
> As far as I'm aware, the only browsers that sandbox plugins effectively are Chrome and Opera. Firefox does not sandbox anything, Opera sandboxes plugins and extensions, and Chrome sandboxes just about everything. From a security perspective, these two make the most sense. You can clearly see they sandbox their processes by opening the system monitor. 
Oh and what you mean, by saying that .debs etc are compressed files, is really quite irrelevant. If a scam site wanted a Linux user to install malware, they would put it in the form of a .deb or .rpm or .aux etc. 

Also, can you cite the last point? I'm curious...

I do agree with Dangertux mentioned. A scam site do not require to install malware by put it in the form of a .deb or .rpm or .aux etc. What they need to use an exploit on the addon/extension/plugins to bypass the sandbox. You better do some reading for the how Google Chrome sandbox was broken exploit through flash in the [Pwn2Own]("http://thehackernews.com/2012/03/finally-google-chrome-gets-hacked-at.html"). Likewise for malwares to break in may not always come from exploit founds in the browser but the addon/extension/plugins it uses.

The point you have stated may only work in the past but it has moved more than what you mentioned.

---

### Post by haqking on 2012-04-14
to the OP

thread gone off track.

All the AV solutions mentioned are decent enough for your needs, there is malware that can effect Linux and does so use good habits and common sense.

The best defence for any system is the user and education.

Read the [Basic Ubuntu Security Wiki]("https://wiki.ubuntu.com/BasicSecurity") and the links from it.

Peace

---

### Post by CharlesA on 2012-04-14
> **haqking said:**
> 
Read the [Basic Ubuntu Security Wiki]("https://wiki.ubuntu.com/BasicSecurity") and the link from it.

+1. I use BitDefender on my file server for scanning files I share with Windows boxes, it does a decent job - a few false positives, but those are taken care of pretty easily.

---

### Post by 0011235813 on 2012-04-14
> **Dangertux said:**
> [http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own](http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own)

Yeah as you can see sandboxing and standard memory protections are trivial to bypass.

> **wacky_sung said:**
> I do agree with Dangertux mentioned. A scam site do not require to install malware by put it in the form of a .deb or .rpm or .aux etc. What they need to use an exploit on the addon/extension/plugins to bypass the sandbox. You better do some reading for the how Google Chrome sandbox was broken exploit through flash in the [Pwn2Own]("http://thehackernews.com/2012/03/finally-google-chrome-gets-hacked-at.html"). Likewise for malwares to break in may not always come from exploit founds in the browser but the addon/extension/plugins it uses.

The point you have stated may only work in the past but it has moved more than what you mentioned.
> **Dangertux said:**
> [http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own](http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own)

Yeah as you can see sandboxing and standard memory protections are trivial to bypass.
> . I can say that Chrome is one of the most secure browsers available.
:lolflag: You will also notice that the exploit targeted Flash, not Chrome, which doesn't bother me since I don't run plugins on untrusted sites, and that it happened in Windows, which might  not affect Linux. 
> **wacky_sung said:**
> I do agree with Dangertux mentioned. A scam site do not require to install malware by put it in the form of a .deb or .rpm or .aux etc. What they need to use an exploit on the addon/extension/plugins to bypass the sandbox. You better do some reading for the how Google Chrome sandbox was broken exploit through flash in the [Pwn2Own]("http://thehackernews.com/2012/03/finally-google-chrome-gets-hacked-at.html"). Likewise for malwares to break in may not always come from exploit founds in the browser but the addon/extension/plugins it uses.

The point you have stated may only work in the past but it has moved more than what you mentioned.
Please stop confusing extensions with plugins, it is not the same thing! And by the way, for any exploit to occur, code must be executed one way or another. Neither of you have mentioned Firefox doesn't have any sandboxing, so it would be pointless to scorn at Chrome for having a less-than-effective sandbox when Firefox itself doesn't even have it.

---

### Post by Hungry Man on 2012-04-14
> **Dangertux said:**
> [http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own](http://www.afterdawn.com/news/article.cfm/2012/03/08/google_chrome_hacked_in_minutes_at_pwn2own)

Yeah as you can see sandboxing and standard memory protections are trivial to bypass.

Don't be silly. It took them weeks to bypass IE9's sandbox, the Chrome bypass was lame and on the Flash sandbox (NPAPI) and also took them a lot of time. Those articles are incredibly misleading, they had a working exploit long before pwn2own so of course it took only a few minutes.

Also keep in mind that that's on Windows. 

The main fault of the Windows sandbox is that a kernel exploit will immediately bypass it. Linux doesn't have this fault (In Chrome), kernel attack surface is significantly reduced due to Seccomp filters, which Chrome is bundled in.

On top of this, the Windows Flash sandbox is **weak** and on Linux the sandbox is much much better (PPAPI) and is much more locked down.

I agree with everything else you've said in this topic though.

To talk about memory protections...

ASLR and DEP are incredibly effective. On Windows there's one bypass I know of that's likely universal, but we're talking about Linux. DEP + ASLR are very hard to bypass - every time you read about a "bypass" it's almost guaranteed to be a faulty implementation of DEP and/or ASLR (ie: opt out, not always on or not everything is randomized) and occasionally there's a heap spray or data leak.

---

### Post by uRock on 2012-04-14
> **0011235813 said:**
> Neither of you have mentioned Firefox doesn't have any sandboxing, so it would be pointless to scorn at Chrome for having a less-than-effective sandbox when Firefox itself doesn't even have it.

For that we have AppArmor.

---

### Post by Dangertux on 2012-04-14
> **Hungry Man said:**
> Don't be silly. It took them weeks to bypass IE9's sandbox, the Chrome bypass was lame and on the Flash sandbox (NPAPI) and also took them a lot of time. Those articles are incredibly misleading, they had a working exploit long before pwn2own so of course it took only a few minutes.

Also keep in mind that that's on Windows. 

The main fault of the Windows sandbox is that a kernel exploit will immediately bypass it. Linux doesn't have this fault (In Chrome), kernel attack surface is significantly reduced due to Seccomp filters, which Chrome is bundled in.

On top of this, the Windows Flash sandbox is **weak** and on Linux the sandbox is much much better (PPAPI) and is much more locked down.

I agree with everything else you've said in this topic though.

To talk about memory protections...

ASLR and DEP are incredibly effective. On Windows there's one bypass I know of that's likely universal, but we're talking about Linux. DEP + ASLR are very hard to bypass - every time you read about a "bypass" it's almost guaranteed to be a faulty implementation of DEP and/or ASLR (ie: opt out, not always on or not everything is randomized) and occasionally there's a heap spray or data leak.

If you're talking about the method published by WP  in Windows yeah it's pretty much universal, due to its ability to target completely position independent libraries. 

That being said, similar methods work in Linux with ret2plt etc...

But yes those articles can be misleading just like forum signatures that claim a browser by name is the most secure ;-)

Though I think google could have saved themself from some embarassment had they actually paid out for POC like they had in the past. Just a thought. Trivial might not have been the correct word, doable is maybe more accurate.

---

### Post by CharlesA on 2012-04-14
Moved to recurring because I have a feeling I know where this one will be going...

---

### Post by haqking on 2012-04-14
> **CharlesA said:**
> Moved to recurring because I have a feeling I know where this one will be going...

didnt it already get there ;-)

---

### Post by Hungry Man on 2012-04-14
Security can't be benchmarked. To say that Firefox is objectively less secure than Chrome would be silly - there is simply no way, Chrome could make use of all of the mitigation techniques int he world but if it manages its memory awfully than it won't matter, there'll be data leaks all over. All anyone can really do is evaluate the methods that they make use of in-depth. Firefox can make use of AppArmor, which is fairly strong. Chrome can make use of AppArmor and comes bundled with a SUID Chroot sandbox, it can also use Seccomp (I suggest any Chrome users reading go ahead and enable seccomp sandboxing.)

I'm more familiar with Windows issues than Linux but I'm quite certain that there are fixed libraries on all OS's - though not every library is going to be suitable for ROP, of course (you can write gadgetless libraries or compile for them, or the library just might not have what the attacker needs.) 

This topic has really gone off of its course though.

More relevant, I don't think AVs are worth it on Linux. If you're using package repositories on a trusted network you shouldn't have any issues (you can use synaptic package manager to transfer packages between networks and do offline installs, to ensure that they are not tampered with.) Increased code on the system = increased attack surface and complications.

---

### Post by 0011235813 on 2012-04-14
> **uRock said:**
> For that we have AppArmor.

...Which is complicated and requires a highly knowledgeable user to 
a.) Know it exists
b.) Know how to use it

So they can write complicated apparmor profiles. Chrome does this by default, and you could harden Chrome with apparmor as well (does anyone know how to do that?). My policy on this is
> If a third party created a (viable) solution for the security problem, then great. But that doesn't make the fault of the programmer any less real
So please, quit bashing Chrome for trying to be more secure.

---

### Post by CharlesA on 2012-04-14
> **haqking said:**
> didnt it already get there ;-)
Nope, it was still in the security area. ;)

But I can see what you mean. :p

---

### Post by haqking on 2012-04-14
> **Hungry Man said:**
> 
More relevant, I don't think AVs are worth it on Linux. If you're using package repositories on a trusted network you shouldn't have any issues (you can use synaptic package manager to transfer packages between networks and do offline installs, to ensure that they are not tampered with.)

well maybe not for Linux itself at this time, but if sharing files with windows users it can help prevent further propogation.

Thats the main reason to run it.

Peace

---

### Post by Hungry Man on 2012-04-14
Apparmor is trivial to set up (that's kinda the point over seccomp.) aa-autodep, aa-logprof. You can have a fully functional profile in no time, and Firefox comes with one already.

Chrome doesn't but Chromium does and you can translate it pretty easily and fill in the gaps with logprof.

---

### Post by Hungry Man on 2012-04-14
> **haqking said:**
> well maybe not for Linux itself at this time, but if sharing files with windows users it can help prevent further propogation.

Thats the main reason to run it.

Peace

True. This is why I'll sometimes recommend **users** to run an AV on Linux (though not usually, I more just mention it for their benefit) but on a server I see no reason as you shouldn't be emailing your friends potentially malicious files etc, it's a server.

---

### Post by CharlesA on 2012-04-14
> **Hungry Man said:**
> True. This is why I'll sometimes recommend **users** to run an AV on Linux (though not usually, I more just mention it for their benefit) but on a server I see no reason as you shouldn't be emailing your friends potentially malicious files etc, it's a server.

File server?

---

### Post by Hungry Man on 2012-04-14
I guess. If that's a feature you want to provide as a file server.

---

### Post by uRock on 2012-04-14
> **0011235813 said:**
> ...Which is complicated and requires a highly knowledgeable user to 
a.) Know it exists
b.) Know how to use it

So they can write complicated apparmor profiles. Chrome does this by default, and you could harden Chrome with apparmor as well (does anyone know how to do that?). My policy on this is

So please, quit bashing Chrome for trying to be more secure.

How is it so complicated? If Chrome is so secure, then why is there a default AppArmor profile running in enforce mode for it? Chrome is a security risk in itself. Imagine someone figuring out your gmail/G+ password and logging into Chrome with it. They will now have all of your passwords and screen names, which is why I stopped using Chrome and changed my G+ password to being more than 16 characters. Chrome is not a supported browser, which errors often, on a site I frequent daily.

---

### Post by 0011235813 on 2012-04-14
> **uRock said:**
> How is it so complicated? If Chrome is so secure, then why is there a default AppArmor profile running in enforce mode for it? Chrome is a security risk in itself. Imagine someone figuring out your gmail/G+ password and logging into Chrome with it. They will now have all of your passwords and screen names, which is why I stopped using Chrome and changed my G+ password to being more than 16 characters. Chrome is not a supported browser, which errors often, on a site I frequent daily.

Why is apparmor complicated? Clearly, you haven't been in much contact with the users I meet to say that. I couldn't imagine the average user writing apparmor profiles, and safe to say, I find it quite complicated, and I'm a geek. My grandma isn't going to make apparmor profiles, and neither is my dad, nor my mom, nor any of my friends. Who are non-technical. And the second bit doesn't really make much sense:
> If Chrome is so secure, then why is there a default AppArmor profile running in enforce mode for it?
If Firefox is so secure, why is there a default apparmor profile running in enforce mode for it? Because apparmor adds an additional layer of security and it would be silly not to include it. By the way, Chromium comes with an apparmor profile, not Chrome, just to prevent any confusion. 

What you are describing is an optional feature, nobody is making you use it. For that matter, Firefox and Opera both have a similar service, and Chrome's is the best developed IMO. PS, you can go to settings (In 17 or later, otherwise preferences) personal stuff, and tick "never remember passwords", and use a password manager like LastPass or KeePass. 

Really? I've surfed heavily, every day, on Chrome for years, and I've never encountered such a problem. What site are we talking about? And anyway, it doesn't matter since it's not Chrome's fault.

In any case, our experiences are both anecdotal, but clearly, if it has 25% of the marketshare, it's doing **something** right.

I don't understand all the anti-Google in here. I'm a huge Google fan, and I find it quite offensive. We should be grateful to the company that has managed to make Linux a mainstream mobile platform, and aided the kernel in the process.

---

### Post by Dangertux on 2012-04-14
I just want to point out something.

We have gone from the OP asking for an AV solution to a bunch of us rambling about browsers, memory protection mandatory access controls and everything else. I thimk i even saw something about formay string exploits in one of those posts. Now we are all on about who hates google and whatever else.

If you have ever read my posts you would know I am very much about security. However does anyone know if the OP even got an answer to THEIR question. 

Seriously, this is the kind of thing that makes people look at the linux community as a bunch of frothy mouthed lunatics who get riled up by the word malware...

Sad really...

---

### Post by Hungry Man on 2012-04-14
Apparmor is ridiculously easy to use and it's fairly automated (sudo aa-autodep firefox, sudo aa-logprof - that's enough to get you a profile in a few hours/ days (depending on the program).)

I think if you guys want to continue a topic about browsers (which is what this has become) you should make a new topic. If you want to discuss it in a security setting, make it in the security subforum, otherwise put it in a different one.

@Dangertux,

I think the OP's question has been answered a few times. I think AVs are only good for specific situations, in general they aren't very useful on Linux.

---

### Post by Dangertux on 2012-04-14
> **Hungry Man said:**
> Apparmor is ridiculously easy to use and it's fairly automated (sudo aa-autodep firefox, sudo aa-logprof - that's enough to get you a profile in a few days.)

I think if you guys want to continue a topic about browsers (which is what this has become) you should make a new topic. If you want to discuss it in a security setting, make it in the security subforum, otherwise put it in a different one.

@Dangertux,

I think the OP's question has been answered a few times. I think AVs are only good for specific situations, in general they aren't very useful on Linux.

I support this post! =)

---

### Post by wacky_sung on 2012-04-15
> **Hungry Man said:**
> @Dangertux,

I think the OP's question has been answered a few times. I think AVs are only good for specific situations, in general they aren't very useful on Linux.

Why you don't try to visit those malware infested sites without any antivirus or protection. I am very sure lamers like people of you.

Try to visit a few sites from below.
[Comodo Site Inspector Link]("http://siteinspector.comodo.com/public/recent_detections/index").

[[img]http://www.freeimagehosting.net/t/1a2gy.jpg[/img]](http://www.freeimagehosting.net/1a2gy)

---

### Post by nothingspecial on 2012-04-15
This thread no longer has anything to do with the original question. There are plenty of chrome vs firefox vs etc threads.

Closed

---

