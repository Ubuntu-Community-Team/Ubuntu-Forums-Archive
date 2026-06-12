---
title: "Installing Ubuntu on old Desktop without any OS"
date: 2016-07-02
forum: New to Ubuntu
---

### Post by wireman67 on 2016-07-02
I have a old Lian-Li PC602 ATX case I have the following Biostar P4M900 M4 MOBO, Pentium 4 CPU 3.20GHz (2 CPUs), 4GB RAM, ATI Radeon HD 4650, 1TB - WDC WD10EZEX-00KUWA0  [Western Digital Blue WD10EZEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive Bare Drive], Floppy Disk drive, LITE-ON LTR-40125S  DVD/CD-ROM, Toshiba DVD-ROM SD-M1502 DVD/CD ROM, 450W Elite Power supply.   I possess the following 32-bit Operating Systems on CDs and Floppies include Win95, Win98, Win98SE, WinNT 4.0, Win XP and 64-bit Win 7 Home on DVD.  This past week I have been attempting to use several of the Live Linux CD/DVD that some of the Linux magazines glue into their magazine.   

[LIST]
[*]this has been frustrating because this whole week I could not boot from any of the Live CDs/DVD; however, a couple of weeks ago I had no problems accessing the Live CDs/DVDs

[*]I would rather mess my old Biostar P4M900 M4  MOBO than purchase a new MOBO and mess it up

[*]I had success booting to the Ubuntu 10.04 Live CD/DVD

[*]I proceeded to install this version of Ubuntu because I thought if I am successful I could then migrate to the latest Ubuntu 16.04

[*]My installation failed due to an input/output error either with my CD/DVD disc or HDD [the window also recommended cleaning CD/DVD disc

[*]I was going to takeout the Ubuntu 10.04 Live CD/DVD and proceed to clean my CD/DVD disc with my Laser Lens Cleaner, but Ubuntu appeared on my desktop

[*]I looked around on my desktop and it appears that Ubuntu installed onto my Biostar P4M900 M4 MOBO

[*]I ran the SMART Data Self-Test from Ubuntu on my 1.0TB HDD ATA WDC WD10EZEX-00BN5AO

[LIST]
[*]according to the test the disc is healthy
[/LIST]

[*]I was going to install Ubuntu again, but the system indicated that Ubuntu is installed on the HDD

[*]I can't access the Ubuntu Update Manager then
[*]I can't access the internet
[*]I took a lot of photos with my smartphone while I was attempting to install Ubuntu
[*]I searched the internet and I read that Ubuntu One was shutting down; thus I was also confused on how I logged into this forum requiring a "Ubuntu One account"
[*]I also visited the I am going to remove the live CD/DVD, shutdown my computer and go to bed because I am too tired
[*]I will revisit here tomorrow or the next day and dig through the forum because I thought I read some good advice, guidance, recommendations and tips.
[/LIST]


Thank you to all and please help me plant my Linux Ubuntu Tree

---

### Post by sudodus on 2016-07-02
Welcome to the Ubuntu Forums :-)

From your description I understand that you were able to install Ubuntu 10.04. It runs but there are some problems with it. This version of Ubuntu has passed end of life. There are no updates, not even security updates, and it will be very difficult to install new programs.

According to the hardware specifications, you should be able to install a current version of linux. I think the current Standard Ubuntu needs more modern hardware to run well, but there are lighter flavours of Ubuntu with the same engine under the hood.

- ***Lubuntu*** with the ultra light desktop environment LXDE
- ***Ubuntu MATE*** with the ultra light desktop environment MATE
- ***Xubuntu*** with the medium light desktop environment XFCE

There are also many other light or ultra light linux distros, that will probably work well in your computer, for example Bodhi, LXLE, Knoppix, ToriOS and Puppy Linux.

I suggest that you download the iso files, check them, burn the iso files to DVD disks or flash the iso files to a USB boot drive (can be re-used) and ***try them before deciding what to install***.

See the following links,

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

