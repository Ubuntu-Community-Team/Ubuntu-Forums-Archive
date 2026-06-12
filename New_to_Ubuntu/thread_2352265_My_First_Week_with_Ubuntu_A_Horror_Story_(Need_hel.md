---
title: "My First Week with Ubuntu: A Horror Story (Need help with legacy BIOS and security)"
date: 2017-02-11
forum: New to Ubuntu
---

### Post by gnomish-pantaloons on 2017-02-11
Firstly, I've read as much as I possibly can about every issue that I've had. In some cases, I can solve it myself. One of the problems is there are often differing opinions and tools around a same solution, and they vary by version, so I humbly ask for some help. 

I don't want to clog this post with unnecessary narrative (unless asked), but I recently had one of the worst virus scares of my life, compounded with a probabilistically insane amount of coincidences.  This has put me in panic mode as I realize just how naive I was. Ok, cut to the chase:

 I am running Ubuntu Gnome 3 dual with Win10 from EFI (Secureboot not supported by BIOS or recognized by Windows). I followed as many directions I could gather before this last install, they both boot fine. However, I still fear that anyone with wireshark could have injected malware into my firmware while my guard was down, or worse, that I've been compromised for a while and had no idea. Reading Kaspersky's threatblog hasn't made me feel any better.


```
 description: Motherboard
       product: Aspire M3970
       vendor: Acer
       physical id: 0
       serial: (omitted just because)
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P01-A1
          date: 03/23/2011
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification

Router: 
System Software Version
eMTA & DOCSIS Software Version: dpc3941-P20-18-v303r20421733-160413a-CMCST
Software Image Name: dpc3941-P20-18-v303r20421733-160413a-CMCST.p7b
Packet Cable: 2.0
```


As you can see, I am stuck with legacy bios, the first release even. Windows 10 lied to me and said my model was supported, but Acer does not maintain drivers for Win10 for this model and they never have. I am quite reluctant  to do anything more until I have an updated BIOS. I've installed 16.10 3-4 times already, and I'm now being very careful with everything I do. I've been on the internet with crap firmware for close to a year, with the bare minimum of router setting security awareness (WEP=1, HOTSPOT=1, UnPnp=1, noooo). If this is the case, no matter how much probing I did with system tools, I might not be able to even see it.

I ran sudo ftws on the command line at the grub2 command line, and I ran it while ubuntu was running as well. For some reason, the grub2 shell use of sudo ftws didn't generate a log anywhere (checked root ftws folder, only a couple .json files). 

Here are the results.log of ftws while in Ubuntu: [http://pastebin.com/WKcQzSFa](http://pastebin.com/WKcQzSFa)
Synopsis: There was a lot of failure and skipping around all the things i cared about. Things with "UEFI" and "BIOS" in them. Trying in the grub2 shell had the same kind of results.

I also attempted to ID tampering with my Cisco router firmware by comparing unique file hashes to the Cisco repository, but this proved to be too difficult and time consuming,  I just do not understand the systems well enough. I've spent dozens of hours trying to solve this myself, read forum posts across the land, even Cisco pen testing manuals (most of which went over my head).

Questions

1. The linux bios version on [Acer do not apply to my specs. ]("https://www.acer.com/ac/en/US/content/support-product/3673?b=1")
I can't expect any kind of proprietary solution from them for anything now.

2. I have read a good deal about OpenBIOS type projects, but finding one that works for my machine is a daunting task. If any of you know how or where I can find a working BIOS for this setup, or if there's a diagnostic I should be running, please let me know. Libre does not seem to be supporting it either.

3. I can't troubleshoot or do anything else on any OS without feeling a sense of security at the firmware level. It might be that I'll have to recycle this box. It might have infected  everything that it touched. Any diagnosis methods, tools, or consolation the wise ones of the community could give me would be greatly, greatly, appreciated.

---

### Post by wildmanne39 on 2017-02-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by HermanAB on 2017-02-11
OK, so you installed Linux following the default install and it works.

Now you have to take a deep breaths a few times: Breathe in..., breathe out..., breathe in..., breathe out...., relax... your computer and your data is safe.

Forget about the horrors of windows, of viruses and malware.  Linux pretty much doesn't have any.

Don't install junkware off the web, use the software install system and the Ubuntu repositories only, set a looong password of 12 characters and all will be well.

Really.

Enjoy your new system.

---

### Post by gnomish-pantaloons on 2017-02-11
Thank you for your reply, Herman. I know that Linux is more protected against the more common Windows-style issues, but based on everything I've read from security sources it doesn't protect you from everything. Bad firmware is still bad.  

[http://routersecurity.org/bugs.php](http://routersecurity.org/bugs.php) 
[http://www.securitynewspaper.com/2017/01/12/attacking-uefi-runtime-services-linux/](http://www.securitynewspaper.com/2017/01/12/attacking-uefi-runtime-services-linux/)

I've read Kaspersky's blog on various kinds of new remote firmware attacks as well... My main point is that my BIOS is really old, and it can never be updated. That's a security problem no matter what OS is on it. I can give up Windows 10 (though I still need it for work), and I just saw something called Winsplash. Just recently saw that in January there was an Ubunutu UEFI vulnerability that made the news, so I really need something more than the adage that linux cures everything. Thank you for trying to help me out. I don't install junk stuff, have always been super careful about 3rd party appcs of any kind, and have actually stayed away from the 3rd party installers (syantec or whatever its called) because of the confusion they can cause.  

Vulnerabilities were: poorly configured router, no firewall (for a few days), ancient firmware BIOS.

---

### Post by Bucky Ball on 2017-02-11
> **gnomish-pantaloons said:**
> stayed away from the 3rd party installers (syantec or whatever its called) because of the confusion they can cause.

Synaptic Package Manager? At the moment its more reliable than the default Software Centre, is used and preferred by many of us and is totally reliable. Not sure where you got the information it's dodgy. It's available in the official Ubuntu repositories for a start ... ;)

No, Linux won't stop everything, but you do seem a little Windows-centric about this, no offence intended (we see it often when a new user has arrived from Windows and/or has read 'Kaskersky's blog' or something like it). You've called this a horror story but have no idea whatsoever if any damage has been done and it is a horror story because you think something 'may' have happened. This seems to be based on vulnerabilities inherent in a Windows release as old as your machine. 

If I'd been using an unsupported version of XP for a month I might be worried. In your situation, I'd listen to HermanAB. Where there's smoke, there's fire. I smell no smoke but I see a cosy fire; namely your dual-boot Win/Ubuntu laptop is working fine so the dual-boot install has been a success. :)

When you smell smoke, let us know. As you can't update the BIOS, that's out so all that's left is locking down your system with software however strenuously you feel is appropriate. Good luck.

---

### Post by gnomish-pantaloons on 2017-02-13
Bucky Ball, thank you for your reply, and for your consoling  advice. I apologize in advance for keeping this thread alive, and for  the following verbose post.

> Synaptic Package Manager? At  the moment its more reliable than the default Software Centre, is used  and preferred by many of us and is totally reliable. Not sure where you  got the information it's dodgy. It's available in the official Ubuntu  repositories for a start ...

I just reinstalled Ubuntu  16.10 once again from a fresh format. The last mess-up came from  clicking "System Configuration" in grub2, then running "fix packages"  from grub2, which I ran because I was getting missing file libraries  that were causing random crashes and critical errors in the OS after  POST. I am not quite sure what I did or installed that caused the  initial failure. I will trust in the Synaptic installer as you say,  though I've read the EXACT opposite of what you just said elsewhere,  that I should "trust the native installers" over anything else,  including Synaptic. This is an example, but I've read it elsewhere:

[I][From Ubuntu documentation]("https://help.ubuntu.com/stable/ubuntu-help/addremove-install-synaptic.html"):
> [/I]Synaptic Package Manager is more powerful and can do some      software management tasks which Ubuntu Software can't.      Synaptic's interface is more complicated and doesn't support newer     Ubuntu Software features like ratings and reviews and **therefore     isn't recommended for use by those new to Ubuntu.***  *I've read this in a few other places, and after getting knocked off my block on a couple installs, I'm trying to be as simple as I can in terms of what I add.

I suppose I'm "Windows-centric" because it's  Microsoft Windows that is mostly responsible for Acer et al abandoning  support for my board by foisting UEFI onto everyone. It is also advised  in the official Ubuntu documentation that new users should transition  slowly from their accustomed OS, which is what I am trying to do. And  unfortunately I really do need Win for many aspects of my work right  now. 

I would love nothing more than to go full Linux, but  because of my frozen legacy BIOS issue, I just shouldn't put all my eggs  in the Ubuntu basket until I know my system is maintainable and driver  extensible. I fully expect someone to say "Just install a new  motherboard and pipe down." I'd rather not do this for financial and  time investment reasons, and I'm also genuinely curious about this  problem as it seems saving slightly older machines (2011?) from the UEFI  lockdown and planned obsolescence  is part of the Ubuntu/open source  ethos. I will likely just give up on new linux OS flavors until I have  new hardware, I suppose.

Can you see where one coming from the  cold might be confused? I have run into this manner of problem on many  issues, where official documentation differs from userbase wisdom, or  the official docs fail to point out that there are newer, better tools  for doing something (I just noted another example of this looking for  drive encryption best practices after one fails to check the home  encrypt checkbox during install), and sometimes official sources might  fail to flag that the pages are  outdated. I have read that this is a  continuing challenge for linux-OS devs who want to convert willing users  (like me). 

The Gnome 3 OS install manual, by the way, does very  little to prepare one for thinking about what they need to be thinking  about. If I were to make a contribution to this community, it would be  to help with documentation and onboarding Windows/OSX refugees such as  myself.

I've experienced apparently common problems getting my  proprietary Nvidia drivers to load without crashes, and spent many hours  researching this issue. When something like this goes wrong, how do I  know if it isn't complicated by my firmware? Isn't it just common sense  to have an updated firmware BIOS? I don't mean to push the issue, but do  legacy BIOS users running Ubuntu really just not worry about this at  all? If not, why not? 

And yes, I realize I made some  grammar/spelling mistakes up there, but it was something like 5am, so  cut me some slack. :P Sorry for how long this is and thank you to  anybody who got this far. :)

