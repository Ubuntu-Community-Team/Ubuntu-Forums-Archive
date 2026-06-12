---
title: "Linux &amp; Mac users will be easy targets?"
date: 2008-10-21
forum: Recurring Discussions
---

### Post by lancest on 2008-10-21
Personally I think this guy is trying to create a new market. 
[The co-founder of IT security company Kaspersky Labs said Linux and Mac users will be “easy targets” for hackers and malware writers over the next few years. ]("http://www.computerworld.com.au/index.php/id;264209080;fp;16;fpid;0")  Linux is an easy target? I doubt it.
IMHO this goes a bit too far.

---

### Post by smoker on 2008-10-21
well, this guy made his millions selling antivirus crap, he's bound to be looking for new expanding markets to exploit!

i don't think most linux users need worry about scare-mongering, though it is, of course, up to the user to ensure their system is secure.

---

### Post by Sealbhach on 2008-10-21
I'm the biggest threat to the security of my system, not anyone else.


.

---

### Post by pt123 on 2008-10-21
They said this about Firefox when the marketshare was around 4%

---

### Post by phoenix_snake on 2008-10-21
I doubt linux will ever be a target or OS X or even Windows Vista cause they all have proper user permissions now so any virus attack is the users fault.

---

### Post by DFlame on 2008-10-21
> **Sealbhach said:**
> I'm the biggest threat to the security of my system, not anyone else.


.
Similar situation here. I'm surprised either of my computers still allow me to work on them :P

Most Internet connections these days travel through routers which offer a base level of protection from most kinds of attack. Any malware that appears won't be able to do much damage unless the user allows it to (read: sudo/root. If you're using Linux, you should already be well educated in this sector) and finally, the open source community can release patches and updates in a very efficient manner.

I'm not worrying :)

DFlame

---

### Post by jacksaff on 2008-10-21
Installing apps from a community-run repository completely undermines the need for software such as this guy sells. It's the debian and ubuntu packaging community that make our distro secure just as much as the (vastly superior to win) inbuilt security mechanisms in linux. 

My system is secure because I use software that is open source and has been packaged by people who have been vetted by the community. There is no need for a theoretically perfectly secure system and it's an impossible dream anyway. Proprietary software vendors either don't get this at all, or fear it and want to undermine it. 

What this guy wants is to control the community by getting to say what software is safe and what isn't (the signed software he talks about). It's the same model we have already, only controlled by a company rather than by the community. I know who I trust.

---

### Post by Dragonbite on 2008-10-21
> **jacksaff said:**
> Installing apps from a community-run repository completely undermines the need for software such as this guy sells. It's the debian and ubuntu packaging community that make our distro secure just as much as the (vastly superior to win) inbuilt security mechanisms in linux. 

That is, until somebody figures out how to hack the Repository servers and plant some "update" that includes a virus of some sort. Since you are already running "sudo apt-get" you may have some access to the computer's inner workings (I don't know enough about sudo to know or say for sure).

The Repositories are basically large fileservers and I don't know if they are accessed via HTTP off hand, but if they are then they are essentially web servers which are mostly secure but it's not like you have to log in to the server to get your packages.

> **jacksaff said:**
> My system is secure because I use software that is open source and has been packaged by people who have been vetted by the community. There is no need for a theoretically perfectly secure system and it's an impossible dream anyway. Proprietary software vendors either don't get this at all, or fear it and want to undermine it. 

Using Open Source software is pretty secure because there is a good (not perfect, but good) chance that anything "sneaky" going into an application will be detected and either fixed or banned (and their good name run through the mud) pretty quickly.  That doesn't guarantee that nobody will try and put forth some application that does what you expect it to and tries to obfuscate malicious code in it in hopes you run it before some prying eyes find it.

> **jacksaff said:**
> What this guy wants is to control the community by getting to say what software is safe and what isn't (the signed software he talks about). It's the same model we have already, only controlled by a company rather than by the community. I know who I trust.

I agree. The best model for saying what is safe and what isn't is the process that is in place now. I'm not sure how Ubuntu vets out the applications before placing them in the repositories but I'm sure there is some level of checking.

I subscribe to the Ubuntu News RSS feed and see a number of vulnerability alerts coming through; CUPS, exiv2, libexif, D-Bus, LittleCMS, Ruby, cpio, OpenSSH (just in the month of October).

I still feel much safer using Linux than I do Windows. Heck, my Windows machine has Trend Micro's Internet Security Suite with firewall, anti-virus, anti-spyware, etc. and guess which system at home is BSOD?!  You betcha!

