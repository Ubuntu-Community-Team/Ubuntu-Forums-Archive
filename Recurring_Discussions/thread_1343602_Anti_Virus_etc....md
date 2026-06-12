---
title: "Anti Virus etc..."
date: 2009-12-02
forum: Recurring Discussions
---

### Post by Diametric on 2009-12-02
So, I finally weened myself of of the Windows teat and am running Linux exclusively...go me.  What, if any, anti-virus/spybot apps should I run to protect myself?  I get that most malware etc is intended for Windows but it seems prudent to defend against the worst.  I believe I have my network settings applied in a defensive posture, but what else can/should I do?  My current set up, from a connection standpoint is a wireless network with 128 WEP encryption running Ubuntu 9.10.  Thanks in advance for the feedback.

Cheers,
-Diametric

---

### Post by camaron1 on 2009-12-02
To start with you can relax. You don't need antivirus in you linux machine. You could install one (clamtk from repositories) if you are going to exchange data with Windows machines (double boot, etc). But **don't** use it to scan your own file system as it will give you false positives and you may end up deleting some important stuff.

This is up for discussion: you don't need a firewall (more so if you are behind a router) as by default no computer can connect to you trough internet (all ports are closed). 

As I said, if you manage to relax about these things you'll probably never want to go back to Windows...

---

### Post by jrrader on 2009-12-02
Avoid riding the bus, get your vaccinations, don't eat anything a small child hands you - their hands are filthy.

Don't worry about viruses on Linux.  A good partition set-up, backing up your files, and a simple list of applications you need will reduce reinstall time to around 30 minutes if anything happens.  But if anything does happen, it's not a virus.  I'm not sure, but I think the fact that making any changes to the system files requires administrator permission is one of the main reasons unix-like systems do not require virus scanners.

You also don't need to defrag anymore.

Welcome.

---

### Post by ed-koala on 2009-12-02
3 years running Ubuntu. No antivirus software. No firewall. No problems.

That says it all.

---

### Post by Diametric on 2009-12-02
Thanks for your reply.  For the moment, I'm not worried, but I'd like to explore this a bit further.  So if you or anyone else can comment on the following, it would be cool to learn a bit: 

What is the difference when a virus/malware is encountered on a windows system vs a Linux system - not being a programmer I assume it's how the code is written and designed to write itself to the registry.  Usually a user is tricked in to clicking something that executes or directs them to a  bad site, but is there something in the Linux Kernel that is natively more secure, or just that the malicious code writers don't exploit Linux distros?

---

### Post by WolfRage on 2009-12-02
[COLOR=black][FONT=Verdana]Man I love linux, virus free is the way to be! Any ways enough of that. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]You should be informed that your Ubuntu installation comes protected, how well you have a rock solid OS for one that uses only trusted repositories for core software installation. Two [SELinux]("https://wiki.ubuntu.com/SELinux") is built in by default which does a whole host of protecting like preventing applications from unnecessarily elevating there privileges on your system.[/FONT][/COLOR]
[FONT=Calibri][SIZE=3]If you still feel that you need a firewall then you can enable (Because it is already installed) UFW or uncomplicated firewall. **[FONT=Calibri]sudo ufw enable[/FONT]**[/SIZE][/FONT]
If you really want to make sure you can even install AVAST anti-virus home edition for linux for free, there are also other anti virus apps for linux.
 
[Just for extra reading for you this is some good information about security on Linux and how it compares to Windows.]("http://www.psychocats.net/ubuntu/security")

---

### Post by Perfect Storm on 2009-12-02
Well, first of all you have to give it permission to access the system, next you have to execute the virus to make it running. Though via social engineering it's possible to do that. But for most Linux distros you get your apps/libs/whatever through a repository that are signed with GnuPG.

Then you have Linux permission system which will make it a hard time to penetrate for a virus, but again social engineering it's possible.

Then we have the AppArmor and SELinux for the kernel for protection.


> If you really want to make sure you can even install AVAST anti-virus home edition for linux for free, there are also other anti virus apps for linux.
The problem with these anti-virus applications are that they give a lot of false positives and they are "retro-reactives".

---

