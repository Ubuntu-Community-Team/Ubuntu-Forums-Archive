---
title: "Antivirus Recommendation"
date: 2009-06-30
forum: Recurring Discussions
---

### Post by Victor43 on 2009-06-30
Looking to download or purchase an antivirus for Ubuntu 9.0.4. Can someone make a recommendation even its not free. Hopefully the installation is with ease.

Thanks

Victor

---

### Post by bodhi.zazen on 2009-06-30
What makes you think you need antivirus at all ? what are you going to use it for ?

For the vast majority of Linux users antivirus is not needed and antivirus does not increase your security.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by kmg90 on 2009-06-30
speak the truth bodhi!

No need to use software that microsoft helped create! if windows didn't have so many holes and exploits there wouldn't be any anti-virus software this applies to Linux Ubuntu though

The only  "anti-virus" software you need to use that comes with ubuntu is something in System -> Admin  menu called the update manager ;)

---

### Post by scorp123 on 2009-06-30
> **Victor43 said:**
> Looking to download or purchase an antivirus for Ubuntu 9.0.4. Anti-Virus software on Linux scans for _Windows viruses._ This may make sense if you run a server on your Linux, e.g. SAMBA or some other file-sharing service that Windows users might access. That's if you are the sort of administrator that cares even for Windows users ... which I am not and I dont care one little bit. :twisted:

I for example don't care - if users are so dumb and dare use Windows in my realm then it's their duty to keep their OS updated with whatever is necessary. Oh, and being a mean person and firm believer in the BOFH-principle I mercilessly destroy any infected Windows OS installation that I find in my networks. I don't even bother to desinfect such a PC. It's a waste of time. I simply destroy anything that's on that disk (it's all infected anyway). And the Windows user responsible for the infection gets a firm kick in their rear end.

But if you've not yet reached such a state of evilness and actually really care even for Windows users ... Yes, having an anti-virus on the Linux file server might be seen as a nice move.

If you're just a Linux home user .... don't bother. There is _NO_ and I really mean _NOT_A_SINGLE_ONE_ Linux virus in the wild. Linux viruses only exist in Microsoft's scare-tactics and in speeches given by sadly misinformed people. In that case you really don't need to bother about anti-virus or anti-anything. Let Windows users solve their own problems. Enjoy your new freedoms: no more anti-virus, no more anti-spyware, no more disk defragmentation ....  Soooo much time to do other things. ;)

---

### Post by Victor43 on 2009-06-30
The only reason I would like to have one running on my linux machine is to prevent against the chance of downloding a virus or trojans like what windows machine get by chance. No other reason. I don't have any plans right now to run any kind of Linux server like the ones already mentioned. 

Appreciate the replies.

---

### Post by bodhi.zazen on 2009-06-30
I suggest you are far better off spending 15 minutes reading the security link I gave you rather the installing antivirus software on Ubuntu.

If after reading that link you still wish antivirus, follow the links ...

---

### Post by Grant A. on 2009-06-30
> **Victor43 said:**
> The only reason I would like to have one running on my linux machine is to prevent against the chance of downloding a virus or trojans like what windows machine get by chance. No other reason. I don't have any plans right now to run any kind of Linux server like the ones already mentioned. 

Appreciate the replies.

Because you grew up with the security hole ridden Windows, this will be something very hard to grasp. I know that it's hard to understand that something is so well put together that it has no viruses, but it's true. The majority of Operating Systems out there do not have viruses in the wild, and this includes Linux.

The main targets for viruses are Mac OS X and Windows.

There are no Linux viruses or trojans in the wild, meaning that there are none that can actually spread and go from place to place on the Internet. The only way you can get a virus in Linux is if you compile it from source itself. Linux cannot get drive-by downloads like Windows does.

Silly Windows lets Spyware and Trojans just install themselves to it. Trust me, you will not need an Anti-Virus on Linux. Windows viruses and programs do not work on Linux, so you are **safe**.

As long as you update your computer regularly, there is almost no chance of getting a virus.

Anti-Viruses are a shot in the foot, anyways, because they scan for the virus **after it already does its damage**, and they can only scan for **what they know about**.

If Billybob made a virus from scratch, and no one had the signatures for it, then the anti-virus couldn't find it.