I just don't like seeing people get complacent about virus and threats because even if Linux is more secure that doesn't mean bad guys aren't looking.

---

### Post by will1911a1 on 2008-10-21
We'll all be easy targets and he'll be happy to sell us a solution.  

Mmmhmm.

---

### Post by ratmandall on 2008-10-21
```
"Modern operating systems are flawed by design,&#8221; Kaspersky said, &#8220;including OpenBSD&#8221;.
```

Piss off look at how many exploits there are for openBSD on milw0rm.com exactly 1
Now that's not the only exploit for openBSD but yea,

---

### Post by Big Nate on 2008-10-21
I would buy this with a tinfoil hat so he couldn't read my thoughts anymore.

---

### Post by iKonaK on 2008-10-21
:lolflag:
dose he really believe that GNU/Linux users and not to mention the BSD users are really that dumb to believe those craps, those lines works for very end windows users....

---

### Post by adouglasmhor on 2008-10-21
Funny when I was running windows. I had anti virus, anti spyware and 2 firelwalls (one hardware one software), I still had problems.

---

### Post by Mr. Picklesworth on 2008-10-21
> **lancest said:**
> Personally I think this guy is trying to create a new market. 
[The co-founder of IT security company Kaspersky Labs said Linux and Mac users will be &#8220;easy targets&#8221; for hackers and malware writers over the next few years. ]("http://www.computerworld.com.au/index.php/id;264209080;fp;16;fpid;0")  [B]Linux is an easy target? I doubt it.
IMHO this goes a bit too far.[/B]

You just proved his point.

Debian has a few big flaws for "trick the user" methods. First of all, installations are done as root, which means that if a general user is allowed to run an install via sudo (totally possible) it is not unlikely that he could be fooled into installing a package which Conflicts with any security subsystems, the updater, and all that stuff and that Provides newer "versions" of other software (which is actually malware).
On that same line of thought, a user being tricked into merely adding a bad repository could lead to his system being compromised -- and if it is done well, completely without the user ever knowing.

It's all about being cautious, and solving the problem is very difficult. I like where systems like ZeroInstall are heading and I think they are a great idea for more user-specific applications like games or miscellaneous tools. It would be cool to see that kind of functionality (installs specific to users) to happen in official Debian. This helps to avoid nuking the system and improves user experience since there is then no need to punch in a password or run as root.

PolicyKit could help here. Different regions of the system could require different policy levels, each region providing a different coloured warning message to drill the points home. Or certain packages could be locked down requiring a certain PGP signature in any updates, although that one's potentially very troublesome.

It is a tough nut to crack. Not uncrackable, but the guy here makes a good point. It isn't fearmongering so much as a reminder that something needs to be done before we all embarass ourselves.

We have the big advantage that anti-virus software could concievably be bundled with the operating system and have virus definition updates through apt.

---

### Post by razerbug on 2008-10-21
> **phoenix_snake said:**
> I doubt linux will ever be a target or OS X or even Windows Vista cause they all have proper user permissions now so any virus attack is the users fault.

I said that in another forum, that the user was the weak link when it comes to computer security - although I was shouted down because it's apparently all Microsoft's fault... oh well 

I agree though - Any system man can make, man can break... and the main way people get infected is having unprotected systems and choosing to download/run suspicious things from untrusted sources.

If people do start attacking Linux and OSx, I would imagine the general computer literacy of Linux uses will mean very few will be hard hit. I would think Mac users may be in trouble though :P

I always wondered when McCafee etc become a protection racket... as OS's make more secure systems with built in virus etc protection, how long before Anti-Virus companies have to start deliberatly making threats to protect us from ;)

---

### Post by jakupl on 2008-10-21
> **razerbug said:**
> as OS's make more secure systems with built in virus etc protection, how long before Anti-Virus companies have to start deliberatly making threats to protect us from ;)

You don't think this has happened allready?

---

### Post by razerbug on 2008-10-21
Well... one doesn't wish to appear paranoid ;)

but yes.

It's one of the reasons I use free things like AVG because there is less (although arguably some) incentive for them to engineer problems. 

Scary though, those trying to protect us are actually the problem. Still... I've never had a problem with a life time of Windows and recently Ubuntu or OSx (although the latter is so crap I consider it malware in itself :P) so I hope I'm reasonably well protected.

---

### Post by MaxIBoy on 2008-10-21
This guy does NOT want to sell anti virus to Linux users, as creating such a thing would be a technological difficulty. And it's not in his best interest to sell software that NEVER finds any native Linux viruses, as that's not at all conducive to the fear he needs from his market.

He's trying to scare people into staying with Windows so he'll be able to continue marketing his crapware to them.

---

### Post by oedipuss on 2008-10-21
> **Dragonbite said:**
> That is, until somebody figures out how to hack the Repository servers and plant some "update" that includes a virus of some sort. Since you are already running "sudo apt-get" you may have some access to the computer's inner workings (I don't know enough about sudo to know or say for sure).
[...]
Using Open Source software is pretty secure because there is a good (not perfect, but good) chance that anything "sneaky" going into an application will be detected and either fixed or banned (and their good name run through the mud) pretty quickly.  That doesn't guarantee that nobody will try and put forth some application that does what you expect it to and tries to obfuscate malicious code in it in hopes you run it before some prying eyes find it.