---

### Post by mastablasta on 2017-02-13
it might help to know what kind of infection you had? was it rootkit (they are OS independent). or was it just some Windows virus you can remove with anti-virus? there are a few other tools for removing the rootkits. flashing the BIOS should also solve it. on Windows it is good to have at leats some basic software firewall and antivirus installed. 

from the writing i am not sure if the router got infected or what?

if you scanned the file after download and checked the hashes you can see if anyhting was "injected" or not. 

it helps if you browse internet with scripts turned off by default. 

and no OS is 100% secure. if someone is after you they will get in, especially if they have more resources they can use. though most easilly and cheaply they do it by con (phishing as they call it).

---

### Post by HermanAB on 2017-02-13
I still think that you worry too much.

Bear in mind that Kaspersky, Symantic and others want to sell you something - snake oil mostly.

Relax and enjoy your Linux system.

---

### Post by Geoffrey_Arndt on 2017-02-13
If you just go with the Ubuntu defaults, you'll be fine.     Make sure your router uses WPA2/psk personal or similar (why the WEP?).   

Or, if all of this continues to vex you, try ChromeOS/Chromebook, (only using a Windows machine offline or rarely for specific apps). 

Google protects all levels of users via built in security and sandboxing.     Well worth the small investment.

---

### Post by martemarziano on 2017-02-15
> **HermanAB said:**
> 
Now you have to take a deep breaths a few times: Breathe in..., breathe out..., breathe in..., breathe out...., relax... your computer and your data is safe.


