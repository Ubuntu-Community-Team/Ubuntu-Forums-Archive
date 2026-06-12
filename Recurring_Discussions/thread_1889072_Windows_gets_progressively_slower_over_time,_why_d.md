---
title: "Windows gets progressively slower over time, why doesn't Ubuntu?"
date: 2011-11-30
forum: Recurring Discussions
---

### Post by williamtdr on 2011-11-30
I, and many other previous Windows users notice that the computer seems to get progressively slower over time. I bought a leapfrog crammer only to find it installed process that sat there waiting for me to plug the crammer in so it could run the software. It took up three percent of the CPU twenty-four seven, seven day a week! This is one of the main reasons I left Windows. But, Ubuntu doesn't seem to slow down over time at all. Does Ubuntu allow programs to install background programs like the leapfrog crammer did to sit there like a leech and suck away at resources? Could someone explain why Windows tends to get slower over time, and is Ubuntu vulnrable to this too? Thanks for any help, this is puzzling me.

---

### Post by 3Miro on 2011-11-30
If you install random stuff off the Internet, you can get any kind of garbage on your machine. In Ubuntu you have the Software Center that is clean from such stuff.

In Windows you can get pretty bad fragmentation, in Ubuntu things fragment, but unless you fill up your entire HDD, things will never get bad.

Windows programs are also dependent on the Windows registry that can get corrupt and/or bloated over time. Ubuntu has no registry, the few things that seem similar to the registry (like the apt database and gconf) are in fact very different or have very small impact.

---

### Post by sdowney717 on 2011-11-30
I agree, it is the Windows registry causing slowdowns. This is a database for the Os which it has to look thru all the time. Gladly linux does not have this problem. You get major registry errors and windows goes dead. And windows is programmed to your hardware, so try to switch the OS to new hardware and you get the error message about damage to your PC. But really what MS means is damage to their earnings.

---

### Post by jwbrase on 2011-11-30
> **williamtdr said:**
> I, and many other previous Windows users notice that the computer seems to get progressively slower over time. I bought a leapfrog crammer only to find it installed process that sat there waiting for me to plug the crammer in so it could run the software. It took up three percent of the CPU twenty-four seven, seven day a week! This is one of the main reasons I left Windows. But, Ubuntu doesn't seem to slow down over time at all. Does Ubuntu allow programs to install background programs like the leapfrog crammer did to sit there like a leech and suck away at resources?

While Windows does have problems with slowing down over time, this particular problem sounds like more of an issue with the software for this "leapfrog crammer" than anything, and could affect any operating system that allows you to setup programs that are run at startup (which is a very useful feature included in most or all modern operating systems, but can cause problems).

It sounds like you installed the software intentionally (though without full knowledge of what would be installed). Modern OS's are good at preventing software from installing when you didn't intend any installation to happen, but, when you tell the OS that it's OK for something to be installed, it has no way of knowing whether the software is buggy or badly written or whether it was written to do things you weren't expecting. 

To me, it sounds like the software for this "leapfrog crammer" was badly written. 

Normally, when you write software that waits to take action when a hardware event happens (like a mouse click, or something being plugged in), you write it so that it tells the OS something like "I'm going to sleep. Wake me up when something gets plugged in so I can see if it's the device I'm waiting for." When you do this, the program just ends up sitting on the process list using absolutely no CPU until something is actually plugged in.

What it sounds like the developers for this "leapfrog crammer" did was write their software so that it tells the OS "I'm going to sleep. Set an alarm and wake me up in a tenth of a second so I can check and see if my device has been plugged in." So the operating system is waking the program up 10 times a second (or however often the program is asking to be woken up), and the program is seeing that its device isn't plugged in yet, and is going right back to sleep on each wakeup. Doing this 10 times a second or so will probably result in a noticeable CPU load (such as your 3 percent, 24/7).

> Could someone explain why Windows tends to get slower over time, and is Ubuntu vulnrable to this too? Thanks for any help, this is puzzling me.

It's vulnerable to some of the things that cause Windows to slow down and not to others.

It's *not* vulnerable to the slowdowns that come from the Windows registry.

It *is* vulnerable to poorly written programs that run on startup, or the user simply having too many startup programs, because running programs on startup is a useful feature and not having it would cause its own problems.

---

### Post by wolfen69 on 2011-11-30
I've gotten more repair jobs from people's windows machine slowing down than any other problem. No problem here.

---

### Post by mamamia88 on 2011-12-01
When you uninstall a lot of programs etc stuff is left behind that slows down the computer.  Also, when you install programs you have to be careful to uncheck certain boxes so it doesn't install crap you don't want.   If you know what you are doing IE don't install software you don't need. Avoid malware etc.  Defrag and cccleaner occasionaly there is really no reason it should slow down. Of course I hate doing all that stuff and it's annoying.

---