Even if a repository server is hijacked to serve some kind of malicious code, wouldn't that code come inside a specific package, and as such be easily located and dealt with, even after a portion of the userbase has installed it ? 
One of the most annoying things with windows malware is more often than not you don't know where it came from.

---

### Post by damis648 on 2008-10-21
I think we should take a more OS X-type of approach to installing applications so that we can tighten security. Any 'normal' user-type applications are installed in a directory (with the same structure possibly, ie /bin /usr, all of this under say /uapps) which has which is owned by root, but have 777 permissions so that when a user installs an application like a word processor or a game, they install here without needing root access. If any of these Applications need root access, they may ask for it, but the sudo action being performed by the applications would be visible. (IE if a program needs to do something as root, the gksudo window will have a "Details" button at the bottom, and the gksudo command being run can be viewed). Any programs that exclusively must be installed traditionally, like a system application, would require root access and would be installed as root. I'm still working on it...

---

### Post by razerbug on 2008-10-21
I'm not sure I like the OS / Linux method of install - while I can see it has allot of benefits, I still like being asked where I would like to install programs etc (even though I usually chose Program Files anyway) - something about the process not being automatic is reasuring... similarly I don't use the Windows default "my documents, My Pictures" folders, but organise my files else where...

On Ubuntu I leave installing alone (cause I don't understand the file system at all :P) but store documents in folders I make. 

That said minor annoyance in the GUI file system is nothing to security.

I do worry about who looks after the Synaptic system though given that it's open source and their isn't as much of a corporate reputation at stake if someone does get in and stick malware in there

---

### Post by razerbug on 2008-10-21
<deleted>

---

### Post by wizard10000 on 2008-10-21
> **pt123 said:**
> They said this about Firefox when the marketshare was around 4%

And they were correct.

US-CERT shows 91 technical alerts for Firefox and 99 for Internet Explorer in the last three years.

---

### Post by ikt on 2008-10-21
> **wizard10000 said:**
> And they were correct.

US-CERT shows 91 technical alerts for Firefox and 99 for Internet Explorer in the last three years.

so this means Firefox is now some massive adware, spyware, activex for cruise control drive by malware installs, piece of bloated, useless crap?

There could be 1000 cert technical alerts for firefox, and only 1 for internet explorer, if that giant gaping hole in ie is still left open, and the 1000 holes in firefox were patched, firefox would still be safer. That and cert doesn't take into account 1/100th of all the issues concerning how to measure a programs security... all it does is count vulnerabilities.

---

### Post by Mr. Picklesworth on 2008-10-21
Speaking of such things, here is my horrifying discovery of the day:
Umit gained root privileges without me entering a password or confirming anything. It was kind enough to give me a popup warning me that it was doing so, but it basically just ran itself via gksu and a user could never know *until it is too late and the software has annihilated his system*. In this case it's because I had run gksu within the last 15 minutes.

I always assumed that the timeout was on a per-process basis, (eg: only sh 14511 has the timeout) which would be the only intelligent way to apply a timeout for a dangerous security procedure. Evidently this is not the case. This means that any program which knows of the existence of gksu can count on luck. Assuming the malware is lucky, it has more freedom to screw things up than in Windows 95.

Not to be totally destructive, but the bottom line is that this guy is right: The only reason Linux is remotely secure is because sensible users use it and because software is peer reviewed (which is why actual software security holes are generally hard to find). As far as helping the *user* be secure, this platform needs a lot of love.

As for "x Internet Security" software, I find the stuff is (as a rule) terrible. BitDefender, for example, kindly disables everything to do with ActiveX in Internet Explorer. Maybe there is some sense here given that ActiveX has lots of security holes, but I thought the job of this software was to watch for intrusions *without* making a mess? No, it just disables ActiveX. That, of course, breaks Windows Genuine Advantage validation for software like Microsoft Office, thus confusing the heck out of users. It also breaks a good three quarters of the Interwebs since ActiveX is what Internet Explorer uses for plugins!
So I don't think that is a valid solution, either. Fixes have to be applied at the source.

---

### Post by VorDesigns on 2008-10-21
> **DFlame said:**
> Similar situation here. I'm surprised either of my computers still allow me to work on them :P

Most Internet connections these days travel through routers which offer a base level of protection from most kinds of attack. Any malware that appears won't be able to do much damage unless the user allows it to (read: sudo/root. If you're using Linux, you should already be well educated in this sector) and finally, the open source community can release patches and updates in a very efficient manner.