Well, breathing in, breathing out might be helpful to stressed souls but it rarely address legitimate security concerns of the people who come to Linux under the impression that now they would be safe from all the evilwares out there threatening your computing security. Maybe I am missing something here, but I feel that many newcomers to Linux are under the false impression that once the have got their favorite flavor up and running they would be shielded from every kind of threats to the security of their system. Unfortunately that is not the case. You can take a look at the following article which is one of the latest in a row of many treating the subject of vulnerabilities of the Linux systems:
 [http://www.makeuseof.com/tag/linux-security-issues-aware/](http://www.makeuseof.com/tag/linux-security-issues-aware/)

cheers,
Marte

PS. I have had my share of "just-relax-and-enjoy-your-linux" advice, expressing my security concerns when those haven't been met with complete silence.

---

### Post by vasa1 on 2017-02-15
Let's keep this thread free of political references. Thanks!

---

### Post by poorguy on 2017-02-15
> **gnomish-pantaloons said:**
> I would love nothing more than to go full Linux, but  because of my frozen legacy BIOS issue,  I'd rather not do this for financial and  time investment reasons, and I'm also genuinely curious about this  problem as it seems saving slightly older machines (2011?) from the UEFI  lockdown and planned obsolescence  is part of the Ubuntu/open source  ethos. I will likely just give up on new linux OS flavors until I have  new hardware, I suppose. 
It was my impression that all bios had some sort of built in protection  against viruses and malware etc or perhaps I'm wrong.  

I have never heard of  anyone having their computers bios infected by a virus or malware. 

I run  computers from the year 2006 and ain't never been concerned about  whether I could update my bios. 

I was under the impression an end-user  updated / upgraded a bios for hardware support and hardware upgrades etc  or perhaps I'm wrong.


> **gnomish-pantaloons said:**
> I've experienced apparently common problems getting my  proprietary Nvidia drivers to load without crashes, and spent many hours  researching this issue. When something like this goes wrong, how do I  know if it isn't complicated by my firmware? 
I to have experienced problems getting Nvidia  proprietary drivers to  install and run with certain graphics cards so I stay with the open-source driver that is working  without crashes. 

> **gnomish-pantaloons said:**
> Isn't it just common sense  to have an updated firmware BIOS? I don't mean to push the issue, but do  legacy BIOS users running Ubuntu really just not worry about this at  all? If not, why not? 
Can't say for any other legacy bios users but this  legacy bios user doesn't worry about this at  all.

I believe you have made yourself PARANOID. ](*,)
----------------------------------------------------------------------------

