---
title: "A newbie's Q: Windows vs ubuntu boot time"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by suphavitp on 2014-01-19
Hey Ubuntu community,
I am a regular window7 user who recently migrated to Ubuntu (dual-boot). I noticed a huge difference between boot time, counting from os selection on  Grub. Even though I regularly defragment my HDD and make sure that crapwares do not make their way into start-up application list. Can somebody tell me why is that?

Also, is an anti-virus software/defregmentation necessary in Ubuntu?

---

### Post by carl4926 on 2014-01-19
To be honest
Between a clean install of windows 7 and most Linux distros, there isn't much in it.

No defrag required on Linux file systems
No anti-virus either

Don't be surprised if they move this thread
Your questions have been asked a quazillion times

---

### Post by Bashing-om on 2014-01-20
suphavitp; Hi !

To add to carl4926's input; My primary OS is 13.10, and I boot in under 5 (yeah five) seconds from the time I push the power button.

Let's see Windows beat that !
In my humblest opinion; -> ubuntu
[INDENT][INDENT][INDENT]The greatest operating system the world has ever known
[/INDENT][/INDENT][/INDENT]

---

### Post by fosterD on 2014-01-20
In my own opinions, booting times between a plain-fresh-installed Windows and a Ubuntu aren't much different. However, after a while (half year or so) Windows tends to take longer. 
One reason is, like you mentioned, loading unnecessary software 
Another matter is virus. Having an up-to-date Antivirus software doesn't necessarily mean the computer is completely free of virus

---

### Post by mastablasta on 2014-01-20
you can make it even faster if oyu optimize the OS to work only on your system. i.e. remove any modules you don't need etc. this is mudular system and since the soruce is open you can really create OS that will only owrk on your computer model, but will be super fast on boot etc.

i have this old mashcine 1,2Ghz Athlon, 224MB ram (32MB is taken by GPU). computer had windows XP and it even has a sticker on it being widnows XP  compatible. now as oyu porbably may know windows XP doesn't run anywhere near normal  with 512MB ram let alone 224MB. not to mention you need to load anti-virus software etc into that ram as well. the mashcine _**took 10 minutes just to boot **_(i timed it a coupel of times and on average it was 10 min). i threw first Ubuntu on it (at the time it was 10.04). it booted in about 45sec -1 minute, but after crtain update system got very slow.

i then replaced Ubuntu with Chrunchbang (debian based). it now boots in 30 secs or less (compared that to previous 10 minutes !!!). it has more or less latest software and can now easilly be used as a netbook (browsing videos, online chat etc...). it was unsuable with windowsxp. unlike in other users experience battery life here increased from 2 hour in windows to about 3 hour in linux. unfortunatelly baterry died now, monitor is cracking, the kid pulled some keys out and i broke them trying to stick them back in etc. i am thinkign it will make a nice file server one day...

---

### Post by slooksterpsv on 2014-01-20
Windows has a ton of services, some installed by updates, some installed by other programs (Google, iTunes, Safari, Antimalware, VPN, etc. etc. etc.); the registry becomes chuck full of empty useless junk that it needs to read through ever bootup - use Eusing Free Registry Cleaner to clean it up really thoroughly; FileSystem is still based on tables instead of nodes (see ext4 vs ntfs); Windowing elements in windows vista and 7 became heaver with the use of DWM for Aero (windows 8 removed Aero). Usually with Windows PCs if it's not spyware, viruses, rootkits, or any other type of malware gobbing it up, it's Apple Software (primarily)

Ubuntu has services, but not as many, plus the don't take up the same amount of resources like Windows does.

---

### Post by Gone fishing on 2014-01-20
Ubuntu is quite a quick OS to boot up, possibly a little quicker than a clean install of Windows. However there are OS that will boot up quicker, Haiku some of the more minimalist Linux distros etc. However, the real killer for Windows is winrot the fact that it gets slower and slower as time goes on, the more you've installed and uninstalled third party software etc - this doesn't happen with other OS (or at least to nothing like the same extent), it's a windows feature. It is likely that your Ubuntu install will be as fast in a year as it is now.  If you want a quick Windows - install windows, then install not more than a few other applications, including an Av and leave it alone other than to update, don't tweak, don't fiddle, don't try new software and you should be OK. 

Anti virus is more debatable, as far as I know there are no Ubuntu or Linux viruses for the desktop, circulating in the wild. However, you may choose to install an AV so that you can check files you are sharing with Windows users to help protect them. Commonly if you were running a Linux file server you would have an AV to check for Windows viruses so having an AV might help you become a good citizen rather than protect you. Obviously because Linux is largely free of the Virus problem this doesn&#8217;t mean you should engage in risky behaviour such as opening every dodgy attachments, running unknown scripts, or using your sudo privileges without thinking why am I doing this? And if you don&#8217;t know then don't do it.

---

### Post by Mark Phelps on 2014-01-20
I have four OSs installed on the same PC, two Linux distros, and two Windows versions -- and with the exception of Win8, they all boot within a few seconds of each other.  Win8 uses Fast Startup, which means really restarts from hibernation, so of course it will be the fastest.

There are guides out there for going into Windows startup and removing services and apps you don't need loaded at startup.

As to AV products delaying startup, I got rid of ESET AV years ago because it was searching for new AV versions of every boot, causing each one to take MINUTES, instead of Seconds. With Norton AV, I don't have that problem.

---

### Post by buzzingrobot on 2014-01-20
Windows loads services at startup.  So does Linux.  Disabling services you (are sure) you don't need can make a a little difference. I've tried several distributions recently and they all take 20-30 seconds to boot on the same hardware. It's not worth an investment of my time to tweak that, especially because I seldom reboot once setup is complete.

Linux users on a network with Windows machines should probably run an anti-virus to check Office files, mail, etc., so they don't unwittingly pass something along to the other folks. 

Linux malware exists, but your chances of coming across it are radically smaller than in Windows.  Whether running anti-malware software on a standalone Linux machine is more effective than simply being a smart net user must be answered by each individual.   I'd want to look at how often my Linux anti-malware software provided updates and how quickly it responded to any new threats, since there are so few it might be easy to become complacent.

As/if use of Linux in the mainstream increases, the threat from Linux malware will increase.

---

