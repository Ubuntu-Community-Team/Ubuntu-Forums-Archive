---
title: "Are bots a problem"
date: 2009-09-13
forum: Recurring Discussions
---

### Post by ex-wirecutter on 2009-09-13
I understand viruses are not a problem for Ubuntu , but what about bots ?
If they can be ignored why is someone distributing" bothunter " for Linux ?
Can they be detected by AV programs like AVG for Linux ?

---

### Post by Rob_H on 2009-09-13
Viruses and other malware (including botnet programs) that target Linux desktops are almost unheard of right now. The tiny market share of Linux on the desktop makes it an unappealing target for malware authors. The [BotHunter]("http://www.bothunter.net/") software you mentioned is designed to detect botnet activity emanating from *other* computers on a network, as far as I can tell.

---

### Post by falconindy on 2009-09-13
> **Rob_H said:**
> Viruses and other malware (including botnet programs) that target Linux desktops are almost unheard of right now. The tiny market share of Linux on the desktop makes it an unappealing target for malware authors. The [BotHunter]("http://www.bothunter.net/") software you mentioned is designed to detect botnet activity emanating from *other* computers on a network, as far as I can tell.
It's not so much the small market share as much as the security model used that makes linux so inhospitable to virii and other malware. In order to do anything malicious in linux, you need root access. Any malware that does make it into Linux will be the result of social engineering or poor judgement on behalf of a user.

---

### Post by Rob_H on 2009-09-13
> **falconindy said:**
> In order to do anything malicious in linux, you need root access. Any malware that does make it into Linux will be the result of social engineering or poor judgement on behalf of a user.

I disagree. That might be the case on a Linux *server*, but on a Linux *desktop*, the important stuff is generally the stuff in the home directory. You don't need to be root to mess with that.

---

### Post by Irvine_himself on 2009-09-13
Recently, I spent over a week digging out a backdoor Rootkit from a friends installation of XP that, among other things,  was running a spam bot. It had even planted a couple of data bombs to trigger re-infection! I did save  most of his data and  installed programs; but... the surgery was very extensive and when I had finished, the installation was so buggy I had to to do a repair-install to clean up.

His biggest problem was the way in which he browsed, he would blithely click  and download anything that looked flashy and alluring.