Only use an Anti-Virus if you plan on using **WINE** to emulate Windows programs, as WINE can run some Windows viruses, or if you are networking (file-sharing) with a Windows computer.

I **do** recommend getting a firewall, though.

Note: I do not take responsibility for anything that may happen due to someone following the ideas laid out in this post.

---

### Post by monsterstack on 2009-06-30
Linux distros already have a firewall built-in, by the way, the Linux kernel firewall. Which you can directly control from the terminal with tools such as iptables or ufw, or from one of the GUI apps available, such as this:

```
sudo apt-get install gufw
```

Ubuntu leaves everything locked-down by default, but it can't hurt to deny incoming connections if you aren't going to be doing server-type stuff.

---

### Post by scorp123 on 2009-07-01
> **Victor43 said:**
> The only reason I would like to have one running on my linux machine is to prevent against the chance of downloding a virus or trojans  That's like saying you want a dark-matter fence to keep the unicorns out .... Don't get me wrong please. What I mean to say is this: Such stuff simply doesn't exist on Linux. Security on Unix-like operating systems such as Linux is such that the Windows-style viruses you know (e.g. infection by mere download) wouldn't even be able to function in that way.

> **Victor43 said:**
>  like what windows machine get by chance. Welcome to a new world then. All those stupid Windows problems don't exist here ):P

---

### Post by colau on 2009-07-01
> **Victor43 said:**
> Looking to download or purchase an antivirus for Ubuntu 9.0.4. Can someone make a recommendation even its not free. Hopefully the installation is with ease.
Thanks

Victor
Antivirus is not needed as there is no virus in linux.

---

### Post by benj1 on 2009-07-01
> **Grant A. said:**
> 

Only use an Anti-Virus if you plan on using **WINE** to emulate Windows programs, as WINE can run some Windows viruses, or if you are networking (file-sharing) with a Windows computer.


even with wine you don't really need AV