I'm not worrying :)

DFlame

Most of the consumer grade routers are fair protection inbound but almost all of them are useless for protection against the more common forms of atack, operator error; they don't care what goes out.  Usually, the user activates some unwanted application which makes outbound connections which are not inspected.
Even an informed user willing to take the time to block undesirable outbound traffic only gains a temporary reprieve as intruder applications often adapt to default port restrictions by rerouting through alternate, generally available ports such as http, https, ftp, etc.
If you want to be completely safe, don't turn it on.  If you have the resources; buy a ICSA compliant firewall and get it configured properly or learn how to manage the software based firewall in your LinOS.  Maintain a browsing system and a work system.  Only have one or the other on or, run them on physically separate networks.  Browsing system goes where you want to go, does what you want to do.  Work system runs only work applications, doesn't go surfing, doesn't use multimedia mail clients and only interacts with the Internet for software updates and commercial communications with trusted business partners.
Then, you are only really vulnerable instead of incredibly vulnerable.

---

### Post by wizard10000 on 2008-10-21
> **Mr. Picklesworth said:**
> ...This means that any program which knows of the existence of gksu can count on luck.

It doesn't even have to be real lucky - a heck of a lot of people will provide a password if prompted  ;)

---

### Post by billgoldberg on 2008-10-21
I'm not aware of the security level of OSX, but they can't sell that crap to me.

Also, the linux crowd in general are much more knowledgeable than the Windows or OSX crowd.

---

### Post by wizard10000 on 2008-10-21
> **ikt said:**
> so this means Firefox is now some massive adware, spyware, activex for cruise control drive by malware installs, piece of bloated, useless crap?

NPAPI isn't inherently safer than ActiveX.

---

### Post by Mr. Picklesworth on 2008-10-21
On the bright side, *downloaded* software is of course not executable until the user explicitly says so. (Unless it is archived, I believe). He can still run it as, say, a shell script but that demands a particular motion by the user anyway.

It would be kind of cool if there was a file handler for such things that said "This is a program but it is not yet allowed to run. Do you wish to run it?", with a little attempt to identify the software, specific libraries it links to (estimating things it does) and its creator. Extra room for a malware scanner to plug itself in since one of the reasons those fail in Windows is because they are obtrusive pieces of junk which add their own interfaces for everything.
It wouldn't need to be sugar coated with "easiness" that prevents all error. I like being able to say "you idiot! Stop running random programs and actually read the messages that appear!" to people who complain about getting viruses. I guess I take it a bit too personally :P

Windows actually uses a similar method, but we could make it better with multi-coloured altert windows!
(Really, I think that may be a good way so users identify important messages in that split second before they automatically dismiss the things).

---

### Post by DrMega on 2008-10-21
> **Mr. Picklesworth said:**
> Speaking of such things, here is my horrifying discovery of the day:
Umit gained root privileges without me entering a password or confirming anything. It was kind enough to give me a popup warning me that it was doing so, but it basically just ran itself via gksu and a user could never know *until it is too late and the software has annihilated his system*. In this case it's because I had run gksu within the last 15 minutes.

I always assumed that the timeout was on a per-process basis, (eg: only sh 14511 has the timeout) which would be the only intelligent way to apply a timeout for a dangerous security procedure. Evidently this is not the case. This means that any program which knows of the existence of gksu can count on luck. Assuming the malware is lucky, it has more freedom to screw things up than in Windows 95.

