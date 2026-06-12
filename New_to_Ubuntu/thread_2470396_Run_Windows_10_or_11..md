---
title: "Run Windows 10 or 11."
date: 2021-12-28
forum: New to Ubuntu
---

### Post by graftedin on 2021-12-28
I have a dream where I stop sending money to Microsoft for stuff that doesn't work.  However I'm a web developer and most of my clients have windows and so I need to still be able to support them on windows machines.

I'm installing a new hard drive on an older laptop that has more resources than my current one.  I was thinking of starting with a linux installation and then installing a windows virtual machine.  But maybe its better to just use wine.  My biggest concern is I don't have time to really learn how to do this right.  I see $150 per year for support.  If that support could help me get this done right I'd be more than happy to pay.  I'd rather pay the linux experts and keep working on what I'm good at.....websites.

I need to run.
- Office 2013.  I don't need Outlook to be my primary email client as long as I can get in to outlook to help clients with settings.  But I need an email client that has tasks and calendars and all the other normal stuff I'd expect in Outlook.  I don't mind using openoffice or an other "office" for the other standard office applications as long as I can get access to Microsoft Office to help my clients.
- Photoshop CS3
- Edge
- Quickbooks - If there really was a good linux based app that was similar I'd pay for it.  I also don't want to send quickbooks any more money.

I think what I need is someone to take my hand and tell me it'll be ok and my $150 per year will keep me from wasting hours on stuff I can't figure out quickly.

Thanks

---

### Post by kurt18947 on 2021-12-28
I'm not going anywhere near Windows 11 for perhaps 2 years. Even then I may not if a couple Windows apps continue to work with Windows 10. You could take a look at Gnucash in lieu of Quickbooks. I'm certain Gnucash doesn't match Quickbooks function for function but it may do what you need to do. My experience with opening and saving MSOffice documents in LibreOffice is pretty good. I think it helps to install the MSOffice fonts in Ubuntu/Linux. I don't open or save heavily formatted documents or anything with macros. There is an old version of Photoshop - CS2? - available for free from Adobe, or at least there used to be. Browsers wouldn't be an issue I wouldn't think. There are lots of chromium based browsers that work with Ubuntu, I have Vivaldi install as secondary to Firefox.

---

### Post by tea for one on 2021-12-28
> **graftedin said:**
> I'm installing a new hard drive on an older laptop that has more resources than my current one. 

As you have two laptops, why not install Windows 10 or 11 on one and Ubuntu on the other?

All the intricacies of dual booting will be avoided and you can spend your time productively with web development.

---

### Post by Tadaen_Sylvermane on 2021-12-28
As much as it kills me to say it you need to run Windows in some way. Your required apps haven't really got a fully functional open source equivalent. The open source stuff can do most of it but not all. Gimp isn't quite enough to compete with Photoshop. Office the same. Edge... Windows only browser. Quickbooks. Gnucash can do most but again not all. To check if any of them would work on wine you should look at the wine website itself. It has user submitted ratings for apps and such that people have successfully, or not so successfully run with Wine. If they can't run with wine then the open source is possible I suppose but your workflow would change quite a bit just having to learn new tools.

There are cloud based options for this stuff except the browser. But they aren't as full featured as their locally run counterparts.

---

### Post by grahammechanical on 2021-12-28
> don't mind using openoffice

Open Office was discontinued in 2011. Libreoffice is a community fork of Open Office that has progress far beyond Open Office. They say "time is money." If you cannot afford the time to learn new applications, then stay with what you know. 

> I see $150 per year for support.  If that support could help me get this done right I'd be more than happy to pay.

What support is this? Ubuntu is sponsored by a commercial organization called Canonical. They offer paid for support of various kinds. I cannot say if that is the support you need.

Ubuntu comes with a email client called Thunderbird. Read about it.

