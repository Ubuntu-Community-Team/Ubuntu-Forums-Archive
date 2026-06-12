---
title: "Why is Linux Safe?"
date: 2007-11-21
forum: Recurring Discussions
---

### Post by baqai on 2007-11-21
Can someone tell me for a layman's point of view why linux is safe? why we say linux is virus free?

i ended up in a debate with a programmer today who happens to be winblows advocate, i couldn't convince him properly since my knowledge on the subject is very vague.

---

### Post by mellowd on 2007-11-21
There are just a lot less viruses out there for linux. They do exist but most linux writers simply target windows. Linux out of the box generally isn't safe either. You'll still need to lock it down.

---

### Post by Darkhack on 2007-11-21
The first reason Linux is safer is because the kernel has a firewall built in, unlike Windows.  The second reason is that the operating system is programmed in such a way that programs cannot self propagate.  Meaning they can't attach themselves to others, or spread through the system.  It's hard (near impossible) to hide a process from the process table on a Linux system too, unlike Windows.  Linux also requires one to be root to do any serious damage.  The third reason is because Linux users are generally more aware of security and don't go around opening "Britney Spears and Paris Hilton Having Sex.exe" in their email.  We can also install programs from the package manager instead of needing to download stuff from sketchy websites.

---

### Post by p_quarles on 2007-11-21
> **mellowd said:**
> There are just a lot less viruses out there for linux. They do exist but most linux writers simply target windows. Linux out of the box generally isn't safe either. You'll still need to lock it down.
Sorry, but both of those assertions are incorrect.

To answer the question, Linux/UNIX implement a much more rigorous separation of privileges than Windows does. Vista, the latest version of Windows, is actually somewhat closer to the *nix model than previous versions.

What this means is that it is inherently much more difficult for someone on the internet to connect to your computer and run malware. Part of Windows bad reputation comes from the fact that Explorer (older versions) would do just about anything a cracker wanted it to. So, if you visited a bad site, you could get attacked without doing anything. That's not impossible in Linux, but the design of the OS makes it much, much more difficult. 

It's the same with viruses. They would need to be able to install themselves in an executable path, and they can't do that without your password. So, you can't just click on something disguised as a song file and find yourself loaded to the gills in viruses. 

The other argument that many people make is that open source software has more eyes looking at the code. If someone discovers a vulnerability, he or she can go look at the code and try to fix it. With Windows, the code is all hidden, so everyone depends on Microsoft's developers to fix any vulnerabilities. 

There are plenty of things you can do to make Linux insecure, but an Ubuntu installation out of the box is very safe.

---

### Post by mellowd on 2007-11-21
> **p_quarles said:**
> Sorry, but both of those assertions are incorrect.

To answer the question, Linux/UNIX implement a much more rigorous separation of privileges than Windows does. Vista, the latest version of Windows, is actually somewhat closer to the *nix model than previous versions.

What this means is that it is inherently much more difficult for someone on the internet to connect to your computer and run malware. Part of Windows bad reputation comes from the fact that Explorer (older versions) would do just about anything a cracker wanted it to. So, if you visited a bad site, you could get attacked without doing anything. That's not impossible in Linux, but the design of the OS makes it much, much more difficult. 

It's the same with viruses. They would need to be able to install themselves in an executable path, and they can't do that without your password. So, you can't just click on something disguised as a song file and find yourself loaded to the gills in viruses. 

The other argument that many people make is that open source software has more eyes looking at the code. If someone discovers a vulnerability, he or she can go look at the code and try to fix it. With Windows, the code is all hidden, so everyone depends on Microsoft's developers to fix any vulnerabilities. 

There are plenty of things you can do to make Linux insecure, but an Ubuntu installation out of the box is very safe.

No, your assumption is incorrect. While your reasons are good they don't show the whole picture. There are plenty of viruses out there for linux, just not nearly as many as there is for Windows. For example: [http://search.mcafee.com/search?q=linux&site=us_site.Virus&num=10&sort=date:D:L:d1&output=xml_no_dtd&proxystylesheet=default_frontend&client=default_frontend&getFields=description&ie=UTF-8&oe=UTF-8&filter=0&](http://search.mcafee.com/search?q=linux&site=us_site.Virus&num=10&sort=date:D:L:d1&output=xml_no_dtd&proxystylesheet=default_frontend&client=default_frontend&getFields=description&ie=UTF-8&oe=UTF-8&filter=0&)


Also, linux is not secure out of the box. The last thing we do at work is install a fresh linux distro on a server and simply put it online. No, it gets locked down first. While it's safer than windows, anyone who really knew what they were doing could do a few things to a freshly exposed linux box

---

### Post by Martin Witte on 2007-11-21
in my opinion two factors make linux (or any unix based os, like bsd, os x) more safe than windows vesions before vista: unix has a more strict separation in rights given to a user versus rights given to a superuser, and popularity of the platform, up to now most computers on this planet run a microsoft windows version. next to this microsoft introduced a lot of trouble with active x

---