That's a good point. I guess there is a trade off though between forcing people to put their password in for every single command (you might be doing several in a row) and upholding security. It is a definite issue. I think a better solution would actually be to force the user to put in their password for every command that needed privileged access, as long as you can whack them all in a script and just sudo that one script (I haven't tried that so I don't know if you can or not).

---

### Post by billgoldberg on 2008-10-21
> **DrMega said:**
> That's a good point. I guess there is a trade off though between forcing people to put their password in for every single command (you might be doing several in a row) and upholding security. It is a definite issue. I think a better solution would actually be to force the user to put in their password for every command that needed privileged access, as long as you can whack them all in a script and just sudo that one script (I haven't tried that so I don't know if you can or not).

I disable that very unsecure behaviour.

I'm bringing my brother up to speed on linux, and even he as a computer noob said it was dangerous.

---

### Post by risu_vk on 2008-10-21
Hmm nothing is 100 percent secure..but the statement that linux and osx will be 'EASY TARGET' cant be true unless in the hand of a careless one and in linux its easy to delete even the entire file system with a sudo ..and some one blindly executing a rm -f  with root privilage can spoil. Second issue may come out of closed source binaries which also need root previlage to do some thing really bad. AV companies has to take care of their profit n markets and willtry do the best for that.
I recollect my windows days with a comp running a bloated antivirus which eat most of the system resourse and a friend of mine had an infected system which performs better than my slow computer with heavy /costly antivirus softwares

---

### Post by ikt on 2008-10-21
> **wizard10000 said:**
> NPAPI isn't inherently safer than ActiveX.

can you explain why?

I'm interested in how something could be less safer than a piece of software which can let random binaries install over the net without prompts and played a part in the biggest malware epidemic in the history of computing.

---

### Post by billgoldberg on 2008-10-21
> **risu_vk said:**
> and in linux its easy to delete even the entire file system with a sudo ..and some one blindly executing a rm -f  with root privilage can spoil.

The exact same can be done in OSX.

---

### Post by eentonig on 2008-10-21
Didn't read the entire thread.

But somewhere, he has a point.

First the facts:
- The more people start using linux/Mac, the more it becomes interesting for blackhats to target them.
- They have full access to the code, to look for vulnerabilities.
- Every peace of code contains some flaw or vulnerability. The fact that Open Source is open, allows for fast retrieval/fixes of these vulnerabilities, but also for fast exploits of them.
- A program initiated by the user might not be able to change anything beyond the boundary of his home folder, but it can still create havoc in there. For a lot of people, loosing documents/photos is worse than loosing an OS. An OS can be reinstalled within 30', if you don't have backup, you loose you're files. Not to mention years or months of setting up a system to your liking. 

Common assumptions:
- Joe Sixpack/Joe Plumber/... is lazy and dumb when it comes to computer security.
- Most people Backups forget to take backups of their personal documents.
- Most malware is triggered by the users themselves. They browse the porn sites, download those funny little programs, mail those stupid jokes around.


Personal conclusion:
A linux/Mac system will be a safer system, as a common desktop won't have listining ports for people to attack. So malware will be limited to tricking the user to execute them. But malware writers seem to be very creative as a group. I'm sure they will succeed in that task. Just as they're succeeding in just that right now on Windows systems.

---

### Post by snova on 2008-10-21
I'm disinclined to believe anything an antivirus company says about security. They make their money by selling security products- the last thing they want as a business is a perfectly secure system. Maybe if a hacker said it. :)

Assuming the software itself has no holes (which is often true), the only way in *is* a user. But there's no point in talking about how Linux systems are vulnerable to uninformed users blindly running commands with sudo when Windows has the same problem, magnified due to default administrator accounts! They don't even need a password.

The only good point I found is that of "signed" applications. The biggest hole I can think of in the entire system is apt-get. If you can find a way to trick a user into installing a .deb and running something included in it, all our security goes to waste. This is one reason why I think the repository model is superior- if you can trust Ubuntu, you're safe.

Besides, all the signatures in the world won't do any good if one of them is on a rootkit.

> 
I think we should take a more OS X-type of approach to installing applications so that we can tighten security. Any 'normal' user-type applications are installed in a directory (with the same structure possibly, ie /bin /usr, all of this under say /uapps) which has which is owned by root, but have 777 permissions so that when a user installs an application like a word processor or a game, they install here without needing root access. If any of these Applications need root access, they may ask for it, but the sudo action being performed by the applications would be visible. (IE if a program needs to do something as root, the gksudo window will have a "Details" button at the bottom, and the gksudo command being run can be viewed). Any programs that exclusively must be installed traditionally, like a system application, would require root access and would be installed as root. I'm still working on it...