### Post by camaron1 on 2009-12-02
> **Diametric said:**
> Thanks for your reply.  For the moment, I'm not worried, but I'd like to explore this a bit further.  So if you or anyone else can comment on the following, it would be cool to learn a bit: 

What is the difference when a virus/malware is encountered on a windows system vs a Linux system - not being a programmer I assume it's how the code is written and designed to write itself to the registry.  Usually a user is tricked in to clicking something that executes or directs them to a  bad site, but is there something in the Linux Kernel that is natively more secure, or just that the malicious code writers don't exploit Linux distros?


If you do see a virus within linux it will be a Windows virus (totally inactive in linux). There are not native linux virus for what we now, and you'll be hared pressed to find anyone who's ever been infected using linux (I've never heard personally, servers are a different thing...)

---

### Post by Diluted on 2009-12-02
Can you upgrade your wireless network from WEP to WPA (preferably WPA2)? I think WEP can be easily cracked nowadays.

As for the difference Windows viruses and Linux viruses, it's just that one doesn't execute on the other. Linux doesn't know how to execute Windows viruses so it can't do anything with it. Combined with the fact that malware authors don't target Linux at the moment means Linux is currently free from viruses.

> **jrrader said:**
> I think the fact that making any changes to the system files requires administrator permission is one of the main reasons unix-like systems do not require virus scanners.
I don't understand this logic. Surely my personal files are more valuable than system files (which can be reinstalled anyway)? As far as I know, the UNIX model only prevents administrators from the users, not users from the programs (and consequently, malware).

> **jrrader said:**
> You also don't need to defrag anymore.
Not exactly true. Linux filesystems do get fragmented over time, just like any other filesystem. Why do you think there is a tool for defragmenting ext4?

---

### Post by Perfect Storm on 2009-12-02
> I don't understand this logic. Surely my personal files are more valuable than system files (which can be reinstalled anyway)? As far as I know, the UNIX model only prevents administrators from the users, not users from the programs (and consequently, malware).
Q1: Sure, that's what Backups are for ;)
Q2: See Social engineering.

---

### Post by Diametric on 2009-12-02
Diluted:

 	Quote:
 	 	 		 			 				 					Originally Posted by **jrrader** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8424843#post8424843") 				
 				*I think the fact that making any changes to the system files requires administrator permission is one of the main reasons unix-like systems do not require virus scanners.*
 			 		 	 	 
I don't understand this logic. Surely my personal files are more valuable than system files (which can be reinstalled anyway)? As far as I know, the UNIX model only prevents administrators from the users, not users from the programs (and consequently, malware).

Good point - assuming malicious code were targeting a Linux system, however unlikely, what is protecting my personal files against said code?  Is it the "root" of the Linux "tree" design - meaning my home folder falls under the protection of Root, or are they exposed.  Admittedly, this is a bit far fetched, however I think for those of us new to Linux could use a clear delineation. 

Thanks for the replies - learning as I go.

---

### Post by Diluted on 2009-12-02
Yes, but having backups doesn't mean I should not care about the data on my computer either. What if my backups fail? What if my off-site backups fail?

If backups were the answer to our malware problem, should Windows users just stop using their security programs?

I don't see a question 2 in my post though. :confused:

---

### Post by amauk on 2009-12-02
There are 4 broad areas of security that affect computer users.

I've ordered these from "most feared" -> "least feared", based purely on my personal experiences with computer users.
Ironically, in this order, under Linux, they're actually ranked from "lowest concern" -> "highest concern".

Everybody and their Grandma has heard of computer viruses. Several films and TV serials have based plots around them.
But believe me, you should be far more concerned about a malicious person with physical access to your machine, than any "virus" or "trojan horse".

Funny thing, really...


1) Viruses

Low level executable code that is tacked onto an innocent file.
When the file is loaded into memory (opened), these low level instructions get executed.
The executed code will copy itself (or a variation of itself) to other innocent files currently loaded into memory.

The reason viruses can exist on Windows, is because the operating system has no security model for in-memory file interaction.
Unix and Unix-like systems (often just called *nix systems) *do* have a security model for in-memory file interaction.

