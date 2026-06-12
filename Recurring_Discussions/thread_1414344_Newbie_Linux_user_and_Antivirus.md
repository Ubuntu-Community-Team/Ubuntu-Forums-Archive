---
title: "Newbie Linux user and Antivirus"
date: 2010-02-23
forum: Recurring Discussions
---

### Post by datpapi on 2010-02-23
Hello everyone. 
 
I'm new to the Linux scene although I've been in IT for many years. I've been a Windows platform cronie and recently decided to jump into the Linux world. 
 
While I understand that Linux by design is far more secure, is there a real need to install an Antivirus program? If so, which would be the best to use?
 
I've come across differing opinions on the internet regarding the need for this and I'm sure it is ultimately a ""to each their own" matter - but I would like to get a feel for the general consensus of the Ubuntu community.
 
Thanks!

---

### Post by ubunterooster on 2010-02-23
The expected answer is likely clamav. I add the "vrius scanner" front-end to it.

---

### Post by quinnten83 on 2010-02-23
have a look see in the "recurring topics" section of the forum; this is discussed at lenght.
I don't use an AV in my Linux and ahven't had any problems. But you should check your flash cookies once in a while.

---

### Post by datpapi on 2010-02-23
Thanks for the quick reply. I'll dig around the forums and read up.

---

### Post by datpapi on 2010-02-23
Well UbuntuRooster, it looks like you called it! Simply because I've lived in fear of Windows based viruses for so long, I'm just going to go ahead and give myself that extra (and probably unneeded) "reassurance" and go with Clamav.
 
The only thing I haven't come across are good instructions for is the installation of the "virus scanner" portion you mention. 
 
Can you point me in the right direction with this?

---

### Post by Sef on 2010-02-23
> The only thing I haven't come across are good instructions for is the  installation of the "virus scanner" portion you mention. 
 
Can you point me in the right direction with this? 	

I would download it from 

Synaptic:  Administration > Synaptic Package Manager > Search > Type in Clam

or 

Ubuntu Software Center: Applications > Ubuntu Software Center > Search > type in Clam

---

### Post by ubunterooster on 2010-02-23
as Sef said, but replacing search>"clam" with search>"virus scanner". Installing the program by the same name (virus scanner) should install itself AND clam.

---

### Post by oldos2er on 2010-02-23
> **datpapi said:**
> Hello everyone.

 Hello. You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by jrusso2 on 2010-02-23
Scanning Linux with CLAMAV is just going to give you a bunch of false positives which a newbie will delete and probably have to reinstall the whole system.

---

### Post by ubunterooster on 2010-02-23
> **jrusso2 said:**
> Scanning Linux with CLAMAV is just going to give you a bunch of false positives which a newbie will delete and probably have to reinstall the whole system.

*non correct* Scanning entire OS, the only positives gotten were in firefox cache. If you have any records of this happening please provide a link.

---

### Post by aysiu on 2010-02-24
If a *real* security threat to Linux appears, having antivirus installed will do **nothing** to protect you.

Antivirus is useless.

Real security doesn't involve antivirus.

---

### Post by MicrosoftFan on 2010-02-24
> **datpapi said:**
> While I understand that Linux by design is far more secure, 
 
It isn't.

---

### Post by ubunterooster on 2010-02-24
Antivirus is not "useless" but it is overemphised. Scanners also do not detect a new virus until that virus has been already found and reported by a human, so with the first appearances of a virus, it dosen't matter whether you have a scanner.

@msFan: actually, due to modularity, synaptic (all programs can be gotten at a safe place), and the open source values, Linux IS more secure by nature. No, it is not all about market share. Note that apple's OSX is UNIX based b/c "that is by nature more secure". Please stop inviting flame-wars.

---

### Post by Arand on 2010-02-24
As of today, most users see little need for an antivirus solution for GNU/Linux, and _in practice_ I would say that that an average user is as safe, or safer, from malware on an ubuntu system with no AV, as on a windows system with a good AV.

