---
title: "What do you recommend wich ubuntu flavour i should install"
date: 2023-10-03
forum: New to Ubuntu
---

### Post by itsjustme12345 on 2023-10-03
Hi everyone :) I have been a microsoft windows guy a very long time but i always hated windows there is always something that just messes up the computer. I just recently found out about linux and i just love it its awesome compared to windows. But because i have a very old computer 10+ years its hard and confusing for me to know wich distro to install with this architecture to know wich i should install to make it work. 

 i have been using ubuntu mate now for a while but im thinking of chaning to another ubuntu flavour like lubuntu or xubuntu. I was hoping maybe you professionals could tell me wich to install so it works smoothly with my old graphic card and processor. Im not sure if this is something this forum can do then i apologize. 

i just must say this about UEFI is really confusing. i have checked if got it but it says i dont  got  UEFI. All the install guides ive been reading is all about UEFI... i am kinda lost when installing because i am very new to linux and i am still learning alll the time. I just want my computer to work and go smoothly.  

And one more thing when installing a new distro all guiedes says to have a swap, home and root or something like that. . but when i just click on normal install and then im done and i am in to my computer i dont got home then. I dont dare to try partion because i dont want my computer to just crash and never work again. i took a screen shot for ya. 

i have recently bought a SSD and some ram memory and upgraded the computer.  

here is a inxi report :) what i read inxi -f was the one to tell everything about the computer. i may be wrong then i apologize. if ya need more then i will gladly do so. 
```

System:
  Host: johndoe6 Kernel: 6.2.0-33-generic x86_64 bits: 64
    Desktop: MATE 1.26.0 Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: eMachines product: eME642G v: V2.14
    serial: LXNB902016041542DF1601
  Mobo: eMachines model: HM53_DN serial: LXNB902016041542DF1601
    BIOS: eMachines v: 2.14 date: 07/27/2011
Battery:
  ID-1: BAT1 charge: 0.8 Wh (100.0%) condition: 0.8/47.5 Wh (1.7%)
CPU:
  Info: dual core model: AMD Athlon II P320 bits: 64 type: MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 800 min/max: 800/2100 cores: 1: 800 2: 800
Graphics:
  Device-1: AMD Park [Mobility Radeon HD 5430/5450/5470] driver: radeon
    v: kernel
  Device-2: Chicony 1.3M Webcam type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: gpu: radeon
    note:  X driver n/a resolution: 1366x768~60Hz
  OpenGL: renderer: AMD CEDAR (DRM 2.50.0 / 6.2.0-33-generic LLVM 15.0.7)
    v: 4.5 Mesa 23.0.4-0ubuntu1~22.04.1
Audio:
  Device-1: AMD SBx00 Azalia driver: snd_hda_intel
  Device-2: AMD Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k6.2.0-33-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Broadcom NetLink BCM57780 Gigabit Ethernet PCIe driver: tg3
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: 1c:75:08:12:83:bf
  Device-2: Broadcom BCM43225 802.11b/g/n driver: bcma-pci-bridge
  IF-ID-1: wlp8s0b1 state: down mac: 18:f4:6a:50:15:0e
Drives:
  Local Storage: total: 223.57 GiB used: 26.76 GiB (12.0%)
  ID-1: /dev/sda vendor: Kingston model: SA400S37240G size: 223.57 GiB
Partition:
  ID-1: / size: 218.51 GiB used: 26.76 GiB (12.2%) fs: ext4 dev: /dev/sda3
  ID-2: /boot/efi size: 512 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 49.5 C mobo: N/A gpu: radeon temp: 45.5 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 215 Uptime: 2h 18m Memory: 5.77 GiB used: 2.57 GiB (44.4%)
  Shell: Bash inxi: 3.3.13
```

i have done a hardinfo report too

---

### Post by ActionParsnip on 2023-10-03
Any you like. You have enough horsepower to run any Ubuntu release you desire

---

### Post by guiverc on 2023-10-03
I'm not familiar with your CPU & not much of I'll say will be based on your hardware.

I perform QA for some Ubuntu *flavors* (*one in particular*), and in most cases, given all *flavors* use the same Ubuntu base, most issues impact all of them.