### Post by toupeiro on 2007-11-21
Linux is generally a safer os by design.  Users are not admins, and admins are not root.  The OS is very modular, and its most important components are extremely lean run independantly of other software, whereas microsoft has a huge set of interdependant services and software just to run, which opens the os up to a tremendous amount of insecurities.  A lot of the things which cause windows to be so vulnerable is unrefined code and a poor elevated rights system.  In Linux, you had to modify a lot of defaults to create even close to the amount of insecurities windows has in its most patched state.

---

### Post by ComplexNumber on 2007-11-21
to echo some other points of view in this thread. the unix family of operating systems were designed from the bottom up to be secure, multiuser, and networked. windows was originally designed to be single user, non-networked, and security wasn't given a thought. no matter how much windows has changed since the early years, security and networking etc are only ever going to be bolt-ons. security etc wasn't necessary in those days for the market that windows was targeted at, whereas it was  important for unix.
therefore, it is unlikely that windows will ever be as naturally secure as *nix, even if they have the same market share and the same number of viruses written for them.

---

### Post by p_quarles on 2007-11-21
> **mellowd said:**
> No, your assumption is incorrect. While your reasons are good they don't show the whole picture. There are plenty of viruses out there for linux, just not nearly as many as there is for Windows. For example: [http://search.mcafee.com/search?q=linux&site=us_site.Virus&num=10&sort=date:D:L:d1&output=xml_no_dtd&proxystylesheet=default_frontend&client=default_frontend&getFields=description&ie=UTF-8&oe=UTF-8&filter=0&](http://search.mcafee.com/search?q=linux&site=us_site.Virus&num=10&sort=date:D:L:d1&output=xml_no_dtd&proxystylesheet=default_frontend&client=default_frontend&getFields=description&ie=UTF-8&oe=UTF-8&filter=0&)


Also, linux is not secure out of the box. The last thing we do at work is install a fresh linux distro on a server and simply put it online. No, it gets locked down first. While it's safer than windows, anyone who really knew what they were doing could do a few things to a freshly exposed linux box
Last I checked there were five proof-of-concept Linux viruses, and none in the wild. There are plenty of other potentials for exploiting a Linux box, but they are simply not self-propegating viruses. If you read the list you linked to, you'll see that they are mostly trojans (which involves social engineering) and daemon exploits (which involves running a service and making it public). 

And, yes, a server absolutely needs to be locked down before it goes onto the WAN. A fresh Ubuntu desktop installation shouldn't require any additional security measures, and if it does it would be considered a bug by the developers.

---

### Post by mellowd on 2007-11-21
> **p_quarles said:**
> If you read the list you linked to, you'll see that they are mostly trojans (which involves social engineering) and daemon exploits (which involves running a service and making it public). 

And, yes, a server absolutely needs to be locked down before it goes onto the WAN. A fresh Ubuntu desktop installation shouldn't require any additional security measures, and if it does it would be considered a bug by the developers.


Which is what my point was exactly. Yes nix systems generally are a lot safer that windows, but not impossible to either get viruses or crack.

---

### Post by kodak on 2007-11-21
> **baqai said:**
> Can someone tell me for a layman's point of view why linux is safe? why we say linux is virus free?

i ended up in a debate with a programmer today who happens to be winblows advocate, i couldn't convince him properly since my knowledge on the subject is very vague.

Welcome to the forums baqai, the topic has been asked many times before as you can imagine,

[http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)

[www.google.com](www.google.com)

---

### Post by corney91 on 2007-11-21
Another reason I would imagine makes Linux safer is that because it is open-source, and so the code can differ widely and therefore some form of malware could affect one computer and not another. This makes the target set of computers an even smaller percentage.
I'm only guessing this so if it's wrong, disregard this and possibly correct me.

---

### Post by smartboyathome on 2007-11-21
> **mellowd said:**
> No, your assumption is incorrect. While your reasons are good they don't show the whole picture. There are plenty of viruses out there for linux, just not nearly as many as there is for Windows. For example: [http://search.mcafee.com/search?q=linux&site=us_site.Virus&num=10&sort=date:D:L:d1&output=xml_no_dtd&proxystylesheet=default_frontend&client=default_frontend&getFields=description&ie=UTF-8&oe=UTF-8&filter=0&](http://search.mcafee.com/search?q=linux&site=us_site.Virus&num=10&sort=date:D:L:d1&output=xml_no_dtd&proxystylesheet=default_frontend&client=default_frontend&getFields=description&ie=UTF-8&oe=UTF-8&filter=0&)


Also, linux is not secure out of the box. The last thing we do at work is install a fresh linux distro on a server and simply put it online. No, it gets locked down first. While it's safer than windows, anyone who really knew what they were doing could do a few things to a freshly exposed linux box

If you check [this list of viruses and worms for linux from Wikipedia]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms"), you should notice there are only 23, and none of them active. While Wikipedia isn't the best source for this info, it is a lot better than Mcafee, as it is maintained by the community, and thus is an independant third party. So, in conclusion, don't use something that tries to make money off of what you are trying to prove as a notable source.

