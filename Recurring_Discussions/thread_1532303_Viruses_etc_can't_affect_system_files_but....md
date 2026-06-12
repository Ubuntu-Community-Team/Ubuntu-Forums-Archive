---
title: "Viruses etc can't affect system files but..."
date: 2010-07-16
forum: Recurring Discussions
---

### Post by CandidMan on 2010-07-16
Sorry if I'm flogging a dead horse here but I can't seem to get around the idea it's "safe"/insignificant to run a virus as myself in my home folder.

I'm coming from Windows XP experience and was ultra-paranoid about system integrity(had CIS installed and Avira, plus others) after one bad incident with my only PC. My XP box was actually rendered useless by a certain Time Machine meant to protect it.:(

I can appreciate that denying viruses access to important system files stops unwanted behaviour. And denying viruses write access to binaries stops their spreading. So in effect a Linux virus has a hard time affecting a system as is stands.

But, is it safe to allow a virus, trojan or whatever to do anything it wants within the home folder.? 

For example, could a keylogger or similar write it's own files and have its own 'system' within home. Or, a worm extend its own connections using "/home/" as a base.

Again, apologies if retreading a tired topic. But I'll admit to being computer savvy, not technical

---

### Post by Peter09 on 2010-07-16
Think of it another way - yes you can write a virus or trojan to infect any operating system, especially if you aim to target a single machine. But hackers etc. are not interested in single machines they want to hit lots of machines.
 
Thats were the real difference lies, in windows its 'relativley' easy to jump an infection from one machine to another, therefore the virus spreads throughout the community. In Linux, it much harder to jump to the 'next' machine, due to the security barriers that Linux inherently has.
 
So to reiterate - yes you could get a trojan or virus on your machine if you are lax and somebody targets you. But in general nobody else will get it. 
 
Thats why none of them are in the wild - they all died out after a couple of infections :)

---

### Post by gradinaruvasile on 2010-07-16
No, it is not safe. Think about it, if it is a keylogger, it might send your passwords to anyone that might break into your system. .

---

### Post by CandidMan on 2010-07-16
Thanks for the prompt replies from Peter09 and gradinaruvasile.

I guess that explains why Linux malware is dead in the water.

To gradinaruvasile, thanks for the advice, but I wouldn't never deliberately install a keylogger or otherwise.

I guess the thing that's been playing on my mind is can an executable run as myself perform typical bad behaviour from the home directory?

That might sound like an intrinsically stupid statement if you know a lot about linux, but are you saying such an executable couldn't add a function without the need alter system files?

Thanks again

---

### Post by digitalcitizenx on 2010-07-16
Only use soft from trusted sources - ie: Ubuntu repositories

Until you get an idea on who is safe to use software from and who is not I recommend keeping your install as stock as possible.

If you are running Wine to use Windows applications then you may have a chance of contracting a virus.

I ALWAYS run Windows apps in Windows running in a Virtual Machine like VirtualBox.

I have the Windows OS's in .iso format so that IF I do contract a nasty bit of malware I simply reinstall the OS and go on about my business.

But overall you should be fine. Don't worry. Most of us have run Ubuntu for many years with no issues at all and have NEVER installed any type of antivirus software.

If you are worried too much about it, using Firefox simply install Flash Block and noscript (stops java scripting from running) and that should stop most of anything that you seem to be worried about.

---

### Post by eriktheblu on 2010-07-16
It wouldn't be safe, as there likely plenty of sensitive files that you can access with user permissions. It may not cripple or take over your system, but it could potentially compromise private information (passwords, etc.) or damage your data.

Best to stick with trusted software and update regularly. Probably not a big worry.

---

### Post by CandidMan on 2010-07-16
> **digitalcitizenx said:**
> Only use soft from trusted sources - ie: Ubuntu repositories

Until you get an idea on who is safe to use software from and who is not I recommend keeping your install as stock as possible.

If you are running Wine to use Windows applications then you may have a chance of contracting a virus.

I ALWAYS run Windows apps in Windows running in a Virtual Machine like VirtualBox.

I have the Windows OS's in .iso format so that IF I do contract a nasty bit of malware I simply reinstall the OS and go on about my business.

But overall you should be fine. Don't worry. Most of us have run Ubuntu for many years with no issues at all and have NEVER installed any type of antivirus software.

