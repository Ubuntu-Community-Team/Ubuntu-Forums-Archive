---
title: "What makes Ubuntu and other Linux &amp; GNU/Linux distros so safe? [MEGA THREAD]"
date: 2011-09-06
forum: Recurring Discussions
---

### Post by linuxuser12345 on 2011-09-06
I have a simple question and I am sure a lot of you may be pondering the same question. In your opinion, if not in fact, what makes Ubuntu and other (GNU/)Linux distributions so safe? Is it just sudo? Is it more than that? Explain.

---

### Post by haqking on 2011-09-06
> **linuxuser12345 said:**
> I have a simple question and I am sure a lot of you may be pondering the same question. In your opinion, if not in fact, what makes Ubuntu and other (GNU/)Linux distributions so safe? Is it just sudo? Is it more than that? Explain.

safe is very open ended statement.

There are lots of things which contribute to its inherent safety such as lack of viruses, using sudo, by default ports are closed etc etc ad nauseum ad infinitum

however its safety is easily corrupted by a little knowledge or lack of any, posts here all the time about enabling root, blank passwords etc etc.

Security (safety) is about a layered approach and a process not a product.

Least privelege all the time, and user/admin training, awareness and experience are what make any OS safe, people always say Windows is not safe, well thats not the case, it is if the Admin knows what they are doing

---

### Post by linuxuser12345 on 2011-09-06
> **haqking said:**
> safe is very open ended statement.

I want it to be an open-ended statement. This is a moment for discussion and learning. I just want to know what makes GNU/Linux and Linux so safe when compared to Microsoft Windows. 

And, by "safe" I mean every possible aspect.

---

### Post by WorMzy on 2011-09-06
File permissions are an important aspect of it. By default, the only thing that a user owns is their own personal home folder, and it's contents. So if you leave your PC unattended, the worst anyone can do is delete all your important documents.

Granted, that doesn't sound very good to *you*, but at least they can't delete every other user's important documents, or worse, the files necessary for the OS to boot.

