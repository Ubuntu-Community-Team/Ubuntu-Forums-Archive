---
title: "regarding viruses attacks less in linux"
date: 2008-01-02
forum: Recurring Discussions
---

### Post by rraj.be on 2008-01-02
generaly there is a opinion that linux bases os's are not much infected by virus or spy ware as windows get.I am a new guy to ubuntu and linux.

could any one give me in depth reason for this......
if possible please mail it to *removed*

---

### Post by Ub1476 on 2008-01-02
1) Noone makes virus for Linux.

2) Linux is just safer compared to Vista, regarding viruses/spyware etc.

3) If you have a dual-boot you need anti-virus. This is to protect Windows (you can get virus on Linux, but it wont infect it, just jump to Windows).

If you're scared of hacking atempts, install Firestarter.

---

### Post by timcredible on 2008-01-02
short explanation is that windows is a single-user system modified for multiple users, which leaves 'administrator' account vulnerable, whereas linux/unix is a multi-user system which leaves 'root' account strong.  in depth reasons are on the web, do a search.

---

### Post by kestrel1 on 2008-01-02
Firestarter is only a frontend for the built in firewall in Ubuntu. You should only need Firestarter if you want to configure the firewall (iptables) The firewall just works in the background.

---

### Post by ~LoKe on 2008-01-02
> **Ub1476 said:**
> 1) Noone makes virus for Linux.
Not true.  Linux is often the target for attacks, including viruses.  The major difference is Linux generally has a permission system in place to ensure that nothing can spread to critical areas.

> **Ub1476 said:**
> 
2) Linux is just safer compared to Vista, regarding viruses/spyware etc.
Vista/Windows XP can be exceptionally secure, if you know what you're doing.  The main difference is still the permission system, which could be "partially" solved by running Windows and using an account that **doesn't** have administrator access.

> **Ub1476 said:**
> 
This is to protect Windows (you can get virus on Linux, but it wont infect it, just jump to Windows).
Not sure where you heard that, but no virus will spread from Linux to Windows.

> **Ub1476 said:**
> If you're scared of hacking atempts, install Firestarter
Firestarter is just a graphical interface for IPTables.

---

### Post by aysiu on 2008-01-02
1. Most Windows users use Windows XP and operate as administrator, because the way XP is set up, it's too much trouble to run as a limited user.

2. There is a higher percentage of Windows users who are not computer savvy and thus are more susceptible to social engineering, which is how a lot of breaches in security happen.

3. Windows is a bigger target on the desktop/laptop scene and has more malware produced for it (almost the computer equivalent of living in a "bad neighborhood").

---

### Post by philinux on 2008-01-02
Have a glance at this.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by kwacka on 2008-01-02
The 'if linux had as many users as windows it would have the same problems' argument has little (if any) validity, its down to how the system works. There are virii for linux, but they are generally not too effective.