If you are worried too much about it, using Firefox simply install Flash Block and noscript (stops java scripting from running) and that should stop most of anything that you seem to be worried about.
Thanks.Have Wine and Noscript. Ran a couple of things in Wine I maybe should have thought twice about but my gut feeling from using Windows, installing my fair share of shareware is that they were alright.

Have virtualbox but no usable copy of windows. My backup XP was recovery partition that I couldn't get to after permanent BSOds. Eggs all in one basket or what? 

It's just mind boggling that if decent security is as simple as file permissions why haven't Windows implemented it before their UAC and why is it still flawed?

So basically, if I only have files in /home/ that I don't particularly care about, accidentally running an executable as limited user results in file copying/deletion at worst?

---

### Post by mike555 on 2010-07-16
to be safer don't run "Wine" or install anything in Windows that lets you write to your Linux partition (info for dual-booters)

---

### Post by philinux on 2010-07-16
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Moved to Recurring Discussions.

---

### Post by CandidMan on 2010-07-16
Thanks for the useful replies. I'm satisfied I've got a good idea of the type and scope of damage malware could to the system. Looks like the biggest threat *might* come from Wine.

A lot of what was said here confirmed bits and pieces gleaned from googling. But there's only so much googling the human brain can take. It's nice to hear these things from real people (no irony intended) :p

---

### Post by ankit singh on 2010-07-16
See wine cannot be a huge issue. When you give your permission to file to be executed on your system - Then the file can Release the Virus to the system.Just focus on what are installing. BUT - if you get Trojan Horse that can and will  Affect the system (If the Trojan Horse point to you modem/router).Just pay attention on what are you doing.Security is not a problem a big deal for a desktop user.

Remember in MS if anything goes wrong then MS and your respective antivirus is responsible and in linux if anything goes wrong then 99% of the time it is  user's fault.

---

### Post by RiceMonster on 2010-07-16
> **ankit singh said:**
> Remember in M$ if anything goes wrong then M$ and your respective antivirus is responsible and in linux if anything goes wrong then 99% of the time it is  user's fault.

Uh, no.

---

### Post by MadCow108 on 2010-07-16
> **ankit singh said:**
> 
Remember in M$ if anything goes wrong then M$ and your respective antivirus is responsible and in linux if anything goes wrong then 99% of the time it is  user's fault.
[/FONT][/COLOR][/FONT][/COLOR]

I can't sign that. It is always the (desktop) user, no matter of linux or windows.

If been a windows user 10 years and have never contracted a virus.
If a windows user updates his software, does not surf with administrative permissions (at the times where this was hard to do there where not many "drive-by-downloads", since xp SP 2 its easy), activates the security features (DEP, ASR, ...) and does not install every thing he finds on the web windows is a perfectly safe system.

The only major difference (in my point of view) is that updating software is much easier in a package manager based distribution.
The architectural advantage of most linux systems does play a big role when you never even get malware on the machine.

---

### Post by renkinjutsu on 2010-07-16
This is what i like about the multi-user system that *nix was built around. Only a script/binary executed by the user can log the user's keystrokes, and only root can log the keystrokes of everyone.