[http://www.linux.com/archive/feature/42031]("http://www.linux.com/archive/feature/42031")

---

### Post by bodhi.zazen on 2009-07-01
> **benj1 said:**
> even with wine you don't really need AV

[http://www.linux.com/archive/feature/42031](http://www.linux.com/archive/feature/42031)

Actually you need to be a little more cautions with wine. That article is from 2005 and is a bit dated.

There are more recent reports of viruses running in wine, and as such I updated the antivirus section of the security sticky, with links, and advice on how to mitigate this (bottom line - DO NOT RUN WINE AS ROOT).

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by benj1 on 2009-07-01
> **bodhi.zazen said:**
>  (bottom line - DO NOT RUN WINE AS ROOT).


good advice for running any program, unless you need to.

my apologies though, my understanding was that anything that ran in wine was restricted to ~/.wine, and removable media, usb drives etc

---

### Post by bodhi.zazen on 2009-07-01
> **benj1 said:**
> good advice for running any program, unless you need to.

my apologies though, my understanding was that anything that ran in wine was restricted to ~/.wine, and removable media, usb drives etc

No, last time I looked there is a link in ~/.wine/dosdevices/z: which is a sym link to /

When I run wine I delete all sym links outside of ~/.wine (call it paranoia).

---

### Post by Tibuda on 2009-07-01
> **bodhi.zazen said:**
> No, last time I looked there is a link in ~/.wine/dosdevices/z: which is a sym link to /
But wine is not able to save files under z:\usr\bin, unless you run it as root, but it can mess with z:\home\username without root.

---

### Post by haiyun211 on 2009-07-01
hey guys so you mentioned firewall how and what do you use?

---

### Post by monsterstack on 2009-07-01
> **haiyun211 said:**
> hey guys so you mentioned firewall how and what do you use?

You already have a firewall installed. It's part of the Linux kernel itself. But if you want to fiddle with the settings, go right ahead and install gufw:

```

sudo apt-get install gufw
```

You'll find it in *System>Administration>Firewall Configuration*. It's a good idea to block incoming connections if you aren't going to be doing any server stuff.

---

### Post by 1clue on 2009-07-01
Hi,

The focus seems to be on viruses (virii?) here, but in my experience people say "virus" when they mean "intrusion."  Linux/Unix doesn't have much to worry about with a traditional virus, but there are all sorts of vulnerabilities to other types of intrusions or malware.  Some of them are more dangerous than you would get from a similar Windows intrusion, and antivirus software will do nothing for you.

The best thing you can do is look at the security documentation referenced earlier in the thread, and implement that stuff as best you can.  And then re-read and re-implement every so often, because things change.

I also recommend a good implementation of tripwire, and that you maintain it.  This means not just installing what comes with your distro, but that you read the tripwire documentation and apply it to your system.  This is not a simple task, and it's not a one-time deal.

Finally, no matter what platform you look at, if the bad guys can convince you to run software they supplied then there's not much that can be done to prevent malware from running.  Even if you don't run as root, chances are that something you find precious will be lost.

Firewall:  First thing I recommend with a home installation is to get a firewall appliance such as a cable modem, and turn off all access from outside to inside.  Next, set up a firewall on your linux box to only allow access you want to get.

Defense in depth is what they call it.  That way you're not vulnerable to any specific security hole, they need to break through multiple barriers.

---

### Post by haiyun211 on 2009-07-01
So what about keyloggers?  Do they affect linux at all or is it another windows paranoia?

---

### Post by bodhi.zazen on 2009-07-01
> **haiyun211 said:**
> So what about keyloggers?  Do they affect linux at all or is it another windows paranoia?

You  can install one if you wish, or if your system is cracked someone could  install one, otherwise windows stuff.

---

### Post by monsterstack on 2009-07-01
> **haiyun211 said:**
> So what about keyloggers?  Do they affect linux at all or is it another windows paranoia?

```
monsterstack@doooombox:~$ apt-cache show lkl
[INDENT]Package: lkl
Priority: optional
Section: universe/utils
Installed-Size: 124
Maintainer: Jean-Michel Kelbert <kelbert@debian.org>
Architecture: i386
Version: 0.1.1-1
Depends: libc6 (>= 2.3.4-1)
Filename: pool/universe/l/lkl/lkl_0.1.1-1_i386.deb
Size: 9980
MD5sum: 1d2b331df9fb069dc8acda60739098e3
SHA1: c8302dbef776de1956533f8f3b31de03f2258b63
SHA256: a85b10a84e84fa08baa6e390dca30382a6c4ec3bae69570b89b121198c7861fa
[B]Description: userspace keylogger for x86 architecture
 LKL is a userspace keylogger that runs under Linux on the x86
 architechture. LKL sniffs and logs everything that passes through the
 hardware keyboard port (0x60). It translates keycodes to ASCII with a
 keymap file.[/B]
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu[/INDENT]

```

---

### Post by haiyun211 on 2009-07-01
ok so how do i prevent some one from installing it on my system and gathering my credit card info and passwords and other personel info?

---

### Post by bodhi.zazen on 2009-07-01
> **haiyun211 said:**
> ok so how do i prevent some one from installing it on my system and gathering my credit card info and passwords and other personel info?

And how would that happen ?

1. You installed it your self - don't do this.

2. You give root (sudo) access to someone else and they install it - don't do this.

3. You are fooled into installing it - see [Social Engineering]("http://en.wikipedia.org/wiki/Social_engineering_%28security%29") - Dont' install softwre from untrusted sources.

4. Your system is cracked - Read [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

If your system is cracked, re-install.

---

### Post by haiyun211 on 2009-07-01
Ok and that puts my mind at ease, so there are no other types of spyware that can affect it as long as i follow those rules?

---

### Post by 1clue on 2009-07-01
> **haiyun211 said:**
> ok so how do i prevent some one from installing it on my system and gathering my credit card info and passwords and other personel info?

Install tripwire.  It checks your system for unexpected changes and warns you about it, every day it will give you a report.

The down side is that you have to READ the report, and keep track of system updates you made.

There are all sorts of intrusions.  Read the security documentation, follow the links they reference and read those too.  Security can be anything from no concern at all to a full-time job, depending on how secure you want to be.  Only you can decide that.

The good thing is that the introductory security docs are fairly simple and short to read, and you can keep going in stages until you get sick of it and quit.  It's probably some of the best-documented functionality in Linux.

---

### Post by haiyun211 on 2009-07-01
sorry im way new ubuntu and dont understand everything yet.  So how do you install tripwire?

---

### Post by 1clue on 2009-07-01
Oof.

If you're that new, then you're in for some really painful stuff.

First go to the security documentation mentioned near the beginning of this thread and secure your box.

Next, set your box up as well as you can, because making changes to the configuration once tripwire is installed is a bit more problematic.

Next, go to System->Administration->Synaptic Package Manager and type 'tripwire' into the search.  Install that.

Tripwire is a program that keeps an encrypted record of executable files, log files and other interesting stuff on your system.  Every day, it checks things like file size, modification date, and lots of other stuff to determine if somebody added or modified anything that executes on your system.  If it detects something, it puts it into the report.  There are different categories of files, depending on if it should be treated as a log file or an executable or whatever, each category gets different treatment based on what is reasonable for that type of file.

This is NOT a trivial undertaking.  Most people just read and try to implement the security settings in the basic docs.  Tripwire is a very good mechanism for finding intruders, but it requires that you be fairly intimate with your system, and it requires a certain amount of time commitment to maintain it.  It gives you a lot, but it demands a lot too.

If you go through with it, you will learn a LOT more about how Linux works.

Good luck and have fun.

---

### Post by haiyun211 on 2009-07-01
Ok thanks alot for the help.

---

### Post by benj1 on 2009-07-02
> **haiyun211 said:**
> Ok and that puts my mind at ease, so there are no other types of spyware that can affect it as long as i follow those rules?

your system will never be 100% secure, you can fit alarms, locks, CCTV to your house, it can still be burgled. for normal usage the default installation is fairly secure (more so than windows with AV etc), if youre planning on using it as a server, then yes extra precautions are a good idea.
remember the weakest link is probably you, ie clicking to download unknown things from unknown web sites, with that in mind most kinds of AV/amti spyware etc are probably a bad idea because they lull you into a false sense of security, you would just be better using a little common sense, only download from trusted sources don't blindly click ok to things, keep backups.

---

### Post by gn2 on 2009-07-02
> **1clue said:**
> ~ viruses (virii?) ~

It's definitely viruses.
There's no latin plural of the word virus.

---

### Post by donkyhotay on 2009-07-02
I've posted this before in similar threads but here is my standard response for concerns about anti-virus on linux. I didn't write this myself, it's part of the 'rootless root' series (do a google search for the others) but it pretty much sums up this issue (for me at least). 


Master Foo and the Nervous Novice
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

“Master Foo,” he asked “why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?”

Master Foo smiled, and said “When your house is well constructed, there is no need to add pillars to keep the roof in place.”

The novice replied “Would it not be better to use these things anyway, just to be certain?”

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

“What are you doing?” the novice asked in surprise.

Master Foo replied simply: “Tying your shoes.”

Upon hearing this, the novice was enlightened.

---

### Post by Victor43 on 2009-07-28
There maybe no viruses for Ubuntu but there does appear to be malicious scripts written for Linux which can steal your passwords and user login for website which you visit. 

Here is a link for a post which provides more information on this topic

[http://www.linuxquestions.org/questions/linux-security-4/malicious-scripts-738153/](http://www.linuxquestions.org/questions/linux-security-4/malicious-scripts-738153/)

---

### Post by bodhi.zazen on 2009-07-28
> **Victor43 said:**
> There maybe no viruses for Ubuntu but there does appear to be malicious scripts written for Linux which can steal your passwords and user login for website which you visit. 

Here is a link for a post which provides more information on this topic

[http://www.linuxquestions.org/questions/linux-security-4/malicious-scripts-738153/](http://www.linuxquestions.org/questions/linux-security-4/malicious-scripts-738153/)

and how would such a script be run on your system ?

1. You write and run it yourself. This is usually not classified as a security flaw.

2. Somebody dups you into running such a script. This is called "Social engineering". The fix is simple, do not run scripts or install software from untrusted sources.

3. There is some other, in this case hypothetical, security hole that allows execution of arbitrary code. In this case the security flaw is the underlying, in this case, hypothetical hole. There are really only 2 things you can do - Keep your system up to date and run Apparmor or SELinux.

If such a hypothetical hole exists, it is true there are thousands of ways somebody can cause problems.

Or 4. Physical access. The only protections are to restrict physical access or encrypt your system. I now routinely encrypt my laptops.

---