In the XP community, AVG does not have a good reputation and in my experience, people who are attracted to AVG are the same people who get infected. (I don't know why: mind-set, laziness, .... ???)

As far as Ubuntu is concerned, the perceived wisdom is that at the moment you don't have a lot to worry about. As a newbie recently migrating from XP, I find this a little bit blasé, it is only a matter of time. Having said that, if you install only from Official repositories, then you should not have anything to worry about.

---

### Post by The Cog on 2009-09-13
> **Irvine_himself said:**
> As far as Ubuntu is concerned, the perceived wisdom is that at the moment you don't have a lot to worry about. As a newbie recently migrating from XP, I find this a little bit blasé, it is only a matter of time.

Having been using Linux for almost a decade, it's hard to maintain that feeling it's only a matter of time without starting to feel a little bit blasé. It may be only a matter of time, but I think your prolonged contact with XP has imbued you with a rather fatalist attitude.

---

### Post by Irvine_himself on 2009-09-13
> **The Cog said:**
> I think your prolonged contact with XP has imbued you with a rather fatalist attitude.

Not really, It may be a heresy in the present environment but if you don't browse as Administrator, use a decent firewall with anti-virus protection and lock down the critical locations then, from a security perspective, XP is comparable to a generic Linux.

The real problem is human nature, the sheep will always be sheep no matter what OS they use and if the wolves can see an exploitable edge then they will take advantage of it.

At the moment, both Mac and Linux user reassure themselves with platitudes about how their low profile vis-a-vis Microsoft gives them a natural immunity to exploitation. The reality is that for the most part the low lying fruit has already been plucked, the bad guys are starting to look for new targets and 5% of the worlds personal computing market is still an awful lot of computers. 

That is without even getting into esoterica like attacking the Bios which recently had a proof of concept attack. 
(see [http://searchsecurity.techtarget.com/tip/0,289483,sid14_gci1359106,00.html](http://searchsecurity.techtarget.com/tip/0,289483,sid14_gci1359106,00.html))

I am not deliberately being provocative, I just have a very low opinion of human nature although I suppose some people would describe it as being a realist.

Ps

The article is on a subscription site, but if you switch off java script, you should be able to read all of it.

---

### Post by falconindy on 2009-09-13
> **Rob_H said:**
> I disagree. That might be the case on a Linux *server*, but on a Linux *desktop*, the important stuff is generally the stuff in the home directory. You don't need to be root to mess with that.
But see, this falls under my category of poor judgement. You should be keeping a backup of at **least** the contents of $HOME in case anything goes wrong (hard drive failure or otherwise). If you run the backup with root permissions, its unlikely anyone can act on the files maliciously. Really, this is the worst case scenario and its easy to prevent.

In my 7+ years of experience with WinXP, I never got a virus that I didn't deserve (downloading suspicious files of origins I won't divulge). Not once did I ever run anti-virus or anti-spyware software. A hardware firewall, adblock plus, noscript and (above all else) common sense are all you need.

---

### Post by atyler on 2009-09-13
I believe that .nix is inherently more secure vs. MS.  However, I also believe that it is certainly exploitable.  That said...

Clearly most malware is targeted toward MS and we're seeing an increasing percentage targeting Mac, which leads us to believe that user demographic may have more to do with targeting rather than technical platform.

I would suspect that the vast majority of .nix users are above average in terms of technical literacy and that (clearly) MS and Mac have garnered the "general user" population.

"General users" are (in my opinion) far more likely to click on the cool flashy link, or download the neat game that their friend IM'd them; whereas a .nix user is typically more technically-savvy and consequently less likely to infect the machine they're on.  I think this holds true regardless of which OS a .nix user is currently on.

So....long answer made short:

I don't think bots pose a significant concern on a .nix system.  One time that one may run into a bot problem is when your system is on a larger network that is infected thus compromising your network performance.  I'm sure there are other cases that could pose a problem, but my post is long enough as is.

---

### Post by __p1n__ on 2009-09-13
> **Irvine_himself said:**
> Not really, It may be a heresy in the present environment but if you don't browse as Administrator, use a decent firewall with anti-virus protection and lock down the critical locations then, **from a security perspective, XP is comparable to a generic Linux.**


This is patently untrue.  On a linux system a process requires privilege escalation to do anything (attach to a running process, r/w to anything, etc.)  On a windows system privilege escalation is unnecessary; threads can migrate to any running process, process memory is not isolated, win32 calls are unnecessary to execute the underlying microcode.

Windows a/v products (setting aside firewalls) which rely upon hooked win32 calls and a hooked pexec are actually wholly inadequate against modern malware which do not use these interfaces.  MS' recent (and flawed) attempts to implement various types of memory protection underscore this reality.

Regardless of user practices the relative security models of W2K (that's the original, shipped-with-29,000-critical-bugs core of all modern versions of windows) and linux don't even begin to compare.

---

### Post by jrusso2 on 2009-09-13
I would not get too cockey esp with this new breed of Linux users coming from Windows.

[http://www.itworld.com/security/77499/first-linux-botnet](http://www.itworld.com/security/77499/first-linux-botnet)


[http://www.linuxtoday.com/news_story.php3?ltsn=2009-09-13-007-39-SC-OO-SV](http://www.linuxtoday.com/news_story.php3?ltsn=2009-09-13-007-39-SC-OO-SV)


[http://lwn.net/Articles/222153/](http://lwn.net/Articles/222153/)


[http://linux.slashdot.org/story/09/09/12/1413246/First-Botnet-of-Linux-Web-Servers-Discovered?from=rss](http://linux.slashdot.org/story/09/09/12/1413246/First-Botnet-of-Linux-Web-Servers-Discovered?from=rss)

[http://it.slashdot.org/article.pl?sid=07/10/05/1234217](http://it.slashdot.org/article.pl?sid=07/10/05/1234217)

---

### Post by atyler on 2009-09-13
> Regardless of user practices the relative security models of W2K (that's the original, shipped-with-29,000-critical-bugs core of all modern versions of windows) and linux don't even begin to compare.

Agreed, but what is undeniable is that user behaviour accentuates the inherent security vulnerabilities in MS, and (dare I go so far to say?) hardens the relative security of .nix.

@jrusso2 - Good point.  At what point, though, will the Windows-user-influx reach critical mass?  In other words, when are there enough of the risk-prone users in the .nix world that they impact the overall security fabric in a significant way?

---

### Post by Sporkman on 2009-09-13
...or, you can have a perfectly good, secure OS, and have your modem or router hacked:

[http://www.theregister.co.uk/2009/03/24/psyb0t_home_networking_worm/](http://www.theregister.co.uk/2009/03/24/psyb0t_home_networking_worm/)

---

### Post by __p1n__ on 2009-09-13
There is a current local privilege-escalation exploit that affects linux systems.  Since it is possible in some cases to remotely induce a segmentation fault and inject shellcode into linux systems the aforementioned local exploit becomes a defacto remote exploit when it is the payload of the latter.  This is a serious vulnerability however it requires a compounding of factors to fully exploit.

Fanbois talk in terms of "their o/s" whatever it might be.  I'm gratified that the majority of discussion on this forum is either on specific technical items or best user practices.

---

### Post by falconindy on 2009-09-13
> **atyler said:**
> At what point, though, will the Windows-user-influx reach critical mass?  In other words, when are there enough of the risk-prone users in the .nix world that they impact the overall security fabric in a significant way?
The actions of cocky Windows users abusing their Linux installs has zero effect on the operating system from a security standpoint and it **certainly **doesn't affect my own security.

@jrusso2: See above. The articles you've listed show what happens when inexperienced users command operating systems such as Linux without truly understanding how they work and how to maintain them. The common thread in those articles seems to be one thing: exercising poor practice with password security.

---

### Post by movieman on 2009-09-13
> **__p1n__ said:**
> There is a current local privilege-escalation exploit that affects linux systems.

I think you mean _un-patched_ Linux systems with Wine, pulseaudio or SELinux installed... it was fixed within a few days of being found.

And I'm sure there are plenty of such exploits in Windows.

---

### Post by Ravernomina on 2009-09-13
ANy type of male ware can get into any computer with easy if their is no security taken. More or less keeping your internet tracks hidden along with monitoring all network traffic. But an exploit is WAY to common in any OS. This is one of the reasons apple left X86 and went to a x86_64 bit kernel to get rid of over 50% (3 viruses) away from a Mac OS. Along with Better security sense 64bit natively has more security and you need a 64bit virus to run As well. Along with this a Secure virtual memory along with a patched Kernel OS and File system can also make a Great security net. Also a Encrypted Data can help as well. A good Firewall that will also not respond to being Pinged Is also really good as well. Over all out of my banter basically states is that if u know ur Computer stuff ur fine.

In my opinion this is what i do for great security

_For a UNIX OS._

Running 64 bit or running 32 bit with secured virtual memory.

Make sure u Have a Firewall and Make sure the settings are to what u need.

Have A rootkit scanning software to make sure all hacking cannot go on

Make Sure u cannot be pinged as this can stop botting by a lot

Back up your hard Disc every 1-2 weeks

Do not Fall for the stupid crap on the internet or advertisements.

---

### Post by __p1n__ on 2009-09-13
> **movieman said:**
> I think you mean _un-patched_ Linux systems with Wine, pulseaudio or SELinux installed... it was fixed within a few days of being found.

And I'm sure there are plenty of such exploits in Windows.

I'm referring to CVE-2009-2698 which should not be a problem if you're running 2.6.19 (a very old kernel) or higher.  Wine and pulseaudio are not prereqs; a variation of the exploit directly circumvented SELinux however that was strictly unnecessary inasmuch as SELinux enforcement can be trivally disabled by a process with superuser privileges.

On a linux system a process requires privilege escalation to do anything outside of it's own or group's account.  On a windows system privilege escalation is not required to do anything at all.

---

### Post by atyler on 2009-09-13
> **falconindy said:**
> The actions of cocky Windows users abusing their Linux installs has zero effect on the operating system from a security standpoint and it **certainly **doesn't affect my own security.


You are correct in saying users don't affect the OS, but they do affect the overall security landscape of a system or network.

You are also correct in saying that they don't affect your own security now.  But, hypothetically speaking, when .nix commands 95% of the overall OS market it is reasonable to assume that many more .nix exploits will be brought to light.  

My question is merely asking, "At what level of less-experienced users is the prevalence of exploits going to reach the point that they DO affect more experienced users such as you and me?"

<edit>This hypothetical may not even be tenable, but is worth considering.</edit>

---

### Post by Irvine_himself on 2009-09-14
> **__p1n__ said:**
> This is patently untrue.  On a linux system a process requires privilege escalation to do anything (attach to a running process, r/w to anything, etc.)  On a windows system privilege escalation is unnecessary; threads can migrate to any running process, process memory is not isolated, win32 calls are unnecessary to execute the underlying microcode.

I agree 100% that windows is botched operating system. There are numerous  reasons why one should put up with the serious inconveniences of a very poor third party support and the steep learning curve involved in migrating to a Linux based OS. My old XP laptop is very close to death, the fact that I have not installed,(and have no intention of installing, ) XP in it's replacement is testament to my true feelings on this subject.

However in the quoted text, I was using a black box model where the underlying details are irrelevant. By using the safe browsing habits indicated, it is nearly impossible to install malware on an XP box without the users active participation, as is the case with a Linux box.

I know it is anecdotal , but I spent five years with XP while using p2P networks and browsing sites that some people find offensive, I don't think I have ever had an actual virus infection. Very rarely, [by agreeing to terms and conditions that I was to lazy to read,] I have been infected with a few of the lesser spy-wares, but these were quickly picked up by regular scans with anti-spyware tools. 

The point I am trying to make is that  if the user clicks yes and gives the appropriate permissions, then he/she will be infected. Even though that OS defaults with a  strict security model.

Alternatively if a user with a more permissive OS configures it to a strict model and employs safe browsing habits, then it is very difficult to become infected.

To give yourself an idea of how risky your online behavior would be in Windows. Ask yourself  how much Junk email you get and be honest. 

Junk email is a similar model to malware and is caught in the same way, by clicking on glossy, shiny, irresistibly attractive lures....  It is easily avoided by following safe practice. 

You may not, believe me, but I have had my gmail account for three years and my junk box is empty. I don't mean a few or a couple, I mean none at all.

---

### Post by Sporkman on 2009-09-14
Does Windows have any services listening on any ports?

---

### Post by scorp123 on 2009-09-14
> **Rob_H said:**
> The tiny market share of Linux on the desktop makes it an unappealing target for malware authors. When will people stop to spread this BS about market share? [-(

---

### Post by scorp123 on 2009-09-14
> **Sporkman said:**
> Does Windows have any services listening on any ports? Out of the box? Sure. That's Microsoft's logic: Instead of shutting down those ports they started shipping that joke of a firewall since XP SP2.

---