One time, my sister borrowed my computer to read manga and google-chrome stopped her in her tracks telling her that the website she was visiting wasn't safe. I got all paranoid, so i created a user account ```
useradd guest
``` and i started another X session with that account, so she can visit any place on the web without affecting my root OR my /home

---

### Post by linux18 on 2010-07-16
> **renkinjutsu said:**
> This is what i like about the multi-user system that *nix was built around. Only a script/binary executed by the user can log the user's keystrokes, and only root can log the keystrokes of everyone.

One time, my sister borrowed my computer to read manga and google-chrome stopped her in her tracks telling her that the website she was visiting wasn't safe. I got all paranoid, so i created a user account ```
useradd guest
``` and i started another X session with that account, so she can visit any place on the web without affecting my root OR my /home
yay google chrome for stopping threats to the system, now if it only stopped phoning home every 2 minutes to google....

if your sister uses windows and is visiting sites that chrome warns about....does she ask you to fix her slow computer every week or what. lol

---

### Post by renkinjutsu on 2010-07-16
> **linux18 said:**
> yay google chrome for stopping threats to the system, now if it only stopped phoning home every 2 minutes to google....

if your sister uses windows and is visiting sites that chrome warns about....does she ask you to fix her slow computer every week or what. lol

She uses OSX and uses both Safari and Firefox to browse the web. As far as i can tell, her OSX is still as snappy as ever.

---

### Post by McRat on 2010-07-16
Viruses were around on desktops before the internet.  

The malware "explosion" started with a combination of 2 brands of fertilizer:  Active Data, and the Internet.

As many predicted, Active Data (information that has executable code imbedded in it) would never be safe and would cause worldwide malware infections.  

Worms were always Microsoft's fault.  Putting backdoors in is never safe.  All data transfer should be initiated by the User.

But the real blame lies with us computer users.  We demand Active Data and Backdoors.  We want automatic updates and pretty web-pages.  

We have no reason to gripe about how messed the whole situation is, because we demanded it.

And there is no "fix".  None.  If you want outsiders to execute programs on your computer, or want outsiders to "repair" your computer, the internet cannot be made safe.

---

### Post by CandidMan on 2010-07-16
I've just taken the longest look at what's in my home directory including hidden files and it seems to be mainly config files for my programs so I guess at worst my programs act odd for a little while.

I know I said I was satisfied, but just to make sure I've got it clear, 
1.) I can't "install" stuff as non-root because everything depends on system files and directories that "I" can't change. (Haven't tried 'installing' suspect package as non-root)

2.)Even if I did sort of install malware in /home/ it would fail to work as it needs to read+write system files

3.)Hypothetically local malware can't alter critical files, capture passwords, log traffic, open ports IF it doesn't have root access.

Sorry, have had nothing but good experiences with Ubuntu so far but Windows has left me paranoid :shock:

Once bitten, twice shy. As they say

---

### Post by Diluted on 2010-07-16
> **CandidMan said:**
> 1.) I can't "install" stuff as non-root because everything depends on system files and directories that "I" can't change. (Haven't tried 'installing' suspect package as non-root)
Just because you can't install something doesn't mean you can't run the files inside the package.

> **CandidMan said:**
> 2.)Even if I did sort of install malware in /home/ it would fail to work as it needs to read+write system files
Not necessarily. If a malware has dependencies, I'd imagine it'll be packaged along with the malware, so it doesn't need access to system files or directories.

> **CandidMan said:**
> 3.)Hypothetically local malware can't alter critical files, capture passwords, log traffic, open ports IF it doesn't have root access.
If the malware runs as you and you own said critical files (which I presume to be things like your documents and stuff), then it has access to it. I think user processes can open port 1024 or above. I'm not sure about the other two, depends on the hooks available to programs I suppose.

---

### Post by zekopeko on 2010-07-17
> **CandidMan said:**
> Thanks for the useful replies. I'm satisfied I've got a good idea of the type and scope of damage malware could to the system. Looks like the biggest threat *might* come from Wine.

A lot of what was said here confirmed bits and pieces gleaned from googling. But there's only so much googling the human brain can take. It's nice to hear these things from real people (no irony intended) :p

Don't fall into the trap that most new Linux users do. You can easily get infected with malware and viruses on Linux if you download stuff from untrusted source.

Most Linux users like to tout how Linux is super safe while ignoring the fact that the most prized part of any Linux system is your /home. Malware doesn't need to install system wide. /home is perfectly suitable for that. Linux isn't being targeted (at the desktop; server is a completely different game) because it has a tiny market share and Linux users are generally tech geeks. So for now it's security through obscurity.

---

### Post by CandidMan on 2010-07-18
Well, most of my practices on XP were fairly safe apart from running as admin by default.

One thing I've noticed with Ubuntu is that I have a better feel of what's going on at any given time. I think that's partly because the OS encourages you to look beneath the hood and understand. 

Whereas Windows was more of a fire it up, and keep your fingers crossed experience.

Back on topic: So, to date, no-one has thought outside the box and done some serious damage from within /home/ , and announced it?

---

### Post by prodigy_ on 2010-07-21
Such threads exist only because people don't understand the difference between **viruses** (a specific type of malware that infects binary files) and **malware** in general.

Linux (like any Unix) isn't vulnerable to **viruses** unless you explicitly run a virus code with superuser privileges. But no OS can be completely invulnerable to all malware. Just because often there's no clear distinction between malicious and legitimate programs.

For example, someone tricks you into running a script that does **rm -rf** on your home directory. Technically, this script is malicious. But **rm -rf** itself is a legitimate command and what it does isn't always an "unwanted behavior". Computers will probably never fully "understand" such fine nuances, therefore users must be cautious.

Most people think that all malware spreads via security holes. But in fact it usually just abuses their own stupidity or carelessness.

---