Also, about the topic, to me Linux is secure because 1) Scripts have to be set as executable to run (the only way around this is through a tar package, but even then you have to have a script to untar the tar package), 2) you have to be root to harm anything other than your home folder, and 3) Linux doesn't have as much market share and generally is thought of as hackers and geeks (who can blame them for thinking people who run linux are back in the MS-DOS days, they don't know!). With the increase in people moving to linux, there will be an increase in the number of trojans on linux (and by definition, trojans require a gullible user to execute them/install them/whatever).

---

### Post by mellowd on 2007-11-21
> **smartboyathome said:**
>  So, in conclusion, don't use something that tries to make money off of what you are trying to prove as a notable source.


You don't have to buy anything. It merely points to the fact that it's not impossible to get a virus on linux

---

### Post by p_quarles on 2007-11-21
Just a quote from Smartboyathome's link, because I think it states the current situation very nicely:
> Like other Unix systems, Linux implements a [multi-user]("http://en.wikipedia.org/wiki/Multi-user") environment where users are granted specific [privileges]("http://en.wikipedia.org/wiki/Privileges") and there is some form of access control implemented. As such, viruses typically have less of an ability to change and impact the host system. That is why none of the viruses written for Linux, including the ones below, have ever propagated successfully to a large number of machines. Also, the security holes that are exploited by the viruses have been fixed shortly after (or more often, before) the viruses started spreading. So the viruses listed no longer pose any concern as long as the Linux system is updated regularly.

---

### Post by happysmileman on 2007-11-21
> **mellowd said:**
> You don't have to buy anything. It merely points to the fact that it's not impossible to get a virus on linux

They want to convince all users that they're unsafe, which is why the list might be over-exxagerated.

I'm not of course saying that the list isn't correct, but I bet a lot of those are just trojans requiring social engineering to install, which couldn't be considered a risk, is there a way to filter out trojans and viruses that are very outdated or require specific installed software or conditions to work?

If you filtered all those out and then compared it to Windows Virus (same filters applying of course) Windows would have so much more it's unbelievable.

And as for the "Windows only has more viruses because it's targeted more", a lot of servers run on Linux, and a lot of programmers know Linux (much moreso than non-programmers, in fact I think I saw recently that over 60% of programs are comfortable using Linux) so you'd think with all those programmers there'd be more effort.

---

### Post by thx11381974 on 2007-11-21
Safe is a relative term Linux is safer. I hate to be  conspiracy theory guy here, But I think M$ has decided to intensionally leave their OS vulnerable, At some point glaring security holes have to looked at as intensional security holes. Anyway whether it's calculated or incompetent only M$ gets to see their source code so only they can diagnose and solve security breaches, that's if they want to solve them of course. Linux on the other hand being open source allows anyone to solve problems as they come up, no one has to beg the Linux Foundation for a fix they can make it them selves and then share what they've done with every one else. This kind of speed and flexibility is imposable with closed source

---

### Post by RJ Fighter on 2007-11-23
> **smartboyathome said:**
> With the increase in people moving to linux, there will be an increase in the number of trojans on linux (and by definition, trojans require a gullible user to execute them/install them/whatever).

I guess we should try to keep the normal computer user-base from using Linux then.  :lol:

---

### Post by LaRoza on 2007-11-23
Social Engineering is the only real way to get access to a *nix system. This is a generalization of course.

---

### Post by mellowd on 2007-11-23
> **LaRoza said:**
> Social Engineering is the only real way to get access to a *nix system. This is a generalization of course.

no it isnt

---

### Post by pjkoczan on 2007-11-23
Also, a fresh Linux install has most services off and most (if not all) ports closed. And, if you want to install a service or a program, there are usually very restrictive defaults that you'd have to make yourself. So, users tend to be clueful about opening things up, and very little can be done by default.

---

### Post by kopinux on 2007-11-23
ask the NSA, they said something like separate OS and content operations, its in their website.

---

### Post by p_quarles on 2007-11-23
> **kopinux said:**
> ask the NSA, they said something like separate OS and content operations, its in their website.
The NSA uses SELinux (security enhanced Linux). So, unless you're running CentOS or something else that ships with that enhancement, privilege separations aren't going to be nearly as strict.

---

### Post by Xbehave on 2007-11-28
i think it was explained very well by a teacher of "intoruction to unix" at my uni

UNIX from the start was written as a networked multi-user system
but windows was designed as a stand alone single-user system

which basically means that while linux has been designed with security in mind
windows have gone "oh ****" and had to add it on later
*bsd was designed to be secure

while windows have improved their design (long release cycles), they are limited by backwards compatibility and users not liking change ( many of vistas improvements are unwelcome ). for windows to become truely secure theyd need a full redesign, maybe theyd call it "windows OS X" 

Unfortunately due to many arguments the huge improvements offered by SSP, SElinux are not standard.But I still don't think windows's defences is as good as apparmor.

Its also  important to bear in mind that by using open source software, linux systems also get faster "critical bug" fixes, people looking to fix exploits not just find them (theres no reson to try and fix an IE7 expoit because your not allowed).

---

