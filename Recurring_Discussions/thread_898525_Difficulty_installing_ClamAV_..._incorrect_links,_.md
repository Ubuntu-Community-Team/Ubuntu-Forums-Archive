---
title: "Difficulty installing ClamAV ... incorrect links, LINUX unsave?"
date: 2008-08-23
forum: Recurring Discussions
---

### Post by meikel14 on 2008-08-23
I am very, very new to Ubuntu. Although I am satisfied with the progress so far (Ubuntu is much better than OpenSUSE) there's a serious problem:

I cannot install ClamAV - there is no installer package nor are the links mentioned on [www.clamav.net](www.clamav.net) *"deb [http://ppa.launchpad.net/ubuntu-clamav/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ubuntu) hardy main"* and *"deb-src [http://ppa.launchpad.net/ubuntu-clamav/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ubuntu) hardy main"* correct. The beforementioned directories are empty. 

What can I do to protect my Ubuntu-System from viruses? :confused::confused:

Thanks in advance,


meikel14

---

### Post by aysiu on 2008-08-23
> **meikel14 said:**
> 
What can I do to protect my Ubuntu-System from viruses? :confused::confused: What can you do? Use strong passwords. Don't install software from untrusted sources. Don't change networking defaults unless you know what you're doing. Read up on social engineering. Don't log in as root.

For more details, read [Does Ubuntu need antivirus?](http://www.psychocats.net/ubuntucat/does-ubuntu-need-antivirus/)

By the way, even though I'm not convinced you have any need for ClamAV (are you running a server for Windows computers?), those directories are not empty. Those are lines to put in your /etc/apt/sources.list. Read more about software installation here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by meikel14 on 2008-09-06
Whether or not Ubuntu needs any AV Protection is beside the point and the question I asked. 

The article I read here and in other magazines state that Ubuntu is a fortress compared to Windows, but it's not so unlikely that somewhere now a hacker attempts to disprove the claims made by the Ubuntu / Linux Experts.  As far as I can see the main reason for the claim of Linux being hacker-save is based on the way Linux handles installation of software. This is indeed different from Windows, and in some cases even difficult. So difficult for some, in fact, that they may force a change. Also, as I already wrote in a response to the article linked to, Linux has according to Wikipedia a market share of just 2% in the overall Desktop OS Segment. These numbers alone make Linux uninteresting to the criminal hacker, who has a bigger target in Window's 90%.
 
&#8220;Safety is in numbers&#8221; - in this case in small numbers.

---

### Post by aysiu on 2008-09-06
> **meikel14 said:**
> As far as I can see the main reason for the claim of Linux being hacker-save is based on the way Linux handles installation of software.  If that's as far as you can see, you haven't read the blog post I linked to in my last post. Read it.

---

### Post by SunnyRabbiera on 2008-09-06
what you fail to understand is that clam is not meant to scan linux viruses as they practically dont exist, it scans for windows viruses.
So unless you run a server there is really no use to have a av client for your linux system.
You can stop being paranoid now :D

---

### Post by cardinals_fan on 2008-09-06
> **meikel14 said:**
> Whether or not Ubuntu needs any AV Protection is beside the point and the question I asked. 

The article I read here and in other magazines state that Ubuntu is a fortress compared to Windows, but it's not so unlikely that somewhere now a hacker attempts to disprove the claims made by the Ubuntu / Linux Experts.  As far as I can see the main reason for the claim of Linux being hacker-save is based on the way Linux handles installation of software. This is indeed different from Windows, and in some cases even difficult. So difficult for some, in fact, that they may force a change. Also, as I already wrote in a response to the article linked to, Linux has according to Wikipedia a market share of just 2% in the overall Desktop OS Segment. These numbers alone make Linux uninteresting to the criminal hacker, who has a bigger target in Window's 90%.
 
&#8220;Safety is in numbers&#8221; - in this case in small numbers.
Antivirus software is worthless security.  Think of it as putting on a bulletproof vest AFTER being shot in the chest.  If you:

a) run as a limited user (default on almost all Linux distros)
[INDENT]1) think carefully before granting a program root privileges (sudo on Ubuntu)[/INDENT]

b) only install software from trusted sources (such as the Ubuntu repos)

c) browse safely (consider NoScript)
[INDENT]1) don't visit shady sites
[/INDENT]
you'll have no virus issues on any operating system.  Antivirus is only useful on servers, and, even then, it has limited value.

---

### Post by SunnyRabbiera on 2008-09-06
> **cardinals_fan said:**
> Antivirus software is worthless security.  Think of it as putting on a bulletproof vest AFTER being shot in the chest.  If you:

a) run as a limited user (default on almost all Linux distros)
[INDENT]1) think carefully before granting a program root privileges (sudo on Ubuntu)[/INDENT]

b) only install software from trusted sources (such as the Ubuntu repos)

c) browse safely (consider NoScript)
[INDENT]1) don't visit shady sites
[/INDENT]
you'll have no virus issues on any operating system.  Antivirus is only useful on servers, and, even then, it has limited value.

yes though in windows people don't know those practices so for most windows users antivirus is more needed.

---