The major problem with Windows is that any application can automatically install itself (don't know about Vista, but prior to this it was open) in linux you need to tell it to install - unless you log on with root privileges, of course.

Another problem is that Windows identifies a file's format by its extension AND by default hides the extension.

A virus could install itself to a user's account, but what can it do there? It can't propogate itself - the worst that can happen is that user could possibly use some data - but all other users can be safe.

See:[http://www.theregister.co.uk/2003/10...ndows_viruses/](http://www.theregister.co.uk/2003/10...ndows_viruses/)

---

### Post by jeffus_il on 2008-01-02
Also the virus writers are hackers who are more likely to be sympathetic to Linux

---

### Post by LowSky on 2008-01-02
> **~LoKe said:**
> 

Not sure where you heard that, but no virus will spread from Linux to Windows.
.

But a linux machine can play host to a windows virus, which can infect windows mahines. a user could potentially download a windows virus that will do nothing in linux but if a windows computer accesses that drive it could end up harming windows.

---

### Post by ~LoKe on 2008-01-02
> **LowSky said:**
> But a linux machine can play host to a windows virus, which can infect windows mahines. a user could potentially download a windows virus that will do nothing in linux but if a windows computer accesses that drive it could end up harming windows.

No.  Again that falls under the super user permission system.  Even if you mounted your Windows hard drive in Linux, it would be in /media/windows.  /media is on the root directory and requires the use of sudo to write to that folder.  Without super user access, nothing will "spread".

---

### Post by ~LoKe on 2008-01-02
> **jeffus_il said:**
> Also the virus writers are hackers who are more likely to be sympathetic to Linux

The people who write viruses and worms aren't sympathetic to any group, that's the whole point.

---

### Post by Steveway on 2008-01-02
> **jeffus_il said:**
> Also the virus writers are hackers who are more likely to be sympathetic to Linux

It's called crackers, not hackers!
That is a major difference.
Also, most people refer to kernel-writers (Linus Torvalds and Co.) as hackers.

---

### Post by jken146 on 2008-01-02
> **~LoKe said:**
> No.  Again that falls under the super user permission system.  Even if you mounted your Windows hard drive in Linux, it would be in /media/windows.  /media is on the root directory and requires the use of sudo to write to that folder.  Without super user access, nothing will "spread".

You can, however, mount your ext2 partitions in Windows very easily, using drivers that ignore the permissions and let you do anything to all the files there.

---

### Post by ~LoKe on 2008-01-02
> **Steveway said:**
> It's called crackers, not hackers!
That is a major difference.
Also, most people refer to kernel-writers (Linus Torvalds and Co.) as hackers.

Sorry bud, but someone who writes viruses is a hacker not just a cracker.  There are several different types of hackers, the most prominent two would be white hat and black hat hackers.

White hat hackers are the guys who mostly go around trying to find vulnerabilities in the systems of random businesses and tell them how to fix it.  Lots of people make a living off this; they don't always do it for free. ;)

Black hat hackers are basically the ones who find and exploit security vulnerabilities for their own personal/political gain.

---

### Post by ~LoKe on 2008-01-02
> **jken146 said:**
> You can, however, mount your ext2 partitions in Windows very easily, using drivers that ignore the permissions and let you do anything to all the files there.

That's a Windows problem.  And still, I'm almost certain that an app like explore2fs won't allow you to write to the ext2/3 partition (but it cold still be formatted).

---

### Post by Ub1476 on 2008-01-02
> **~LoKe said:**
> Not true.  Linux is often the target for attacks, including viruses.  The major difference is Linux generally has a permission system in place to ensure that nothing can spread to critical areas.

Alright, but this not the issue for desktop users is it? I suppose it's regarding servers, right? 

> **~LoKe said:**
> Vista/Windows XP can be exceptionally secure, if you know what you're doing.  The main difference is still the permission system, which could be "partially" solved by running Windows and using an account that **doesn't** have administrator access.

I never said Windows was insecure, but that Linux were safer. One point as you said, root/admin is not enabled by default. This has been fixed in Vista though (UAC), but in such a way that many disables it.

> **~LoKe said:**
> Not sure where you heard that, but no virus will spread from Linux to Windows.

I heard it in almost every thread regarding viruses on this forum. There's a reason for ClamAV picks up Windows viruses isn't it?


> **~LoKe said:**
> Firestarter is just a graphical interface for IPTables.

IPTables is turned off by default. You do not need Firestarter to restrict ports, but most people prefer a graphical frontend.

---

### Post by ~LoKe on 2008-01-02
> **Ub1476 said:**
> Alright, but this not the issue for desktop users is it? I suppose it's regarding servers, right? 
A desktop computer is an unlikely target for a "hacker" or "cracker", but if someone were spreading viruses/worms around they would try to infect anyone and anything.  Not that they'd get far....Servers are more on the receiving end of direct attacks by someone trying to get unauthorized access.  A much bigger issue.

> **Ub1476 said:**
> 
I never said Windows was insecure, but that Linux were safer. One point as you said, root/admin is not enabled by default. This has been fixed in Vista though (UAC), but in such a way that many disables it.
I wasn't disagreeing with you, simply saying that Windows could be secure.

> **Ub1476 said:**
> 
I heard it in almost every thread regarding viruses on this forum. There's a reason for ClamAV picks up Windows viruses isn't it?
ClamAV probably shares a database with both clients.  I don't use AV software because there's no need for it.  However, I think it's just in case you've already let it spread.  It **can't** write to the root folder without the permissions.

> **Ub1476 said:**
> IPTables is turned off by default. You do not need Firestarter to restrict ports, but most people prefer a graphical frontend.

IPTables is never "off" as far as I know, but there are generally no rules by default.

---

### Post by jken146 on 2008-01-02
> **~LoKe said:**
> That's a Windows problem.  And still, I'm almost certain that an app like explore2fs won't allow you to write to the ext2/3 partition (but it cold still be formatted).

The ext2IFS driver at fs-driver.org allows you to write to ext2/3 partitions.

And you're right, it is a Windows problem, but a problem nonetheless.  If someone downloads a windows virus in Linux and saves it on an ext3 partition, then mounts that partition in Windows, they can run the virus.  Of course if they had anti virus sortware for Windows with some sort of constantly running protection thy might not be able to run the thing.  It's not something Linux can do a lot about.

---

### Post by Mud.Knee.Havoc on 2008-01-02
> **Ub1476 said:**
> I heard it in almost every thread regarding viruses on this forum. There's a reason for ClamAV picks up Windows viruses isn't it?


This isn't because linux allows the virus to spread, it's because infected files can be sitting on a linux system (doing nothing harmful) and get passed on to a Windows system (where it will do something harmful).  

Linux users use ClamAV to make sure that everything on their system is clean.  Files infected with Windows viruses will not do anything to linux.

---

### Post by Mud.Knee.Havoc on 2008-01-02
> **~LoKe said:**
> Sorry bud, but someone who writes viruses is a hacker not just a cracker.  There are several different types of hackers, the most prominent two would be white hat and black hat hackers.

White hat hackers are the guys who mostly go around trying to find vulnerabilities in the systems of random businesses and tell them how to fix it.  Lots of people make a living off this; they don't always do it for free. ;)

Black hat hackers are basically the ones who find and exploit security vulnerabilities for their own personal/political gain.

You're correct in your black/white hat descriptions, but not entirely justified in correcting Steveway.  "Hacker" used to be a term describing guys who do cool stuff with technology, whereas "cracker" was a guy who did the bad stuff.  These terms are outdated, though, and now it's useless to try to keep the distinction alive - the public has gotten its claws into the term and has been using it incorrectly for so long that it's now accepted to refer to a hacker as a guy who does the bad stuff. :D

Some people are still trying to hold on to the original meanings, but they're fighting a losing battle (actually, a battle that has been lost for decades) - sorry Steveway! ;)

---

### Post by ~LoKe on 2008-01-02
> **Mud.Knee.Havoc said:**
> You're correct in your black/white hat descriptions, but not entirely justified in correcting Steveway.  "Hacker" used to be a term describing guys who do cool stuff with technology, whereas "cracker" was a guy who did the bad stuff.  These terms are outdated, though, and now it's useless to try to keep the distinction alive - the public has gotten its claws into the term and has been using it incorrectly for so long that it's now accepted to refer to a hacker as a guy who does the bad stuff. :D

Some people are still trying to hold on to the original meanings, but they're fighting a losing battle (actually, a battle that has been lost for decades) - sorry Steveway! ;)

A "Hacker" is someone who makes an electronic (telephone, computer, etc) do something it's not supposed to do.  So, a cracker is still a hacker, just not a nice one. ;)

---

### Post by thelatinist on 2008-01-02
This whole thread is getting a little off topic.  To get back to **rraj.be**'s original question, there are several reasons Linux is more secure than Windows:

[LIST=1]
[*]There are fewer viruses and spyware and malware applications written for Linux.

[*]Security holes tend to get patched more quickly in such an active development community.

[*]It does not have a very insecure web browser (IE) built into the operating system in such a way that it is almost impossible to remove without breaking the system.

[*]The system of user priviliges prevents applications from installing themselves without your knowledge and inhibits their spread.

[*]The repository system is safer than downloading unknown software from the Internet.

[*]No ActiveX.[/LIST]

That'll do for a start.  Anyone have any others to add?

---

### Post by PeterJS on 2008-01-02
> **Mud.Knee.Havoc said:**
> 
Some people are still trying to hold on to the original meanings, but they're fighting a losing battle (actually, a battle that has been lost for decades) - sorry Steveway! ;)

Hey, I for one refuse to give up the linguistic difference The public may be uninformed and misusing the term but that's only because the people in the know let them. I go out of my way to correct people when possible, and if everybody stepped up and corrected people we could get this mess cleaned up in a few years.

---

### Post by ~LoKe on 2008-01-02
> **PeterJS said:**
> Hey, I for one refuse to give up the linguistic difference The public may be uninformed and misusing the term but that's only because the people in the know let them. I go out of my way to correct people when possible, and if everybody stepped up and corrected people we could get this mess cleaned up in a few years.

I used to be the one to correct people when they spoke of hackers and crackers, but if you get down to definitions, a cracker is a hacker.

---

### Post by PeterJS on 2008-01-02
> **~LoKe said:**
> I used to be the one to correct people when they spoke of hackers and crackers, but if you get down to definitions, a cracker is a hacker.

I'll grant you that a cracker is a sub set of hacker. All crackers are hackers, but not all hackers are crackers.

---

### Post by eolson on 2008-01-02
I think I need another beer!

---

### Post by ~LoKe on 2008-01-02
> **PeterJS said:**
> I'll grant you that a cracker is a sub set of hacker. All crackers are hackers, but not all hackers are crackers.

Depends which definition of hacker you go by.  All white hat hackers are crackers. ;)

---

### Post by eolson on 2008-01-02
I gave up on this argument 20 years ago.

---

### Post by downhillgames on 2008-01-04
> **aysiu said:**
> 1. Most Windows users use Windows XP and operate as administrator, because the way XP is set up, it's too much trouble to run as a limited user.

2. There is a higher percentage of Windows users who are not computer savvy and thus are more susceptible to social engineering, which is how a lot of breaches in security happen.

3. Windows is a bigger target on the desktop/laptop scene and has more malware produced for it (almost the computer equivalent of living in a "bad neighborhood").

It says your forum staff... I question why.
1) True, but no relevance[ was said].
2) Wrong.
3) So extremely wrong I could cry.