As  for graphics, they do tend to be impacted a little differently as  regards older GPUs, but each GPU is unique & thus what I'll provide  won't apply to all cards.

I generally experience issues first  with older GPUs with GNOME (Ubuntu Desktop) first, KDE (Kubuntu) next,  then MATE (Ubuntu-MATE).  The last impacted *flavors* will almost  always be either LXQt (Lubuntu) or Xfce (Xubuntu); and most recently  (5.19 & later kernel stacks) I've had least issues actually in  Xfce/Xubuntu  (though at 5.3 it was LXQt/Lubuntu being last impacted,  Xubuntu earlier at 5.0); either way usually Lubuntu & Xubuntu are  last impacted.

I did note AMD CEDAR, & some radeon numbers  that remind me rather closely with a cedar radeon card I've added to the  box I'm using currently (*it's my second GPU, being salvaged from my prior PC which was a 2008 dell; I don't recall where I'd use it before then either*), alas the *numbers* differed slightly.

With regards radeon cards; I've experienced differences between actual AMD made cards, and other *clones* using the chipsets (*both AMD & NVidia sell chips for others to make cards with*), but the details read by `inxi` & like tools show only the chipset details & thus do not provide the full picture (*ie. no clues as to if a better or cheaper card using the chips*).

**Desktop, libraries & toolkit**

As for desktops; two key things to consider are

- how much RAM & resources your machine has
- your tastes (*what will make you happy!*)

Key  is what you'll use the machine for; and what apps you'll want to run.  Those apps will use specific toolkits/libraries, and for best  performance, you want the apps to use the same libs/toolkits as used by  the desktop, otherwise you're wasting RAM & CPU will be required to  take extra *cycles* (*who cares if your CPU is newer enough & will sit idle, but on older slower hardware it may feel slower*).

Lubuntu uses LXQt which is a Qt5 desktop, thus will perform best using Qt5 apps. 

Xubuntu  uses Xfce which is a GTK desktop, mostly GTK3 but the GTK4 port is  getting real close (Xfce was much slower to port to GTK3 (from GTK2)  than MATE, but Xfce is ahead of MATE when it comes to GTK4)

If you're going to use Qt5 apps, then Lubuntu will be best (*as for performance; I'm ignoring tastes*).   If you're using GTK apps, you'll find Xfce/Xubuntu will outperform  LXQt/Lubuntu as the desktop & apps can share resources.  If you've  plenty of RAM the different fades to insignificance anyway, and you can  worry more about tastes.

