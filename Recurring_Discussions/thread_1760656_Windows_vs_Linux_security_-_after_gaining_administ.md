---
title: "Windows vs Linux security - after gaining administrative rights"
date: 2011-05-17
forum: Recurring Discussions
---

### Post by Nyromith on 2011-05-17
There is a very common argument that Linux is more secure than Windows just because it is much less popular. An also very common response to that is that Linux actually is a much better target for attacks because it runs on most servers, and servers are a lot more tempting target than clients.

I personally think that when Linux is more secure in the scenario of a hacker who is determined to compromise a single system. It is also a lot more immune to worms (viruses that don't need a user to infect the system, like Blaster).

But - most of the malware in Windows infects the system when the user installs software that is infected with it. When we compare Windows 7 and Linux, both (apparently) react the same way to installing software - a user is asked to give an administrative access to the system (UAC or sudo). And here comes the part that I'm interested in - are there any additional security layers in Linux that make it more immune to malware after this stage, or does it become as vulnerable as Windows before UAC?

Thanks for your responses.

---

### Post by Npl on 2011-05-17
first, windows NT always had a sudo equivalent ("runas"), so UAC makes no difference for security. Before Vista users where given administrative rights by default which was the primary issue - a stupid configuration. You could easily take away administrative rights from a user in Win2000/WinXP and he couldnt install software from his account without using runas or switching to the admin account

and as soon as you give malware full administrative rights theres no restriction or safeguards on either system

---

### Post by gradinaruvasile on 2011-05-17
In a nutshell: in both cases the deciding factor is between the seat and the computer. 

After YOU gave the go for a program (that was not verified) to use administrative rights, both systems can be compromised. Duh.

And if someone is a determined and experienced hacker and targets a specific system, only a good sysadmin and enforced security practices can prevent it. On any platform.
If you look it up, you will see that most high profile ownage was caused by sloppy admins/non enforced good security measures coupled with users ignorance. Not via a magical remote exploit.

---

### Post by 3Miro on 2011-05-17
Linux distributions have repositories. In Linux, you usually don't go around installing random stuff off the Internet (where most malware is).

---

### Post by Lucradia on 2011-05-17
> **Npl said:**
> first, windows NT always had a sudo equivalent ("runas"), so UAC makes no difference for security. Before Vista users where given administrative rights by default which was the primary issue - a stupid configuration. You could easily take away administrative rights from a user in Win2000/WinXP and he couldnt install software from his account without using runas or switching to the admin account

and as soon as you give malware full administrative rights theres no restriction or safeguards on either system

Windows XP (32-bit only) has sudowin.

Also, root =/= Admin. root = root. If you give a user in linux full admin rights, they still aren't root, but they can still do damage. Also try adding yourself to the root group, you'd be surprised at how much stuff you can't do even though you should be root.

Some Windows tasks still require logging in as admin, but only a very rare few, even on Windows 7 and Vista.

---

### Post by Spice Weasel on 2011-05-17
> **3Miro said:**
> Linux distributions have repositories. In Linux, you usually don't go around installing random stuff off the Internet (where most malware is).

So there is no chance at all of bad code getting in to the repositories or the repositories being hacked?

Or a security hole being left unpatched?

---

### Post by Lucradia on 2011-05-17
> **Spice Weasel said:**
> So there is no chance at all of bad code getting in to the repositories or the repositories being hacked?

Or a security hole being left unpatched?

There was a malicious DEB that was put on the Web, but it never got into the repos. When it was installed, it did some nasty things.

When something wants to go into the official or head repos, a lot of checking is done on the DEB Package, the deps have to be found out, a small description has to be made, an MD5sum has to be written for it, signature check, and lots, lots more. (Architecture tests, IE: Can it work with IA32-libs?, etc.)

---

### Post by screaminj3sus on 2011-05-17
> **3Miro said:**
> Linux distributions have repositories. In Linux, you usually don't go around installing random stuff off the Internet (where most malware is).

They are generally more secure than downloading stuff off the net yes, but imagine a scenerio where a repository for a popular distro was hacked, you could distribute malware to ton of people.

---

### Post by pookiebear on 2011-05-17
I have seen and repaired malware on windows computers that the user did not even have admin privileges. 

THAT is the main difference.

---

### Post by Spice Weasel on 2011-05-17
[http://it.slashdot.org/story/07/07/18/0319203/Major-Security-Hole-In-Samsung-Linux-Drivers](http://it.slashdot.org/story/07/07/18/0319203/Major-Security-Hole-In-Samsung-Linux-Drivers)
[http://linux.slashdot.org/story/10/10/21/181234/RDS-Protocol-Bug-Creates-a-Linux-Kernel-Hole-Now-Fixed](http://linux.slashdot.org/story/10/10/21/181234/RDS-Protocol-Bug-Creates-a-Linux-Kernel-Hole-Now-Fixed)
[http://it.slashdot.org/story/09/07/18/0136224/New-Linux-Kernel-Flaw-Allows-Null-Pointer-Exploits](http://it.slashdot.org/story/09/07/18/0136224/New-Linux-Kernel-Flaw-Allows-Null-Pointer-Exploits)
[http://linux.slashdot.org/story/09/08/13/2022212/Local-Privilege-Escalation-On-All-Linux-Kernels](http://linux.slashdot.org/story/09/08/13/2022212/Local-Privilege-Escalation-On-All-Linux-Kernels) (unpatched from 2001 to 2009)
[http://linux.slashdot.org/story/10/09/18/2325240/Hole-In-Linux-Kernel-Provides-Root-Rights](http://linux.slashdot.org/story/10/09/18/2325240/Hole-In-Linux-Kernel-Provides-Root-Rights)
[http://tech.slashdot.org/story/10/08/18/1534258/Linux-Xorg-Critical-Security-Flaw-Silently-Patched](http://tech.slashdot.org/story/10/08/18/1534258/Linux-Xorg-Critical-Security-Flaw-Silently-Patched)

> **Lucradia said:**
> There was a malicious DEB that was put on the Web, but it never got into the repos. When it was installed, it did some nasty things.

When something wants to go into the official or head repos, a lot of checking is done on the DEB Package, the deps have to be found out, a small description has to be made, an MD5sum has to be written for it, signature check, and lots, lots more. (Architecture tests, IE: Can it work with IA32-libs?, etc.)

You have to rely on the developer to check every single bit of code, not to skip anything and to be trustworthy. Somehow I can see that this system isn't foolproof.

Then there is also the issue of relying on the repos host server to be completely secure, and not let anyone who might cause some trouble in.

Also - the subject of this thread is "Windows vs Linux security - **after gaining administrative rights**".

---

### Post by Thewhistlingwind on 2011-05-17
It depends on weather or not the system has a MAC, and how it's set up.

AFAIK, you can prevent a lot of damage by restricting the root user with something like SELinux

---

### Post by heartbeatz on 2011-05-17
:) I think it's a bit more than just where malware is ie on the web or who has admin password, it's about how the OS is built which has a defining factor for potencial of malware once it's in and Windows is no match for Linux.

---

### Post by 3Miro on 2011-05-17
> **Spice Weasel said:**
> So there is no chance at all of bad code getting in to the repositories or the repositories being hacked?


Yes there is a chance of the repos being hacked, but it is way way smaller than getting malware from a random Internet site.

You can make the same argument for windows updates being infected by a virus. If MS lets a virus on their update server, this can affect most windows machines in the world almost instantly.

> 
Or a security hole being left unpatched?

???? We are talking about installing malware, what does security holes have to do with it? Security holes is another issue altogether. The FOSS community works very fast when it comes to patching holes, MS on the other hand is often taking their time. This is why people with windows need AV programs to temporarily cover-up the issues until MS comes around to actually fix it.

Nothing is 100% secure, however, Linux is more secure.

---

### Post by RiceMonster on 2011-05-17
> **3Miro said:**
> In Linux, you usually don't go around installing random stuff off the Internet

This is bad practise regardless of OS.

---

### Post by 3Miro on 2011-05-17
> **RiceMonster said:**
> This is bad practise regardless of OS.

True! However, the issue with Windows is that there is no repository and when people need simple programs (like a rar program or better text editor or hardware monitoring utility) then they have to go on the web. You can spend the extra time to do the research and figure out if the software is legit, but many users can't or don't do that.

---

### Post by Spice Weasel on 2011-05-17
> **3Miro said:**
> 
We are talking about installing malware, what does security holes have to do with it? Security holes is another issue altogether.


Everything. Malware needs access to root in order cause real damage, if the programmers who wrote the software have an exploit to gain extra privileges it makes their job a lot easier.

> **3Miro said:**
> 
The FOSS community works very fast when it comes to patching holes, MS on the other hand is often taking their time. 


[Eight years is fast?]("http://linux.slashdot.org/story/09/08/13/2022212/Local-Privilege-Escalation-On-All-Linux-Kernels")

> **3Miro said:**
> 
This is why people with windows need AV programs to temporarily cover-up the issues until MS comes around to actually fix it.


No, Windows users need AV programs to remove malicious programs that they have downloaded or have obtained through other ways.

---

### Post by RiceMonster on 2011-05-17
> **3Miro said:**
> True! However, the issue with Windows is that there is no repository and when people need simple programs (like a rar program or better text editor or hardware monitoring utility) then they have to go on the web. You can spend the extra time to do the research and figure out if the software is legit, but many users can't or don't do that.

But how many people know what to choose from the repos, and how can you guarentee that people will use the repos in the first place? Many people would end up asking someone else or searching around the web trying to figure out what they should install. In this regard, no real difference here.

> **Spice Weasel said:**
> Malware needs access to root in order cause real damage

Not necessarily. Programs like pidgin store plain text passwords in the home directory, and people also store their personal data in their home directory as well.

---

### Post by Spice Weasel on 2011-05-17
> **3Miro said:**
> True! However, the issue with Windows is that there is no repository and when people need simple programs (like a rar program or better text editor or hardware monitoring utility) then they have to go on the web. You can spend the extra time to do the research and figure out if the software is legit, but many users can't or don't do that.

Windows 8 will come with a software store. ;)

---

### Post by Nyromith on 2011-05-17
I don't think it's possible to fit all the Windows software in the world to one giant repository, so this argument does exploit the fact that Ubuntu has much less software than Windows and it's still possible to manage and monitor all of it from a single place.

A repository won't be a practical solution if Linux will be much more popular.

---

### Post by el_koraco on 2011-05-17
> **3Miro said:**
> True! However, the issue with Windows is that there is no repository and when people need simple programs (like a rar program or better text editor or hardware monitoring utility) then they have to go on the web. You can spend the extra time to do the research and figure out if the software is legit, but many users can't or don't do that.

Poeple rarely pick up junk when they're installing a OSS or piece of software that they've payed for, they get into trouble with warez. The repository thing is more an (excellent) technical than a security feature.

---

### Post by 3Miro on 2011-05-17
> **Spice Weasel said:**
> Everything. Malware needs access to root in order cause real damage, if the programmers who wrote the software have an exploit to gain extra privileges it makes their job a lot easier.


Read the OP. The question is specific about installing software. An attack where a program is getting privileges without permission is another subject. And yes it is harder to do on a Unix.

> 
[Eight years is fast?]("http://linux.slashdot.org/story/09/08/13/2022212/Local-Privilege-Escalation-On-All-Linux-Kernels")


I am counting from the time of discovery to the time of being fixes. MS takes its time to fix **known** issues.

Why do you keep thinking in absolutes? Nothing is absolutely secure or insecure. However, there are things that are more secure and Linux is more secure than windows.

> 
No, Windows users need AV programs to remove malicious programs that they have downloaded or have obtained through other ways.

So if I don't download and install programs from the Internet, then I don't need an AV? Are you serious?

The only time you would not need an AV is if you don't have an internet connection at all.

---

### Post by 3Miro on 2011-05-17
> **Spice Weasel said:**
> Windows 8 will come with a software store. ;)

Good .... that is how many years after Linux. Same with all of their new and good features. Unix has security build top to bottom since the late 60's. Linux has it since day 1 in the early 90's. Windows 98 comes with zero security and windows XP SP 2 is the first version with integrated firewall. Windows Vista was the first Linux designed with good security in mind. That is what, 16 years behind?

On the other hand, would MS check if the software in their store respects privacy and such. Not all malware steals credit card numbers, some of it just spies on you.

---

### Post by 3Miro on 2011-05-17
> **Nyromith said:**
> I don't think it's possible to fit all the Windows software in the world to one giant repository, so this argument does exploit the fact that Ubuntu has much less software than Windows and it's still possible to manage and monitor all of it from a single place.

A repository won't be a practical solution if Linux will be much more popular.

You don't have to put all the software in the world, just enough to do simple work. Windows doesn't come with rar archiver, pdf reader, good text editor and so on. You need that to be included in a repository.

If you need additional special software, then you do some research as such software would be commercial anyway.

---

### Post by Npl on 2011-05-17
> **3Miro said:**
> Read the OP. The question is specific about installing software. An attack where a program is getting privileges without permission is another subject. And yes it is harder to do on a Unix.



I am counting from the time of discovery to the time of being fixes. MS takes its time to fix **known** issues.

Why do you keep thinking in absolutes? Nothing is absolutely secure or insecure. However, there are things that are more secure and Linux is more secure than windows.



So if I don't download and install programs from the Internet, then I don't need an AV? Are you serious?

The only time you would not need an AV is if you don't have an internet connection at all.Well, I havent used AV since 8 years or so (as in permanently running) and I never catched a virus/malware (just checking what runs at startup and very sporadically let an AV check my drives).
Most infections just fall into the category of a dumb user clicking on a file and bringing the pain on himself manually. Of course there are exploits which are more sophisticated but against those a AV is pretty ineffective aswell. AV is usefull for warning naive/inexpierenced users, but it doesnt make the system itself more secure.

---

### Post by RiceMonster on 2011-05-17
> **3Miro said:**
> So if I don't download and install programs from the Internet, then I don't need an AV? Are you serious?

You'd do fine without one. I installed MSE because it's free and doesn't slow down your machine. It's never found a single thing.

---

### Post by Spice Weasel on 2011-05-17
A potential security issue that is not known to the developers is not necessarily unknown to people who develop malware. Sure, it's important to fix the problem quickly after the developers find out about it but think, what's worse, an exploit existing for eight years before being fixed or an exploit that has been around for less than a year taking an extra week to fix?

> **3Miro said:**
> 
So if I don't download and install programs from the Internet, then I don't need an AV? Are you serious?

The only time you would not need an AV is if you don't have an internet connection at all.

or have obtained through other ways (through the internet or not).

I used my last Windows setup for a year and only installed an antivirus a month before removing it. Nothing was found, and I never had any problems.

My point was that all AVs do is remove malicious software. Anti-Viruses do not "cover up issues" in the operating system.

---

### Post by fuduntu on 2011-05-17
> **3Miro said:**
> Yes there is a chance of the repos being hacked, but it is way way smaller than getting malware from a random Internet site.

You can make the same argument for windows updates being infected by a virus. If MS lets a virus on their update server, this can affect most windows machines in the world almost instantly.



???? We are talking about installing malware, what does security holes have to do with it? Security holes is another issue altogether. The FOSS community works very fast when it comes to patching holes, MS on the other hand is often taking their time. This is why people with windows need AV programs to temporarily cover-up the issues until MS comes around to actually fix it.

Nothing is 100% secure, however, Linux is more secure.

There is also the possibility of malware being injected into the source that distribution packages are built from.  It happened to Arch and Gentoo this last year (unrealircd).

---

### Post by fuduntu on 2011-05-17
> **Spice Weasel said:**
> Everything. Malware needs access to root in order cause real damage, if the programmers who wrote the software have an exploit to gain extra privileges it makes their job a lot easier.

Hmm, no.  Malware just needs to be executed to cause real damage.  The risk is largely dependent on what is more important to the individual.

Which is more valuable, the content of /etc or the content of /home?  I'd argue the latter, and with that Malware doesn't need root.

> **Spice Weasel said:**
> [Eight years is fast?]("http://linux.slashdot.org/story/09/08/13/2022212/Local-Privilege-Escalation-On-All-Linux-Kernels")


:(

> **Spice Weasel said:**
> 
No, Windows users need AV programs to remove malicious programs that they have downloaded or have obtained through other ways.

+1 but AV can also block certain known or heuristic patterns which can sometimes stop new infections for malware that hasn't yet been added to a definitions file.  This can sometimes stop malware from entering a system remotely via remote exploit (worm).

---

### Post by fuduntu on 2011-05-17
> **Npl said:**
> Well, I havent used AV since 8 years or so (as in permanently running) and I never catched a virus/malware (just checking what runs at startup and very sporadically let an AV check my drives).

How do you know?  I know people that used to believe this, they swore it wouldn't happen to them.  Next thing you knew, the cable company shuts down their internet connection because they were compromised.

They had no idea, until that moment.

Without AV on the Windows platform you would not know if you have been compromised or not (in many cases).

---

### Post by 3Miro on 2011-05-17
The AV thing is interesting then. I never saw anyone not using AV in windows before (well, if they were, then they were surely infected).

As for the repository, let me repeat myself to Spice Weasel and fuduntu:

> 
Why do you keep thinking in absolutes? Nothing is absolutely secure or insecure. However, there are things that are more secure and Linux is more secure than windows.


Windows is getting there slowly, but it is still years behind.

Also, fuduntu can you provide al ink about Arch and Gentoo breaks, I want to read about it.

---

### Post by fuduntu on 2011-05-17
> **3Miro said:**
> The AV thing is interesting then. I never saw anyone not using AV in windows before (well, if they were, then they were surely infected).

As for the repository, let me repeat myself to Spice Weasel and fuduntu:



Windows is getting there slowly, but it is still years behind.


It isn't really years behind anymore, it's arguably ahead.  It took Microsoft a complete shift in business practice and mindset, and countless dollars but .. they put forth the effort.


> **3Miro said:**
> Also, fuduntu can you provide al ink about Arch and Gentoo breaks, I want to read about it.

Sure.

[http://forums.unrealircd.com/viewtopic.php?t=6562](http://forums.unrealircd.com/viewtopic.php?t=6562)

The core issue was that the source mirror was compromised, and the distributors didn't check md5sums.

Gentoo: [http://bugs.gentoo.org/323691](http://bugs.gentoo.org/323691)
Arch: [https://bugs.archlinux.org/task/19780](https://bugs.archlinux.org/task/19780)

It could happen to any distributor, simple mistakes can be catastrophic.  I don't blame Arch, or Gentoo, nor do I blame the authors of unrealircd.  My point is only that it can happen. ;)

---

### Post by sydbat on 2011-05-17
> **RiceMonster said:**
> But how many people know what to choose from the repos, and **how can you guarentee that people will use the repos in the first place?** Many people would end up asking someone else or searching around the web trying to figure out what they should install. In this regard, no real difference here.To add - I have seen numerous threads from new users who have gone "into the wild" and downloaded some application that is also found in the repos. They ask how to install it, usually because their 'point and click' method doesn't work as it did in Windows (where most claim to have come from).

Then there are those who want "the newest, greatest, most tigery blooded app in the universe" and go outside the repos to find it. These are almost always people who have been using Linux for awhile and think they know what they are doing.

---

### Post by fuduntu on 2011-05-17
> **sydbat said:**
> To add - I have seen numerous threads from new users who have gone "into the wild" and downloaded some application that is also found in the repos. They ask how to install it, usually because their 'point and click' method doesn't work as it did in Windows (where most claim to have come from).

Then there are those who want "the newest, greatest, most tigery blooded app in the universe" and go outside the repos to find it. These are almost always people who have been using Linux for awhile and think they know what they are doing.

Users also use PPAs which aren't policed, and should be considered untrusted repositories.

---

### Post by Npl on 2011-05-17
> **fuduntu said:**
> How do you know?  I know people that used to believe this, they swore it wouldn't happen to them.  Next thing you knew, the cable company shuts down their internet connection because they were compromised.

They had no idea, until that moment.

Without AV on the Windows platform you cannot know if you have been compromised or not.There are enough tools (eg. sysinternals suite) that can tell you the software thats "hooked in". Of course sophisticated malware could prevent beeing detected but then it could prevent the detection by current AV including the primitive heuristics involved more easily.

And as i said I did/do sporadic checks with AV (AVG, MSE, Windows Defender) without having them running all the time.

You wont stop a sophisticated malware with an AV, and the primitive one can be stopped by common sense already. The is little that doesnt fall in one of those categories.
If some malware gets into my system (through unpatched vulnerabilities) Im pretty sure an AV wouldnt have stopped it either.

---

### Post by 3Miro on 2011-05-17
> **fuduntu said:**
> 
Sure.

[http://forums.unrealircd.com/viewtopic.php?t=6562](http://forums.unrealircd.com/viewtopic.php?t=6562)

The core issue was that the source mirror was compromised, and the distributors didn't check md5sums.

Gentoo: [http://bugs.gentoo.org/323691](http://bugs.gentoo.org/323691)
Arch: [https://bugs.archlinux.org/task/19780](https://bugs.archlinux.org/task/19780)

It could happen to any distributor, simple mistakes can be catastrophic.  I don't blame Arch, or Gentoo, nor do I blame the authors of unrealircd.  My point is only that it can happen. ;)

Gentoo does checksum source code (they use sha sums not md5). The only way would be is Gentoo accepted the new checksum without checking to make sure the new .tar was indeed legit. (it is odd for developers to release a new .tar file without bumping the version number, but it does happen).

---

### Post by aysiu on 2011-05-17
> **Nyromith said:**
> I don't think it's possible to fit all the Windows software in the world to one giant repository, so this argument does exploit the fact that Ubuntu has much less software than Windows and it's still possible to manage and monitor all of it from a single place.

A repository won't be a practical solution if Linux will be much more popular. Tell that to Apple's iOS AppStore or Google's Android Market. Each has about 300,000-400,000 apps in it.

Apple also just recently launched a Mac AppStore for its Snow Leopard laptops and desktops.

What is an "AppStore" but a giant repository?

---

### Post by weasel fierce on 2011-05-17
While I don't think "security in obscurity" is the only thing linux has going for it, I do think it adds some help.

Obviously some things are the same on most linux systems but plenty of things aren't.

Exploit in firefox? Plenty of people running chrome or rekonq f.x.
Exploit in Gnome? Plenty of people running KDE 

etc etc etc
This makes widespread infection a lot harder to accomplish.

---

### Post by Larkspur on 2011-05-17
Once a program has Administrative rights, in either situation, it can do anything the programmer wants it to.  In that, both Linux and Windows are the same.  Windows did shoot themselves in the foot by making the default user a root user, but they are changing now, and the availability of MSE is a huge leap forward.  As someone else says, that behavioral scanning of some AV suites in windows is a layer of security that exists after giving admin rights, something Linux doesn't have.

The one advantage Linux has  - apart from the default setup - is that there isn't enough easy money to be had at the moment.  This is, in part, due to it's low market share.

Before you bring up servers, note I said "easy money": a would-be cracker who has written (or spent thousands of pounds on) malware wants a good return, and with Windows, there are enough people running without AV downloading stuff from anywhere and clicking the UAC without a second.  With Linux, there just aren't enough users like that for it to be a valuable investment.

By the way, PPAs are a security hole waiting to happen: I can't imagine a better way of getting malware on a computer with full rights, and to keep it full updated.

---

### Post by 3Miro on 2011-05-17
> **Larkspur said:**
> As someone else says, that behavioral scanning of some AV suites in windows is a layer of security that exists after giving admin rights, something Linux doesn't have.


Have you heard of AppArmor and SELinux? AV software does more than one thing, whatever additional protection AV may give to windows, AppArmor and SELinux do that for Linux.

---

### Post by fuduntu on 2011-05-17
> **3Miro said:**
> Have you heard of AppArmor and SELinux? AV software does more than one thing, whatever additional protection AV may give to windows, AppArmor and SELinux do that for Linux.

Not really, SELinux and AppArmor are pretty much just labeling and permissions tools, and to my knowledge they don't protect /home by default.  They also don't do any pattern recognition (AppArmor will report anomalies, but that isn't a pattern).

They are good tools for system level protection, but useless for anything else (at least by default).

---

### Post by tgm4883 on 2011-05-17
> **Nyromith said:**
> 
But - **most of the malware in Windows infects the system when the user installs software that is infected with it.** When we compare Windows 7 and Linux, both (apparently) react the same way to installing software - a user is asked to give an administrative access to the system (UAC or sudo). And here comes the part that I'm interested in - are there any additional security layers in Linux that make it more immune to malware after this stage, or does it become as vulnerable as Windows before UAC?

Thanks for your responses.

You are making an incorrect assumption here. Most malware is not installed as part of something the user installed. Most malware gets onto the system with zero user interaction.

---

### Post by Larkspur on 2011-05-17
> **3Miro said:**
> Have you heard of AppArmor and SELinux? AV software does more than one thing, whatever additional protection AV may give to windows, AppArmor and SELinux do that for Linux.

I agree that AppArmor (I don't know about SELinux - I've haven't used that, but I believe it does the same thing) makes browser exploits nowhere near the problem they are on windows (especially with Internet Explorer), but it does not protect the systems from things downloaded from the internet.  Apparmor works brilliantly - didn't someone who was trying to crack Ubuntu pull out of Pwn2Own because Firefox's Apparmor profile was going to be active? - but it only works when a profile is defined for it, and when that profile is enforced.  AV on windows watches systems processes as they happen, and make the user aware when processes start acting like malware and can restrict them.  It's like Apparmor, if Apparmor could produce profiles on the fly without being asked.

Say, for example, a screensaver was made available to download with a script to call home.  Once you'd given the admin password, it installs and you are given no further warning until you look at the code.  With Windows, theres a chance that the AV will pick it up (not all AVs are programmed equal).  Of course you could say that scanning it with Clam would pick it up. But it depends on its static database already having signatures that are similar to the behaviour of the malware.  Windows AV (well some) decide on the threat level of a program based on what it is actually doing.  This is actually one of the reason they can slow down a system

---

### Post by 3Miro on 2011-05-17
> **fuduntu said:**
> Not really, SELinux and AppArmor are pretty much just labeling and permissions tools, and to my knowledge they don't protect /home by default.  They also don't do any pattern recognition (AppArmor will report anomalies, but that isn't a pattern).

They are good tools for system level protection, but useless for anything else (at least by default).

On Fedora I always have trouble with SELinux giving me false positives on Matlab and Matlab is installed locally on /home/username/MATLAB. SELinux will block executables downloaded in /home, I am not sure what other capabilities they have.

Pattern recognition also goes two ways, it can give plenty of false-positive. I remember on windows I had to disable the AV to use the trainer when I was playing Stalker.

---

### Post by fuduntu on 2011-05-17
> **3Miro said:**
> On Fedora I always have trouble with SELinux giving me false positives on Matlab and Matlab is installed locally on /home/username/MATLAB. SELinux will block executables downloaded in /home, I am not sure what other capabilities they have.

There are tons of compatibility problems with SELinux, it isn't designed for consumer grade use, it is more of a bullet proof vest for servers.  Different use case really.

> **3Miro said:**
> Pattern recognition also goes two ways, it can give plenty of false-positive. I remember on windows I had to disable the AV to use the trainer when I was playing Stalker.

I don't disagree.  Sometimes it's a pain.

---

### Post by Larkspur on 2011-05-17
> **fuduntu said:**
> Not really, SELinux and AppArmor are pretty much just labeling and permissions tools, and to my knowledge they don't protect /home by default.

Based on my attempts to rejig the Firefox aa profile, Apparmor has difficulty protecting the whole of /home.  It stops bash.rc and other important files being written to, but other areas can be, unless you define the rights of every folder individually.  It's not really a risk as far as I can see; if an exploit put a bit of malware in your .abiword folder, it can't do much unless it's activated.

---

### Post by Larkspur on 2011-05-17
> **3Miro said:**
> Pattern recognition also goes two ways, it can give plenty of false-positive. I remember on windows I had to disable the AV to use the trainer when I was playing Stalker.

+1 - My AV identified both Rainmeter and the Synaptics Multitouch driver (which came direct from Synaptics) as possible trojans.  However, compare the amount of false positives in windows AV with something like rkhunter.  Rkhunter throws up so many because they can't deliver the volume of definition updates that paid apps can.  Rkhunter would be much better to use for non server admins if it could determine what file changes are expected to happen and which aren't.  I haven't used it myself, but based on what I've read here, doesn't it just tell the user what files have changed?

---

### Post by fuduntu on 2011-05-17
> **Larkspur said:**
> Based on my attempts to rejig the Firefox aa profile, Apparmor has difficulty protecting the whole of /home.  It stops bash.rc and other important files being written to, but other areas can be, unless you define the rights of every folder individually.  It's not really a risk as far as I can see; if an exploit put a bit of malware in your .abiword folder, it can't do much unless it's activated.

What about .config/autostart, or execution from .vimrc? ;)

.abiword is probably not a risk, sure but there are other targets in ~ that could be exploited.  It would be really difficult to apply policies to /home which is why it isn't there by default (in my opinion of course).

---