Dell-Precision-380:~$ inxi -Fx
System:    Host: Dell-Precision-380 Kernel: 4.4.0-62-generic i686 (32 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: Precision WorkStation 380
           Mobo: Dell model: 0CJ774 Bios: Dell v: A07 date: 04/18/2006

---

### Post by gnomish-pantaloons on 2017-02-16
Thank you all for your thoughtful responses. It's quite funny, but I accidentally clicked on "run Windows in recovery mode" on the routine ubuntu grub2 loader menu and this apparently destroyed the EFI bootloader. I ended up messing something up in scandisk, got into grub rescue land, managed to get my usb live disk working again using set/syntax/root commands, and took a deep breath, as the first poster advised.

It would seem my worst enemy is myself, or maybe WIndows recovery mode, I can't decide. In any case, I'm looking at my boot record on paste2.org. I have no idea what any of this means, but I seem to be able to enter all the drives from my USB Live disk; all the files are there, I just can't boot to win10 or Ubuntu from my HD anymore.  I backed up all the stuff I really cared about to the cloud before I started this ubuntu adventure. I was getting ready to nuke this hard drive and replace it. don't really know why I shouldn't just roast windows forever, other than being afraid that I couldn't get onto Steam to play a few games with old friends due to BIOS/Nvidia weirdness.

And yes I've been far and wide reading about router firmware hacks and various vulnerabilities associated with outdated bios (it's a real thing). It's true the virus companies want to make a quick buck, but they also know a few things. Kaspersky isn't going to protect your router, but he publishes security research  on router vulnerabilities anyway, because that's his thing. Anyway, it appears to be divisive and unsettled so I'll let it rest.

Not quite sure what my next move is going to be, but it will likely involve formatting my entire hard drive into a single linux partition and going from there. If I still have problems, I guess I'll have to save up for a new win box. Cobbling together boot records and tracing all my steps just seems like an enormous time investment and one that will just leave me more frustrated, not to mention I will still feel insecure, like I missed something important. 

Thank you for all of your help.

---

### Post by Bucky Ball on 2017-02-16
> **gnomish-pantaloons said:**
> Not quite sure what my next move is going to be, but it will likely involve formatting my entire hard drive into a single linux partition and going from there.