### Post by kio_http on 2011-12-01
I'll be fair here, I have used Ubuntu and Windows for a very long time. All the NT based OS's are quite good actually if the user is smart enough. Startup antivirus scans and all the software that you install for startup slows down the system. If you install and use Windows sensibly it does not get slow over time. 

I have a system running XP since 2001 and it still runs fast.

---

### Post by Basher101 on 2011-12-01
> **kio_http said:**
> I'll be fair here, I have used Ubuntu and Windows for a very long time. All the NT based OS's are quite good actually if the user is smart enough. Startup antivirus scans and all the software that you install for startup slows down the system. If you install and use Windows sensibly it does not get slow over time. 

I have a system running XP since 2001 and it still runs fast.

sure, if you really mean it you can make it even run alot faster than usual...but..thing is, in ubuntu this "maintainance" is incredibly easier and alot less time consuming..

---

### Post by kio_http on 2011-12-01
> **Basher101 said:**
> sure, if you really mean it you can make it even run alot faster than usual...but..thing is, in ubuntu this "maintainance" is incredibly easier and alot less time consuming..
I agree, but I was trying to point out that unlike what the title states, Windows does not get slower on its own.

---

### Post by Chame_Wizard on 2011-12-02
Tux is just awesome.:popcorn:

---

### Post by screaminj3sus on 2011-12-04
> **williamtdr said:**
> I, and many other previous Windows users notice that the computer seems to get progressively slower over time. I bought a leapfrog crammer only to find it installed process that sat there waiting for me to plug the crammer in so it could run the software. It took up three percent of the CPU twenty-four seven, seven day a week! This is one of the main reasons I left Windows. But, Ubuntu doesn't seem to slow down over time at all. Does Ubuntu allow programs to install background programs like the leapfrog crammer did to sit there like a leech and suck away at resources? Could someone explain why Windows tends to get slower over time, and is Ubuntu vulnrable to this too? Thanks for any help, this is puzzling me.
Its a myth that windows just magically slows down over time. Windows slows down when you install a bunch of crap on it. If you bloat your ubuntu install with tons of software, and have tons of programs startup automatically at boot it will slow down too. 

The main difference is two things: Its harder to do this in linux/ubuntu. There is practically no "crapware" since all the software we get is from the repos, its not nearly as common for apps to add themselves to startup at boot like most windows apps do ect.. The other factor is ubuntu is easier to maintain. Apps uninstall cleaner, you don't need to defrag ect.. (but at the same time, posters in this thread are ridiculously exaggerationg how much maintenence windows needs. Fragmentation has hardly been an issue since windows vista, hell it hasn't been a big issue since fat32)

I run win7 on my desktop (linux on my laptop) I have no problem with my windows install slowing down, I've had no speed issues with win7, and no slowdown over time. Because I keep my system clean, don't install things I don't need, and disable every non essential startup item. Thats all the maintenence windows needs, it handles defragging automatically and its nota big issue with ntfs anyway. When it comes down to it, its always 98% the user's fault for this "slowdown over time"

---

### Post by PhilGil on 2011-12-04
> **screaminj3sus said:**
> Desktop: Windows 7 x64 | Intel Core i5-2500 | 8 GB DDR3 | ATI 6850 | 64gb Vertex 2/320gb/750/750 hdd
I'm shocked, shocked I tell you, that Windows hasn't slowed down on your year old desktop with an i5, SSD boot drive, 8GB of RAM and high-end video card :lolflag:

Nevertheless, you're right. 90% of the poor performance people see on Windows boxes is the software they install, not the OS itself. Windows developers seem to think that their users have an unlimited supply of RAM, and that their program is so important that it must be loaded at boot.

The registry is still be a problem, though. What a unholy mess that can get to be.

---

### Post by *^kyfds( on 2011-12-04
> **PhilGil said:**
> 
90% of the poor performance people see on Windows boxes is the software they install, not the OS itself.

The registry is still be a problem, though. What a unholy mess that can get to be.

there are also viruses, too.
 
a relative of mine (he was about 11 years old at the time) had been compaining that his computer was running incredibly slowly.

after having a quick look, it turned out that he had been torrenting -** literally** -  tonnes and tonnes of programs, ranging from video editors to games.
he'd even installed **bus simulator**.

i ran a scan of malwarebyte's anti malware, and the results showed why his PC was running so slowly.

**he had over 2,000 infected objects on his computer.**

it took over 4 hours to scan and remove them all.

---

### Post by neu5eeCh on 2011-12-04
> **PhilGil said:**
> Nevertheless, you're right. 90% of the poor performance people see on Windows boxes is the software they install, not the OS itself. 

I disagree. Strongly. This is a question I've also asked at this forum, a couple years ago, and never got an answer. And that's ok, because I don't think anyone here really knows Windows all that well - or at least they're not talking.