Viruses do not exist on *nix operating systems.
Well, they do exist, I mean anyone can write a virus (it's not hard), but the thing is under *nix viruses won't propagate to other files without the root user giving *express* permission for the interaction to happen.

The root user can do anything, including damaging / destroying the system (or allowing something else to damage it). 
This is why people should never login to a system as root.
Always use su (or sudo) to elevate your privileges, should you need to.
Never run an 'untrusted' binary as root.

As stated above, the root user has the authority to destroy the system, a normal user does not.
A normal user, using a computer in a normal manner, is immune to viruses under *nix.


2) Trojan Horses

Programs that you *think* do one thing, but instead do something else, usually destructive (like delete your files)
(Note: *your* files, not system files - again, only root can damage the system. *you* are a lowly user, and can only affect your own files)

Trojan horses are not a security issue. It's an issue of social engineering.

These are *your* files, and you are free to alter and delete them as you see fit.
The computer is not intelligent. The fact that *you* were duped into running a destructive program, is not something the computer can determine.

Some, *cough* Microsoft *cough*, have foolishly tried to tackle trojan horses from a security aspect.
"Are you sure you want to do this?"
"Are you sure you want to do that?"

99.999% of the time, yes, the user wants to do these things.
Constantly asking the user's permission to do simple tasks with the files he owns will only annoy the user.
He'll find some way to disable the confirmations, or get so used to pressing "Yes" that asking for confirmation becomes redundant.

Trojan horses are a social issue
You need to be able to "trust" a program does what it's supposed to, and is not destructive.

Linux distributions give you vast collection of software, stored in a repository.
The software in these repositories has been vetted by your distribution, and you can trust that they do what they're supposed to.

This is in stark contrast with Windows, which provides no central software store, or any kind of management.
You are on your own with regards to obtaining, installing and managing programs.
How do you *know* that random program X is safe to install and run?
The simple answer is, you don't.

Back on the Linux front. Venture outside the repos for anything, and you are at risk (albeit slim) of being duped.
This is where the Open Source aspect comes into play.

Open Source means just that. The source code of the program is freely viewable by everybody.
Anything suspicious, or otherwise undesirable, will be right there in the code.
You can't hide anything in an open source program.

In the vast majority of cases, there will be a sizeable community of users & developers actively participating in the software project.
It is unlikely that all the participants in the project are in cahoots with each other to dupe you into damaging your system.
So you can most likely trust an open source project not to contain any kind of trojan horse.

99% of all users will be safe from Trojans because they do not venture outside of their distro's repos.
For the 1% that do (they require some specialised, niche program not provided by their distro), then make sure the program is open.

Know what you're running, and if your business relies on this niche program, it may be beneficial to employ a programmer to review the source code.
Running random, opaque binaries is just not a sensible thing to do.

Again, it comes down to trust & common sense.
Trojan Horses are not an issue for Linux users, as there is a comprehensive "web of trust" from you -> your distro, and from your distro -> upstream


3) Software Vulnerabilities

Now we get to some minor threats.

Software is written by people, and people make mistakes; mistakes can lead to vulnerabilities in the programs execution logic.
99% of all potential vulnerabilities are caught and dealt with during the program's peer review and testing,
but inevitably some do slip through to end-user installs.

Software vulnerabilities under Linux are usually only a concern for what's called "local exploits".
That is, you have to be physically sat at the machine, in order to exploit the vulnerability.
Remote exploits (Ie. Hackers hacking into a system over the Internet and causing havoc) are almost unheard of.

Linux is highly modular in it's design; it is extremely rare for remote exploits to occur.
Simply because, remote users are more than a single "step" away from local applications.
Local users directly control the system, so a single vulnerability could potentially allow them to do something they shouldn't be allowed to do.
Remote exploits would require more than one vulnerability, causing a chain of events.

Linux systems are fully open source.
Again, being open source allows for potential issues to be nipped in the bud before (normally, way before) they can cause any problems.


4) Physical Access, with Malicious Intent

This is by far the most serious threat to a Linux user
as someone with physical access to your machine can do anything

