---
title: "antivirus for ubuntu"
date: 2007-03-08
forum: Recurring Discussions
---

### Post by prrao3 on 2007-03-08
hi everybody!!
i was serching net for antiviruses for ubuntu
i came across F-PROT.  AVAST ,  BIT-DEFENDER
does anybody have any feedback on any of them 
do u know any good anti-virus and firewall  for ubuntu??
thanks in advance

---

### Post by Del Boy on 2007-03-08
You don't really need a AV for linux. Try firestarter...

Edit:
```
sudo aptitude update
sudo aptitude install firestarter
```

It's a frontend for iptables.

---

### Post by compiledkernel on 2007-03-08
Firewall: sudo apt-get install firestarter 

AV: not nessecary, however -- [http://jodrell.net/projects/aegis](http://jodrell.net/projects/aegis), youll find Aegis in Add/Remove or Synaptic if you need it.

---

### Post by steve101101 on 2007-03-08
> **Del Boy said:**
> You don't really need a AV for linux. Try firestarter...


I agree

---

### Post by Mizled on 2007-03-08
[http://avast.com/eng/download-avast-for-linux-edition.html](http://avast.com/eng/download-avast-for-linux-edition.html)

Grab the .deb package of Avast and enjoy! You have to signup but it's completely free.

---

### Post by Malac on 2007-03-08
ClamAV with ClamTK are good. They are in repos.

---

### Post by Ek0nomik on 2007-03-08
In comparison to Windows, you probably won't need any AV software unless you are really hammering away at bad sites.

---

### Post by Perfect Storm on 2007-03-08
Antivirus for linux : Not needed

Ubuntu comes with Firewall by default (IPtablets), firestarter is only a frontend for it.

---

### Post by girard on 2007-03-12
i'm also new to the linux movement. recently installed 6.10 but still using XP as i want to learn the basics first - not even knowledgeable about the terminal and commands. SO WHAT ABOUT SPYWARE - and all other harmful stuff that you dread of as a windows-to-linux user?

---

### Post by Timtro on 2007-03-12
I really don't think one more 'you don't need it' is necessary, but I will add that I've used Avast on Windows for years and it is fabulous and FREE! (to non commercial users).

---

### Post by zipperback on 2007-12-29
> **girard said:**
> i'm also new to the linux movement. recently installed 6.10 but still using XP as i want to learn the basics first - not even knowledgeable about the terminal and commands. SO WHAT ABOUT SPYWARE - and all other harmful stuff that you dread of as a windows-to-linux user?

The manner in which the user security levels are handled in Linux, generally prevent Spyware and Virus payloads from being a problem. Spyware is a problem on the Window$ platform for example, because it does very little to prevent standard user level accounts from creating system level changes and therefore it is highly vulnerable to system level exploitations and security compromise issues.

Some general advice I often give to people who ask me about staying safe and secure with Linux.

* Don't use your root account as a general purpose account. Use a user level account.

* Install software from reputable sources. In other words install validated packages only from official Ubuntu repositories.

* Use open source solutions and try to stay away from using closed source solutions wherever possible.

* If you are unsure of something, then check with the Linux community and see what they have to say about your concerns.

* Use a firewall to protect your system from unauthorized access.

* There are anti-virus solutions available for Linux, if you feel you need them. Then please by all means use one. It doesn't hurt to have that extra level of protection.


When it doubt. ASK! :)

zipperback
:popcorn:

---

### Post by hyper_ch on 2007-12-29
Antivirus is not needed on linux. AV programs act retroactiv. Meaning they (mostly) handle only viruses that are known. If a virus gets known (there are about 60 known viruses for Linux compared to 40'000 for windows) then linux get patched and the virus will become ineffective. Just keep yourself updated with security updates...

Some other reasons have also been told already. Normally you don't run a provileged account here and get your software from trusted sources only.

By default there are no services listening to the ports. So a firewall is IMHO not needed. Only when you are going to add server services then you should worry about a firewall and - as already pointed out - firestarted is just a frontend for iptables.

---

### Post by Gone fishing on 2007-12-29
As a slight voice of dissent - an av is useful if you share files with Windows users your system wont be damaged by viruses but you can still pass them on to Windows users.

the AVG av for Linux can be found here [http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl) and although I prefer the Avast for Windows over AVG the AVG Linux looks better than Avast Linux. Antivir also has a good Linux av with gui

---

### Post by hyper_ch on 2007-12-29
> **Gone fishing said:**
> an av is useful if you share files with Windows users your system wont be damaged by viruses but you can still pass them on to Windows users.

I tend to think that's up to Windoze users to protect themselves. Why should I waste my resources to do a job that belongs into their domain?

---

### Post by eolson on 2007-12-29
If it will ease ur twitchies,  go here

[http://www.symantec.com/business/security_response/threatexplorer/threats.jsp](http://www.symantec.com/business/security_response/threatexplorer/threats.jsp)

click on any virus and see which systems it affects.

---

### Post by davarino on 2007-12-29
As a wise old man said 2100 years ago, "Don't say *anything* is impossible."

Viruses and other nasties **can** and **do** appear in the the Linux/Unix world. Anyone who says differently is either blind or deaf - and usually because s/he wishes to live in the world of faeries.

There are many well-known stories about security breaches in *n*x systems.

Just last year, some Ubuntu Iso-download servers were cracked! Despite the excuses that were made at the time: the Emporer's clothes were very lightweight. The clothes may have been mended, but new clothes are being made in the same workrooms.

There are continual attacks on programs that run on Linux: in the past year, both Firefox and Opera have had serious exposures. To say that browsers are unassailable in either Linux or Windows is to deny the grotesquely obvious.

Read[COLOR="Blue"] [The Cuckoo's Egg]("http://en.wikipedia.org/wiki/The_Cuckoo's_Egg")[/COLOR] to see what happened with US nuclear secrets because of a "movemail" flaw exploited by a KGB hacker. Admittedly old news, but there have been no changes in the way that *n*x code is vetted since that time.

Yes, use reasonable precautions.

And just as an observation: a really good Linux-specific anti-malware system (equivalent to Kaspersky or better) is long overdue to protect our machines.*** It's simply a matter of time and growth of user base before we find a Linux-specific virus clobbering all of us.***

---

### Post by jas0 on 2007-12-29
> **davarino said:**
> As a wise old man said 2100 years ago, "Don't say *anything* is impossible."

Viruses and other nasties **can** and **do** appear in the the Linux/Unix world. Anyone who says differently is either blind or deaf - and usually because s/he wishes to live in the world of faeries.

There are many well-known stories about security breaches in *n*x systems.

Just last year, some Ubuntu Iso-download servers were cracked! Despite the excuses that were made at the time: the Emporer's clothes were very lightweight. The clothes may have been mended, but new clothes are being made in the same workrooms.

There are continual attacks on programs that run on Linux: in the past year, both Firefox and Opera have had serious exposures. To say that browsers are unassailable in either Linux or Windows is to deny the grotesquely obvious.

Read[COLOR=Blue] [The Cuckoo's Egg]("http://en.wikipedia.org/wiki/The_Cuckoo%27s_Egg")[/COLOR] to see what happened with US nuclear secrets because of a "movemail" flaw exploited by a KGB hacker. Admittedly old news, but there have been no changes in the way that *n*x code is vetted since that time.

Yes, use reasonable precautions.

And just as an observation: a really good Linux-specific anti-malware system (equivalent to Kaspersky or better) is long overdue to protect our machines.*** It's simply a matter of time and growth of user base before we find a Linux-specific virus clobbering all of us.***


The only issue I see with your post (which is for the most part inarguably true) is that it doesn't really promote the use of anti-virus software, over, say, running aptitude safe-upgrade once in a while. 

Look at the Windows world. There are at least 10 serious anti-malware software providers who spend every waking moment trying to scour the internet for bad stuff, analyze it and write signatures for it. The result? You still can't relax and do what you want on your Windows machine. The best anti-malware was, is, and will be user behavior modification.

>  Just last year, some Ubuntu Iso-download servers were cracked!Anti-malware can't solve this. Once the bad guys have access to your house, it doesn't matter how secure your office safe is.

>  There are continual attacks on programs that run on Linux: in the past year, both Firefox and Opera have had serious exposures.Without even researching this I have a hunch that you could update your software for said flaws ages before a solution was provided by a anti-malware provider. 

So in conclusion, reasonable precautions should not be having to install software to protect you from other software. Reasonable precautions should be modified user behavior. Anti-malware is in my opinion a bad, ineffective idea.

---

### Post by davarino on 2007-12-30
> **jas0 said:**
> 
[R]easonable precautions should not be having to install software to protect you from other software. Reasonable precautions should be modified user behavior. Anti-malware is in my opinion a bad, ineffective idea.

Agreed.

The problem, to extend your metaphor, is that burglars **do** burglarize even the houses of people who have moved to good neighborhoods and follow police recommendations to avoid burglaries.

Anti-malware software is similar to the weapon you pull out to make the burglar drop his loot: it didn't stop him from getting in, but it sure isn't going to make his job as easy as he thought it would be.

My remarks about an anti-malware app being needed were pretty much an afterthought, by the way.

The main thrust of my remarks was that Linux is **not** a secure system. (FYI, I have not yet seen a truly secure system.)

Linux may be good, but there are demonstrated weaknesses both in the software and in the software development and audit processes. The processes show no sign of being changed in any near future.

Remarks like "you don't need protection, just choose the right partner", which are on this thread, minimize the very real threat that exists. What about the "rape victims"? What about the bamboozled?

IIt reminds me of the situation of a friend of mine who contracted Hepatitis C from her (truly good) husband who had had the virus dormant for 20 years: if the threat is unknown or unacknowledged, the threat exists nevertheless. (And we know that a lot of people are still going to fall in love and get married, no matter what diseases are wandering about, and no matter how careful they are about partners.)

Good computer hygiene includes acknowledgment of the danger, avoidance of vectors of infection, prophylaxis, and post-exposure measures. Minimization of the importance of any of these measures is harmful to the overall situation.

---

### Post by jeffus_il on 2007-12-30
Keep your house locked and you have less chance of a burglar entering, Linux has a nice lock called sudo, without you password, it is difficult for a program to do great damage. Most Windows installations that I know run as administrator, on open door for malicious viruses, equivalent to running as root in Linux, which only nuts do (not the ones grown in Brazil)

Also sticking to open source means that someone can read it, and with all the distros and sourceforge etc. someone can pick up malicious code, With windows you need antivirus pattern matching programs running wildly through your disk trying to find anything that looks suspicious, reporting on anything that moves to justify you having bought the software.

Purchase of antivirus software is indirect support of viruses, They have a financial interest in the reproduction and dispersion of those mean litlle viruses.

:idea:

---

### Post by LaRoza on 2007-12-30
I don't use AV on Windows, I consider AV to be a waste of resources. I use a safe browser, and a good firewall and my brains. No infections to date, except WGA.

---

### Post by scorp123 on 2007-12-30
> **davarino said:**
>  There are many well-known stories about security breaches in *n*x systems.  But these are deeds of **human** hackers ... and not some automated virus launched by a script kiddie. And usually hackers target servers (e.g. web servers, mail servers, application servers, and so on) that are running some sort of service (e.g. database, some sort of e-shop, whatever) and are accessible to the outside world via the Internet. You as a home user are probably not running such kind of service 24 x 7 and are most likely not accessible from the outside (because you are probably behind a router + firewall). In other words: You are comparing apples and oranges here. The virus threat level on Linux is nowhere as high as it is on Windows. And human hackers are a different story.

> **davarino said:**
>  Just last year, some Ubuntu Iso-download servers were cracked!  By **humans** who obviously found a way into the system  ... this was not done by some some stupid script-kiddie virus (as it constantly happens on Windows). BIG difference!

> **davarino said:**
>  It's simply a matter of time and growth of user base before we find a Linux-specific virus clobbering all of us.[/B][/I]  That's just plain silly FUD and panic-making, IMHO.

You talk as we still were in the early 80's and as if the "Morris" worm was still spreading, when in fact the Unix world has learned from that experience and a virus would have a very very hard time these days to even come remotely close to the spreads and mass-infections we see on Windows.

---

### Post by jrthom444 on 2007-12-31
Hey everyone,

Was doing some research on Unix/Linux viruses.  While they are not immune to such unpleasentries it seems very unlikely that your computer will become infected.  Linux/Unix has less than 1% of the total number of virus'/malware/spyware that windows has.  Statistically speaking you are far safer than someone who runs windows with a really tripped out firewall.

Just don't run something in root that you don't trust.  Check the forum first if you are not sure.

---

### Post by HermanAB on 2007-12-31
Heh, even the Asus Eee PC has an useless anti-virus application pre-installed, to keep the ex-Windowsers pacified.  I thought it was pretty funny.  The code of a typical Linux only virus scanner would be rather simple.  Something like this:

#! /bin/bash
echo Sooper Dooper Linux Virus Scanner
sleep(5)
echo Commencing countdown, engines on...
sleep(10)
echo Scanning...
sleep(20)
echo Almost done...
sleep(10)
echo Wait for it...
sleep(10)
echo Drum roll!
sleep(10)
echo Woohoo! No virus found!

---

### Post by Perfect Storm on 2007-12-31
We need a gui for the script: Well some people like flashy thing why not include drumroll.ogg and a progress bar :mrgreen:

---

### Post by jrthom444 on 2007-12-31
Haha Nice!

---

### Post by barney385 on 2007-12-31
Have there ever been any issues with downloaded torrent files?

:popcorn:

---

### Post by ayenack on 2007-12-31
Don't know if this has been suggested but it's always a good idea to have rkhunter (Root kit Hunter) installed. rkhunter scans for worms, suspect files, hidden files etc and it's actually relevant to your linux box.

**sudo apt-get install rkhunter**

Then update it.

**sudo rkhunter --update**

Then your ready to do a scan which will take about a 40 seconds or so.

**sudo rkhunter -c -sk**

It'll probably bring up some warnings which can probably be ignored. If you're not sure do a google for the files that have warnings. In general if it shows no suspect files at the end you should be fine.

---

### Post by tommytomthms5 on 2007-12-31
> **ayenack said:**
> Then your ready to do a scan which will take about a 40 seconds or so.

hahaha 40 seconds??? i know on microsux winblows it takes like an hour!

---

### Post by zipperback on 2007-12-31
> **barney385 said:**
> Have there ever been any issues with downloaded torrent files?

:popcorn:


What kind of issues would you be referring to?

- zipperback
:popcorn:

---

### Post by Dimitriid on 2007-12-31
Actually, I could use a Linux antivirus specifically made to catch and clean up virus infections on windows environments. I get asked to do a lot of support and most of the time I have to clean up something from a bricked windows installation on a system that otherwise has perfect hardware functionality.

Then I might be able to get a small distro with an antivirus and ntfs read so I can quickly clean up and fix a windows install.

---

### Post by jas0 on 2007-12-31
> **davarino said:**
> Agreed.

The problem, to extend your metaphor, is that burglars **do** burglarize even the houses of people who have moved to good neighborhoods and follow police recommendations to avoid burglaries.

Anti-malware software is similar to the weapon you pull out to make the burglar drop his loot: it didn't stop him from getting in, but it sure isn't going to make his job as easy as he thought it would be.

My remarks about an anti-malware app being needed were pretty much an afterthought, by the way.

The main thrust of my remarks was that Linux is **not** a secure system. (FYI, I have not yet seen a truly secure system.)

Linux may be good, but there are demonstrated weaknesses both in the software and in the software development and audit processes. The processes show no sign of being changed in any near future.

Remarks like "you don't need protection, just choose the right partner", which are on this thread, minimize the very real threat that exists. What about the "rape victims"? What about the bamboozled?

IIt reminds me of the situation of a friend of mine who contracted Hepatitis C from her (truly good) husband who had had the virus dormant for 20 years: if the threat is unknown or unacknowledged, the threat exists nevertheless. (And we know that a lot of people are still going to fall in love and get married, no matter what diseases are wandering about, and no matter how careful they are about partners.)

Good computer hygiene includes acknowledgment of the danger, avoidance of vectors of infection, prophylaxis, and post-exposure measures. Minimization of the importance of any of these measures is harmful to the overall situation.

Yes, those are valid points. I think that the logical end of the argument is that while security awareness needs to be BIG, security-specific software may not be the best solution, or a substitute to security awareness. If users were educated in not running as administrators on Windows machines, that by itself would eliminate 50% of the Windows computer infections and widdle down on the vask Windows zombie army. 

Defense in depth is always a good thing, but blind and ignorant defense is never in depth.

We can go on all kinds of tangents at this point in the argument

---

### Post by hyper_ch on 2008-01-01
> **Dimitriid said:**
> Then I might be able to get a small distro with an antivirus and ntfs read so I can quickly clean up and fix a windows install.
Wouldn't that result in putting *nix on it? I tend to think windoze is an infection itself ^^

---

### Post by scorp123 on 2008-01-01
> **Dimitriid said:**
> Actually, I could use a Linux antivirus specifically made to catch and clean up virus infections on windows environments. .... Then I might be able to get a small distro with an antivirus and ntfs read so I can quickly clean up and fix a windows install. There used to be a Linux live CD with anti-virus software on it (to catch Windows viruses!): "Linux Defender" by the BitDefender company. But this thing hasn't been updated in ages. But it probably will still catch most older Windows viruses that are still floating around.

[http://www.bitdefender.com/bd/site/presscenter.php?menu_id=25&n_id=58](http://www.bitdefender.com/bd/site/presscenter.php?menu_id=25&n_id=58)
[http://www.mckeay.net/secure/2004/11/experience_with_bitdefender_li.html](http://www.mckeay.net/secure/2004/11/experience_with_bitdefender_li.html)

Downloads (probably outdated?):
[http://archive.bitdefender.com/bd/site/mirrors.php](http://archive.bitdefender.com/bd/site/mirrors.php)

---

### Post by Mazza558 on 2008-01-01
> **LaRoza said:**
> I don't use AV on Windows, I consider AV to be a waste of resources. I use a safe browser, and a good firewall and my brains. No infections to date, except WGA.

QFT.

I'm behind 2 firewalls (router and the XP firewall - which isn't bad), don't run an AV and use my brains. I haven't had a virus on my PC for over 2 years now.

---

### Post by hyper_ch on 2008-01-01
> **Mazza558 said:**
>  use my brains

The use of brains is IMHO one of the biggest defenses against malware.

---

### Post by quinnten83 on 2008-01-01
> **Dimitriid said:**
> Actually, I could use a Linux antivirus specifically made to catch and clean up virus infections on windows environments. I get asked to do a lot of support and most of the time I have to clean up something from a bricked windows installation on a system that otherwise has perfect hardware functionality.


Then I might be able to get a small distro with an antivirus and ntfs read so I can quickly clean up and fix a windows install.


try puppy linux on a memory stick with ntfs-3g and avast installed?

---

### Post by Dimitriid on 2008-01-01
> **hyper_ch said:**
> Wouldn't that result in putting *nix on it? I tend to think windoze is an infection itself ^^

Well hopefully it would result in that, and I do try to point out how windows calling home and disabling itself with WGA means they won't really know when it can happen again.

But alas some people are not ready to give up windows, but do need their pc up and running.

---

