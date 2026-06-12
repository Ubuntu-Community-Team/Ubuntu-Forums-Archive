---
title: "Freshly installed Ubuntu on laptop. wifi connect, dual o/s, switch between o/s, etc."
date: 2014-11-04
forum: New to Ubuntu
---

### Post by Mark_McDonald on 2014-11-04
Hello, I erased the crappy Windows Vista O/S on my laptop and installed Ubuntu Linux. It successfully installed, however I seem to have difficulty finding where I can log into my homes wireless router, I set it to not broadcast the network, for basic security reasons. This is my first ever Linux O/S. You see the reason I did this move is my laptop was very slow, it always crapped out with the "Not Responding" program window issues, which after reading up on the problem in forums, is a common issue, and Vista I now learned is the worst Windows O/S ever by Microsoft. Since I learned this, my desktop too has Vista, so now I am going to install the new Windows when it comes out next year onto the desktop, as I need Windows for work. I have several different questions in regards to my laptop and my desktop. 

I will be using my laptop strictly for music downloads, as I want to keep my desktop as clean as possible. The Dell Inspiron laptop specs are 1GB of ram, I believe its most likely DDR2, 300GB 7200rpm HD and most likely 1Ghz CPU. The batteries are toast, so it always has to be plugged in. It currently has Ubuntu, but like I mentioned how do I connect to my houses wireless router. Is it an option that I should have added during installation? I do see the little icon on the top right, beside battery power and options icon.

The workhorse is the desktop, used for business and pleasure. So it has to be stable, run smooth, which is probably an oxymoron for Microsoft. It also has the "Not Responding" window issue. So I was wondering if it is possible to have both O/S's on one computer, and how do you switch between the 2 O/S's, do I have to reboot into a specific O/S? I just upgraded the power supply to a 600 watt ~40A (from 300W 11A), this was needed for the graphics card I installed. GeForce GTX 650 (previous graphics was an onboard p.o.s.) and that was done for the sole purpose of a better gaming expirience on World of Tanks for my son (went from 6fps to ~35fps). My next moves for this computer will be next years new Microsoft O/S Windows 10 (I believe its called this, they are skipping over 9), I could install the stable and most popular Windows 7, but I think 10 will be good..hopefully.  Also I think I will have to upgrade motherboard and ram if I want SSD HD, but the only advantage will be quick boot time, and quicker software loads that are installed on low storage space SSD's. But the ram should be faster too, by next year the DDR4's should be widely accepted. The 2007 HP desktop specs are Dual Core 2.6GHz and 4gb of ddr2 ram, ~300GB HD @ 7200rpm, 64 bit Vista SP2. Uses for the desktop are just internet use with a lot of youtube, multiple pages on internet and google maps, and  online flash games, email, world of tanks online game, word, excel, powerpoint,  adobe reader. Thats about it. Like right now I have web-based email tab, 2 or 3 Ubunutu pages open, cell phone company web page open, an article on motorcycles, a motorcycle forum, wikipedia on motorcycles. A window for computer. A window for a dating service. Then I have System Explorer, CCleaner, Volume, wifi router, and a few malware icons on the bottom right.

Summary of questions from my previous ramble.
------------------------------------------------------
 - Setup of wireless router in my Ubuntu Linux laptop to connect to non-broadcasting home router?

- Dual O/S (Windows and Linux) on one system?

- How do I switch between the 2 different O/S's?

- Does Ubuntu support SSD HD's?

- Is this the most popular Linux O/S? I only really installed it because of a recommendation off another forum, plus I did a google search and found a list which listed this as a good Linux O/S.

- Can I use any and all PC software, or does it have to say Linux on the software box. I was thinking PC games I can buy or download from Bestbuy, or antivirus programs. 

Anyway thanks for reading, hopefully I can connect to the internet on my newly installed Ubuntu laptop.

---