However if you don't want to propagate viruses onto unsuspecting windows users, through email etc., or if you very frequently install a lot of possibly-questionable stuff through wine, or through untrusted deb packages/repositories you _might_ still want to use a AV solution.
In which case I personally wouldn't use clamAV, since it is, unfortunately, one of the least effective AVs available, from what I can gather.
I know the usual freeware contenders ([wikipedia list](http://en.wikipedia.org/wiki/Linux_malware#Anti-virus_applications)) has free linux clients, but if they're good or not I have no idea.

I expect to see continually more malware coming in through untrusted packages/repos, especially if rise in popularity continues.
Simple solution is to only use trusted repos, but as always, user habits is the culprit.
(How many users download out-of-repo debs and binaries and routinely grant root access to them?)

The notion of GNU/Linux being "immune" to viruses is in my opinion naive and stupid.
Yet in practice, and as of _today_, most users do not need to take any direct steps to avoid them.
Malware for GNU/Linux is kind of like the Avian Flu; the only needs are precaution ad preemption as of now..
(which I would claim is severely hampered by the continual stream of "Linux is inherently secure, hence no AV needed")

@ubuntuterooster: Database-based detection is only one side, proactive detection is often what makes an AV useful.

- Arand

---

### Post by MicrosoftFan on 2010-02-24
> **ubunterooster said:**
> @msFan: actually, due to modularity, synaptic (all programs can be gotten at a safe place), and the open source values, Linux IS more secure by nature. No, it is not all about market share. Note that apple's OSX is UNIX based b/c "that is by nature more secure". Please stop inviting flame-wars.
 
I'd just like someone to explain how: "Linux by design is far more secure". Modularity: wel that's a bit vague; Synaptic: doesn't count for that statement; and open source values: well I'd like to see some evidence that that makes Linux "far more secure".

---

### Post by ubunterooster on 2010-02-24
@Arand: I read up on proactive, this appears to be the cause of all false positives, but is very important. Hmmm, thanks for reminding me of the proactive, I'd forgoten about it.

@OP: more important than AV is firewall; sudo ufw enable
 UFW=uncomplicated firewall

---

### Post by aysiu on 2010-02-24
> **Arand said:**
> 
The notion of GNU/Linux being "immune" to viruses is in my opinion naive and stupid. The notion that antivirus is any effective means of protecting computers is, in my opinion, naive and stupid, yet it's a very widespread notion.

> 
@ubuntuterooster: Database-based detection is only one side, proactive detection is often what makes an AV useful. Actually, it's what often makes users complacent or unnecessarily paranoid. So-called "proactive detection" really just leads to false positives and the labeling of cookies as "spyware."

---

### Post by ubunterooster on 2010-02-24
@aisyu: pretty true.

@msfan: "ubuntu...STARTS [that means by default] as a very secure operating system. Without [even] installing security patches, it poses few risks from external and remote attackers...Ubuntu is usually safe enough from the start, but with a few hacks it can be made far safer"
Dr Neil Krawetz: skilled in security for about 20 years. Skilled in: computer forensics, profiling, cryptography/cryptanlysis, AI, software solutions, and aids frequently in law enforcement.
 He also has considerable experience with: red hat, OSX, Windows, openBSD, Solaris, OS/2, HP-UX, and more.

I've yet to see any reliable quotes saying Windows is at all more secure.

---

### Post by MicrosoftFan on 2010-02-24
> **ubunterooster said:**
> @msfan: "ubuntu...STARTS [that means by default] as a very secure operating system. Without [even] installing security patches, it poses few risks from external and remote attackers...Ubuntu is usually safe enough from the start, but with a few hacks it can be made far safer" 
 
I don't see how that quote in any way validates the statement: "Linux by design is far more secure". Especially since it's talking about Ubuntu, not Linux, and that it doesn't use any comparatives.
 
> I've yet to see any reliable quotes saying Windows is at all more secure.
 
As I haven't seen anyone make that claim, I don't think that's a problem.

---

### Post by Arand on 2010-02-24
@aisyu: I can fully well agree on AV not being "real" security, or an effective way to protect a _computer_.

What they are effective for is protecting stupid (a.k.a. Everyday) _users_, who does download free_office_2007_warez_lulz.exe and try to install it.
This userbase isn't exactly tiny..

And on that note, I wonder how ubuntu will fare when free_office_2007_warez_lulz.deb shows up.. [*clickclick, *sudo password, whoops...]

- Arand

---

### Post by ubunterooster on 2010-02-24
"It's talking about ubuntu, not Linux" "I haven't seen anyone make that claim" So we have agreed Ubuntu is more secure. "Security" is a relative term there is no such thing as "secure". Therefore saying something is "secure" IS a comparitive statement; comparing it to the default (perhaps MS).
 All that matters is that Ubuntu IS more secure. How MUCH more, and WHY is irrelevant.

---

### Post by Brindled on 2010-02-24
> **MicrosoftFan said:**
> I'd just like someone to explain how: "Linux by design is far more secure". Modularity: wel that's a bit vague; Synaptic: doesn't count for that statement; and open source values: well I'd like to see some evidence that that makes Linux "far more secure".

while you'd like to see evidence that linux is "far more secure," i'd like to see evidence that it's not "more secure."

---

### Post by Tibuda on 2010-02-24
> **Arand said:**
> @aisyu: I can fully well agree on AV not being "real" security, or an effective way to protect a _computer_.

What they are effective for is protecting stupid (a.k.a. Everyday) _users_, who does download free_office_2007_warez_lulz.exe and try to install it.
This userbase isn't exactly tiny..

And on that note, I wonder how ubuntu will fare when free_office_2007_warez_lulz.deb shows up.. [*clickclick, *sudo password, whoops...]

- Arand

> **Brindled said:**
> while you'd like to see evidence that linux is "far more secure," i'd like to see evidence that it's not "more secure."
As you wish
[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)

---

### Post by cariboo on 2010-02-24
@danielrmt, the link you provided just proves that downloading a .deb from an untrusted source, is not a good idea. If you noticed the timing of the thread, the whole thing happened in the space of a couple of hours, the op downloaded the software, and a fix was suggested all on the same day.

This suggests that while in general linux is more secure out of the box, when something bad happens, the problem is resolved very quickly.

BTW a virus scanner would not have detected that particular problem.

---

### Post by aysiu on 2010-02-24
> **Arand said:**
> @aisyu: I can fully well agree on AV not being "real" security, or an effective way to protect a _computer_.

What they are effective for is protecting stupid (a.k.a. Everyday) _users_, who does download free_office_2007_warez_lulz.exe and try to install it.
This userbase isn't exactly tiny.. I don't think antivirus will protect against that either. In fact, social engineering has been shown to be successful on all three major platforms (Windows, Mac, Linux).

If people can be easily tricked into installing untrustworthy software, antivirus won't really help.

---

### Post by MicrosoftFan on 2010-02-24
> **ubunterooster said:**
> So we have agreed Ubuntu is more secure.
Nope, I'm not offering any opinion on that statement, since it's irrelevant. If you haven't got it yet, the statement I'm disputing is: **"Linux by design is far more secure"**.
 
> "Security" is a relative term there is no such thing as "secure". Therefore saying something is "secure" IS a comparitive statement; comparing it to the default (perhaps MS).
 
Yes, except he doesn't mention MS.

---

### Post by Tibuda on 2010-02-24
> **cariboo907 said:**
> @danielrmt, the link you provided just proves that downloading a .deb from an untrusted source, is not a good idea. If you noticed the timing of the thread, the whole thing happened in the space of a couple of hours, the op downloaded the software, and a fix was suggested all on the same day.

This suggests that while in general linux is more secure out of the box, when something bad happens, the problem is resolved very quickly.

BTW a virus scanner would not have detected that particular problem.

I agree. That's why I think we should not think like "I don't have to worry about security because I use Linux", and go downloading everything out there.

EDIT: and also we should **not** think "I don't have to worry about security because I use anti-virus"

---

### Post by lykwydchykyn on 2010-02-24
> **jrusso2 said:**
> Scanning Linux with CLAMAV is just going to give you a bunch of false positives which a newbie will delete and probably have to reinstall the whole system.

I don't know that it'll be that bad, but clamav does give me a lot of false positives. 

I have a bunch of debian samba servers at work that host files for our windows machines.  They get scanned nightly with clamav and email me details about anything found.

I'd say about once every 2-3 weeks I get informed that some completely harmless print driver .cab file is a dangerous trojan.  

I try to report false positives back to the developers (if nothing else so I'll stop getting harassed by bogus reports), but inevitably new ones pop  up.  I'd only recommend clamav to someone who is savvy enough to look at a reported file and have a good handle on whether or not it's actually a true threat.  Definitely don't take it at face value.

---

### Post by Brindled on 2010-02-24
> **cariboo907 said:**
> @danielrmt, the link you provided just proves that downloading a .deb from an untrusted source, is not a good idea.
BTW a virus scanner would not have detected that particular problem.

i read the thread dan posted, and was going to ask what you answered already, cariboo. i had a feeling an AV software wouldn't have found this on any platform.

it reminds me of a map that could be download through steam on windows for counterstrike that could phish passwords. AV's couldn't find it at first either.

i guess it's possible on any front to find holes, but DoS is definitely much easier in windows, especially since its languages are more prevalently taught in schools, and businesses use windows more often than not.

linux being open source, more people can look for potential fixes than the closed systems, where you have to wait for fixes from said closed systems.

---

### Post by aysiu on 2010-02-24
> **danielrmt said:**
> I agree. That's why I think we should not think like "I don't have to worry about security because I use Linux", and go downloading everything out there.

EDIT: and also we should **not** think "I don't have to worry about security because I use anti-virus" Yes, I agree with both of those sentiments. What really irks me is people equating antivirus with security. The two are almost completely unrelated.

---

### Post by oldsoundguy on 2010-02-24
All this about an AV .. when the stuff that targets MS most now is NOT VIRUS programs, but other forms of malware that no standard MS AV program is designed to address.  Many are BROWSER items (and those can attack a BROWSER in Linux if so directed.  HOWEVER, all that will happen is browser problems on a Linux box unless you are on line as root .. which is the dumbest thing you could ever do!)

Most stuff I find removing from client's MS boxes is spyware and adware .. trojans, keyloggers, and so on. And MOST AV programs do not see that trash!

All this scare stuff (FUD) from MS is just that, scare FUD.

---

### Post by ubunterooster on 2010-02-24
> **MicrosoftFan said:**
>  the statement I'm disputing is: **"Linux by design is far more secure"**.Yes, except he doesn't mention MS.
First, it was said "more" not "much more"
Second, if there is a comparison and only one thing is mentioned, the other is usually the norm, perhaps Windows.
Third, further posting on this topic appears useless and I am removing my subscription. If you wish to talk further, PM me and we won't be wasteing the OP's time.

---

### Post by aysiu on 2010-02-24
The the OP, if you find this discussion constructive, you can also read these other threads posted on the same topic in the last month:
[http://ubuntuforums.org/showthread.php?t=1341347&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1341347&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=1405017&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1405017&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=1401266&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1401266&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=1399048&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1399048&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=1380452&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1380452&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=1392897&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1392897&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=1385025&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1385025&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=681039&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=681039&highlight=antivirus)
[http://ubuntuforums.org/showthread.php?t=1383255&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=1383255&highlight=antivirus)

---

### Post by MicrosoftFan on 2010-02-24
> **ubunterooster said:**
> First, it was said "more" not "much more"
 
The statement is the one in the OP of this thread, and is the only one I have referenced and copied exactly throughout: 
> **datpapi said:**
> While I understand that Linux by design is far more secure,
 
> 
Second, if there is a comparison and only one thing is mentioned, the other is usually the norm, perhaps Windows.

 
1) To claim that he was stating Ubuntu is more secure than Windows would be putting words in his mouth.
2) That line of argument is irrelevent to the statement I was disputing anyway.

---

### Post by Arand on 2010-02-24
The screensaver .deb is a great example, it was insultingly harmless and poorly written, yet it caused the amount of strife it did. In my mind a clear indicator that if anyone actually tries to make real malware, things will fall.

If we did have any decent proactive (or even database) "AV" for GNU/Linux (I don't think there are at the moment though) I am assuming that this is exactly the kind of things it would be able to detect.

EDIT: As you might be able to tell, this is a pet peeve of mine.. and I'm somewhat slipping offtopic... /ENDEDIT

- Arand

---

### Post by aysiu on 2010-02-24
> **MicrosoftFan said:**
> 
1) To claim that he was stating Ubuntu is more secure than Windows would be putting words in his mouth. Sure, but it's a logically reasonable inference. The vast majority of people who identify themselves as "Newbie Linux user[s]" are former or current Windows users.

Also the only conventional wisdom (whether it is factual or not is up to debate) regarding Linux being more secure by design than another platform involves Linux being more secure by design than Windows.

---