And unfortunately you won't be going far. :)

You're going to need more than 'one big partition'. I suggest you do a little more research about installing Ubuntu and Ubuntu before going much further. Boot from the Live media (try ubuntu) and play around for awhile. Get that online and see what you find. When you're ready, hit the 'Install Ubuntu' icon on the desktop, but not before you read up a bit.

You can let it do the automatic install on a full drive (but you might not like the partitioning you end up with) or you can manually partition yourself. [See here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"). Down below there's the instructions, with pics, for a 'Something Else' install where you manually partition. You will need at least two partitions. / and /swap. You need to make sure you know what you are going to do and what you are aiming the partitioning to look like at the end  before you leap into an install and waste more of your time.

---

### Post by gnomish-pantaloons on 2017-02-17
```
/dev/sda1        2048    1050623    1048576  512M EFI System
/dev/sda2     1050624 1940975615 1939924992  925G Linux filesystem
/dev/sda3  1940975616 1953523711   12548096    6G Linux swap
```

Looks like I got home, swap, and the boot. (/ for root, /home for my stuff,  /swap for memory) that's all I need pretty much, right?
If I run into some problems, I certainly know where to go. Don't worry, it won't take long :)

---

### Post by Bucky Ball on 2017-02-17
Yep, for a basic install, that's all you need. Once you use it for awhile you might find a different partitioning scheme may work better for you.

For a lot of people, their first Ubuntu install is a bit of a 'test run'. The partitioning can often be different on their second or down the track a bit.

Who knows? What you have now may be all you ever need. In the meantime, looks like you're good to go if everything's working as should so enjoy! :)

PS: Just thought I'd mention it, but with a setup like yours with less than four partitions, you really don't need EFI for any good reason. Not necessary. Generally used for dual-boots where Win is preinstalled in EFI and for installs where you want more than four partitions on one physical drive. 

You also don't need 6Gb of RAM, particularly if you have plenty of physical. 2Gb is fine unless you hibernate the machine then should be same or more than amount of installed physical RAM. You could fix this by:

Launching Gparted (you can install from package manager)> right click and unmount sda2> right click and choose 'swapoff' on /swap. Shrink /swap by 4Gb, expand sda2 into the free space created by the /swap shrink.

Or maybe next time. Have fun.

---

### Post by gnomish-pantaloons on 2017-02-22
Bucky Ball,  Thank you for all of your help. I am learning quite a bit at a rapid clip. Here's two things I've read in "official documentation" that I believe should be placed as headers on every single piece of Ubuntu documentation:    1) "Ubuntu was made by tinkerers, for tinkerers."  2) "It takes 2-4 years to get acquainted with Linux."   The latter is sort of a big one. Right now, I am taking it slow. I am trying to get one beloved app working after another. I am also keeping an Ubuntu journal/rantbook so I know what I actually did to make my system broken again, as Logs are inaccessible to me (they require consulting with super users to grok).    Posting every problem I have here or searching does not seem like the best use of my time or anyone else's since it can create as many problems as it solves (that "tinkering" thing).     Searching for topics proves to be challenging as there are many different ways to skin the same (chaotic evil) cat in Ubuntu.  Right now, I have a hash confirmed copy of 16.04 Gnome and I'm thinking of reformatting my main partition again with a fresh formatted zeroed out Fat32 USB Live stick with a 16.04 system, as this build appears to be far better supported than 16.10 at this point.   Part of the reason why I'm doing this is that every proprietary Nvidia driver I've installed including those Yakkety recommends for my GeForce card has caused the usual black screen/death boot issues that require command line package fiddling and a general sense of terror resulting in reinstall.       Would anyone recommend a complete reformat and install to the earlier build? Am I breaking rules by asking this in this thread or should I start a different one about 16.10 vs 16.04 (yes, I've searched, I've looked for answers, I always do before coming here!); it feels like my past narrative is kind of necessary to understand why the heck I'm making these decisions.

---

