---
title: "Virus Free"
date: 2011-10-11
forum: Recurring Discussions
---

### Post by Tinker Tantrum on 2011-10-11
Sorry if this is in the wrong section. I was wondering why Ubuntu is not prone to virus' (like other OS' that shall remain nameless)?

---

### Post by ColeTurner on 2011-10-11
There are two reasons that I know of.

One reason is that there are many fewer viruses for Linux operating systems than for the "un-named" operating system.

The other reason is that all software that you install on Ubuntu comes from repositories. These repositories are databases which contains software that is pre-screened for malware. In order for a piece of software to be added to a repository, it is first checked for viruses and other nasty stuff. If it contains nasty stuff, it is not included. If it does not contain nasty stuff, it is included.

---

### Post by Tony Flury on 2011-10-11
The other main reason is the security Model. Ubuntu (and other liunux distros) require you to positively confirm (by entering your password) that you wish an application to modify your system critical files or directories. This is another line of defence against the social engineered type trojan that comes up : The video being offered might be enticing, but if, when you click it, it prompts you for your passowrd - that is a massive warning sign to all but the most stupid of users.

In contrast the most common "unnamed" OS, the vast majority of users log in with admin rights enabled - yes that makes installing s/w a bit easier for everyone - but it also makes it a lot easier for s/w to be silently installed by anything.

Open Source is a key factor too - even if you use s/w not from a repository, you (and 1000s of other can (and do) inspect the source code - and even rebuild from source. That level of scrutiny makes a malware installation unlikely.

---

### Post by Tony Flury on 2011-10-11
> **ColeTurner said:**
> There are two reasons that I know of.

One reason is that there are many fewer viruses for Linux operating systems than for the "un-named" operating system.

The other reason is that all software that you install on Ubuntu comes from repositories.

Not true - most people i think install most of it from respositories, but there are times when you can and need to install s/w from trusted sources where they are not in the repositories.

---

### Post by ColeTurner on 2011-10-11
> **Tony Flury said:**
> Not true - most people i think install most of it from respositories, but there are times when you can and need to install s/w from trusted sources where they are not in the repositories.

Okay then, most software comes from repositories. :D But, either way, the software which is available for Linux is highly scrutinized before people download and install it.

---

### Post by haqking on 2011-10-11
Linux does not suffer from Viruses like other OS, there are no known viruses in the wild currently, the main reason using AV on linux is to scan incase you share files with windows users.

The reason it is not prone is because there are none out there to infect it, it doesnt get infected from the current ones as they are designed for Windows.

Malware writers have not as yet targeted Linux as they have other OS, they could do so, it is not to say that Linux is inpenetrable from Malware as it is not, however currently there are no known viruses which could effect it, conversely even though viruses have been known about for a very long time certain OS are still susceptible from viruses written 10 years ago.

**No system is 100% secure when on a network or sharing data, security is best in a layered approach and with ongoing vigilence and awareness, the main security flaw in any system is PEBKAP = Problem Exists Between Keyboard And Person**

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

[B]See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)[/B]

---

### Post by Paqman on 2011-10-11
> **ColeTurner said:**
> 
The other reason is that all software that you install on Ubuntu comes from repositories. These repositories are databases which contains software that is pre-screened for malware. In order for a piece of software to be added to a repository, it is first checked for viruses and other nasty stuff. If it contains nasty stuff, it is not included. If it does not contain nasty stuff, it is included.

You're right, the repos are important. Getting all our software from centralised repos and having a package manager on the system means that when a vulnerability is found in a piece of software the version in the repos can be patched, and the updated version get pushed out to all users very quickly. Windows and Mac can't do this nearly as well as the Linux distros can, and it's one of the main reasons we have a better security track record.

---

### Post by ColeTurner on 2012-03-09
This brings a question to mind.
Mac is a *nix based system. So, why doesn't it have package management?

---

### Post by haqking on 2012-03-09
> **ColeTurner said:**
> This brings a question to mind.
Mac is a *nix based system. So, why doesn't it have package management?

[Fink]("http://www.finkproject.org/")
[Homebrew]("https://github.com/mxcl/homebrew")
[macports]("http://www.macports.org/")
[URL="http://www.darwinports.info/"]Darwinports
[/URL]
Cheers

---

### Post by aysiu on 2012-03-09
> **ColeTurner said:**
> This brings a question to mind.
Mac is a *nix based system. So, why doesn't it have package management?
The package management isn't necessarily tied to being a *nix system.

But, yes, Mac OS X now does have a native package manager:
[http://www.apple.com/mac/app-store/](http://www.apple.com/mac/app-store/)

---

### Post by ColeTurner on 2012-03-09
> **haqking said:**
> [Fink]("http://www.finkproject.org/")
[Homebrew]("https://github.com/mxcl/homebrew")
[macports]("http://www.macports.org/")
[URL="http://www.darwinports.info/"]Darwinports
[/URL]
Cheers

> **aysiu said:**
> The package management isn't necessarily tied to being a *nix system.

But, yes, Mac OS X now does have a native package manager:
[http://www.apple.com/mac/app-store/](http://www.apple.com/mac/app-store/)

Hm, Good for them!

---

### Post by 3rdalbum on 2012-03-10
> **ColeTurner said:**
> This brings a question to mind.
Mac is a *nix based system. So, why doesn't it have package management?

Because, as a *nix system, it is seriously deficient ;-)

---

### Post by tuxmarc on 2012-04-13
Hi !
I had launched a similar topic ont he French forum : who has ever got or seen a virus with Linux ?
The final answer was : nobody :p
I have learnt that Linuxes are likely to be infected by rootkits and since that time, I have installed "rkhunter" which did not find anything.
Marc

---

