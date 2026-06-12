---
title: "[SOLVED] R there any antivirus, or antispyware, in Ubuntu 8.10?"
date: 2008-11-23
forum: Recurring Discussions
---

### Post by Jammanuser on 2008-11-23
i'm kind of new to Ubuntu, so maybe i just haven't found it yet, but it doesn't look like there's any kind of antivirus or antispyware programs installed on my version of Ubuntu 8.10...or maybe its just different in Ubuntu, and the OS uses some other kind of thing to keep security risks such as virii and spyware off ur system!!! i don't know, and i would appreciate if someone would explain it to me!

Thanks!

---

### Post by Dr Small on 2008-11-23
There are no viruses that are in the wild, nor spyware/adware that could infect your system. There are proof of concept viruses, but Linux is so strong built around security, that *you* would have to enable them for them to work properly.

---

### Post by Jammanuser on 2008-11-24
> **Dr Small said:**
> There are no viruses that are in the wild, nor spyware/adware that could infect your system. There are proof of concept viruses, but Linux is so strong built around security, that *you* would have to enable them for them to work properly.

what do u mean? r u saying that spyware and viruses don't exist for linux? :confused: so there's no need for antispyware or antivirus on it? it seems like spyware would exist for **all** OS and platforms! r u saying that it only exists for Windows? 

i would be thankful if u would explain!

---

### Post by johnkzin on 2008-11-24
If you're really worried about it, there's a software project called ClamAV.  I don't know if they're in the Ubuntu packages, or if there are .deb's for them, but it's a pretty mature package.

If there isn't an Ubuntu package for it, there should be.

---

### Post by sambarusty on 2008-11-24
I have to agree, it is one of the benifits of the linux world.  I have had a dual boot machine for about 9 years and never had the virus or spyware problems on the linux side that I had on the windows side.

---

### Post by Twitch6000 on 2008-11-24
I will break this down for you before everyone else confuses you.

Yes there is viruses for linux(no spyware though)

However the viruses that are out there is very little(last reported under 1000)

Then with this number of viruses alot of them were test viruses and such. Meaning they have been patched and you do not even have to worry about them.

However if you are worried about viruses and such there is ClamAV in the repos.

Just open add/remove type that in and install it.

It mainly scans for windows viruses,however it does scan for the known Linux viruses aswell.

Truly I would not worry about installing ClanAV unless you are running a server.

---

### Post by theApokalypsis on 2008-11-24
Ah, the transitional shock continues! nice save twitch lol

whats that? the echos of a growing chant....

"I'm never going back"


in a serious note: its better to not have to deal with extra sluggish monitoring tools. :D

---

### Post by johnkzin on 2008-11-24
> **Twitch6000 said:**
> 
Truly I would not worry about installing ClanAV unless you are running a server.

Or if you're running anything that is macro-compatible with MS Office, as Office Macro Viruses are cross platform in nature. (I don't recall if Open Office is currently vulnerable to Office Macro Viruses, but I seem to recall that Star Office was, in its original versions)

Or, if you're forwarding Office documents you got from other people onto 3rd parties (where you may not be infected yourself, but you may be acting as a disease-carrier by passing the infection on to other people).

In the latter case, your own immunity is irrelevant to whether or not you're being a good net.citizen.

Better to be safe than sorry.  These aren't "linux viruses", but that doesn't mean you're without worry.  If your Office suite is vulnerable, you're vulnerable.  If you pass Office documents along to third parties without cleaning them, you're potentially infecting your correspondents.

---