[https://www.thunderbird.net/en-GB/](https://www.thunderbird.net/en-GB/)

[https://www.lifewire.com/access-outlook-in-thunderbird-3572532](https://www.lifewire.com/access-outlook-in-thunderbird-3572532)

Regards

---

### Post by TheFu on 2021-12-28
> **grahammechanical said:**
> What support is this? Ubuntu is sponsored by a commercial organization called Canonical. They offer paid for support of various kinds. I cannot say if that is the support you need.

Canonical's support is for the OS and patches only. They won't hold your hand to teach any specific program.
To learn about any specific program, there are a few choices.
* Youtube videos
* Paid training webclasses - this assumes they have a class on the exact program you want, which is unlikely.
* Private tutor - I'd guess this would be $30+/hr, but it would depend on the exact program.

If you won't/don't want to learn to do it yourself, you can pay someone else to setup an environment using gig-work websites like fivr. Of course, the ability for these remote people to do work for you would be 100% dependent on providing remote access.

I'm really good at virtualization for all levels - personal to enterprise - but setting up 1 system wouldn't be sufficient effort/profit get get my attention and I wouldn't want to be contacted for "support" without a full-on monthly support contract of perhaps $150/system with a 50 system minimum. I'm just ballparking that. The exact software, storage, OS, and total number of VMs, containers, etc. would all go into the proposal.

I know next to nothing about Win10 or 11, so perhaps a Windows expert would need to be engaged?

---

### Post by graftedin on 2021-12-29
I don't have enough desk space for 2 computers....it would just be a hassle.  And the current computer is snail slow and needs to just be started over with a fresh install.

---

### Post by graftedin on 2021-12-29
Ok....it was a nice dream.  Thanks for the insight.

---

### Post by TheFu on 2021-12-29
> **graftedin said:**
> I don't have enough desk space for 2 computers....it would just be a hassle.  And the current computer is snail slow and needs to just be started over with a fresh install.

A Linux computer only needs 8G of storage. Much less if you are careful.  Of course, much more if you want a GUI with a full, bloated, DE like Gnome.  I have a few linux servers that use under 1GB of storage and these weren't just installed. They've been running and doing their jobs for months.  Windows wants 100G, not Linux.  My main desktop system is using 40G total, including swap.

Computers don't need to be in the same room to be extremely useful.  I'm typing on a laptop in my breakfast nook now, but the window I'm typing into is running on a computer upstairs, inside a virtual machine. With networking, especially LAN networking, any computer on the LAN is accessible from almost any other computer on the same LAN with or without a GUI.

Doing a fresh install shouldn't have any impact on performance.  It won't with Linux, unless you swap the hardware that is the root cause for the system being slow.  We had a discussion in these forums a few months ago about reloading OSes to make things faster.  The general consensus was that might be a Windows thing, but some of use have been running the same Windows install for over a decade and haven't noticed any slowdown.  For people that install the programs they use and simply patch, there is little to be gained by reloading an OS just for that purpose.
However, I do feel that doing backups of computer storage DOES exercise the storage in a way that lets it notice areas that will fail far in advance of any failure, so the storage HW can either refresh the location or relocate that data to other storage blocks.  This is preventative.  Systems that don't get backed up routinely don't get this exercise, so when it is finally time to provide the data from those long forgotten blocked, they might have faded too much for any silent fix to be possible.  Doing backups is preventative on many levels, I'm convinced.

Of course, for people that constantly add and remove programs, regardless of the OS, it is very likely that cruft will be left behind and storage allocations will be highly fragmented.  I know that Windows has a monthly de-fragmentation task that runs automatically.  On Unix file systems, the rule of thumb is to leave 1% of the storage on each file system free to prevent fragmentation.  With SSDs, I try to leave 20% un-allocated to massively increase the SSD write storage lifespan.  On some systems, the SSD is less than 50% used ... like on my laptop.

BTW, you don't need a different computer to run different OSes. That's why we have virtual machines.  If you'd like to learn more and youtube or reading isn't working, join a LUG - Linux Users Group - in your area or over the internet. Attend some meetings and ask questions.  My LUG meets weekly and we have members from multiple different states.  Locally, we have meetings in 4 different parts of the metro area, for people fully vaccinated.  Almost every week, someone will setup a virtual machine at a cloud provider and do an install of some Linux flavor. Then we'll each get ssh logins to the system and be able to look around to see what's new and different.  In October, we did a few Ubuntu flavors of 21.10. More recently, we've done Mint, MXLinux, Pop! OS and some I don't recall.  Each was running inside a VM, but only for a few hours. I think it costs about $0.05. One of our members is all about using cloudy VPS for his OSes.  OTOH, I run everything on my LAN, on my hardware and avoid using other people's computers and storage.

---

### Post by T6&amp;sfpER35% on 2021-12-29
from your post #1 ... all i can recommend is to to stick to windows .

---

### Post by kurt18947 on 2021-12-31
I have 3 or 4 systems dual boot - Windows 10 and some linux flavor. I've never had a problem that couldn't be fixed with a boot-repair USB. The big not-so-secret is to install Windows first. Then use Windows tools to resize the Windows partitions to make room for the linux installs. The only thing I've had to do with GRUB is to change the default boot install. A VM is handy for a few reasons, one of which is to switch between Linux and Windows with a click of the mouse.

---