Some technical provisions exists to safe-guard you against physical access,
including encrypted home directories / whole disk encryption
but to be honest, it's easier for someone to just steal your box (or hit it with a hammer, or whatever)

---

### Post by Diametric on 2009-12-02
Amauk - Helluva reply.  Lots of good info.  Thanks for taking the time to post that.  My next post will be on the remote desktop connection issue - quickly, I want to be able to log into my Ubuntu machine from work (XP Pro) using remote desktop.  I tried tonight, but need to figure out the details.  I'll post a full question soon.

Thanks...

---

### Post by WolfRage on 2009-12-02
Very nice Amauk.

---

### Post by jrrader on 2009-12-02
Aren't you fun...

> **Diluted said:**
> 
I don't understand this logic. Surely my personal files are more valuable than system files (which can be reinstalled anyway)? As far as I know, the UNIX model only prevents administrators from the users, not users from the programs (and consequently, malware).


Never claimed that the system files were more important than personal files.  I implied that the system is completely and easily replaceable in the case that something is botched (most likely by the user messing around with root, not a virus).  An unprivileged user may be able to download torrents and access most programs but nothing he does is going to effect anyone else that uses that computer, even if he comes across some linux virus in all his downloading.  He might wipe away every file in his home folder, but he and the virus in his home folder, does not have the ability to do anything else.  What if his files are important?  He should be more careful.

> Yes, but having backups doesn't mean I should not care about the data on my computer either. What if my backups fail? What if my off-site backups fail?

Backup is part of the solution, as is using safe download sources, knowing what you're downloading, keeping your passwords safe, not opening your ports to the internet and restricting physical access to your computer.  Anti-virus is not.  Windows users should also do everything they need to do to keep their files safe.  If someone told you "not talking on your cellphone is a key to safe driving" would you assume they meant that you should feel free to  drive as fast as you want, watch television, send text messages, not watch the road, put on make-up, and not wear your seatbelt because those things aren't "talking on your cellphone?"

Ext4 fragments if you create large files over a long period of time but for the most part it finds places for files to fit in without fragmenting them.  On a windows computer you can feel the effects of fragmentation after only a few months.  I have never heard anyone complain about a Linux computer using ext3 or 4 slowing down from normal use.

---

### Post by Diluted on 2009-12-02
> **jrrader said:**
> Never claimed that the system files were more important than personal files. I implied that the system is completely and easily replaceable in the case that something is botched (most likely by the user messing around with root, not a virus).
That would probably apply to the first part of your post, but my assumption comes from the part where virus scanners are not needed because system files are protected. That implies (to me) you're ignoring that viruses could infect personal files as well. That said, if my assumption was incorrect, then I apologize.

> **jrrader said:**
> An unprivileged user may be able to download torrents and access most programs but nothing he does is going to effect anyone else that uses that computer, even if he comes across some linux virus in all his downloading. He might wipe away every file in his home folder, but he and the virus in his home folder, does not have the ability to do anything else. What if his files are important? He should be more careful.
Not entirely true. If someone manages to execute malicious code, then you cannot guarantee that root will not be compromised, nor can you guarantee that personal information has not been leaked (I'm not sure how feasible is it to have a keylogger work under a normal user in Linux, but there are keyloggers for OS X which does not require an administrator's password.) Without any detection in place, how would you discover that someone is wrong with your system and how would you go about minimizing the damages of malware?

No matter how careful we are, there is always a way to execute code without notifying the user.

> **jrrader said:**
> Backup is part of the solution, as is using safe download sources, knowing what you're downloading, keeping your passwords safe, not opening your ports to the internet and restricting physical access to your computer. Anti-virus is not.
Maybe not, but it serves as a detection when the defense is broken. If users finds malware on their computer, then they can take steps to find out how it is getting into their computer and close that hole if possible. Without one, you may not even realize you're backing up malware and corrupted data.

Download sources can be compromised. Even websites that appear safe can be compromised.

> **jrrader said:**
> Windows users should also do everything they need to do to keep their files safe. If someone told you "not talking on your cellphone is a key to safe driving" would you assume they meant that you should feel free to drive as fast as you want, watch television, send text messages, not watch the road, put on make-up, and not wear your seatbelt because those things aren't "talking on your cellphone?"
My response to Artificial Intelligence was under the assumption that he (or she, who knows :)) points to backups as a solution for UNIX not protecting users from the system. I'm not sure where you get the impression that I'm recommending Windows users not to secure themselves.

