---
title: "ubuntu-minimal mini.iso packages"
date: 2018-09-18
forum: New to Ubuntu
---

### Post by santerikannisto on 2018-09-18
Hello,

I was checking mini.iso to use it as a base for making a new desktop GNU/Linux distro. There were the following packages I am considering leaving out:
- rsyslog reliable system and kernel logging daemon
- sensible-utils Utilities for sensible alternative selection
- ubuntu-advantage-tools management tools for Ubuntu Advantage

The rest made sense and I was happy to see [lsb-release]("https://packages.ubuntu.com/cosmic/lsb-release") among the packages.

My reasons:
1) They are security risks. I am planning to secure the system by other means than forcing users to accept updates
2) A typical desktop user who I am targetting with my distro does not have any clue of what those packages are doing nor the data they generate.

My question is, why they have been added to minimal core and all Ubuntu distros in the beginning?

Also any thoughts of possible side effects and troubles I will run into later would be greatly appreciated.

Cheers,

Santeri

---

### Post by mastablasta on 2018-09-19
> **santerikannisto said:**
> 
- rsyslog reliable system and kernel logging daemon

Don't know about others, but this one provides the logs i believe. home users or anyone actually needs them (or similar device) as soon as they encounter problems.

>  
My reasons:
1) They are security risks. I am planning to secure the system by other means than forcing users to accept updates


how did you come to this? i haven't read any hack being made through them.
 
also i would like to see how you can make a secure system without patches that close the security holes.

1. connecting to internet is automatically a security risk.
2. the biggest security issue is usually between chair and keyboard.

---

### Post by santerikannisto on 2018-09-19
Thanks for sharing your thoughts.

> **mastablasta said:**
> Don't know about others, but this one provides the logs i believe. home users or anyone actually needs them (or similar device) as soon as they encounter problems.