I never use /usr/local, all my compiled software goes in ~/install/<package>/. Mostly that's just because I don't like touching anything not in /home, though.

And anyway, how is that supposed to help? The risk that a user might run something with sudo still stands. It's just from a different place.

---

### Post by birddog165 on 2008-10-21
I think that's ridiculous to say that us Linux people are targets, because we're the hackers.

But seriously, with the community of people working together, I'm sure that we'll be able to block those problems before they start.

---

### Post by Giant Speck on 2008-10-21
> **birddog165 said:**
> But seriously, with the community of people working together, I'm sure that we'll be able to block those problems before they start.

Sure, there is a community of people there working together to fix problems and block them, but who is to say there isn't a completely separate community of people working together to cause or exploit those very problems?

---

### Post by DrMega on 2008-10-21
> **billgoldberg said:**
> I disable that very unsecure behaviour.

I'm bringing my brother up to speed on linux, and even he as a computer noob said it was dangerous.

Which bit is not secure? Putting the password in for every command or writing a script and sudoing it?

If it is the latter, then how else would you do it?

---

### Post by lancest on 2008-10-21
> **maxiboy said:**
> this guy does not want to sell anti virus to linux users, as creating such a thing would be a technological difficulty. And it's not in his best interest to sell software that never finds any native linux viruses, as that's not at all conducive to the fear he needs from his market.

He's trying to scare people into staying with windows so he'll be able to continue marketing his crapware to them.

+1

---

### Post by cardinals_fan on 2008-10-21
If Linux becomes more popular on preinstalled machines, I think this will be true.  Not because of any weaknesses with the system, but because simple social engineering attacks will get ignorant or foolish users on any system.

---

### Post by Grant A. on 2008-10-21
We'll all be sitting ducks since all of us run root 24/7 with every single port open.

---

### Post by ikt on 2008-10-23
> **cardinals_fan said:**
> If Linux becomes more popular on preinstalled machines, I think this will be true.  Not because of any weaknesses with the system, but because simple social engineering attacks will get ignorant or foolish users on any system.

That's true, but it can only go so far, and the potential damage is much more limited vs automated attacks.

I remember reading about MS cleaning millions of people's pc's with the blaster worm on it, only to find that something like 30% of them all got reinfected a short time later because they were running XP gold.

> **Giant Speck said:**
> Sure, there is a community of people there working together to fix problems and block them, but who is to say there isn't a completely separate community of people working together to cause or exploit those very problems?

Either way we still won't need anti-virus programs because the way to stop that malware will be via updating our software to patch the vulnerabilities so the malware can't get in our systems in the first place.

---

### Post by wizard10000 on 2008-10-24
> **ikt said:**
> can you explain why?

I'm interested in how something could be less safer than a piece of software which can let random binaries install over the net without prompts and played a part in the biggest malware epidemic in the history of computing.

Two reasons - first because IE doesn't "let random binaries install over the net without prompts".  IE6 and later don't allow installation of unsigned ActiveX controls by default - just as FF prompts the user before installing an .xpi.

Second, because you can do exactly the same malware tricks with NPAPI.  IE is just a bigger target.

---

### Post by ikt on 2008-10-29
> **wizard10000 said:**
> Two reasons - first because IE doesn't "let random binaries install over the net without prompts".  IE6 and later don't allow installation of unsigned ActiveX controls by default - just as FF prompts the user before installing an .xpi.

Second, because you can do exactly the same malware tricks with NPAPI.  IE is just a bigger target.

That still doesn't make less safer than Active X.

I'm sure you've read the wikipedia page, there are several reasons under it as to why NPAPI is safer than Active X, it's not 'inherently more secure' but several features of the browsers which use it (inc. the most popular one) make it safer overall.
 and this comes to my original point:

A programs security is not based on the number of cert technical alerts/vulnerabilities.

---

### Post by phoenix_snake on 2008-10-29
> **ikt said:**
> That still doesn't make less safer than Active X.

I'm sure you've read the wikipedia page, there are several reasons under it as to why NPAPI is safer than Active X, it's not 'inherently more secure' but several features of the browsers which use it (inc. the most popular one) make it safer overall.
 and this comes to my original point:

A programs security is not based on the number of cert technical alerts/vulnerabilities.
I hear Internet Explorer 7 is the safest browser for Vista cause of Internet Explorer Protected Mode, some of you must know about it.

---