I may also consider age of stack (ie.  release), as some newer GTK apps for newer releases will be GTK4, and  thus an older GTK3 desktop will lose ground there too.. ie. this  decision is getting somewhat 'messy' (esp. if you're not technical  background)

Another minor issue (*this I tend to ignore, but it's there*),  LXQt I mentioned (Lubuntu) doesn't require KF5 (KDE Frameworks 5), but a  very large proportional of  Qt5 apps are written for KDE (a Qt5 desktop  that also uses KF5) meaning many Qt5 apps can use more resources than  other Qt5 apps..

Until late 2022, my *primary* PC was a 2009 dell (*alas it died, my secondary PC is still a 2008 dell though*), and for me, I have more disk space than RAM, thus I worry most about RAM.  I *'bloat'*  my systems with multiple desktops, meaning I can decide how I interact  with them when I login. One benefit of this is I can select which will  perform best for me when I login based on what I'll actually do.. as  what I worry about most is what's in my RAM.  I don't care that my extra  '*bloated*' system uses more disk space, and more bandwidth to  upgrade, just the performance when I'll use it. I still use some really  old boxes (*single core 1GB RAM*) where I'm more careful with what's sharing RAM on rare occasion too.  ie. there are always alternatives !

**Swap**

Yes SWAP can make a huge difference, esp. if RAM is tight (*less than 5GB I consider tight, though I worry most when <4GB**, and get serious if <=2GB*). If installing though, I'd just use defaults & adjust if I considered it a problem.

**uEFI**

When  it comes to uEFI; I'd not worry.  If you write the ISO correctly to  your install media; install the system, it'll work out what is  correct/best for you anyway. In QA I install test on old legacy boxes (*the oldest box I installed to today was a 2005 HP*),  more modern uEFI, and Secure-Boot Secure-uEFI is also tested. I'll use  the same thumb-drive for testing all & it'll work; the installer  will create an ESP (EFI System Partition) when it needs to (*some  installers do it anyway for all installs; but older pre-uEFI systems  don't know what do to with it, thus ignore it; its tiny so ignore it*).

**Partitioning**

When  it comes to partitioning and a Ubuntu Desktop system, keeping it  simplier works. You can non-destructively re-install a Ubuntu desktop  (& it's easier with *flavors*) even if using a single partition. I have systems here I don't apply upgrades to, but do *weekly* re-installs of them for QA testing purposes using the *daily*  images, as it achieves my upgrades of packages at the same time  completes a QA test of an unreleased product (22.04.4 for 24.04, or *mantic* for 23.10). I check my music & other files are still there (*the non-destructive re-install has failed if my files are erased*), plus my additional apps (*those I added post-install*) also got auto-reinstalled too, on using only a single partition (*excluding ESP if required*). Partitioning is optional for Ubuntu Desktop installs.

If  however I wanted to be able to move away from a Ubuntu system, then yes  I'd separate the /home partition, as not all OSes can re-install  (*non-destructively*) without separating data & system via partitions;  but only you'll know if you'll want this available. Simple systems are  usually easier to maintain (*splitting into many partitions means you have more partitions to watch to ensure they don't fill as re-sizing is a pain!*).

---

### Post by The Cog on 2023-10-03
I suggest you download a few installer ISOs and try them out live. Half an hour each is easily enough to get a feel for how they look and behave. Some you may love, some you may hate. But after trying them live (they will be slow running off USB so don't judge them on that), you should have a good idea which you prefer. It's a very personal matter of taste, really.

---

### Post by itsjustme12345 on 2023-10-03
Hmm okey. Well I forgot to say write something. After a while my computer has been on for a few hours or so it gets very warm and it starts to lag and freeze. And I even got that thing under my computer that should cool it down. Plus I have tlp installed too and stacer

---

### Post by Rubi1200 on 2023-10-03
Hi and welcome to the forums :-)

My advice is to stick with LTS (long-term support) releases for more security and stability.

Separate swap partitions are, more or less, a thing of the past. Nowadays most distros create a swap file. Whether you want/need a separate /home partition tends to be a matter of personal preference.

I don't use one but some people prefer to keep system and personal separate.

As ActionParnsip mentioned, you can run any version/flavor. My personal favorites are MATE and Xubuntu.

Try them all and see which one you like the best.

---

### Post by mikewhatever on 2023-10-03
Ubuntu Mate 22.04 is a good choice for an old 2010 PC. I doubt Xubuntu or Lubuntu will work any better.
UEFI is probably irrelevant in this case, anyway, the installer should auto-handle it.
There is no need to have "swap, home and root or something like that..". Some guides, not all, recommend it, but the automated installer does a good job as well, so what you have now is good.
Lastly, about it running smoothly, are there any serious problems? It should work reasonably well, but not break any records, given its age and limitations.

---

### Post by TheFu on 2023-10-03
> **mikewhatever said:**
> Ubuntu Mate 22.04 is a good choice for an old 2010 PC. I doubt Xubuntu or Lubuntu will work any better.
UEFI is probably irrelevant in this case, anyway, the installer should auto-handle it.
There is no need to have "swap, home and root or something like that..". Some guides, not all, recommend it, but the automated installer does a good job as well, so what you have now is good.
Lastly, about it running smoothly, are there any serious problems? It should work reasonably well, but not break any records, given its age and limitations.

I agree with this.

Mate 22.04 will be fine.  Or Xubuntu 22.04. 

Most complex partitioning matters only for maintenance and future upgrade ease, but it may not be worth the effort if you don't really care about that.  

You can run 22.04 until mid-late 2024, since Mate gets 3 yrs of support, but you will need to upgrade or fresh install 24.04 at some point.  Most desktops (DEs) have 3 yrs of support for their LTS releases, so you can't wait 4 yrs and do every other LTS.  If you don't understand "LTS" - look up what that means for ubuntu in general and for Ubuntu-Mate specifically.  As an end user, you don't want to run non-LTS versions at all.

For a desktop system, I'd force swap to be 4.1GB in size.  It is most important for systems with less than 16GB of RAM and becomes more and more important as 8G and less RAM is available.  Looks like your system has 6GB with some of that stolen for the GPU to use. That's pretty normal.

[LIST]
[*]For example, the reason to have a separate /home partition is to make OS upgrades less risky.
[*]The reason to setup separate data partitions is to keep backups a little cleaner.  I typically backup at the partition level, so I want to ensure I get the place with HOME and data backed up and don't usually worry too much about backing up installed programs. That's because I strive to install only programs in the main Canonical repos and those can be re-installed very easily by just keeping a list of installed packages.
[*]The reason to have a separate /var partition is to aid system stability so when /var fills up, it doesn't crash the entire OS.
[*]The reason to have a separate /tmp partition is for system security.  Mount options used for /home and /  and /var aren't as secure as they can be, but permissions usually provide enough protection. If a hacker breaks into your system, they will try to do things under /tmp/ usually ... so having more secure mount options there can be good.
[/LIST]
But all those different partitions aren't mandatory. They are choices. Typical end-users won't really need to worry about all that ... except having swap sized right.

---

### Post by itsjustme12345 on 2023-10-03
Hi everyone I'm sorry for taking so long to answer. I have been very busy reading and trying to get it right. 

I want to thank you all for your answers I really appreciate it. 

First of all I really like Ubuntu mate i didn't really want to change I didn't think I had a choice
Well ever since I wrote this I have been reading all your answer and other sites. 

So I decided to reinstall ubuntu mate  22.04.3 but it wouldn't work I got stuck in the bios it just stood there forever it never ends. 
And when I was on that version 22.04.3 it was just laggy and slow for me. I don't know why. 

But because I like Ubuntu mate I thought I could try to install the version before this so I downloaded that 20.04.6  LTS  just to see what happened 
and it actually went very smoothly and very fast. So I am very happy now :)

But I got a question for you professionals that knows Ubuntu mate well. Is there something special I need to do because I think this version is not supported anymore ?
But I have read about people on sites that are using very old versions of all kind of disrots so I figure it wouldn't do any harm. At least I got what I wanted :)

After been using this Ubuntu mate now for a while I must say it's alot better and smoother then the new one for me. I don't know why but it feels alot better for me.

One thing that you maybe can help me with its thats the system really like to send me that "there is a upgrade do you want to upgrade" kinda alot. And even when I have gone to "software and updates" in "updates" section and changed the "notify me of a new Ubuntu version" to
Never. I still get the pop ups..

---

### Post by guiverc on 2023-10-03
> **itsjustme12345 said:**
> But I got a question for you professionals that knows Ubuntu mate well. Is there something special I need to do because I think this version is not supported anymore ?
But I have read about people on sites that are using very old versions of all kind of disrots so I figure it wouldn't do any harm. At least I got what I wanted :)

After been using this Ubuntu mate now for a while I must say it's alot better and smoother then the new one for me. I don't know why but it feels alot better for me.

One thing that you maybe can help me with its thats the system really like to send me that "there is a upgrade do you want to upgrade" kinda alot. And even when I have gone to "software and updates" in "updates" section and changed the "notify me of a new Ubuntu version" to
Never. I still get the pop ups..

Yes all Ubuntu 20.04 LTS Desktop *flavors* which includes Ubuntu-MATE 20.04 LTS are EOL.

An official notice for Ubuntu-MATE 20.04 can be read here - [https://ubuntu-mate.community/t/ubuntu-mate-20-04-lts-reaches-end-of-life/26477](https://ubuntu-mate.community/t/ubuntu-mate-20-04-lts-reaches-end-of-life/26477) which states

> As of 30 April 2023 Ubuntu MATE 20.04 LTS has reached EOL (End of Life) and is no longer supported.


 Being a long term release (LTS), official Ubuntu flavors are only supported for **3 years**,  as opposed to Ubuntu's 5 years. This means MATE components of your  system will no longer receive updates after today, but foundational  components will continue to receive security updates from Ubuntu.



I'll refer to one I posted with [Lubuntu 20.04 LTS here]("https://discourse.lubuntu.me/t/lubuntu-20-04-lts-is-end-of-life/4190") which suggests exploring what this means via use of `ubuntu-security-status`which can show which parts of your system will still receive *security fixes*, or upgrades.

The repositories for 20.04 or *focal* will remain open until 2025-April (*at least!*) meaning any bug reports made, can still be fixed/patched by anyone with upload rights (MOTU, Core Dev etc) however that is no longer guaranteed to be done after 2023-April (3 years for 'universe' packages), only 'main' (5 years guarantee applies there).

How *risky* that is to you is for you to decide.  I do have 20.04 boxes here still, and my preference is *flavors*, though those are not my main boxes or boxes I'll use for things I consider *critical* (especially with regard security; online payments etc).

I'm not sure which upgrade message you asked about; if it's a *release-upgrade* message, you can stop that by changing the notification level to *'never*', but that also will prevent you from receiving EOL/EOSS notices when they come out early 2025 (*warnings come out in advance of the EOSS so you've time to plan ahead*).

FYI:  The HWE kernel stack for Ubuntu 20.04 LTS (5.15) is also the GA kernel stack for Ubuntu 22.04 LTS (5.15), thus if 20.04 with HWE is *stable*, I'd usually expect the 22.04 to also be *stable* IF you used GA kernel stack  (*easily found media downloaded today will be the latest using HWE, but GA media still exists*).  *go beyond just the release details in your comparisons*

---

### Post by TheFu on 2023-10-03
Mate 20.04 support ended. You shouldn't use it.  I'm trying to keep this answer simple.  Anyone asking the question probably would miss the subtle aspects of every slightly different gray answer that's possible.

An option would be to try an upgrade from 20.04 --> 22.04, but I suspect that will fail, because so many packages aren't current anymore.  But sometimes upgrades work when a new install doesn't.
[LIST]
[*]Patch what you can with 20.04.
[*]Backup whatever you don't want to loose.
[*]do-release-upgrade
[*]Hope for the best. Expect the worst.
[/LIST]

Unrelated to this question, but the flagship "Ubuntu Desktop, which has been Gnome-based for some time now, has 5 yrs of support.  If you want to see how bad your system is for support and non-supported packages, there's a command that will show this information.  Don't worry about the scare/FUD tactics in the output.  Canonical wants to connect installs to humans for some reason ... and to make money.  For a home user, the ESM program would probably be free like the "Ubuntu Pro" is (currently).

On one of my 20.04 systems:
```
$ ubuntu-security-status 
This command has been replaced with 'pro security-status'.
1711 packages installed:
     1294 packages from Ubuntu Main/Restricted repository
     383 packages from Ubuntu Universe/Multiverse repository
     28 packages from third parties
     6 packages no longer available for download
```

In general, the more GUI programs installed, the more likely they won't be getting priority support.

---

### Post by poorguy on 2023-10-03
**@itsjustme12345**

I'm not one of the forum professionals just another user.

 I have Lubuntu 22.04 installed on a 2010 Dell desktop with a dual core processor, integrated graphics adapter, 4.0 GB of memory and a mechanical hard drive.

Lubuntu 22.04 runs well on this 13 year desktop OOTB.

I suggest installing it and give it a try and see how it runs.

[https://lubuntu.me/](https://lubuntu.me/)

---

### Post by TheFu on 2023-10-09
> **ActionParsnip said:**
> Any you like. You have enough horsepower to run any Ubuntu release you desire

I decided to look more closely at the CPU.  That specific Athlon only has 630 passmarks. There are chromebooks with 3x the CPU. In 2012, I had a $200 new Chromebook with 20% higher passmark ratings. Just sayin'. It was never a powerhouse.

Stick with Lubuntu or Xubuntu, but if you are happy with Ubuntu-Mate, it won't be terrible, but not great.  If it were me, I'd use either Lubuntu or Xubuntu, depending on which toolkit applications I preferred.

Lubuntu for KDE/Qt applications.
Xubuntu for Gnome/GTK+ applications.

As you advance, you could remove the bloat that a DE brings and go lighter, but I wouldn't suggest that to anyone new.

---