[Checking the iso file and the boot drive - detailed tips](http://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Bucky Ball on 2016-07-02
Welcome. Don't go for a demo glued to a magazine. [Download the official ISO]("http://www.ubuntu.com/download/desktop") instead.

4Gb of RAM? I'd give 16.04 LTS a go and see what happens. If nothing, try for a lighter flavour, as suggested by sudodus. I'd go Xubuntu next, then [Xubuntu-core]("https://unit193.net/xubuntu/core/"), then Lubuntu, but that is my preference and probably order of lightness, too.

Good luck.

---

### Post by nerdtron on 2016-07-02
It's a Pentium 4 CPU, and limited only to 32-bit OS. You can try to download Ubuntu 32-bit version here, just scroll a little down.
 [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

And I'd recommend Xubuntu, download it here, just click the 32-bit link.
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

[URL="http://xubuntu.org/getxubuntu/"]
[/URL]Just a side note, if your ISO has a filename with **amd64**, that means it is 64-bit and you can't use it. Download ISO with the **i386 **on the filename, which means it is for 32-bit systems.

---

### Post by grahammechanical on 2016-07-02
An explanation.

Ubuntu One was the name of an online storage product that the sponsor of Ubuntu (Canonical) set up. But it proved to be uncompetitive and not financially viable. So, it was closed down.

At that time Ubuntu users could set up a Single Sign On account where the same user name and password would log us into several Ubuntu related web sites. The Ubuntu One online storage used Single Sign On. When Ubuntu One online storage closed down the label "Ubuntu One" was attached to Ubuntu Single Sign On. So, the account that you registered when you joined Ubuntu forums was a Ubuntu One account and it has more uses that just logging in to this site. But no online storage.

I use web searches a lot to find information. But we have to watch out for outdated information.

Regards.

---

### Post by wireman67 on 2016-07-03
I read each of your responses and I thank you very much.  I booted my Lian-Li box and no operating system was installed on it; hmmm, I thought I had Ubuntu 10.04 installed on it last night.  I attempted to use my Laser Lens Cleaner CD and DVD players, but I started thinking it won't clean because I don't have an operating system installed on this computer and the CD/DVD Lens Cleaner also needs a operating system for usage.  I removed the CD/DVD Len Cleaner and I attempted to use a couple of the Live CDs/DVDs from the most recent to the oldest, so I inserted the Ubuntu 16.04 Final Beta | Desktop | 32-bit Launch Pack Live-Booting DVD; my computer went through a couple of reboot cycles forced by me [CTRL+ALT+DEL] and once on its own.  When my computer rebooted on its own I thought it would install after I selected the 32-bit option - argh! I received an error "EDD Error 8000 reading sector sector 1746598"?  

I will follow the advise from each of you by commencing with downloading the Linux ISO Image for a couple of the distros or flavors; which this gets very frustrating too for newbies: there are many, many distros and flavors and trying to learn the terminology is challenging in of itself.  I read and heard the many debates and discussions about Linux until I finally decided I would go with Ubuntu because according to most Linux Blogs and Forums it appeared that Ubuntu is the best distro to transition from Windows to Linux, but then I recently read in one of my Linux magazines that Dell is dropping Linux Ubuntu from their "pre-manufactured" computers to "special order only" because it is too hard for their customers.  I read in some of your responses that there are easier or lighter versions than Ubuntu.  Therefore I will download a couple of the Linux distros and determine which Linux distro is best for my computer because it is very old.  I accept all of this as part of my learning curve and with me in my life I have had a lot of steep learning curves.   

My next steps to the Linux World: 
[LIST]
[*]visit each of the recommended threads in this forum and read the content
[*]visit each of the recommended websites and read the content
[*]determine the method of downloading to either DVDs, CDs or USB thumb-drives
[/LIST]

Questions about downloading the Linux ISO image:
[LIST]
[*]What is a bit-torrent client?
[LIST]
[*]is it software that I need to install on my computer before I can join a peer-to-peer network
[*]I am not ready to join a peer-to-peer network
[/LIST]

[*]Do I need the bit-torrent client just to download the ISO image?
[LIST]
[*]Yes I do need it - more reading and deliberating of options
[/LIST]

[*]Which Bit Torrent Reader do I download?
[/LIST]

Other options to get Linux installed onto my Lian-Li box because I cannot RISK messing up my only working computer:
[LIST]
[*]Install Windows XP back onto my Lian-Li Box
[LIST]
[*]I am wondering if I am missing items in the registry, firmware or software that is needed just to get this computer running
[*]Say Win XP successfully installs then
[LIST=|INDENT=2]
[*]download the Bit Torrent client
[*]install the Bit Torrent client
[*]download the Linux ISO images
[/LIST]
[/LIST]

[*]Visit the local Linux User's Group
[LIST]
[*]they offer free installation help
[*]experienced Linux users will be present to assist me
[/LIST]
[/LIST]

Thank you for your help

---

### Post by sudodus on 2016-07-03
Maybe it is easiest to start by downloading the iso files 'the regular way' with a web browser, and to check the downloaded files with md5sum.

Later on you can start using torrents. I use the client Transmission, which comes with my flavour of Ubuntu (and I think also other flavours, so I needed no extra effort to get it). You download a small torrent file for each iso file that you want to get. The torrent file helps Transmission control the torrent process. In most cases it is faster and more reliable to use the torrent method.

Avoid Window XP, if you intend to connect to the internet. It has passed end of life, and receives no security updates.

---

### Post by Bucky Ball on 2016-07-04
> **sudodus said:**
> Maybe it is easiest to start by downloading the iso files 'the regular way' with a web browser, and to check the downloaded files with md5sum.

FTR: A torrent is actually the safest, most reliable, possibly simplest and Canonical preferred way of downloading the ISO (and best for Canonical as it doesn't use up so much server). From [here]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME#Torrent"):

> Please use the torrent link to download, using BitTorrent. It will be a faster download and will save on costs for bandwidth for the Canonical servers which means more money in the budget for all of the Ubuntu flavours. Please, seed as much as possible to help others as well.

... and from [here]("http://www.ubuntu.com/download/alternative-downloads"):

> 
BitTorrent is a peer-to-peer download network that sometimes enables higher download speeds and more reliable downloads of large files.

And [here]("https://help.ubuntu.com/community/BitTorrent"). 

Just thought I'd mention. I never use anything else to download the ISO. :)

Good luck.

---

### Post by wireman67 on 2016-07-04
Bucky Ball, 

What is "FTR"? 
What is "Please, seed as much as possible to help others as well"?

> **Bucky Ball said:**
> FTR: A torrent is actually the safest, most reliable, possibly simplest and Canonical preferred way of downloading the ISO (and best for Canonical as it doesn't use up so much server). From [here]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME#Torrent"):


... and from [here]("http://www.ubuntu.com/download/alternative-downloads"):


And [here]("https://help.ubuntu.com/community/BitTorrent"). 

Just thought I'd mention. I never use anything else to download the ISO. :)

Good luck.


sudodus,    [INDENT]Ah, based on your feedback, I guess the P2P Network really requires a lot of trust because essentially you're sharing each other's resources and P2P installation is "irregular (or more advanced) method of a Linux installation"? Your comment *"The torrent file helps Transmission control the torrent process. In most cases it is faster and more reliable to use the torrent method." * I guess the torrent method helps the user who has a slow internet connection.  If I can install WinXP onto my Lian-Li box then I know the computer is still operational. If I cannot install WinXP onto my Lian-Li box then I know that there is something wrong with my computer and maybe beyond my abilities to fix it.  Since it is a old computer and there isn't any data on it, I am not worried about the security risks and vulnerabilities.

My next steps: 

[LIST]
[*]Review information about WinXP installation, formatting and partitioning
[*]Install WinXP on my Lian-Li box
[*]Assuming WinXP successfully installs
[LIST]
[*]Prepare to dual-boot Linux Ubuntu with WinXP
[*]Read more information about Linux and the tools to install Linux
[*]Read more about the tools that are essentially a pre-requirement to installing Linux - this is great! - I get an opportunity to use something that was mentioned in my cybersecurity classes
[*]Install the tools that aid in the installation of Linux
[/LIST]

[*]If I cannot install WinXP on my Lian-Li box
[LIST]
[*]I already have a few MOBOs, CPUs, and RAM options that I am considering for purchase
[/LIST]
[/LIST]


Thank You

[/INDENT]

---

### Post by Bucky Ball on 2016-07-04
FTR='for the record'. ;)

---

### Post by sudodus on 2016-07-05
> **wireman67 said:**
> 
What is "Please, seed as much as possible to help others as well"?

You seed, when you keep the torrent client running so that other people can get chunks of the iso file from your computer:

With torrents you get the torrent file from the 'original source' (for example from Ubuntu's web site), and the iso file itself in small chunks from many other sources, the peers, that seed the torrent. Bucky Ball suggests that you keep the torrent client (e.g. Transmission) running, when you have received the iso file. Then the small chunks of the iso file will be available from your computer for other people to get via the torrent network.

---

### Post by Bucky Ball on 2016-07-05
> **sudodus said:**
> Bucky Ball suggests that you keep the torrent client (e.g. Transmission) running, when you have received the iso file. Then the small chunks of the iso file will be available from your computer for other people to get via the torrent network.

I actually omitted to suggest that, I was just suggesting downloading the ISO via torrent, but thanks, yes, it is polite to keep the torrent open til you've uploaded at least some back to the community (some folk like to upload equal to what they've downloaded and I think you can preset how much you want to upload after download has finished in Transmission somewhere or just stop the torrent upload when you like). :)

---

### Post by wireman67 on 2016-07-05
Argh! Nothing works on any of my attempts to install any Linux Package or Windows OS.  I attempted a couple more times with both Linux and Windows because I hoped some little bit somewhere in my machine would wakeup and install one of the operating systems.  I think I might have to purchase a low budget MOBO, CPU and Memory to install in my Lian-Li box.  However, the next meeting of the local Linux User's Group is next Monday.  I requested of the Group's Leadership if I could bring my desktop pc with me.  I am scheduled to meet some group members on July 18th.

Thank you

---

### Post by X-RED_Tech on 2016-07-05
Why are you still trying to install 10.04?
All the response in this thread have been quite clear about NOT using outdated, unsupported releases.

To start with something, your Biostar board is crap (aren't all Biostars?) and it may not support 1TB drives and it's so old that and hardware failure should be considered at any given moment.

What were the error when trying to install Windows and what Windows?

---

### Post by Bucky Ball on 2016-07-05
> **X-RED_Tech said:**
> Why are you still trying to install 10.04?

This is a good point. Please confirm if you are still trying to install 10.04. I have just gone through the thread and can't see that you have changed your intention there, unless I'm missing something.

We generally don't give support for obsolete, unsupported releases. Generally little point encouraging someone to install an old, insecure OS.

---

### Post by wireman67 on 2016-07-06
You both missed the point and I was also in a insanity loop!  However, I did say that I will attempt to reinstall one of my windows operating systems because I couldn't install any package of Linux.  Why am I using old hardware?  I have very little money and I have very little money because I have been unemployed for a very long time!  Besides in my research of Linux the Linux communities state that you [I] can convert your [my] old windows computer into a Linux computer.  This implies that I need a functioning windows operating system on my computer before I can attempt to convert my Windows desktop into a Linux desktop.  My Lian-Li box doesn't have any operating system because the last functioning HDD crashed in 2014.  Why am I installing a windows operating system?  I am installing windows, so I can install Linux!  I attempted to install Win XP, no luck! I attempted to install Win98SE, no luck! I attempted WinNT4.0, no luck!  I received a lot of different errors and nothing seemed consistent except I could not boot! I researched about Windows and ironically I found one of my old Win98 repair floppy disks, so I attempted to install Win98, Progress!  Now, I am at the point of where I can partition my HDD and format it.  I will partition it as small as possible and then format it too.  I read in my Linux magazines that dual booting with Linux is easier than installing Linux on an old windows computer.  Yes, you are missing the point about why I am using old hardware, I would rather mess up my old hardware that I can't give away.  If none of my attempts are fruitful then I will need to purchase a new MOBO, CPU and memory; however, on July 18th I will meet with the local Linux User's Group and maybe someone there could help me get Linux installed on this computer.

---

### Post by X-RED_Tech on 2016-07-06
You're still missing the point you shouldn't use unsupported operating systems, either Linux and especially Windows Do not even think about XP or 98 but more later).
You're still missing the point that you can run a supported current release with a lighter desktop like Lubuntu. Standard Ubuntu or Kubuntu are most likely too much for that hardware. The point is to choose what can run acceptably in your hardware to start with.
You're still missing the point that no, you don't need Windows to install Linux. And no, it isn't easier to have a dual boot than Ubuntu (or variants) as the single OS. You're reading outdated information that probably refers to WUBI, which isn't a real dual boot.

The fact that you could boot some Win98 installer is promising but knowing what were the actual errors you experienced before would be much better.
Anyway, how does the Win98 installer sees the drive?

---

### Post by sudodus on 2016-07-06
I would like to add the following:

You had to go all the way to Window 98 to be able to install a Windows operating system. This makes me think that you might need a linux distro that is made for really old hardware. ***Wary Puppy*** (a flavour of Puppy Linux) comes to my mind. You can also try a more modern version of Puppy, for example ***TahrPup***. Another alternative is ***Tiny Core***.

If/when you have such a flavour of linux running in the computer, you can settle down and take your time to find out more about the hardware to find the limits, and after that maybe you can install a modern 'full size' linux distro with a light or ultra-light desktop environment, for example Lubuntu.

Maybe it would be better to install only a window manager and 'cherry-pick' your favourite application program packages. Maybe you need some boot option(s) to make it run, and then you can run even a more demanding desktop environment. You may have problems to find a new linux graphics driver that works with the on board graphics chip of your motherboard, 'VIA Chrome9 HC IGP, On Board Graphic Max. Memory Share Up to 256MB' according to a link I found.

---

### Post by mörgæs on 2016-07-07
> **wireman67 said:**
> on July 18th I will meet with the local Linux User's Group and maybe someone there could help me get Linux installed on this computer.

I think that's a good idea. You have many (different) errors which are easier to solve with someone sitting next to you. Just bring all of your installation media (Windows and Linux) to the meeting and take it from there.

---

### Post by blackeagle2 on 2016-07-07
Maybe this will be of help, maybe not !! but I have 14.04 running on hardware that is at least 10 years old - Pentium 4, 250Gb HDD, 1Gb ram but reasonably new Nvidia graphics card.

The ONLY way I managed to install it was by using the minimal installer from a USB drive.  See [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Burning it to a CD and booting with that just failed - I have no idea why (possibly BIOS issues) but it just wouldn't work.  DVD drive was/is not faulty and the CD's were error free.

Another option at your user group meeting may be to put the HDD into another PC, install the installer into a partition on your drive, put it back into your PC and boot the installer.  Again I'd go for the minimal installer and a wired connection to the internet.

---

### Post by Bucky Ball on 2016-07-08
Windows not required. My wife just bought a brand new screamer of a machine, no OS, now running Xubuntu-core, no issue, no Win. :)

As mentioned, the users' group will clear up a few misunderstandings I think. If you want a running, up-to-date operating system and you don't want to spend, or can't spend, any money, Linux IS for you. You'll get there, if you still want to.

---

### Post by DuckHook on 2016-07-08
> **wireman67 said:**
> ...Why am I using old hardware?...I would rather mess up my old hardware that I can't give away...As an old-hardware hound, I applaud your efforts to revive your old computer before throwing it away. In that light, I encourage you to read the following thread authored by mörgæs who has also responded to you in your current thread: [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

I agree with mörgæs that you should make full use of the resources of your LUG. In the meantime, you can be better prepared if you go through the contents of his thread.

Best of luck to you, and let us know how it goes! ;)

---

### Post by wireman67 on 2016-11-16
I only recently returned to attempting to install Ubuntu on my old computer.  Yes, I was successful in installing WinXP SP3, but I had to daisy chain up from Win95: this was very frustrating and tedious.  I cannot remember the date that I was successful in installing Win XPSP3, but I think it was in late July.  I think the root cause of my Linux installation problem was a hardware/software problem and a DVD standard problem - oh yeah a little forgetfulness too.  Again I tried the Linux distros DVDs from the magazines starting from the newest 16.04 until 12.04.  In hindsight I don't think all of the DVDs packaged in the magazines were faulty; however some of them were problematic because when I followed the installation process I was prompted to report my installation problem then immediately a message popped-up stating we are already aware of this problem.  

I went through a couple of the Linux magazine's packaged DVDs until I got to the one titled _Linux Starter Kit Ubuntu 12.04 Precise Pangolin_ that actually installed and as I type it is still "getting new packages" [2186 files] and presumably the installation will commence afterwards.  After I installed Ubuntu 12.04 Precise Pangolin, I was prompted to update to a newer distro, thus my Ubuntu is currently upgrading to "Trusty Tahr 14.04"! 

I previously identified and annotated my computer's hardware in this thread that my computer has the following two CD/DVD players A) LITE-ON LTR-40125S  DVD/CD-ROM and B) Toshiba DVD-ROM SD-M1502 DVD/CD ROM.  I downloaded the latest Ubuntu to my Lian-Li computer thinking I would burn the latest Linux .iso file.   I looked at my DVD brands and types and then I headed to the local store and purchased "DVD-R"; after a closer look at my players, I realized that my DVD player is "Read Only Memory". All of my attempts to "Copy/Burn files to the DVD" was a futile attempt.  

 I just noticed that a installation error occurred "Could not install 'tex-common'  "The upgrade will continue, but the 'tex-common' package may not be in a working state. Please consider submitting a bug report about it."  

I hope this "Trusty Tahr 14.04 installation is a success and Trusty performs beyond my expectations.

Thank You

---

### Post by Bucky Ball on 2016-11-16
This is well old. If you have any issues you will greatly improve your chances of support by posting a new thread, more so if you state your support question clearly. Thanks and good luck.

---

### Post by mörgæs on 2016-11-17
Good that you got it working. Please read Bucky Ball's signature.

Next time I suggest that you try installing from USB and not DVD. Faster and more secure.

---

### Post by wireman67 on 2016-11-18
Thank you for your responses and referrals to links about Linux distro installations and other threads with advice and tips.  The Linux Road has just begun for me and gee whiz there is a lot of information! 

In summary I had a desktop computer without a  operating system - all I had was a BIOS!  I can only surmise that since my old computer was built and configured in the late 1990's or early 2000 as a windows desktop computer; therefore, it initially had to be revived as windows computer before I could install Linux.  Every one of my attempts to install Linux failed miserably.  One day as I was reading my Linux magazines it then dawned on me that most of the articles I read about installing Linux started with the fact that the desktop already had either a windows file operating system running on the computer or a older Linux distro.  Thus I begun my effort to install Win XP SP3, but it failed too: after reading about windows installations I realized I needed the utility programs: it wasn't until I used my Windows 95 Boot disk (W95BOOTDSK) Version 01.02.00.01 Disk 1 of 1 that my computer commenced booting.  After I had Win95 installed on my computer I was able to perform some administrative tasks.  Shortly thereafter, I reformatted the partition and installed Win XP SP3.  I used this configuration sporadically over the next couple of months until I was ready to attempt a Linux installation. For some reason or another this was the path I had to take to get Linux installed onto my Lian-Li desktop computer.   

I have a few other questions that I ponder, but I am happy that I have Linux 14.04 LTS aka "Trusty Tahr" operating on my desktop! 

Providing that my hardware keeps functioning without any major failures my Lian-Li Trusty Tahr desktop computer has a new shelf life until April 2019!  

Thank You

---

### Post by Bucky Ball on 2016-11-18
> **mörgæs said:**
> Good that you got it working. Please read Bucky Ball's signature.

+1. Please mark this thread as 'solved' to help others. See the link in my signature at the bottom of this post. Thanks.

---

### Post by wireman67 on 2016-11-18
I guess I am so new to this Forum that I need a "How To Use Guide to the "**Mark this thread as Solved"** Guide"!  

To those who visit this thread, my main problem was as stated in the title of this thread, but unknown to me I had prerequisite problems.  Once I solved the prerequisite problems, I was able to install Linux successfully.  To begin with I was constrained with my internet service (DSL) and I was constrained with lack of knowledge and skills [a good reason to use old computers instead of new computers unless you have unlimited monetary funds].   I never visited the local LUG because they are a "Debian" group and the logistics; however, I may visit them in a couple of months now that I have a successful "Ubuntu Linux" installation under my belt.  They meet once a month.  

Installing Linux requires Persistence!  Although Linux is open source it really isn't free! It also requires money: those Linux magazines aren't cheap!  I bought many Linux magazines over the years and most of them range from $15.99 to $25.00+, but I am happy with my purchases.  Knowing both your hardware and software also means more than just identifying the make, model and version etc., you have to learn about the capabilities of the hardware and software.  During my pre-Linux project, I had to review both Linux literature and old Microsoft product literature from my own library and online sources too.  

I have many questions about Linux, Microsoft, hardware and software and sometimes I don't know what question to inquire with one exception, "How do I mark this thread as solved?".

---

### Post by Bucky Ball on 2016-11-18
> **wireman67 said:**
> I guess I am so new to this Forum that I need a "How To Use Guide to the "**Mark this thread as Solved"** Guide"!

I pointed you to one in my last post. 'Thread Tools' at the top right or see the link in my signature at the bottom of my post, the last (blue) link right below this text: '* How to mark threads 'Solved''

Click it.

Thanks.

---

### Post by mörgæs on 2016-11-19
> **wireman67 said:**
> Although Linux is open source it really isn't free! It also requires money: those Linux magazines aren't cheap!  I bought many Linux magazines over the years and most of them range from $15.99 to $25.00+, but I am happy with my purchases.

I don't know why you consider them necessary. Most of them target advanced users and have only limited relevance to a beginner. 

One free alternative is here but I doubt it would have helped you installing: [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by mörgæs on 2016-11-19
> **wireman67 said:**
> ...since my old computer was built and configured in the late 1990's or early 2000 

The Radeon 4650 graphics card is from 2008-9 so your gear is only semi-old. I agree, you have a useful computer for many years to come.

---

### Post by wireman67 on 2016-11-20
> **mörgæs said:**
> I don't know why you consider them necessary. Most of them target advanced users and have only limited relevance to a beginner. 

One free alternative is here but I doubt it would have helped you installing: [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)


You made my point for me and your response also contradicts the claim of which I read so many times in Linux literature both online and in print, that Ubuntu is for beginners.  Thank you for validating my position.  I didn't claim that the Linux magazines were necessary, but I thought they were essential for me to learn about Linux.  I am not a programmer, coder or script writer, but I am persistent to learn.  I once read on another board that to FAIL actually means "First Attempt In Learning"!  I always got frustrated with the Linux publications because it they were more advanced than the beginner's level.  Thank you for the link to full circle magazine and for each of your responses.

---

### Post by Bucky Ball on 2016-11-20
> **wireman67 said:**
> I once read on another board that to FAIL actually means "First Attempt In Learning"!

Couldn't have said it better myself. No mistakes, no learning. We should never be (too, depending on what's at stake) afraid of them when learning. If you were flying a passenger jet on the other hand ... but you'd have already made your mistakes in training hopefully! :)

PS: For what it's worth, I bought a Linux magazine about a dozen or more years ago that had some OS on a disk (Knoppix) which I tried. It or I royally screwed up my machine so didn't touch Linux again for some years. That is the only Linux mag I've ever bought and only read the bits that were relevant to checking out Knoppix (and perhaps not very well!).

---

### Post by wireman67 on 2016-11-20
> **mörgæs said:**
> The Radeon 4650 graphics card is from 2008-9 so your gear is only semi-old. I agree, you have a useful computer for many years to come.
 
I purchased the computer in 2001 from a co-worker's friend whom built it in early 2001.  I remember updating the graphics card and MOBO because I had a major crash in 2008, but I didn't make the changes until 2009.  I upgraded the graphics card, I had help from a vendor at the Computer Show who swapped the MOBO for me.  Believe me I am happy this computer is running and I am learning.  Thank you for your responses.

---