### Post by coldcritter64 on 2014-11-04
> Setup of wireless router in my Ubuntu Linux laptop to connect to non-broadcasting home router?
Problematic at best in Linux from my experiences. I used to think the same way about security, but hiding an ssid gives NO protection from a hacker with the right tools, just makes your life a misery at times (from first hand experience in the days I was running Vista as well as Ubuntu Lucid).

Something for you to read and consider with respect to hiding your networks SSID.

[http://www.howtogeek.com/howto/28653/debunking-myths-is-hiding-your-wireless-ssid-really-more-secure/](http://www.howtogeek.com/howto/28653/debunking-myths-is-hiding-your-wireless-ssid-really-more-secure/)
Pay special note to the second section title ...> Finding Hidden SSIDs Is a Trivial Task

If you do decide to transmit the SSID (after reading the above link) hooking up your Ubuntu install with an ethernet cable temporarily will give easy access to the routers homepage, after resetting the connections SSID visibility via ethernet cable the wireless becomes easier to connect to and the cable can be disconnected/removed.

> - Dual O/S (Windows and Linux) on one system?

- How do I switch between the 2 different O/S's?Dual booting can be set up with gparted from a live cd or Windows tools (best used if resizing or adjusting a Windows partition) for the partitioning. When Ubuntu is installed it writes the boot records and installs the Grub boot-loader, and it includes access to any Windows operating systems installed. Ubuntu should be installed after Windows, Windows has a tendency of overwriting the boot  records while ignoring Linux partitions thus blocking access to Linux, whereas Ubuntu will give an entry in the Grub boot-loader to boot any installed Windows partitions. 

You choose the OS just after initial boot up (or from a reboot from within either OS) from the Grub boot loader screen.

Further info link : [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

> - Does Ubuntu support SSD HD's?From what I've been reading here, *_Yes_*. I don't use them though and have no personal experience with them.

>  - Is this the most popular Linux O/S? I only really installed it because  of a recommendation off another forum, plus I did a google search and  found a list which listed this as a good Linux O/S. 
I'm not up on the current user statistics, but Ubuntu seems to, by far, have the largest Linux user base. It is a very good OS, with plenty of options. If you don't like the standard set up there are plenty of other desktop environments to experiment with. Adding another DE (desktop environment) is only a click or 2 away in the Software Center and can be accessed from the current log in screen (by clicking on the cog icon and selecting the newly installed DE entry). Try unity out thoroughly first, you may like it and not need any changes/additions. I've been on Ubuntu since 7.10 "Gutsy Gibbon", Ubuntu is a *_very_* good beginners distro in my opinion. 

> - Can I use any and all PC software, or does it have to say Linux on the  software box. I was thinking PC games I can buy or download from  Bestbuy, or antivirus programs. 
Try researching Linux alternatives to what you use in Windows and see if they can meet your needs. Most applications have a Linux alternative. Check out [http://www.linuxalt.com/](http://www.linuxalt.com/) for common application alternatives in Linux.

Some windows programs can be run under WINE. Windows programming/games can be "iffy" when used in Ubuntu via the Wine package (Wine = **w**ine **i**s **n**ot **e**mulation ... wine is a code compatibility layer on Linux to run _***some***_ Windows apps ... your mileage will vary using it, some apps work, a lot won't).

Use [https://appdb.winehq.org/](https://appdb.winehq.org/) to check out any game or application from Windows for compatibility and in some cases reviews.

For PC games if they don't work in Wine or in Windows in a virtual machine, you really need a Windows install if you want to play them, dual booting serves well here for when you absolutely need to play a specific game ... boot into windows and play away ;). 

Check out Steam on Ubuntu for some games. [https://wiki.ubuntu.com/Valve](https://wiki.ubuntu.com/Valve) and [https://apps.ubuntu.com/cat/applications/steam-launcher/](https://apps.ubuntu.com/cat/applications/steam-launcher/)

> ...or antivirus programs. I personally haven't used or installed an antivirus program in Linux in about the last 5 years without incident. There are far more important security aspects that you need to be aware of than viruses. None "in the wild" and only a few dozen or so known. They are possible, but by the OS design it is very difficult for them to operate effectively.

Some security information for your consideration/information:
[URL="https://help.ubuntu.com/community/Antivirus"]Antivirus - Community Help Wiki
[/URL][https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) (especially note point #2 in the "Most Basic Set of Rules" section :))
[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812") ("Windows Mindset" section is well worth reading in particular)

I just noted you mention Flash games etc. Flash in Linux is no longer supported by Adobe (I believe they may still be pushing out security updates, but not any newer releases). There is a version available in the repos (old but still usable) or you can install google chome browser and use pepperflash. You may get better flash games support on Windows so a dual boot set up may be a good idea for you to consider particularly as gaming has been previously mentioned as well.

Regards, coldcritter64

---

### Post by Bucky Ball on 2014-11-04
Welcome. You have a lot of questions. Which one do you want to tackle first? I suggest you post threads for each support request you have (in the appropropriate forum section and with a descriptive title) and it will be MUCH less confusing. There's plenty of room here. ;)

For now, we'll get the simple ones out of the way.

- Setup of wireless router in my Ubuntu Linux laptop to connect to non-broadcasting home router?

Unsure how you would connect to a router that's not broadcasting.

- Dual O/S (Windows and Linux) on one system?

I thought you'd installed Ubuntu with Windows dual-boot? If not, yes, fine, standard, most users do.

- How do I switch between the 2 different O/S's?

There is a menu when you boot up.

- Does Ubuntu support SSD HD's?

Yes.

- Is this the most popular Linux O/S? I only really installed it because of a recommendation off another forum, plus I did a google search and found a list which listed this as a good Linux O/S.

? Linux is about using what suits the way you work and is most productive for you. Even if Ubuntu is the most popular Linux OS, most of us don't know, and Ubuntu might not be right for you. There a gazillions of other open-source options. Is that important? It's certainly has a thriving community and some of the best support because of it. ;)

As mentioned, pick on support request, give plenty of detail, and do the same for any other support requests on their own thread. Hope that all helps and enjoy the forums. ;)

---

### Post by Bucky Ball on 2014-11-04
Welcome. You have a lot of questions. Which one do you want to tackle first? I suggest you post threads for each support request you have and it will be MUCH less confusing. There's plenty of room here. ;)

For now, we'll get the simple ones out of the way.

- Setup of wireless router in my Ubuntu Linux laptop to connect to non-broadcasting home router?

Unsure how you would connect to a router that's not broadcasting.

- Dual O/S (Windows and Linux) on one system?

I thought you'd installed Ubuntu with Windows dual-boot? If not, yes, fine, standard, most users do.

- How do I switch between the 2 different O/S's?

There is a menu when you boot up.

- Does Ubuntu support SSD HD's?

Yes.

- Is this the most popular Linux O/S? I only really installed it because of a recommendation off another forum, plus I did a google search and found a list which listed this as a good Linux O/S.

? Linux is about using what suits the way you work and is most productive for you. Even if it is the most popular, most of us probably wouldn''t know or care, and Ubuntu might not be right for you. There a gazillions of other open-source options. One thing is certain, Ubuntu would have the best support community. The more obscure you get with your choice of Linux flavour/distro, the harder you will find it to get help. ;)

As mentioned, pick one support request, give plenty of detail, and do the same for any other support requests on their own thread. Hope that all helps and enjoy the forums. ;) 

You might want to read [THIS]("http://linux.oneandoneis2.org/LNW.htm") and the third link in my signature.

---

### Post by Mark Phelps on 2014-11-04
Text removed

---

### Post by Bucky Ball on 2014-11-05
> **Mark Phelps said:**
> You should read through the material in the link -- to see what you're getting into in switching to Linux: [http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

I just gave that link at the end of my last post. ;)

---