### Post by -grubby on 2008-11-24
Linux has malware, yes. Every piece of malware is patched, and I can guarantee you will never get viruses or spyware on Ubuntu. However, there are other malicious things in the Linux world, watch out for shoddy repositories, [malicious commands](http://ubuntuforums.org/announcement.php?a=54), and things that ask for root when they shouldn't

---

### Post by Jammanuser on 2008-11-24
WOW!!! :shock: so linux is pretty much immune to such threats as trojans, adware, malware, and such??? that's AWESOME!!! :) sweet! great! absolutely WONDERFUL!!! that means i wont have to take up more space on my hard drive then, just to protect my computer from malicious **** that lurks on the internet! yay! :)

about ClamAV...i'd rather not download and install it on my computer, if there's no serious threat with viruses on Linux!!!

---

### Post by Jammanuser on 2008-11-24
> **nathangrubb said:**
> Linux has malware, yes. Every piece of malware is patched, and I can guarantee you will never get viruses or spyware on Ubuntu. However, there are other malicious things in the Linux world, watch out for shoddy repositories, [malicious commands](http://ubuntuforums.org/announcement.php?a=54), and things that ask for root when they shouldn't

ok...i'll definitely take that under consideration then!!! i'll make sure never to run any command on my computer that hasn't been recommended by trusted sources first! 

thanks for the warning! :)

and what did u mean by shoddy repositories? :confused: it would help a lot if u would explain!

Thanks!

---

### Post by Twitch6000 on 2008-11-24
> **Jammanuser said:**
> ok...i'll definitely take that under consideration then!!! i'll make sure never to run any command on my computer that hasn't been recommended by trusted sources first! 

thanks for the warning! :)

and what did u mean by shoddy repositories? :confused: it would help a lot if u would explain!

Thanks!

By shoddy repos he means repos that just seem not trust worthy.

Or repos that seem not to great to download from.

Basically if you don't think you should download from it don't do it :).

---

### Post by Ozor Mox on 2008-11-24
> **Jammanuser said:**
> WOW!!! :shock: so linux is pretty much immune to such threats as trojans, adware, malware, and such??? that's AWESOME!!! :) sweet! great! absolutely WONDERFUL!!! that means i wont have to take up more space on my hard drive then, just to protect my computer from malicious **** that lurks on the internet! yay! :)

about ClamAV...i'd rather not download and install it on my computer, if there's no serious threat with viruses on Linux!!!

Don't forget that no operating system is immune from viruses. However, thanks to the much better security model in Ubuntu (and Linux in general), such as not being an administrator/root user by default, as well as better* patching of security holes, it is generally not necessary to install anti-virus software. In fact, the only reason most people do is to protect their Windows using friends from picking up viruses that they might accidentally pass along.

* I can't back this up with numbers, but I'm pretty sure I've seen a comparison of the number of critical/security related bugs open in Windows and Ubuntu (and possibly other distributions) and how fast they are patched and Ubuntu (and other Linux) came out considerably on top.

---

### Post by Jammanuser on 2008-11-24
> **Twitch6000 said:**
> By shoddy repos he means repos that just seem not trust worthy.

Or repos that seem not to great to download from.

Basically if you don't think you should download from it don't do it :).

ok..thanks! thanks for the advice! :)

---

### Post by Jammanuser on 2008-11-24
> **Ozor Mox said:**
> Don't forget that no operating system is immune from viruses. However, thanks to the much better security model in Ubuntu (and Linux in general), such as not being an administrator/root user by default, as well as better* patching of security holes, it is generally not necessary to install anti-virus software. In fact, the only reason most people do is to protect their Windows using friends from picking up viruses that they might accidentally pass along.

* I can't back this up with numbers, but I'm pretty sure I've seen a comparison of the number of critical/security related bugs open in Windows and Ubuntu (and possibly other distributions) and how fast they are patched and Ubuntu (and other Linux) came out considerably on top.


ok...cool! i'm not in the habit of passing documents around right now, but **if** i ever do it, i'll remember ur advice, and probably install ClamAV first! :)

Cheers!

---

### Post by johnkzin on 2008-11-24
> **Ozor Mox said:**
> However, thanks to the much better security model in Ubuntu (and Linux in general),


s/Linux/Unix/

---

### Post by klange on 2008-11-24
Get ClamAV (clamav)
The get ClamTK (clamtk)
Then complain that ClamTK has a horrible interface and I'll give you my fork.

---