[http://www.theregister.co.uk/security/security_report_windows_vs_linux/#execsummary](http://www.theregister.co.uk/security/security_report_windows_vs_linux/#execsummary)
Enjoy.

> **eolson said:**
> I gave up on this argument 20 years ago.
Well said.

---

### Post by hyper_ch on 2008-01-04
> **downhillgames said:**
> It says your forum staff... I question why.
1) True, but no relevance[ was said].
Sure it has relevance:
By finding a security hole in Windows you can control the whole system then as admin. By finding a security hole in a linux application you are (most likely) to be restricted controling that one application.
So if Windows users wouldn't run as administrators, there's also less things one can do with that security hole.

> **downhillgames said:**
> 
2) Wrong.

Why?

---

### Post by aysiu on 2008-01-04
> **downhillgames said:**
> It says your forum staff... I question why. Go ahead and question it. I hope you have fun doing so.

> 1) True, but no relevance[ was said]. Of course it's relevant. The original question was [I]generaly there is a opinion that linux bases os's are not much infected by virus or spy ware as windows get.I am a new guy to ubuntu and linux.

could any one give me in depth reason for this......[/I]

That's one of the reasons Windows is more infected--the habits of Windows users.

> 2) Wrong. Not a very thorough rebuttal.

> 3) So extremely wrong I could cry. Again, no reason given.

> [http://www.theregister.co.uk/security/security_report_windows_vs_linux/#execsummary](http://www.theregister.co.uk/security/security_report_windows_vs_linux/#execsummary)
Enjoy. I've read it. So what?

Even if Linux is more secure by design, the end user ultimately determines whether the operating system gets breached or not, since most attacks take advantage of social engineering or too-simple passwords. And, actually, if you run Windows XP as a limited user, it can be quite secure. As I said before, though, most Windows users run Windows as administrator.

---