An average desktop user has no clue about any logs, how to use them or what they tell. Logs are slowing down the system and offering information about users actions violating their privacy. If a user knows what is a log, he is surely able to enable and configure [COLOR=#000000]*rsyslog*[/COLOR] by himself, isn't he?

> **mastablasta said:**
> how did you come to this? i haven't read any hack being made through them.

There has been vulnerabilities and they use network access. That makes those components a higher risk for hacking than not installing the updates they provide.

> **mastablasta said:**
> also i would like to see how you can make a secure system without patches that close the security holes.

It is better to design the system so that it blocks inbound network access, remove risky components and disable risky OS features by default because updates are always a security risk and may break the system functionality.

---

### Post by mastablasta on 2018-09-19
> **santerikannisto said:**
> Thanks for sharing your thoughts.
An average desktop user has no clue about any logs, how to use them or what they tell. Logs are slowing down the system and offering information about users actions violating their privacy. If a user knows what is a log, he is surely able to enable and configure [COLOR=#000000]*rsyslog*[/COLOR] by himself, isn't he?


i am not sure who the OS would be aimed at. but stroll the forums a bit and you get messages  like my desktop crashes, my computer freezes, my computer boots to blinking cursor after update/upgrade, my sound doesnt' work, my GPU drivers are not working. many of these issue can be solved just by looking at the logs and see if everything loads properly. and upon freezes you can see exactly what component of the OS froze.
[/QUOTE]

> 
It is better to design the system so that it blocks inbound network access, remove risky components and disable risky OS features by default because updates are always a security risk and may break the system functionality.

by default all inbound network access is blocked in Ubuntu. so i am not sure what kind of special or different design you have in mind here.
 
The security patches on stable version as well as the intermediate releases close the security holes. and are not considered a risk. after all they are tested before being released. in any case this advice is just wrong. risky component is a browser. so you would create desktop OS with no browser or with unpatched browser?!

there is no 100% security. but we can all do our best to secure the OS and give as many hurdles as possible for hackers to overcome (layered security) . but as i know every device, every OS so far has been hacked. patched on not. security patches just remove the easier access.

OS should be tailored to it's user base. if user base is home user, you are off to a bad start (IMO). if the OS is aimed at experts then i guess they will know what to do if they need to add something.

removing services you really do not need does indeed improve security.

---

### Post by santerikannisto on 2018-09-19
Thanks again for sharing you thoughts!

> **mastablasta said:**
> i am not sure who the OS would be aimed at. but stroll the forums a bit and you get messages  like my desktop crashes, my computer freezes, my computer boots to blinking cursor after update/upgrade, my sound doesnt' work, my GPU drivers are not working. many of these issue can be solved just by looking at the logs and see if everything loads properly. and upon freezes you can see exactly what component of the OS froze.


True for experienced users. I am not aiming for those, but ordinary people who use computers for word processing and surfing internet, not playing with operating systems.

> **mastablasta said:**
> 
by default all inbound network access is blocked in Ubuntu. so i am not sure what kind of special or different design you have in mind here.
 

Good to know. I was reading docs and saw there that by default the firewall was disabled, but maybe it was just the configuration interface, not iptables. Have to check that again.

> **mastablasta said:**
> 
The security patches on stable version as well as the intermediate releases close the security holes. and are not considered a risk. after all they are tested before being released. in any case this advice is just wrong. risky component is a browser. so you would create desktop OS with no browser or with unpatched browser?!


I have seen too many hacked and messed up computers thanks to automatic updates, virus scanners scamming users to download crapware and firewalls installing unwanted add-ons. The worst things happen in Africa where connection speeds are low and people pay for every byte. Having an automatic update on there is incredibly expensive and makes the already bad connection speed even worse. You know, just opening my gmail in the country side of Uganda took me 4 hours and over 100MB data transfer quota which costs over 1 USD/GB. To put things in perspective, with that one dollar you can buy vegetables, avocados and fruit for a week.

> **mastablasta said:**
> 
OS should be tailored to it's user base. if user base is home user, you are off to a bad start (IMO). if the OS is aimed at experts then i guess they will know what to do if they need to add something.


You can't protect users from themselves, but at least you can offer them a system that does not get automatically messed up behind their backs. And still, if they know what they are doing and want, they can always switch back automatic updates etc.

---

### Post by mastablasta on 2018-09-20
> **santerikannisto said:**
> 
Good to know. I was reading docs and saw there that by default the firewall was disabled, but maybe it was just the configuration interface, not iptables. Have to check that again.

That is correct. only the configuration interface (the UFW) is off. 

i do not believe system logs connect online. maybe the error/bug reporter?!

> 
I have seen too many hacked and messed up computers thanks to automatic updates, virus scanners scamming users to download crapware and firewalls installing unwanted add-ons. The worst things happen in Africa where connection speeds are low and people pay for every byte. Having an automatic update on there is incredibly expensive and makes the already bad connection speed even worse. You know, just opening my gmail in the country side of Uganda took me 4 hours and over 100MB data transfer quota which costs over 1 USD/GB. To put things in perspective, with that one dollar you can buy vegetables, avocados and fruit for a week.


You can't protect users from themselves, but at least you can offer them a system that does not get automatically messed up behind their backs. And still, if they know what they are doing and want, they can always switch back automatic updates etc.

this is some important background. by default there are no automatic updates. for that you would need unattended upgrades. yes, updates can eat up any quotas fast. particularly kernel patches. kernel patches are relatively big downloads (200-300MB) if you are on mobile only. 

automatic upgrades (the unnatended updates) have to be enabled in order to work. there are are various options you could explore there. 

in Ubuntu i never heard of users being hacked due to security update, there are no virus scanners for linux and there is no "crapware" or commercial firewalls with adds that we see in windows. so there is not much worries in this direction.  but the problem is that hackers do not need to upload 100MB to your pc to hack you. rootkits are only a few bites long. and without at least security patches you have nothing to protect when you browse the internet. there is no linux virus scanner because there are no known linux viruses in the wild. however there are hack made though unpached software. 

the issue here is actually poor internet infrastructure in Uganda. but i know this is too much for one person to take on.

again the user base is important and what they will do on PC. if it's banking, then they will get hacked with unpatched stuff. i have a small familly server. server is a bit different than desktop in that it has a port open. on a normal day i get about 8-10 hacking attempts. during national holidays in China or Russia, there are 30-50 attempts. mostly these are bots, but they are quite persistently trying to break in.

on a hosted server i didn't patch a small app i used. i received the update email on Wednesday but i though i will apply the patch during weekend on Saturday, when i have a bit more time. i got hacked on Friday and the website server started sending out spam. backup resolved the issue. later on i found that as the patch went out a security blog detailed the vulnerability. the hackers started abusing it the very next day. 

just something to think about....

---

### Post by santerikannisto on 2018-09-20
> **mastablasta said:**
> 
i do not believe system logs connect online. maybe the error/bug reporter?!

Logs are for my target users useless. And those who know about them can switch them on if they want. I don't like the idea of leaving around the file system any kind of information that might be used against the user, and take disk space and CPU time without good reason. Perhaps I will only disable logging from the package and leave it in the system if there is no risk for network vulnerabilities.

> **mastablasta said:**
> 

automatic upgrades (the unnatended updates) have to be enabled in order to work. there are are various options you could explore there. 



Good to know, thanks. In this case I just need to make sure that the updater does not try to access Internet and/or download anything without user enabling it.

> **mastablasta said:**
> 

in Ubuntu i never heard of users being hacked due to security update, there are no virus scanners for linux and there is no "crapware" or commercial firewalls with adds that we see in windows. so there is not much worries in this direction. 



If I was hacking a system, the automatic updates of the system or virus scanner would be my first target.

> **mastablasta said:**
> 

on a hosted server i didn't patch a small app i used. i received the update email on Wednesday but i though i will apply the patch during weekend on Saturday, when i have a bit more time. i got hacked on Friday and the website server started sending out spam. backup resolved the issue. later on i found that as the patch went out a security blog detailed the vulnerability. the hackers started abusing it the very next day. 

just something to think about....

I am aware of the issues with server updates and agree with you that they are time sensitive and very important, but for an extremely limited, small and light desktop system I would auto-update only the browser and nothing else.

---

### Post by mastablasta on 2018-09-21
> **santerikannisto said:**
> extremely limited, small and light desktop system I would auto-update only the browser and nothing else.

have you looked at super light distroz such as slitaz? or even one of the kiosk distros? or a few of the existing light distros reviewed on distrowatch?

why start from scratch to get something that might already exist?

---

### Post by santerikannisto on 2018-09-21
> **mastablasta said:**
> have you looked at super light distroz such as slitaz? or even one of the kiosk distros? or a few of the existing light distros reviewed on distrowatch?

why start from scratch to get something that might already exist?

Nope. I haven't been working with GNU/Linux for 15 years so all this is very new to me. Thanks for the tip. I will take a look at it.

There is one thing I did not yet tell you. The distro has to look, feel and work like Windows 7 as it is for my wife and she does not want to learn anything new or change the ways she is used to using computers.

Fortunately she has already been using LBA Office/Open Office/Libre Office for a very long time so that should help with migration. Windows 7 is not be working anymore well enough on her new computer (USB 3 issues, [COLOR=#000000][FONT=&amp]UEFI[/FONT][/COLOR], lack of hardware support, continuous update attacks from Micro$oft, crappy firewalls and virus scanners messing up the system and trying to scam users) and I need a long term solution for her future computing needs. I am going to update that distro only when it is no longer working with the latest hardware.

---

### Post by mastablasta on 2018-09-24
> **santerikannisto said:**
> Nope. I haven't been working with GNU/Linux for 15 years so all this is very new to me. Thanks for the tip. I will take a look at it.

There is one thing I did not yet tell you. The distro has to look, feel and work like Windows 7 as it is for my wife and she does not want to learn anything new or change the ways she is used to using computers.


Cinnamon, KDE, Xubuntu and Lubuntu are all configurable and kind of look like windows. i installed KDE to my wifes PC after messing arround with gnome at the start. i setup the classic menu, so it looked and felt like windowsxp she was used to at the time. she had no issues in transition. we then repeated this with my father promising to get him (at the time the latest) windows 7 if he wont' be able to get used to it. he has no issues. Libre office was just like the old word2003 he used before. he was used to firefox and he even learned to use some new programs (digikam). to me KDE is the most widnows like in a way that you can achieve most htings through menues, applications, settings, icons (the GUI in short).

XFCE is much lighter and very configurable as well. can fast be made to look just like windows. 

but looks work only if the user doesn't need to abandon GUI to do what they want to do.

> 
Fortunately she has already been using LBA Office/Open Office/Libre Office for a very long time so that should help with migration. Windows 7 is not be working anymore well enough on her new computer (USB 3 issues, [COLOR=#000000][FONT=&amp]UEFI[/FONT][/COLOR], lack of hardware support, continuous update attacks from Micro$oft, crappy firewalls and virus scanners messing up the system and trying to scam users) and I need a long term solution for her future computing needs. I am going to update that distro only when it is no longer working with the latest hardware.

most of the issues are likely from not updating the OS regulary, antivirus+firewall. Comodo firewall joined with free avira, avast or MS windows defender do the job just fine at catching up the hackers. but everything is pointless without the regular browser, OS and security software updates. even the British NHS fell to this issue - they had security in place, but they didn't update the OS. i see the same problem with my family in SE Asia. they use mobile internet to connect. updates are therefore expensive, so they do not do them or they even use a hacked OS or unregistered OS. resulting in various issues you describe. as well as bugs or quirks and annoyances that were fixed by OS updates long ago are still present at their PCs. my advice to them was to at least go once a month to a "free-wifi" place (or maybe do it at work?!) and do an update. not perfect but better than no updates at all.

---

### Post by santerikannisto on 2018-09-24
> **mastablasta said:**
> Cinnamon, KDE, Xubuntu and Lubuntu are all configurable and kind of look like windows. i installed KDE to my wifes PC after messing arround with gnome at the start. i setup the classic menu, so it looked and felt like windowsxp she was used to at the time. she had no issues in transition. we then repeated this with my father promising to get him (at the time the latest) windows 7 if he wont' be able to get used to it. he has no issues. Libre office was just like the old word2003 he used before. he was used to firefox and he even learned to use some new programs (digikam). to me KDE is the most widnows like in a way that you can achieve most htings through menues, applications, settings, icons (the GUI in short).

XFCE is much lighter and very configurable as well. can fast be made to look just like windows.

I ended up working with xubuntu. Could not get debian-live-9.5.0-amd64-xfce.iso installed due to hardware incompatibilities probably because of some missing proprietary drivers debian-live-9.5.0-amd64-lxde+nonfree with should have included them didn't have then in the installer. There is plenty of work to do with XFCE to make things looks and work like Win7, and the installer has some issues, but I am hopeful it is doable. The test system is already up and running including.

By the way, the theme that looks closest like Win7 called redmond is totally broken. It does not even provide xterm to get to command line to fix things.

---

### Post by santerikannisto on 2018-09-25
By the way, what is the correct place to report xubuntu kernel issues?

> [    0.047101] ACPI Error: [_SB_.PCI0.RP05.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[    0.047197] No Local Variables are initialized for Method [PXSX]
[    0.047198] No Arguments are initialized for method [PXSX]
[    0.047200] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20170831/psobject-252)
[    0.047285] ACPI Error: Method parse/execution failed \_SB.PCI0.RP04.PXSX, AE_NOT_FOUND (20170831/psparse-550)
[    0.047923] ACPI Error: [_SB_.PCI0.RP09.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[    0.048004] No Local Variables are initialized for Method [PXSX]
[    0.048005] No Arguments are initialized for method [PXSX]
[    0.048007] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20170831/psobject-252)
[    0.048091] ACPI Error: Method parse/execution failed \_SB.PCI0.RP08.PXSX, AE_NOT_FOUND (20170831/psparse-550

---

### Post by mastablasta on 2018-09-25
> **santerikannisto said:**
> I ended up working with xubuntu. Could not get debian-live-9.5.0-amd64-xfce.iso installed due to hardware incompatibilities probably because of some missing proprietary drivers debian-live-9.5.0-amd64-lxde+nonfree with should have included them didn't have then in the installer. There is plenty of work to do with XFCE to make things looks and work like Win7, and the installer has some issues, but I am hopeful it is doable. The test system is already up and running including.


forget about it looking like windows 7. just get s start menu, applications the user needs or their best alternatives (and give some training) and you are good to go. if people really needed (!) the windows look on all their computers, then no one would ever use Andorid, iOS... instead they just need something that makes sense and is easy to use.

> **santerikannisto said:**
> By the way, what is the correct place to report xubuntu kernel issues?

i am not sure these are any critical errors, but to report bugs you need to use launchpad. read more here: [https://docs.xubuntu.org/contributors/qa-bugs.html](https://docs.xubuntu.org/contributors/qa-bugs.html)

kernel is the same as in Ubuntu + you will get a bit more information on reporting bugs here at the Ubuntu documentation: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by santerikannisto on 2018-09-25
> **mastablasta said:**
> forget about it looking like windows 7. just get s start menu, applications the user needs or their best alternatives (and give some training) and you are good to go.

No worries, I already got it done well enough so that my computer illiterate wife is happy and able to use the system.

> **mastablasta said:**
> i am not sure these are any critical errors, but to report bugs you need to use launchpad. read more here: [https://docs.xubuntu.org/contributors/qa-bugs.html](https://docs.xubuntu.org/contributors/qa-bugs.html)

kernel is the same as in Ubuntu + you will get a bit more information on reporting bugs here at the Ubuntu documentation: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Thanks for the pointers! I will take a look at them.

---

### Post by santerikannisto on 2018-09-25
> **mastablasta said:**
> by default all inbound network access is blocked in Ubuntu.

I checked this and unfortunately it is not true. By default iptables is not blocking any traffic. This is a huge security blunder. How to get this fixed ASAP? Also having ufw disabled is Very Bad Idea™.

---

### Post by mastablasta on 2018-09-26
sorry not inbound, outbound. you do need inbound traffic else you won't be able to see anything online. when you load a web page it travels from outside to inside. you need that traffic free of obstacles. but basically you can't log in to your PC from outside. i am sure google, facbook and similar would not use the OS if it was a big security mess as you claim.

ufw is just frontend for iptbels

---

### Post by santerikannisto on 2018-09-26
> **mastablasta said:**
> sorry not inbound, outbound.

iptables is not blocking any traffic, not inbound nor outbound. And I am not the only one who has discovered this. Maybe the others simply ditched ubuntu without even bothering to report the issue...

See for example [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) :
> [COLOR=#333333][FONT=Ubuntu]When you install Ubuntu, iptables is there, but it allows all traffic by default.[/FONT][/COLOR]

---

### Post by mastablasta on 2018-09-26
because you know only half of the story.

[https://askubuntu.com/questions/22667/why-is-the-firewall-disabled-by-default/](https://askubuntu.com/questions/22667/why-is-the-firewall-disabled-by-default/)

Out of the box, Ubuntu ships with no TCP or UDP ports open, hence the belief that there's no reason to run Uncomplicated Firewall (ufw) by default.

> [COLOR=#242729][FONT=Arial]In general a properly hardened Unix or Linux system will not need a firewall. Firewalls (except of certain security problems with Windows computers) make more sense to block internal networks to the Internet. In this case local computers can communicate with each other over open ports which are blocks towards the outside by the firewall. In this case, the computers are intentionally opened up for internal communications which should not be available outside the internal network.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The standard Ubuntu desktop would not require this, hence ufw is not enabled by default.[/FONT][/COLOR]


[https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

bottom line install gufw and be done with it.

---

### Post by santerikannisto on 2018-09-26
> **mastablasta said:**
> because you know only half of the story.

[https://askubuntu.com/questions/22667/why-is-the-firewall-disabled-by-default/](https://askubuntu.com/questions/22667/why-is-the-firewall-disabled-by-default/)

Out of the box, Ubuntu ships with no TCP or UDP ports open, hence the belief that there's no reason to run Uncomplicated Firewall (ufw) by default.

[https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

bottom line install gufw and be done with it.

I read also that one earlier and it's a pretty lame excuse. Even the guy who wrote it don't agree as you must have read.

I also understand the need to keep the core packages identical for server and desktop distribution, but there is no excuses for leaving the firewall open in a desktop distribution.

Moreover, having an unconfigured firewall and unused firewall config software in the distribution makes even less sense. It's simply making the distro bloatware without any reason. I think they should be left out in the first place if they are not used out-of-the-box.

---

### Post by mastablasta on 2018-09-27
i believe Mint enables it by default.

---

### Post by santerikannisto on 2018-09-27
> **mastablasta said:**
> i believe Mint enables it by default.

That makes sense for all desktop distros. Do you know what is causing such brain farts in ubuntu? I have so far discovered several of them.

The snap "thingie" seems to be another. It seems to provide duplicate (apt-get), obsolete and useless functionality for the system cluttering up the file system and users desktop with crap. I think it should be left out and buried.

Another is plymouth. Although it provides nice animation during boot, but makes system slow, does not really work (many boot notification escape the overlapping graphics), take disk space and complicates the system unnecessarily. I would simply turn all notification off by default and offer blank screen during the boot. With modern computers its anyway so quick that nobody will  start rebooting their computer because they think they hanged up like in the old days.

How do you feel about those?

---

### Post by mastablasta on 2018-09-28
> **santerikannisto said:**
> 
The snap "thingie" seems to be another. It seems to provide duplicate (apt-get), obsolete and useless functionality for the system cluttering up the file system and users desktop with crap. I think it should be left out and buried.

snap apps are not the same as apt-get. they are sandboxed. you can for example run multiple versions of same application at the same time. additionally as i understand it the "sandbox" provides another security layer.

> 
Another is plymouth. Although it provides nice animation during boot, but makes system slow, does not really work (many boot notification escape the overlapping graphics), take disk space and complicates the system unnecessarily. I would simply turn all notification off by default and offer blank screen during the boot. With modern computers its anyway so quick that nobody will  start rebooting their computer because they think they hanged up like in the old days.

How do you feel about those?

modern computers also usually have broadband access but as you know it is not always the case. our business laptops all have HDD. maybe bosses have SSD. in any case it is there to make it look nicer and more presentable. if you bought Ubuntu preloaded PC (e.g. dell or system76 ...) they would work properly. it also works well on my wife's and my PC. the system resource used is tiny. 

anyway if we go into resources, why use desktop at all. for example i3 does it all. have a look at it. it is also very easy to use and doesn't really require a mouse. so might as well throw that away :p

---

### Post by santerikannisto on 2018-09-28
> **mastablasta said:**
> additionally as i understand it the "sandbox" provides another security layer.

To me that looks like yet another unnecessary security risk. In the old days there was a lot of debate about creating universal package manager that could deal with both deb and rpm. There were many proposals and tries, and today all of them are dead. Snap looks exactly like them. If it is alive after 3 years that will be a miracle. 

> **mastablasta said:**
> if you bought Ubuntu preloaded PC (e.g. dell or system76 ...) they would work properly.

Unfortunately they don't. I have bought two and both were breached by Dell crapware. The only way to secure them was format and re-install.

> **mastablasta said:**
> why use desktop at all. for example i3 does it all. 

What is i3?

One more inclusion to my brain fart list. I am working with Ubuntu kernel. There is one generic kernel for all ubuntu versions meaning that both server and desktop run the same kernel. The configs I have been reading so far are peculiar. The kernel has been made seriously bloated, slow and insecure only to make it suitable for every possible use. As I told in the beginning when you make something for everyone it is no good for anyone. When I finish compiling my kernel I can measure the gains in speed and size.

---

### Post by mastablasta on 2018-10-01
i3 windows manager: [https://i3wm.org/](https://i3wm.org/)

---

### Post by santerikannisto on 2018-10-01
> **mastablasta said:**
> i3 windows manager: [https://i3wm.org/](https://i3wm.org/)

Thanks for the link and explanation.

---

### Post by santerikannisto on 2018-10-05
I fixed ufw to start automaticly out-of-the-box: [https://launchpad.net/~santerikannisto/+archive/ubuntu/desktop](https://launchpad.net/~santerikannisto/+archive/ubuntu/desktop)

Now I am working with the desktop kernel.

---