---

### Post by jrrader on 2009-12-02
From here:

> **Diluted said:**
> 

If backups were the answer to our malware problem, should Windows users just stop using their security programs?


---

### Post by Diluted on 2009-12-02
Yes, but that doesn't imply I believe that statement is true, and neither do I think Artificial Intelligence would do so either. It's more like an incredulous question to bring out the (in my opinion anyway) ridiculousness of the suggestion.

---

### Post by jdunn on 2009-12-06
Diamtetric,
Here's my 2 cents.  There are many viruses, worms, trojans, etc that exclusively affect MS Windows systems.  None of these will harm your linux install but they can still spread to Windows if you transfer infected files between linux and Windows.  They can also infect your Wine applications (if any)...but you'd know if you were running Wine on Linux.  There are real-time and on-demand anti-virus programs for linux but all of these scan for Windows viruses (to prevent the transfer of a virus to Windows).  Due to the highly secure nature of linux AND the lack of popularity of linux (compared to M$ Windows), there is no need for linux anti-virus software.

By default, all ports on Linux are closed.  there is no need for a linux firewall unless you run an ftp server or web server.  If your computer is behind a hardware firewall, you're even more secure.  Having said that, I use a laptop, am fairly mobile and have written some small software applications (for school) that access the local area network so I installed Gufw.  Gufw is a very easy-to-use firewall for Ubuntu that makes use of iptables and Ufw.  Unlike Windows firewalls, linux firewalls do not run memory-resident.  Most of the time, I just have Gufw disabled, anyway.

Other suggestions:  Run NoScript on your Firefox browswer.  Maybe use OpenDNS as your dns server.  These are designed to provide a safer browsing experience.  Firefox alone is one of the most secure browsers there is but these provide additional protection from harmful websites, fishing scams, etc.

On my laptop, I have dual-boot MS Windows Vista 64-bit and Ubuntu 9.10 64-bit.  On Windows, I run Comodo firewall, Avira anti-virus personal, and SuperAntispyware (as a trojan, spyware malware and rootkit on-demand scanner).  I've been using linux since 2001.  I've been virus-free during all that time.

---

### Post by ibuclaw on 2009-12-06
> **jdunn said:**
> Diamtetric,
Here's my 2 cents.  There are many viruses, worms, trojans, etc that exclusively affect MS Windows systems.  None of these will harm your linux install but they can still spread to Windows if you transfer infected files between linux and Windows.  They can also infect your Wine applications (if any)...but you'd know if you were running Wine on Linux.  There are real-time and on-demand anti-virus programs for linux but all of these scan for Windows viruses (to prevent the transfer of a virus to Windows).  Due to the highly secure nature of linux AND the lack of popularity of linux (compared to M$ Windows), there is no need for linux anti-virus software.

By default, all ports on Linux are closed.  there is no need for a linux firewall unless you run an ftp server or web server.  If your computer is behind a hardware firewall, you're even more secure.  Having said that, I use a laptop, am fairly mobile and have written some small software applications (for school) that access the local area network so I installed Gufw.  Gufw is a very easy-to-use firewall for Ubuntu that makes use of iptables and Ufw.  Unlike Windows firewalls, linux firewalls do not run memory-resident.  Most of the time, I just have Gufw disabled, anyway.

Other suggestions:  Run NoScript on your Firefox browswer.  Maybe use OpenDNS as your dns server.  These are designed to provide a safer browsing experience.  Firefox alone is one of the most secure browsers there is but these provide additional protection from harmful websites, fishing scams, etc.

On my laptop, I have dual-boot MS Windows Vista 64-bit and Ubuntu 9.10 64-bit.  On Windows, I run Comodo firewall, Avira anti-virus personal, and SuperAntispyware (as a trojan, spyware malware and rootkit on-demand scanner).  I've been using linux since 2001.  I've been virus-free during all that time.

Rather than saying it, I usually just point users to here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