The evidence is this: I bought my wife a netbook with XP pre-installed. My wife used only two pieces of software: Chrome and Works. The Netbook came with a 16G SSD. Within two to four months, without installing any other software, XP had slowed to a crawl and filled up the HD. I thought she or I had done something wrong. I scrubbed the HD and reinstalled XP, Works and Chrome. Within 2 to 4 months XP had slowed to a crawl and the HD was full - my wife had not installed any software and used a USB key for storage. This pattern repeated itself a third time and that's when she finally relented and let me install Linux Mint, based on 9.04. That was almost three years ago. Linux Mint hasn't taken up one iota of extra space, has never been reinstalled, and is running as smoothly and quickly as the day I installed it. She. Loves. Linux.

I can attest to the same issue on my workmate's computer using Vista. Windows progressively bloats, needs more and more HD space, and slows down. I put Xubuntu on a second partition and he tells me that he can't remember the last time he used Windows.

I don't know what Windows does or is doing, but I'm sure  I could reproduce this problem on any computer. It's the OS itself. Windows 7 went from requiring 8G of space, when I first partitioned my 64bit laptop, to 45G later.

---

### Post by BC59 on 2011-12-04
Assuming all the above, the magical slowdown of Windows occurs for 3 main reasons:

1. The NTFS file system needs frequently defragmentation.

2. The registry is getting oversized after some time.

3. Every new program installed, is trying to get to the autostart. 

Of course there are other reasons as well, like viruses, malware etc.

---

### Post by screaminj3sus on 2011-12-04
> **PhilGil said:**
> I'm shocked, shocked I tell you, that Windows hasn't slowed down on your year old desktop with an i5, SSD boot drive, 8GB of RAM and high-end video card :lolflag:

Nevertheless, you're right. 90% of the poor performance people see on Windows boxes is the software they install, not the OS itself. Windows developers seem to think that their users have an unlimited supply of RAM, and that their program is so important that it must be loaded at boot.

The registry is still be a problem, though. What a unholy mess that can get to be.

lol :) I do have more computers than is shown in my sig though, including:
My old laptop: 2ghz core 2 duo, 4gb ddr2, 250gb hdd, win7 64 bit. Win7 installed on it since the day it was released (laptop originally ran vista)

My dad's computer: 3GHz P4, 2gb ddr2, 160gb hdd, 9600gt. Dell desktop that's probably about 6 years old, upgraded slightly with spare parts. Upgraded to win7 64 bit from xp when it was released and its been running smooth ever since.

I had also been running win7 since release on the desktop in my sig and it was still running great, but I happened to rebuild it recently so I had to reinstall.


> **BC59 said:**
> Assuming all the above, the magical slowdown of Windows occurs for 3 main reasons:

1. The NTFS file system needs frequently defragmentation.

2. The registry is getting oversized after some time.

3. Every new program installed, is trying to get to the autostart. 

Of course there are other reasons as well, like viruses, malware etc.

People are really overstating fragmentation and the registry as causes of windows slowdown. The truth is you have to have really high levels of fragmentation to have it noticeably effect performance. Since windows vista NTFS can handle some fragmentation issues itself, and windows defrags automatically once a week when the computer is idle. You have to try pretty hard to have your windows system so fragmented that its slowing down. Fragmentation was a big issue in the FAT32 days, but not anymore. Defragging once a week may seem "frequent" if you are used to linux filesystems, but windows does it automatically and in an unobtrusive way.

Same with the registry, you have to have a REALLY f'd up and bloated registry to have it actually effect performance. And if you get all technical the registry is faster than using flat configuration files. Of course many programs/malware and such can misuse and abuse the registry, but its rarely a cause of performance issues unless the system is horribly maintained and abused. In the end it mainly comes down to the user.

3rd party defragging, registry cleaning, and other "system maintenence" software for windows is largely pointless. Just keep your system clean and let windows handle the rest.

---

### Post by inobe on 2011-12-04
> **kio_http said:**
> I'll be fair here, I have used Ubuntu and Windows for a very long time. All the NT based OS's are quite good actually if the user is smart enough. Startup antivirus scans and all the software that you install for startup slows down the system. If you install and use Windows sensibly it does not get slow over time. 

I have a system running XP since 2001 and it still runs fast.

the trick is simple, don't go off on the freeware binge.

install the os.

install needed apps and drivers, take care of that fragmented drive.

setup limited user accounts, group policy etc..

leave it be, or do what everyone does, run as administrator, spend lots of time in hjt forums, going to the restroom after starting the system, only to come back to see it's still booting.

going on a freeware rampage, uninstalling, re installing, completely causing havoc upon an insecure system, error messages all the time, rootkits, malware laden systems connected to other insecure systems, now the sky is falling, madness and mayhem abroad.

my eyes popped out of their sockets, i'm done here:P

---