### Post by mastablasta on 2017-02-22
> **gnomish-pantaloons said:**
> Bucky Ball,  Thank you for all of your help. I am learning quite a bit at a rapid clip. Here's two things I've read in "official documentation" that I believe should be placed as headers on every single piece of Ubuntu documentation:    1) "Ubuntu was made by tinkerers, for tinkerers."  2) "It takes 2-4 years to get acquainted with Linux."   The latter is sort of a big one. Right now, I am taking it slow. I am trying to get one beloved app working after another. 

it really shouldn't say that. i got a Linux preinstalled laptop for my dad. he is no techy. as the default Suse was limited (1 month access to repos) it got replaced with Kubuntu. told him to try it out and if he finds too many problems we can always install Windows later. as it turns out except from a minor glitch during upgrade (GPU drivers) it was all smooth. and he never used linux before in his life. of course the hardware was obviously linux compatible. as for software we installed what was easy to use. DigiKam for pics, Firefox for browser, Thunderbird for email, Skype for video calls. Libre office is used for office. but he wanted better connectivity with excel files so we added office 2007 in wine for that. easy to install via playonlinux. this is the only windows app on that PC.

you shouldn't try to install or battle with windows apps. do you often try to install andorid apps on windows PC? surely no. point is find an alternative and learn to use it. they are often better anyway. use software center to install apps. if it's not there and you really must have it, search and add a ppa for it.

so what it might actually say is: 
1. make sure your hardware is compatible with linux or prepare to do workarorunds or not have full features of the hardware available
2. use linux apps or apps with linux ports if you can. for windows apps there is wine, for DOS apps there is dosbox. for all OS and their apps there are virtual machines.

> 
I am also keeping an Ubuntu journal/rantbook so I know what I actually did to make my system broken again, as Logs are inaccessible to me (they require consulting with super users to grok). .

i am not sure what you mean by inaccessible. they are in /var/log. all have access to read them.
the .old files are older versions of the logs. one of the cool things abotu linux is most if not all things are logged.

---

### Post by gnomish-pantaloons on 2017-02-23
Mastablasta all I meant by "inaccessible" was that a series of errors in the logs does not necessarily point to what you're doing wrong if you don't know what you're looking at, so you need to post them on the forums. To an alien to the myriad of dependencies and millions of things that can go wrong, it's not eay to get on top of. You need a back and forth to decipher particular chunks of logs. I have t google Priority 1-5 logs reports and wonder what, or if, I should be focusing on anything. This equates to time. Searching for solutions is more time, and even even more time when I post log caps for the friendly folks here to look at.    I've read the ubuntu manual. I am not averse to clearly written documentation. Speculately, I might have been installing those 16.10 fresh installs from a corrupted USB live disk. I made a new fresh USB live out of a kingston right out of the box, and might just start over again to see if life gets better. Thanks again, all :)  p'loons

---

### Post by vasa1 on 2017-02-23
> **gnomish-pantaloons said:**
> ... Am I breaking rules by asking this in this thread or should I start a different one about 16.10 vs 16.04 (yes, I've searched, I've looked for answers, I always do before coming here!); it feels like my past narrative is kind of necessary to understand why the heck I'm making these decisions.
Well, my personal preference is to have a separate thread for each specific issue I face. I try to give the thread a descriptive title that may improve my chances of getting the help I need. Having a descriptive title also may help those who come by later in case they have a similar issue.

Another point, which is entirely subjective, is that shorter paragraphs are more readable.

---

### Post by mastablasta on 2017-02-23
> **gnomish-pantaloons said:**
>  To an alien to the myriad of dependencies and millions of things that can go wrong, it's not eay to get on top of. You need a back and forth to decipher particular chunks of logs. 

if hardware is not working, you focus on the parts that talk abotu that hardware or port hwere it resides. grep command will filter out the lines.

if software is the issue then it usually has a separate log.

dependencies and installing form source is another matter. most people install form Google play on Andorid. it is for the most part known to work and will install well. they don't add 3rd party stuff. software center is the same as google play - a repository. if you install from it there hsould be no issues (although they still are - abandoned apps - but this is a topic for another thread). since the software center is rather empty there are PPAs which make it really easy to add more repositories. all you add is a link and digital signature to software center and application is available.

---