Things like su -c and sudo are there to make your life easier. Instead of having to log in as the root user to install software, or change system-wide config files, you can simply run a single command as the root user, then have the elevated privileges revoked immediately afterwards (or after 10 minutes or so, depending on what you've set in the Defaults in /etc/sudoers), that way you're not in danger of logging in as root, leaving *that* unattended, and then having someone come along and nuke the entire OS, or worse, *every* OS on the hard disk(s).

Because of the way that file permissions work, you're pretty well protected against malicious scripts. Unless you go ahead and run ```
sudo destroy-all-my-data.sh
``` you're not likely to fall victim to some scriptkiddy's attempt to mess up your OS.

---

### Post by alegomaster on 2011-09-06
> **linuxuser12345 said:**
> I want it to be an open-ended statement. This is a moment for discussion and learning. I just want to know what makes GNU/Linux and Linux so safe when compared to Microsoft Windows. 

And, by "safe" I mean every possible aspect.


The fact that every Linux user is smarter then the suitable Windows counterpart

---

### Post by haqking on 2011-09-06
> **alegomaster said:**
> The fact that every Linux user is smarter then the suitable Windows counterpart

.

That is hardly accurate and very elitist.

I speak as a very experienced Windows user (historically)

---

### Post by WorMzy on 2011-09-06
> **haqking said:**
> That is hardly accurate and very elitist.

Agreed. There are some damned stupid Linux users out there (see any "help, I rm -rf'd /" topics). Just as there are some damned intelligent Windows users.

---

### Post by linuxuser12345 on 2011-09-06
What does "rm -rf" do?

---

### Post by haqking on 2011-09-06
> **linuxuser12345 said:**
> What does "rm -rf" do?

man rm

;-)

and read here [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

second post by [jdong]("http://ubuntuforums.org/member.php?u=780")

---

### Post by alegomaster on 2011-09-06
> **haqking said:**
> That is hardly accurate and very elitist.

I speak as a very experienced Windows user (historically)


I know it was elitist, but I just wanted to put some lol to this.


Truly the reason why I find that Linux is so safe is because of how the kernel was made. It was made with security in mind and system calls are great for preventing your time variable from being overwritten by "accident". I know every OS has this these days, but one thing they don't all have is the ability to load or unload packets of code (In Linux: Modules). That means that if you know that your foo module is not working properly, then you can unload it and your OS won't blow up.

Actually when you consider the above comment, I am very wrong. The real issue is that there are many "uneducated" people who are not smart about what they download online. I never got a virus on windows and that is because I was smart on the Internet on what sites I visit and what I download.

---

### Post by linuxuser12345 on 2011-09-06
Are there any other security vulnerabilities that Linux has?

---

### Post by alegomaster on 2011-09-06
> **linuxuser12345 said:**
> Are there any other security vulnerabilities that Linux has?

There is somebody using su instead of sudo.

---

### Post by WorMzy on 2011-09-06
Sure, although it depends entirely on which applications you choose to run, in particular, daemons. Apache, as you may have noticed from a post or two floating around, has recently released version 2.2.20. This was released with the primary purpose of [fixing a DoS vulnerability]("http://nakedsecurity.sophos.com/2011/08/31/apache-2-2-20-released-to-fix-dos-vulnerability/") that was recently discovered. Applications like apache, which can interact with the outside world via the internet, are run as specific users to minimise the damage that could be caused by someone gaining access to your system by using an vulnerability in the software. If these "vulnerable" applications were run as root, a malicious person could exploit the vulnerability and have free reign of your system.

But, since these exploits are normally discovered by the Linux community, they're usually fixed before anyone can take advantage. Of course, unless a vulnerable computer is updated, the security risk remains; which is why you should endeavour to keep your system up-to-date.

---

### Post by jwbrase on 2011-09-06
> **linuxuser12345 said:**
> What does "rm -rf" do?

It deletes a folder and everything in it without asking for confirmation or sending anything to the recycle bin (things are deleted permanently). This can be useful, but if you don't know exactly what you're deleting it can be dangerous. If you use sudo and try "rm -rf"ing /, the root folder, it will start deleting every file on every disk attached to your computer until it deletes something critical and the system crashes.

---

### Post by drs305 on 2011-09-06
Moved to Recurring Discussions.

---

### Post by sisco311 on 2011-09-06
> **jwbrase said:**
> If you use sudo and try "rm -rf"ing / **(and the --no-preserve-root option is enabled)**, the root folder, it will start deleting every file on every **filesystem mounted** until it deletes something critical and the system crashes.

Fixed :)

Since 2006 (too lazy to google the version number) or so, the commands from GNU coreutils (rm, chown, chmod, ...) default to the --preserve-root options...

---

### Post by 3Miro on 2011-09-06
There are two types of attacks: psychological and technological.

Psychological attacks attack the USER and not the OS. The relative obscurity of Linux and the overall literacy of Linux users helps Linux become more secure in the psychological aspect, but if Linux were to become main-stream and more regular people started using it, then it would be just the same as any other OS. Remember that the psychological vulnerability is the USER (i.e. YOU).

(Perhaps even with popularity, Linux would be more psychologically secure due to things like the trusted Software Center, very few people with little skills ever have to outside of it and that helps, but this is a minor point since other OS are including their versions of the Software Center in their next releases)

Technological attacks occur despite the users best of skills and knowledge. When Unix was first designed in the late 60's early 70's, it was designed bottom up with security in mind. In contrast for many years, Windows security was an afterthought left to the AV and Security Suit software to patch. Windows XP SP2 was the first release (actually patch) to come with default firewall, Windows Vista was the first Windows to be designed with security from bottom up. Most of Vista and 7's security features were directly taken from Unix, it is safe to say that MS is trying to catch up in a few years after several decades of lagging.

Unix design is one aspect of Linux security, the second powerful aspect is the open community. Linux beats both Windows and OSX in terms of fast response to threats. When someone finds a problem with Windows or OSX, then they have to report it and wait for MS or Apple to respond and fix the issue (that is assuming the person hasn't done anything illegal to find the problem, it is illegal to poke too much within Windows and OSX). In Linux, the person who finds the issue is often the person to fix it, patching time averages in hours.

---

### Post by _d_ on 2011-09-06
> **alegomaster said:**
> The fact that every Linux user is smarter then the suitable Windows counterpart

Rather quite elitist, don't you think? Also appears to be an unneeded bash against people that use Windows.

---

### Post by sisco311 on 2011-09-06
> **3Miro said:**
> 
(Perhaps even with popularity, Linux would be more psychologically secure due to things like the trusted Software Center, very few people with little skills ever have to outside of it and that helps, but this is a minor point since other OS are including their versions of the Software Center in their next releases)


Not sure why did you use the parentheses. I think, that the Software Center/package manager/trusted software source is one of the key things that makes a modern Linux system secure for average computer user (whatever average means).

---

### Post by 3Miro on 2011-09-06
> **sisco311 said:**
> Not sure why did you use the parentheses. I think, that the Software Center/package manager/trusted software source is one of the key things that makes a modern Linux system secure for average computer user (whatever average means).

It is only a partial improvement, people installing random software is only one aspect of the problem. Ultimately educating the user is the only way to defend against psychological attack, I didn't want anyone to think otherwise. The USER is the vulnerability here.

Also, MS is including their version of Software Center in the next Windows and I think Apple is doing something similar (they have had ports for quite some time also).

---

### Post by 3Miro on 2011-09-06
> **_d_ said:**
> Rather quite elitist, don't you think? Also appears to be an unneeded bash against people that use Windows.

alegomaster's may have stated it in a somewhat impolite way, however, it is a fact that for many years Linux distributions required at least basic computer literacy for someone to even install them. And Linux hardly ever comes pre-installed. The bulk of Linux users are fairly computer savvy people, while most computer illiterate people just use whatever comes pre-installed (i.e. Windows). 

This obviously doesn't mean all Windows users ate illiterate, but if a less savvy user falls victim to a virus or a bot, then other Windows machines are that much more vulnerable (i.e. the savvy windows users have to put quite a bit more effort in keeping themselves safe).

---

### Post by Dangertux on 2011-09-06
You're not going to like it...But the honest answer.

Nothing but a thinly veiled layer of obscurity, and the efforts of thousands of people worldwide.

---

### Post by WorMzy on 2011-09-06
> **Dangertux said:**
> You're not going to like it...But the honest answer.

Nothing but a thinly veiled layer of obscurity, and the efforts of thousands of people worldwide.

That is actually a really good point. Why target 1 in 100 users when you can target the other 99 much more easily?

I still think that Linux is vastly more secure than Windows will ever be, but if focus switched from Window to Linux, how long would it take for "bad people" to break past the extra security?

We may never know.

---

### Post by Dangertux on 2011-09-06
> **WorMzy said:**
> That is actually a really good point. Why target 1 in 100 users when you can target the other 99 much more easily?

I still think that Linux is vastly more secure than Windows will ever be, but if focus switched from Window to Linux, how long would it take for "bad people" to break past the extra security?

We may never know.

I honestly think the concept that Linux is vastly superior to Windows in the security department is very contrived.

Yes -- the default out of box configuration for most Linux distros is head and shoulders above an out of the box Windows configuration. However, when you really get into security features they are comparable on most levels in terms of desktop operating systems. So long as the end user doesn't boff up their configuration too bad.

When you get into the server realm Windows server can be configured very secure. However, Linux is superior in that it is truly more configurable, and more scalable (this is my opinion)

---

### Post by linuxuser12345 on 2011-09-07
Ubuntu needs to start coming by default with a firewall. That is one thing Canonical needs to catch on about. I mean, Microsoft for crying-out-loud has made firewalls a crucial and default part of their OSs since Windows XP SP2!
Also, Fedora has caught on, so why can't Ubuntu? Ubuntu is supposed to be the best of the best when it comes to Linux, and it is, but there are some aspects that need to be improved upon, like security. It is one thing to say the OS is safe and secure, but it is a whole other thing to actually show the proof. Maybe Canonical will get their act together come 11.10.
(If someone wants to tell Canonical about this, please go ahead, because I don't know who to tell besides the people on the forums!)

---

### Post by WorMzy on 2011-09-07
> Ubuntu needs to start coming by default with a firewall.

?

I'm pretty sure that Ubuntu comes with iptables and ufw out of the box.

> Ubuntu is supposed to be the best of the best when it comes to Linux

lol, no. Ubuntu is certainly the most popular distro, and it's a great first step into the world of Linux; but I wouldn't consider it the best. Not by a long stretch.

---

### Post by haqking on 2011-09-07
> **linuxuser12345 said:**
> Ubuntu needs to start coming by default with a firewall. That is one thing Canonical needs to catch on about. I mean, Microsoft for crying-out-loud has made firewalls a crucial and default part of their OSs since Windows XP SP2!
Also, Fedora has caught on, so why can't Ubuntu? Ubuntu is supposed to be the best of the best when it comes to Linux, and it is, but there are some aspects that need to be improved upon, like security. It is one thing to say the OS is safe and secure, but it is a whole other thing to actually show the proof. Maybe Canonical will get their act together come 11.10.
(If someone wants to tell Canonical about this, please go ahead, because I don't know who to tell besides the people on the forums!)

The Linux kernel has [Netfilter/IPTables]("http://www.netfilter.org/") hardcoded into it so comes with most Linux Distros depending on kernel.

Anything added such as UFW/GUFW, Firestarter is merely an interface for it so people are not stuck with command line.

So linux([ubuntu iptables]("https://help.ubuntu.com/community/IptablesHowTo")) does come with a firewall.

---

### Post by linuxuser12345 on 2011-09-07
> **WorMzy said:**
> ?

I'm pretty sure that Ubuntu comes with iptables and ufw out of the box.


[The Ubuntu Desktop Guide says otherwise, and recommends getting a firewall last time I checked.]edit: Well, the firewall that comes with Ubuntu needs to be activated anyways.

---

### Post by haqking on 2011-09-07
> **linuxuser12345 said:**
> [The Ubuntu Desktop Guide says otherwise, and recommends getting a firewall last time I checked.]edit: Well, the firewall that comes with Ubuntu needs to be activated anyways.


See my post above.

and:

By default, Ubuntu ships with no open ports on public interfaces. In  other words, a "port scan" would show all closed ports, nothing open. As  a result, putting up a firewall would provide no more security than not  putting one up. Remember that open ports provide services that hackers  can connect to, and only if they can connect to these services can they  be potentially abused and exploited. 

from [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by linuxuser12345 on 2011-09-07
What is the best branch of Linux or GNU/Linux, in your opinion?

---

### Post by haqking on 2011-09-07
> **linuxuser12345 said:**
> What is the best branch of Linux or GNU/Linux, in your opinion?

Distro i presume you mean ?

Depends on level of experience really, it is a very broad and often elitist subject.

Ubuntu is obviously geared towards the masses and abstracts the complex.

Slackware/Debian for nitty gritty of Linux (complexity is not abstracted as in more user friendly Linux distros)

Redhat/Novell Suse are generally corporate etc.

In my opinion i like Debian and Ubuntu which is what i run, i run slack and a couple of others in a VM

at end of day when experience is gained you can pretty much do the same in all just a case of the preferred way of doing it i guess ;-)

---

### Post by Dangertux on 2011-09-07
Real quick on the firewall topic. It's already been stated that Ubuntu includes a VERY mature and capable firewall. 

That being said, I really think entirely too much emphasis is put on a network firewall for the home user. Here's the thing about firewalls.

If you're not running a service , the point of a firewall is utterly non-existant.

If you are, the dynamic that a firewall plays in the security of that service changes greatly from inbound filtering to outbound filtering. Since you clearly shouldn't be blocking connections to your services (if you want them to work). The focus changes more toward trying to enforce that the application behaves properly.

On server systems a firewall is much more useful in outbound traffic filtering (for things like reverse connections which generally signify something really bad is about to happen). 

However, firewalling a port that does not have a listening service bound to it is extremely redundant and pretty much pointless. I really do think that firewalls are one of the most misunderstood applications in network security.

---

### Post by lykwydchykyn on 2011-09-07
One often-overlooked aspect of GNU/Linux when it comes to security is its modularity and subsequent diversity.

Someone who wants to attack Windows knows that an exploit targeting something in the current version of Windows can be used against a huge number of Windows users.

On the other hand, an exploit against the current Linux kernel, gcc, ssh, etc.  may only affect a handful of Linux machines.  Every distro ships different versions of various packages, patches them differently, or may not even ship them at all.

There are a lot of things I can't remove from a Windows install  without using some extreme 3rd-party tools (like n-lite).  By contrast, there's very little I can't remove or swap out from most Linux distros.

That doesn't do much if you have millions of people installing Ubuntu and using the default desktop and apps, I guess.  But it definitely limits the scope of a potential exploit.

Ultimately, I'd never say Linux is inherently more "secure", but I would assert that it's more securable and harder to target for specific exploits.

---

### Post by WorMzy on 2011-09-07
> **linuxuser12345 said:**
> What is the best branch of Linux or GNU/Linux, in your opinion?

I'm going to assume you mean distro as well. I don't have any time for any distro except Arch these days. It's certainly not a newbie friendly distro like Ubuntu, but it offers a much higher level of control, and since it adopts a rolling release update method, you don't need to install a huge update twice a year. Also, ABS is a damn sight simpler than APT.

---

### Post by linuxuser12345 on 2011-09-07
Is Ubuntu safer than Mac OS X?

---

### Post by haqking on 2011-09-07
> **linuxuser12345 said:**
> Is Ubuntu safer than Mac OS X?


see recurring discussion[ Is Ubuntu more secure than OSX recurring discussion thread]("http://ubuntuforums.org/showthread.php?t=1817209")

also the concepts already mentioned.

---

### Post by linuxuser12345 on 2011-09-07
Is security significantly better in Ubuntu than in Windows 7?

---

### Post by linuxuser12345 on 2011-09-07
Why would a person use Ubuntu at all when he/she can just use Windows 7 with a superuser account set up, and have awesome compatibility with everyday applications? What are the advantages of Ubuntu?

---

### Post by haqking on 2011-09-07
> **linuxuser12345 said:**
> Why would a person use Ubuntu at all when he/she can just use Windows 7 with a superuser account set up, and have awesome compatibility with everyday applications? What are the advantages of Ubuntu?

you pay for Windows 7.

Linux is free

its all choice, the concepts which cover the whys and wherefores of security have been covered.

Its a layered approach, a ongoing vigilant process easily secured or unsecured by the user/admin.

---

### Post by linuxuser12345 on 2011-09-07
So, if I ever get a new computer, I should just stay with the copy of Windows that it comes with and set up a superuser account? Is there any malware, adware, or are there any viruses that can get past a set up superuser system in Windows?

---

### Post by haqking on 2011-09-07
> **linuxuser12345 said:**
> So, if I ever get a new computer, I should just stay with the copy of Windows that it comes with and set up a superuser account? Is there any malware, adware, or are there any viruses that can get past a set up superuser system in Windows?

Use what you are comfortable with and meets your needs.

The topics of AV on Linux and in Windows have been discussed many times here and the security concepts have been covered already.

Most of the Viruses in the Wild are targeted at Windows environments, file permissions are different.

---

### Post by linuxuser12345 on 2011-09-07
So, is there any malware, adware, or are there any viruses that can get past a set up superuser system in Windows?

---

### Post by WorMzy on 2011-09-07
Security isn't the only advantage that most Linux distros have over Windows.

For example, installing new software, and keeping current software up-to-date. On Windows, this is a chore: searching on google with vague words and phrases, and hoping you find some software that is A) trustworthy, B) hosted on a secure website, and, optionally, C) free to download and use. Then you have to keep visiting the various websites you downloaded the software from, to see if there's an update available.

On Linux, you generally download and install software from a single place, and keeping it all updated is as easy as running a single command.


In terms of drivers, on Windows, you often need to download and install drivers for a lot of your hardware -- graphics cards, network adaptors, web cams, etc.. On linux, almost everything is built into the kernel (or added into the kernel at boot as modules).

Then you have the freedom that Linux offers you. Windows is incredibly limited in terms of customization. The OS is mostly locked down, and all you can do is change colour themes and mouse cursors.

Linux, on the other hand, is almost completely customizable. Just look at desktop environments for example: you can have GNOME, or KDE, or XFCE, or LXDE, or none of the above. You can pick and mix applications as you see fit. You can even customise the kernel itself -- choosing which parts of it are built into the kernel, which parts are left out but are still built as modules, and which bits are just left out entirely.

In short, Linux is damned awesome. Windows, eh, not so much.

---

### Post by haqking on 2011-09-07
> **linuxuser12345 said:**
> So, is there any malware, adware, or are there any viruses that can get past a set up superuser system in Windows?

[http://nakedsecurity.sophos.com/2009/11/03/windows-7-vulnerable-8-10-viruses/](http://nakedsecurity.sophos.com/2009/11/03/windows-7-vulnerable-8-10-viruses/)

There is a superuser account by default in Windows its called administrator and most people run everything as that user.

these questions have been asked lots and lots and covered on here alot.

Try the search facility it should answer any more comparative questions.

---

### Post by Quadunit404 on 2011-09-07
> **WorMzy said:**
> For example, installing new software, and keeping current software up-to-date. On Windows, this is a chore: searching on google with vague words and phrases, and hoping you find some software that is A) trustworthy, B) hosted on a secure website, and, optionally, C) free to download and use. Then you have to keep visiting the various websites you downloaded the software from, to see if there's an update available.
A lot of software for Windows comes with a built-in update checker and in some cases, automatically update itself.

> **WorMzy said:**
> On Linux, you generally download and install software from a single place, and keeping it all updated is as easy as running a single command.
```
sudo apt-get install some-software
sudo add-apt-repository ppa:johndoe/ppa-for-some-software
sudo apt-get upgrade

``` I do realize not all Linux distros use Apt as their package manager or the PPA system Ubuntu uses, but that is definitely not one command.

> **WorMzy said:**
> In terms of drivers, on Windows, you often need to download and install drivers for a lot of your hardware -- graphics cards, network adaptors, web cams, etc..
Unless you buy a PC prebuilt, which comes with everything you need to do what you want your computer to do (work) ootb.

> **WorMzy said:**
> On linux, almost everything is built into the kernel (or added into the kernel at boot as modules). ```
sudo apt-get install nvidia-current
sudo apt-get install fgrlx
``` Those don't ship with the kernel.

> **WorMzy said:**
> Then you have the freedom that Linux offers you. Windows is incredibly limited in terms of customization. The OS is mostly locked down, and all you can do is change colour themes and mouse cursors. And backgrounds. And screensavers. And sounds. And if you hack it (which is actually really easy) you can do even more.

> **WorMzy said:**
> Linux, on the other hand, is almost completely customizable. Just look at desktop environments for example: you can have GNOME, or KDE, or XFCE, or LXDE, or none of the above. You can pick and mix applications as you see fit. You can even customise the kernel itself -- choosing which parts of it are built into the kernel, which parts are left out but are still built as modules, and which bits are just left out entirely. The average user doesn't care. All they want is for their computer to work. They don't care if they can customize their desktop, or change how their kernel works, or anything. They just want to use their computer.

> **WorMzy said:**
> In short, Linux is damned awesome. Windows, eh, not so much.

Your argument has been invalidated.

---

### Post by WorMzy on 2011-09-07
I fail to see how your points invalidate any of mine.

Okay, I skipped over some of the customisation possible on Windows; but Linux is still more customisable than Windows.

Installing software is still a lot easier than in Windows, and you're not likely to add a new software repository for every application you install anyway.

Keeping software up-to-date is still simpler than Windows.

I'm not familiar with the second package you mentioned there, but the nvidia driver is owned by nvidia and is closed-source, which is why it's not shipped with the kernel; the nouveau driver is, for most intents and purposes, an ideal substitute anyway.

If the average user doesn't care about customisability, then they can stay with Windows (or whatever they're using).

Oh, and a ready built computer may have all the drivers pre-installed for the hardware it ships with, but any new hardware still needs to have it's own drivers installed.

---

### Post by KiwiNZ on 2011-09-07
There is no safe OS. The primary security flaw will always exist, that is, between the Chair and the Keyboard.

---

### Post by linuxuser12345 on 2011-09-07
That, is an excellent quote my friend! :)

---

### Post by linuxuser12345 on 2011-09-07
> Installing software is still a lot easier than in Windows, and you're  not likely to add a new software repository for every application you  install anyway.

Installing software on Linux isn't necessarily much easier than on Windows. Most 3rd party applications, etc. that you don't find in the repositories are in a compressed tar.gz format that the average user does not understand or want to understand how to install through the command line. While on Windows, everything you find that is installable (besides a few rare exclusions) is in a pre-built excutable format with built-in commands and code that work as the terminal in the background without actually having to deal with the terminal at all.

---

### Post by Dangertux on 2011-09-07
Sigh... I'm totally with KiwiNZ on this one.

Also -- this is a point that has been debated over and over into the ground. The bottom line is this.

Any operating system can be made reasonably secure. It really depends on what your needs, and desires are as to which operating system you use. They each have strengths and weaknesses.

---

### Post by sisco311 on 2011-09-07
> **linuxuser12345 said:**
>  While on Windows, everything you find that is installable (besides a few rare exclusions) is in a pre-built excutable format with built-in commands and code that work as the terminal in the background without actually having to deal with the terminal at all.

Including malwares, unfortunately on Linux you have to follow a guide, like this one to install them: 
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

j/k

---

### Post by Tibuda on 2011-09-07
> **WorMzy said:**
> On Linux, you generally download and install software from a single place, and keeping it all updated is as easy as running a single command.

Good luck keeping all your software updated in Ubuntu without updating the whole operating system every six months or messing with third-party repositories.

---

### Post by WorMzy on 2011-09-07
> **Tibuda said:**
> Good luck keeping all your software updated in Ubuntu without updating the whole operating system every six months or messing with third-party repositories.

I already stated that I use Arch. ;D

It's a fair point though, although you don't *have* to upgrade to the latest and "greatest" every six months.

---

### Post by beew on 2011-09-07
> **Tibuda said:**
> Good luck keeping all your software updated in Ubuntu without updating the whole operating system every six months or messing with third-party repositories.

Who would keep all their software up to date in Windows? You must have either very few softwares or a lot of money to burn.

My Ubuntu box is very up to date (yes, I mess with third party repo a lot) and it is a lot of easier to me to do it this way than with Windows.

---

### Post by walt.smith1960 on 2011-09-08
> **Tibuda said:**
> Good luck keeping all your software updated in Ubuntu without updating the whole operating system every six months or messing with third-party repositories.

Non-LTS releases are supported for 18 months, LTS releases for 3 years.  I just reinstalled a Win7 setup yesterday. It took me 3.5 hours to get the basics installed, SP1, updates, antivirus, etc. etc.  This didn't include an office suite or other apps or any user data.  Ubuntu takes about an hour on the same machine, it'd take less if I'd create a post-install script.

---

### Post by Tibuda on 2011-09-08
> **beew said:**
> Who would keep all their software up to date in Windows? You must have either very few softwares or a lot of money to burn.
You know there are free* software for Windows too. Most of major Linux apps have a Windows version: OpenOffice, GIMP, Pidgin, Vim, LyX, Firefox, Thunderbird, GnuCash, VLC, Audacity, Handbrake, Teeworlds, Minecraft.

* as in both beer and speech


> **walt.smith1960 said:**
> Non-LTS releases are supported for 18 months, LTS releases for 3 years.  I just reinstalled a Win7 setup yesterday. It took me 3.5 hours to get the basics installed, SP1, updates, antivirus, etc. etc.  This didn't include an office suite or other apps or any user data.  Ubuntu takes about an hour on the same machine, it'd take less if I'd create a post-install script.
What is your point? This has nothing to do with my post.

EDIT: I see your point now. Yes, the releases are supported, but they only get security updates, not major releases. My post is about having updated software.

---

### Post by branded7k on 2011-09-12
> **linuxuser12345 said:**
> I have a simple question and I am sure a lot of you may be pondering the same question. In your opinion, if not in fact, what makes Ubuntu and other (GNU/)Linux distributions so safe? Is it just sudo? Is it more than that? Explain.

I have been involved with computers for over 40 years now.  I am  also a retired government network administrator, with over 25 years of  experience supporting various operating systems on "big iron" systems,  down to LAN/WAN environments on micro computer platforms.  I've  supported Windows client/servers from versions 3.xx through XP.  I've  also taught CIS at a local community college for over 11 years, teaching  introductory courses, programming in BASIC, C, C++, COBOL, database  administration, FORTRAN and systems analysis, to name a few.

I've  listed my credentials, not to show you how "smart" I am, but to let you  know I have an unbiased and varied experience with all types of  operating systems.  As others have pointed out, no operating system is  perfect, for any number of varied reasons.

Now, to get down to  the meat of your question.  I've had friends and family bring their  Windows PCs to me over the years to fix.  They were usually loaded with  spyware, viruses, etc.  As one of the members here pointed out,  restoring a Windows PC is a "layered" approach.  First you must restore  the OS, then re-install all the applications.  Yes, you could create an  "image", but it was machine-specific, due to all the driver  requirements.  To make this long story shorter, over the past 5 years, I  have converted all family and friends to Ubuntu Linux.  No more BSOD,  hanging applications, viruses, spyware, etc. and I'm not getting calls  every couple of weeks to come look at their machines!  Ages of users  vary from 20-77 years.  Not one user has ever requested to have Windows  put back on their machine!!  Take it for what it's worth...

---

### Post by Dangertux on 2011-09-12
> **branded7k said:**
> I have been involved with computers for over 40 years now.  I am  also a retired government network administrator, with over 25 years of  experience supporting various operating systems on "big iron" systems,  down to LAN/WAN environments on micro computer platforms.  I've  supported Windows client/servers from versions 3.xx through XP.  I've  also taught CIS at a local community college for over 11 years, teaching  introductory courses, programming in BASIC, C, C++, COBOL, database  administration, FORTRAN and systems analysis, to name a few.

I've  listed my credentials, not to show you how "smart" I am, but to let you  know I have an unbiased and varied experience with all types of  operating systems.  As others have pointed out, no operating system is  perfect, for any number of varied reasons.

Now, to get down to  the meat of your question.  I've had friends and family bring their  Windows PCs to me over the years to fix.  They were usually loaded with  spyware, viruses, etc.  As one of the members here pointed out,  restoring a Windows PC is a "layered" approach.  First you must restore  the OS, then re-install all the applications.  Yes, you could create an  "image", but it was machine-specific, due to all the driver  requirements.  To make this long story shorter, over the past 5 years, I  have converted all family and friends to Ubuntu Linux.  No more BSOD,  hanging applications, viruses, spyware, etc. and I'm not getting calls  every couple of weeks to come look at their machines!  Ages of users  vary from 20-77 years.  Not one user has ever requested to have Windows  put back on their machine!!  Take it for what it's worth...

For what it's worth you have way cooler friends than me :-P Just kidding.

You have some very valid points in there.  However, I definitely have my issues with the argument. I agree whole-heartedly that Ubuntu Linux is a an amazing desktop operating system, especially for those coming from the malware-laden world of Windows.

However, I would like to pose a few questions to you. Since you have expressed that System administration and Information Systems Management is your forte`. 

I think for those inexperienced with enterprise environments they tend to take the fundamental assumption that "Linux is safer" to an extreme. Would you agree that in an enterprise or small business environment where production systems are involved Linux (Ubuntu or otherwise) is just as easily targeted as Windows Server? 

Also, would you agree that with the advent of more complicated web technologies (database powered CMS's, Analytics systems such as SAP, and ERP) and the general movement to the "cloud" that platform agnostic attacks such as SQL Injection are a very real threat on Linux, Unix and Windows powered servers?

And if you agree with that statement, would you say that overall system administrators do not take such threats seriously enough? Often times forgoing the use of measures they have (such as proper IDS configuration, application level firewalls, NAC's and Web application firewalls such as mod-security) blaming it solely on the "developer's bad code"?

The last question, I personally believe that Linux truly shines when it comes to support for virtualization, which I happen to believe is the next big thing in the IT industry. Obviously as it lowers the bottom line for the bossman, which is what bossman likes to hear. How would you say that virtualization security translates from the traditional physical machine models that most system admins (linux or otherwise) are used to implementing? Obviously, we have different technologies involved and a lot of our standard appliances are no longer applicable in a "virtual" world. Do you feel that virtual security in the Linux environment is ready to go mainstream yet? Do you think that solutions from vendors like Juniper or Citrix are up to the task? Do you think companies like Canonical and Red Hat are properly implementing these technologies for the best experience their clients can get? 

Sorry if this is long winded, but I'm curious on a professional standpoint, you seem to have a long history in system administration, and I'm very interested in your opinions. As well as possibly steering the discussion to shed light on other topics that the average "Linux is secure so I use it" end user might not be aware of. 

Thanks

---

### Post by branded7k on 2011-09-13
> **Dangertux said:**
> I think for those inexperienced with  enterprise environments they tend to take the fundamental assumption  that "Linux is safer" to an extreme. Would you agree that in an  enterprise or small business environment where production systems are  involved Linux (Ubuntu or otherwise) is just as easily targeted as  Windows Server?

Wheeee... This discussion could get very  long-winded!  Alright, let's enlighten those who have not had the joy of  supporting the "enterprise" environment.   To give everyone an idea of  the size of my enterprise, we had over 211 servers and just over 5500  workstations.  The biggest security threat always comes from "within"  the organization.  Whether it's users with bad security habits, or  incompetent administrators.  Many times some security measures are not  implemented merely to ease administration of the network.  Another  factor can also be companies/organizations who are unwilling to invest in  CE/mentoring of their IT staff and employees.

As far as Linux  being more vulnerable than Windows.  Unix is still the most widely used  O/S in the world.  Is that due to the fact it's just a de-facto  standard?  I don't think so.  When MSCEs were scrapping to pull down  $40K a year, any competent Unix administrator could walk in the door at  $80-110K.  I recall an instance where a top IT staff member forgot the  admin password on the PDC.  I was able to run chntpw from a Slackware  floppy boot disk (pre-active directory days) and overwrite the SAM.   Needless to say, everyone ran around with their hats pulled down collars  pulled up!

Another point.  When we were migrating from Win2K to  XP, we were told by Uncle Bill to wait for SP1.  There were over 600,000  known bugs in the first release, but there would only be 32,000+ in  SP1!  In addition, we paid Uncle Billy over 2.6M dollars a year in  licensing and maintenance fees to use his wonderful product!

> Also, would you agree that with the advent of more  complicated web technologies (database powered CMS's, Analytics systems  such as SAP, and ERP) and the general movement to the "cloud" that  platform agnostic attacks such as SQL Injection are a very real threat  on Linux, Unix and Windows powered servers?

Human factors  aside, there's no comparison between Apache and MS Web Server (IMH0).   Could tell you more horror stories, but trying to keep this from  snowballing into a big p***ing contest between Unix/Windows.

> And if you agree with that statement, would you say that  overall system administrators do not take such threats seriously enough?  Often times forgoing the use of measures they have (such as proper IDS  configuration, application level firewalls, NAC's and Web application  firewalls such as mod-security) blaming it solely on the "developer's  bad code"?

Yep.  I addressed those issues earlier in my  reply.  Bottom line - I'll take a Unix/Linux kernel over an NT kernel  any day of the week!

> The last question, I personally believe that Linux truly  shines when it comes to support for virtualization, which I happen to  believe is the next big thing in the IT industry. Obviously as it lowers  the bottom line for the bossman, which is what bossman likes to hear.  How would you say that virtualization security translates from the  traditional physical machine models that most system admins (linux or  otherwise) are used to implementing? Obviously, we have different  technologies involved and a lot of our standard appliances are no longer  applicable in a "virtual" world. Do you feel that virtual security in  the Linux environment is ready to go mainstream yet? Do you think that  solutions from vendors like Juniper or Citrix are up to the task? Do you  think companies like Canonical and Red Hat are properly implementing  these technologies for the best experience their clients can get?

Sorry if this is long winded, but I'm curious on a professional  standpoint, you seem to have a long history in system administration,  and I'm very interested in your opinions. As well as possibly steering  the discussion to shed light on other topics that the average "Linux is  secure so I use it" end user might not be aware of. 

Thanks

Virtual environments?  Again, I attribute the power of the  Unix/Linux kernel being able to truly "multi-task".  After all, Unix was  the first true multi-taking O/S (albeit, text-based at the time).  As  far as going "mainstream", absolutely.  The architecture is proven and  mature.  Again, the problem is finding good Unix administrators.   They're like hens teeth.  MSCEs are a dime a dozen these days (I used to  be one!).  As far as Juniper and Citrix goes, I've never had the joy of  supporting them.  Right after I retired they were talking about  implementing a Citrix solution for MVD clients.  Heard later it was a  kludge at first, but they got it up and limping around.

So, bottom line?  Both O/Ss can be secured in an enterprise environment with the appropriate measures in place.  IMHO, Unix is still a much more mature O/S and will always maintain an edge over any other O/S who has its roots in the micro-computer architecture.

---

### Post by Dangertux on 2011-09-13
Very well thought out reply. I really enjoyed reading about your experiences.  

The only thing that I don't think you really addressed completely was the virtualization bit, but if you didn't have much experience with it like you said no worries. 

I cometely agree with you about good nix admins being very rare, I also laughed at the msce anecdote because it's still very much like that lol.  Also I completely agree about IIS vs Apache although in MS defense IIS has come a long way in the past few years. Still IMO not as stable as Apache but is at least a contender finally. You are also correct that UNIX is much more mature, truth of the matter is, the way I see it at this point unless Microsoft steps up their game they may lose any footing they had in the enterprise market because to be honest I don't see very many MS server implementations being efficient or successful in business with more then 200 or so employees. 

Again thank you for taking the time to reply to that, it was probably a little "much" for lunch hour on a Monday :-P

---

### Post by linuxuser12345 on 2011-09-15
So, for the average computer user, what would you recommend? Microsoft Windows 7 or Ubuntu 11.04?

---

### Post by Dangertux on 2011-09-15
> **linuxuser12345 said:**
> So, for the average computer user, what would you recommend? Microsoft Windows 7 or Ubuntu 11.04?

An average computer user can mean a wide variety of things. I would recommend the OS that best fit their needs. 

If they are a hardcore gamer I'm obviously not going to recommend Ubuntu. If they are a tech savvy blogger who enjoys surfing the internet I would likely recommend Ubuntu. If they are a graphic designer I would recommend anything with photoshop on it (sorry to the gimp fans, it's not quite there in terms of production).

All the security in the world can't help you if your system is essentially useless for what you need it to do. You have a very secure, very expensive paperweight.

---

### Post by linuxuser12345 on 2011-09-15
> **Dangertux said:**
> 
All the security in the world can't help you if your system is essentially useless for what you need it to. You have a very secure, very expensive paperweight.
What do you mean by that?

---

### Post by Dangertux on 2011-09-15
> **linuxuser12345 said:**
> What do you mean by that?

I mean you should use the right tool for the right job. You wouldn't use a rake to dig a hole, you'd use a shovel.

---

### Post by branded7k on 2011-09-18
> **linuxuser12345 said:**
> What do you mean by that?

"Average" computer user is a relative term.  I would advise anyone considering using Linux to assess both your software and hardware needs.  In other words, if one does mostly word processing, email, etc. and has commonly branded hardware, I personally would recommend Linux over Windows.  On the other hand, if you're thinking of converting from Windows and use applications which have a narrow purpose (we called them "vertical" applications in the old days) you may want to stick with Microsoft.  For example, you have a heavy investment in a high-end accounting application.  There may not be a direct port to Linux, requiring you to invest many hours in a manual conversion, or possess a high level of programming skill.

One last note on this subject.  Users who are considering converting to Linux must also be willing to research answers to their problems.  Be patient.  There are several forums and users willing to share with you.  Remember, there is no "Linux" company.  The Linux community is a world-wide consortium of users, programmers and academics who are donating their time to provide computer users with viable (and more secure) alternative to the commercial standard.

---

### Post by linuxuser12345 on 2011-09-19
I still think that Ubuntu by default should come shipped with an easy to customize, easy to use, easy to turn on and off firewall, like the Firewall Configuration tool.

---

### Post by Dangertux on 2011-09-19
> **linuxuser12345 said:**
> I still think that Ubuntu by default should come shipped with an easy to customize, easy to use, easy to turn on and off firewall, like the Firewall Configuration tool.

You can install gUFW for Ubuntu like Mint has if that is what you're referring to. However, in my personal opinion it really doesn't get much more simple than...

```

sudo ufw enable

```As far as configuring it, it's a very easy syntax. For most desktop installations there is no need to configure it further than turning it on, and on a server you would want full access to the more robust features of iptables that UFW doesn't utilize. So really, it's a pretty good balance in my opinion. Plus, in its default configuration Ubuntu isn't running any services, so what would even be the need of a firewall? Other then those folks who chase that ever illusive "stealth" rating on grc.com, which imho is complete garbage.

---

### Post by linuxuser12345 on 2011-09-20
But new users do not know how to enable the firewall through a terminal, or know how to manipulate a terminal at all.

---

### Post by Dangertux on 2011-09-20
> **linuxuser12345 said:**
> But new users do not know how to enable the firewall through a terminal, or know how to manipulate a terminal at all.


And I doubt that a user who has no experience with Windows would be able to find the Microsoft Windows Firewall either.

The point is if you have no experience with something you're obviously going to have to consult the documentation or someone who does know.

---

### Post by linuxuser12345 on 2011-09-20
But the microsoft firewall is easily configurable with a GUI. Ubuntu needs a firewall easily configurable with a GUI by default.

---

### Post by haqking on 2011-09-20
> **linuxuser12345 said:**
> But the microsoft firewall is easily configurable with a GUI. Ubuntu needs a firewall easily configurable with a GUI by default.

Windows needs a firewall by default, Linux doesnt !

---

### Post by WorMzy on 2011-09-20
> **linuxuser12345 said:**
> But the microsoft firewall is easily configurable with a GUI. Ubuntu needs a firewall easily configurable with a GUI by default.

Why?

---

### Post by haqking on 2011-09-20
@Linuxuser12345

If you go back and read this thread you will see you already raised the firewall question and it has already been answered in the following posts:

27
29
32

all in response to your previously raised question on firewalls in your post 25

---

### Post by Dangertux on 2011-09-20
Getting back into the firewall, as I've said before (in this thread even). Firewalls are greatly misunderstood.

A firewall will do NOTHING if you have no services running. It seems there is a general lack of understanding about ports. A "cracker" can't magically open a port that doesn't have a service running and start communicating with the machine. 

The ONLY good a firewall will do on a machine that has no services running is in the event of a reverse connection. IE: User downloads some malicious file, malicious file phones home and establishes a reverse connection to an evil "cracker". 

That being said, neither windows firewall, iptables, NOR proprietary desktop firewall solutions block outbound traffic by default. So simply turning on a firewall wouldn't stop this anyway.

---

### Post by BBQdave on 2011-09-20
> **Dangertux said:**
> If they are a graphic designer I would recommend anything with photoshop on it (sorry to the gimp fans, it's not quite there in terms of production).

I find myself very productive with *GIMP* and *SCRIBUS.*:D

And has pointed out in various statements throughout this thread, the user has much (perhaps the most) affect on security and safe computing.  I think too (and I am not putting down Windows users) there is a different mind set with the two distros (anything Linux and Windows).  From what I have observed, though productive, Windows users consume.  And they are not always careful about what they consume or it's origin.  Linux users tend to be more concerned with what they consume, it's origin, how it fits with their Linux distro.

Again, not saying one user is smarter than another.  Just observed that Windows users are more at risk in their style of computing (and consuming).

---