### Post by amauk on 2008-11-24
[http://www.linux.com/articles/60208]("http://www.linux.com/articles/60208")

> One of the most common questions I hear new Linux users ask is "What program should I use for virus protection?" Many of them lose faith in me as a source of security information when I reply, "None." But you really don't need to fear malware on your new platform, thanks to the way Linux is built.

Savvy Windows users have to watch their virus checkers as closely as the head nurse in the ICU keeps an eye on patient monitors. Often, the buzz in the Windows security world is about which protection-for-profit firm was the first to discover and offer protection for the malware du jour -- or should I say malware de l'heure? The only thing better than having backed the winning Super Bowl team come Monday morning at the office coffeepot is having the virus checker you use be the one winning the malware sweepstakes that weekend.

If a rogue program finds a crack in your Windows armor, paying $200 per infection to have your machine scrubbed and sanitized by the local goon^H^H^H^H geek squad not only helps to reinforce the notion that you have to have malware protection, but that it has to be the right protection, too. The malware firms are aware of this, and all of their advertising plays upon the insecurity fears of Windows users and the paranoia that results. Chronic exposure and vulnerability to malware has conditioned Windows users to accept this security tax.

It's no wonder, then, that when Windows users are finally able to break their chains and experience freedom on a Linux desktop, they stare at me in disbelief when I tell them to lay that burden down. They are reluctant to stop totin' that load. They have come to expect to pay a toll for a modicum of security.

I try to explain that permissions on Linux make such tribute unnecessary. Without quibbling over the definitions of viruses and trojans, I tell them that neither can execute on your machine unless you explicitly give them permission to do so.

Permissions on Linux are universal. They cover three things you can do with files: read, write, and execute. Not only that, they come in three levels: for the root user, for the individual user who is signed in, and for the rest of the world. Typically, software that can impact the system as a whole requires root privileges to run.

Microsoft designed Windows to enable outsiders to execute software on your system. The company justifies that design by saying it enriches the user experience if a Web site can do "cool" things on your desktop. It should be clear by now that the only people being enriched by that design decision are those who make a buck providing additional security or repairing the damage to systems caused by it.

Malware in Windows Land is usually spread by email clients, browser bits, or IM clients, which graciously accept the poisoned fruit from others, then neatly deposit it on their masters' systems, where malware authors know it will likely be executed and do their bidding -- without ever asking permission.

Some malware programs require that you open an attachment. Others don't even require that user error. By hook or by crook, malware on Windows often gets executed, infecting the local system first, then spreading itself to others. What a terrible neighborhood. I'm glad I don't live there.

On Linux, there is built-in protection against such craft. Newly deposited files from your email client or Web browser are not given execute privileges. Cleverly renaming executable files as something else doesn't matter, because Linux and its applications don't depend on file extensions to identify the properties of a file, so they won't mistakenly execute malware as they interact with it.

Whether newcomers grok permissions or not, I try to explain the bottom line to them: that because they have chosen Linux, they are now free of having to pay either a security tax up front to protect themselves from malware, or one after the fact to have their systems sterilized after having been infected.

So Linux is bulletproof? No. Bulletproof is one of the last stages of drunkenness, not a state of security. Linux users, like users on every operating system, must always be aware of security issues. They must act intelligently to keep their systems safe and secure. They should not run programs with root privileges when they are not required, and they should apply security patches regularly.

Misleading claims and false advertising by virus protection rackets to the contrary, you simply don't need antivirus products to keep your Linux box free of malware.

---

### Post by MaxIBoy on 2008-11-24
NO operating system is immune from trojans.

A trojan isn't a proper virus. It relies on fooling the user into installing it. Viruses can install themselves and spread themselves without you having to click on anything. You can protect yourself from trojans by not being stupid.

Viruses rely on certain security holes, such as "buffer overflows" (the jailbreak exploit on an iPhone actually uses a buffer overflow to implant code in the RAM, where it will be accidentally run by the OS later.) All Linux viruses currently in the wild rely on security holes that have been fixed right away after the virus was released, so if you update your computer regularly, you'll be fine. In fact, many Linux viruses are harmless, and they're just sent to security staff as a helpful way of pointing out the flaw, not with actual malicious intent.

---

### Post by johnkzin on 2008-11-24
> **amauk said:**
> So Linux is bulletproof? No. Bulletproof is one of the last stages of drunkenness, not a state of security. Linux users, like users on every operating system, must always be aware of security issues. They must act intelligently to keep their systems safe and secure. They should not run programs with root privileges when they are not required, and they should apply security patches regularly.

Misleading claims and false advertising by virus protection rackets to the contrary, you simply don't need antivirus products to keep your Linux box free of malware.

Both of those paragraphs can easily be applied to Windows.  And I call anyone who says that you should completely forgo a virus scanner on Windows, Linux, Mac, Solaris, etc. to be equally naive.


It's orders of magnitude less likely that you'll end up with an infection of some kind, true.  That doesn't make it intelligent to just blindly trust that you'll catch every piece of malware through other techniques (that's just pure arrogance).  Or that you'll never receive nor pass on an Office Macro Virus (that's just stupid, unless you don't use any Office compatible software).

Nor is this about "Misleading claims and false advertising by virus protection rackets to the contrary".  ClamAV is free.  The updates are free.  The front-ends for using it as a general purpose scanner are free.  The add-ons for tracking all sorts of other malware are free (Sanesecurity, MBL, MSRBL).

Use your brain.  Get ClamAV.  Get the add-on signature databases.  Use them.

---

### Post by Jammanuser on 2008-11-25
amauk: thanks for the great article! it was a **very** good read, and made me reconsider the whole antivirus thing again! there were a lot of people that noted that while linux may not have as much of a problem with viruses, malware and such, getting infected with a virus is still possible, although the chances r slim, and much less that for Windows, to be sure, and a couple people raised the point that even though they may not be a large threat right now, it is quite possible that malware authors will begin to write them for linux too, as the OS gains more and more popularity! 

i have decided that i would rather have ClamAV installed, just in case, since its always better to be safe than sorry! :) 

Thanks for the great read!

---

### Post by Jammanuser on 2008-11-25
> **johnkzin said:**
> Both of those paragraphs can easily be applied to Windows.  And I call anyone who says that you should completely forgo a virus scanner on Windows, Linux, Mac, Solaris, etc. to be equally naive.


It's orders of magnitude less likely that you'll end up with an infection of some kind, true.  That doesn't make it intelligent to just blindly trust that you'll catch every piece of malware through other techniques (that's just pure arrogance).  Or that you'll never receive nor pass on an Office Macro Virus (that's just stupid, unless you don't use any Office compatible software).

Nor is this about "Misleading claims and false advertising by virus protection rackets to the contrary".  ClamAV is free.  The updates are free.  The front-ends for using it as a general purpose scanner are free.  The add-ons for tracking all sorts of other malware are free (Sanesecurity, MBL, MSRBL).

Use your brain.  Get ClamAV.  Get the add-on signature databases.  Use them.

right! i suddenly realized my stupidity, after reading the article posted by one of the commenters on this thread! i have decided to get ClamAV, after all, just to be safe! better to be prepared then to assume that linux is invulnerable to viruses and such!

Thanks for the tip!

---

### Post by Grant A. on 2008-11-25
> **Jammanuser said:**
> right! i suddenly realized my stupidity, after reading the article posted by one of the commenters on this thread! i have decided to get ClamAV, after all, just to be safe! better to be prepared then to assume that linux is invulnerable to viruses and such!

Thanks for the tip!

It is a novel idea to be prepared, but I recommend you not take everything ClamAV says as 100% positive, ClamAV has tons of false positives and once locked up my bootloader because it was a little bigger than it was supposed to be (by like 1kb). Always ask the people on the forums if it is a virus or not, before locking it away. Btw, there is a nice little tool in the ubuntu repositories called firestarter. It is a very nice little firewall tool.

---

### Post by halovivek on 2008-11-25
hi 
the virus exists in the linux is very low and it is even negligible.
i am using linux system from 2001. till now i would to use to browse lot of sites including spyware sites and malware. which i dont know. i did not get any problem with it. but i did that in windows. i got lot of errors and problems.
so linux is safe.

---

### Post by Jammanuser on 2008-11-25
> **Grant A. said:**
> It is a novel idea to be prepared, but I recommend you not take everything ClamAV says as 100% positive, ClamAV has tons of false positives and once locked up my bootloader because it was a little bigger than it was supposed to be (by like 1kb). Always ask the people on the forums if it is a virus or not, before locking it away. Btw, there is a nice little tool in the ubuntu repositories called firestarter. It is a very nice little firewall tool.

ok...thanks for the tip!!! i'll be sure then to install firestarter on ubuntu...whenever, that is, i can boot into it again!!! 

here's the link to the thread in which i posted my problem:

[http://ubuntuforums.org/showthread.php?t=992506](http://ubuntuforums.org/showthread.php?t=992506)

---

