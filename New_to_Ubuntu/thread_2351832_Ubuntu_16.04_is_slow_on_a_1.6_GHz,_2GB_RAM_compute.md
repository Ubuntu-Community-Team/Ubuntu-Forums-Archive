---
title: "Ubuntu 16.04 is slow on a 1.6 GHz, 2GB RAM computer"
date: 2017-02-07
forum: New to Ubuntu
---

### Post by simplex1 on 2017-02-07
[COLOR=#111111][FONT=Ubuntu]**Ubuntu 16.04 is slow on a 1.6 GHz, 2GB RAM computer. What can be done?**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I put the [32-bit PC (i386) desktop image of Ubuntu 16.04]("http://releases.ubuntu.com/16.04/") on a 16 GB USB stick, using Rufus. I set my 1.6 Ghz -32 bit, 2GB RAM laptop to boot from the stick, started the PC and after about 3 minutes I had a working Ubuntu on my computer (I have not installed it yet on the HDD).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Unfortunately, this Ubuntu 16.04 is terrible slow even for basic tasks like a single window opened, more precisely "Search Your Computer", where I write the word "terminal". The next letter appears at about 0.5 seconds after the previous one. So, it will take about 4 seconds just to type the string "terminal".[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Now, with Firefox opened, I can write this question faster than 0.5sec/letter but the editor is still 4-5 letters behind. This is, it continues to print the last 4-5 letters after the moment I finish writing the sentence.

Also, no matter what window I try to open, and even if the USB stick shows no activity, the reaction of Ubuntu is slow. For example, I have to wait like 0.5 seconds if I click on the upper right button that displays the list of Wi-Fi networks.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
QUESTION: Is it a fix for this or simply Ubuntu 16.04 requires a computer much more powerful, than mine, to run smoothly?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Note: I mention that the laptop runs Windows 7, 32 bit and it works smoothly.
[/FONT][/COLOR]

---

### Post by Perfect Storm on 2017-02-07
you'll properly want Lubuntu for this machine, it is lightweight compared to ubuntu: [http://lubuntu.net/](http://lubuntu.net/)
If it was a 64-bit machine I would have recommended elemetary OS as lightweight distro.

---

### Post by simplex1 on 2017-02-07
[COLOR=#666666][FONT=Ubuntu]I have found this: 
"*Lubuntu ...*[/FONT][/COLOR]*[COLOR=#666666][FONT=Ubuntu] is currently mainly developed by [/FONT][/COLOR][Julien Lavergne]("https://twitter.com/gilir")**.*[FONT=Ubuntu][COLOR=#666666]"[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=#666666]
Maybe I will try it but if a single man is behind the maintenance of an OS, I am afraid that despite being faster than Ubuntu 16.04 I will have a lot of troubles with [/COLOR][/FONT]*Lubuntu.*[FONT=Ubuntu][COLOR=#666666]
Anyway, if nothing can be done to speed up the 16.04 I will use it as it is because a slower OS with a lot of users is better than a faster one with not so many clients.  [/COLOR][/FONT]

---

### Post by Perfect Storm on 2017-02-07
The core behind Lubuntu is maintained by the Ubuntu developers.

---

### Post by Impavidus on 2017-02-07
That computer is underpowered for Ubuntu. You need a lighter flavour. You could try Xubuntu, but I think Lubuntu will be best. All Ubuntu flavours use the same core, software from the same sources. The difference is in the set of default applications, including the default desktop environment, which in Linux is just another application.

Running Ubuntu from a live usb is slower than as an installed system, so after installation it may be somewhat better. You may also have a problem with the graphics driver. Do you know the graphics hardware in that computer?

---

### Post by simplex1 on 2017-02-07
> *[COLOR=#000000]Do you know the graphics hardware in that computer?[/COLOR]*

The computer is an Acer Aspire One D270.

Its video card has the characteristics listed in the attached picture.

---

### Post by Autodave on 2017-02-07
Ubuntu uses a great deal of RAM to keep the desktop going. Xubuntu or Lubuntu would be way better alternatives.

---

### Post by ajgreeny on 2017-02-07
I am using Lubuntu 16.04 32bit on a netbook with an Atom single core N270 cpu @ 1600.00 MHz, Intel Mobile 945GSE Express Integrated Graphics Controller, and 1GB ram, so by no means a quick machine, but it runs very well for the uses to which I put it, and I also would thoroughly recommend it on your machine also.

If you search deeply I think you will see there is usually a single named person as the leader of the dev group for each OS, so don't get too worried about the commant "Lubuntu ... is currently mainly developed by Julien Lavergne." as it is of little importance in the real world.

Frankly, Ubuntu with the unity desktop will always be a non starter on your machine; Xubuntu may be another choice but Lubuntu will, or should be, the perfect fit.

---

### Post by mörgæs on 2017-02-07
Most parts of the Lubuntu distro, first of all the kernel and xorg, are shared with the other Buntus, as mentioned above. 

Development of the Lubuntu specific parts is done by Julien and a few other developers. It's so slow that it's close to a stand-still, which in many respects is a good thing: From release to release not much new functionality is added but bugs are fixed. This makes Lubuntu a very stable distro. 

As always: Test for yourself and don't judge only from what googling brings you.

---

### Post by simplex1 on 2017-02-07
I run a **free -m** command with Firefox and LibreOffice opened:

This is the result:

```
ubuntu@ubuntu:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           2002         772         129         103        1100         887
Swap:             0           0           0
```

There is one thing that I do not really understand. Why, in Search Your Computer (the upper left magenta button with Ubuntu symbol on it), the text appears so slowly. It is not 0.5 sec., as I said before, it is more than 1 second / letter. It looks like I have enough RAM memory.

---

### Post by leunam12 on 2017-02-07
I have used Lubuntu for a quite a few years without any problems, it is fast and lightweight. A minimal Arch Linux installation with LXDE and OpenBox (same configuration than Lubuntu) is also very fast and responsive but Arch is definitely not for beginners.

---

### Post by simplex1 on 2017-02-07
I run another command, in the same conditions as before, that gave more detailed results:

```
ubuntu@ubuntu:~$ cat /proc/meminfo
MemTotal:        2050680 kB
MemFree:          172104 kB
MemAvailable:     788704 kB
Buffers:          265728 kB
Cached:           657324 kB
SwapCached:            0 kB
Active:          1382124 kB
Inactive:         394992 kB
Active(anon):     904516 kB
Inactive(anon):    68608 kB
Active(file):     477608 kB
Inactive(file):   326384 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1172168 kB
HighFree:          54308 kB
LowTotal:         878512 kB
LowFree:          117796 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        854120 kB
Mapped:           292064 kB
Shmem:            119060 kB
Slab:              55712 kB
SReclaimable:      36500 kB
SUnreclaim:        19212 kB
KernelStack:        3968 kB
PageTables:        10276 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1025340 kB
Committed_AS:    4400320 kB
VmallocTotal:     122880 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
AnonHugePages:    421888 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       59384 kB
DirectMap2M:      854016 kB
```

As a note, the system requirements for Ubuntu 16.04 are: 2 GHz dual core processor or better, 2 GB system memory.

I am not so far from them with a 1.6 GHz processor and 2 GB RAM.

Also, it appears that I am on the wrong forum because most of the users here, or at least most of the user names, tell me to use Lubuntu.

The CPU and memory usage for my Acer Aspire One D270 computer running Ubuntu 16.04 (see the attached picture).

None of the 4 cores reached 100% and the memory is used 60%. So, Ubuntu with Firefox and LibreOffice running do not push the computer to its limits. It is not so evident why the PC is so slow.

---

### Post by howefield on 2017-02-07
Hello, please enclose terminal output in [noparse]```

```[/noparse] tags rather than use a non default font.

Not read all your thread, but the graphics card is likely to be more of a bottleneck than your cpu or memory footprint. Start putting some load on your machine and you'll most likely see it get a whole load worse as you start using swap space and the cpu toils.

---

### Post by pauljw on 2017-02-07
From what I see, your biggest problem is that you haven't actually installed the system.  Running from a usb stick is going to be noticeably slower than a hdd installation.  I would install lubuntu see how it goes.  I have an AspireOne D257 with 2G RAM and a 275G SSD running xubuntu 16.04 and it runs very well but can easily become overwhelmed if I try to run more than a couple of things at once.  I normally run firefox and hexchat and call it good.  :)

---

### Post by verymadpip on 2017-02-07
I run 64 bit Lubuntu 16.04 on an MSI U180 netbook, 1.6GHz Atom CPU (dual core, 4 threads); 2Gb RAM upgraded from 1Gb at very little cost.
It runs very well.  I can't ask much of the little machine but it does the things I want it to with no problems.
The graphics get a little laggy if I push t too hard, infinite window borders & the like for a moment or two.  Not a deal breaker for me.

---

### Post by martemarziano on 2017-02-07
Hi everyone,
I'm running Ubuntu Mate on a rather low spec machine, so if install the "Lubuntu Desktop Environment - minimal installation" would I get any benefit in terms of functionality? Would that almost amount to having installed Lubuntu from the start?

---

### Post by ajgreeny on 2017-02-07
> **martemarziano said:**
> Hi everyone,
I'm running Ubuntu Mate on a rather low spec machine, so if install the "Lubuntu Desktop Environment - minimal installation" would I get any benefit in terms of functionality? Would that almost amount to having installed Lubuntu from the start?
You can do that, certainly, and you will end up with both Lubuntu-core and Ubuntu-Mate installed together.

That should not be a major problem, but you will probably have a few duplicate applications, eg both gedit and leafpad as text editors.
I assume you are talking of the lubuntu-core package when you say "Lubuntu Desktop Environment - minimal installation"?

---

### Post by martemarziano on 2017-02-07
> **ajgreeny said:**
> 
I assume you are talking of the lubuntu-core package when you say "Lubuntu Desktop Environment - minimal installation"?

Thanks ajgreeny!
Yes, I mean lubuntu-core, sure. Sorry for taking a detour for saying the same thing. I think, I'll go for it then. I like actually lxde's rather minimalist approach. Any performance betterment is just a bonus.

---

### Post by HermanAB on 2017-02-07
Well, Ubuntu is like EMACS - it makes any computer slow.  If you want a fast system, then you should look at Slackware.  Even BSD desktops are faster than Ubuntu.  It is quite tragic how bloated desktop Linux has become.

---

### Post by martemarziano on 2017-02-07
> **HermanAB said:**
>  If you want a fast system, then you should look at Slackware.  Even BSD desktops are faster than Ubuntu.

I will surely take a look at them. Thanks!
cheers,
:KS

---

### Post by simplex1 on 2017-02-07
1) The fact that I run Ubuntu 16.04 from an USB stick can not explain why, while writing a text using, for example, this online editor: [http://www.editpad.org/](http://www.editpad.org/) , the last 4-5 characters continue to appear after I finish typing the text. There is no USB activity while using the editor. So, I have serious doubts that once installed on the HDD there will be no visible delay between the moment I press a key and the moment the character is shown on the screen.

Regarding the "Search Your Computer" text box, there might be a logical explanation regarding why the characters of a search string are displayed with a delay of more than 1 second. This is likely because once a letter is pressed, Ubuntu starts searching for programs containing the group of characters that letter belongs to. This operation takes time.

2) I opened "Unbutu Software" (pressed the orange icon with a white A on it) and wrote "hardinfo" (a benchmark tool), this is just to see where the performance of the Ubuntu running on my computer might be as compared with other laptops. Unfortunately, Unbutu searches forever and displays nothing.

---

### Post by Geoffrey_Arndt on 2017-02-07
Simplex1 . . . I can assure you running from HDD is up to 20 times faster than running off usbv2 due in part to memory mgmt & bus I//O limitations.    To get a much more accurate depiction of what installed speeds will be like . . try out a Live system like "Parted Magic" which uses LXDE & OpenBox and runs 100% in ram - - no I/O barriers.    On some hardware, many Live Linux distros basically slow down to a crawl . . . not really usable.   If you're doubtful - install it properly to hdd or use a better designed Live distro like Parted Magic.

Note that "Parted Magic" is not free - but the $9.00 is well spent as PM is the best (along with Knoppix) Live Linux distro.   [https://partedmagic.com/](https://partedmagic.com/)

---

### Post by simplex1 on 2017-02-08
Like this we go to nowhere. As long as the LED of the USB stick does not blink, Ubuntu runs from the RAM which is fast. This is my case. I do not talk about the situations in which I press a button, open a window, etc., and the USB stick starts to blink. For those cases I understand that the stick introduces some delays.
Most of the time Ubuntu is slow even if it runs directly from the RAM.

---

### Post by mörgæs on 2017-02-08
> **simplex1 said:**
> Most of the time Ubuntu is slow even if it runs directly from the RAM.

Yes, people have repeatedly explained that Ubuntu is too heavy for your machinery.

---

### Post by howefield on 2017-02-08
Do you get any fails when running this test for Unity support ?

```
/usr/lib/nux/unity_support_test -p
```

eg.

```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD REDWOOD (DRM 2.46.0 / 4.8.0-37-generic, LLVM 3.8.1)
OpenGL version string:  3.0 Mesa 12.0.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by pauljw on 2017-02-08
> **simplex1 said:**
> 1) The fact that I run Ubuntu 16.04 from an USB stick can not explain why, while writing a text using, for example, this online editor: [http://www.editpad.org/](http://www.editpad.org/) , the last 4-5 characters continue to appear after I finish typing the text. There is no USB activity while using the editor. So, I have serious doubts that once installed on the HDD there will be no visible delay between the moment I press a key and the moment the character is shown on the screen.

I just fired up my D257 running Xubuntu and went to that link above and there is zero delay when entering data.  I highly recommend you stop trying to use Ubuntu and download either Lubuntu or Xubuntu and try again.  The Unity DE is simply too much for these old limited machines.

Good luck.

---

### Post by simplex1 on 2017-02-08
[COLOR=#b22222]**YES, Xunbutu 16.04 is fast on my Acer Aspire One D270, unlike Unbuntu 16.04**.[/COLOR] It is as rapid as the original Win 7, 32 bit which I have installed on the HDD.

I was initially reticent to download something else than the original Unbuntu but seeing that Xunbuntu has the same version, 16.04, as the last Unbuntu LTS, I said that maybe they are the same thing excepting the graphical interface. I am quite pleased with this Xubuntu. There are no perceptible delays as long as the USB stick does not blink.

One more thing that I miss is the persistence of the settings I make. Each time I restart the computer all my changes are lost. Is there a (preferably easy) way to somehow save these settings?

---

### Post by martemarziano on 2017-02-08
> **simplex1 said:**
>  One more thing that I miss is the persistence of the settings I make. Each time I restart the computer all my changes are lost. Is there a (preferably easy) way to somehow save these settings?

I have used Universal USB Installer ([https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)) a few times before for making persistent live installation with quite high success rate.

---

### Post by simplex1 on 2017-02-08
I have tried that Universal USB Installer on Unbuntu 16.04, yesterday. The boot time (which was initially about 3 minutes when Ubuntu was installed with Rufus) grew to more than 6 minutes. Also this Universal USB Installer was considerably slower than Rufus in installing Ubuntu. However, it worked. If nothing better is available I have no choice but to try it also for Xubuntu. As long as Xubuntu boots now in the same time as Ubuntu, the Universal USB Installer will likely increase the boot time to more than 6 minutes.

---

### Post by mörgæs on 2017-02-08
> **simplex1 said:**
> seeing that Xubuntu has the same version, 16.04, as the last Ubuntu LTS, I said that maybe they are the same thing excepting the graphical interface.

Yes, that's the point. Goes for the other Buntus as well.

Good that you found a suitable distro.

It will help other users if you could change the thread title to *Installing on Acer Aspire One D270* or similar. The present title is misleading as you have 64 bit hardware.

---

### Post by simplex1 on 2017-02-08
I installed Xubuntu using the Universal USB installer to make it persistent on an USB drive. Unfortunately, while working with Firefox the LED of the stick blinks most of the time (this was not the case of Xubuntu non-persistent installed with Rufus). Firefox is so slow now that is nearly useless.
I was interested in a persistence for basic settings, for saving files, in general for things that are not changed all the time. If all kind of temporary files are saved continuously then this persistence is not so useful because it slows down Xubuntu.

Is there a version of Ubuntu that runs well from an USB stick, with persistence but without writing and reading continuously all kind of temporary files. I would like something that has the speed of the non-persistent Xubuntu 16.04 installed with Rufus on an USB drive.

1) I think that it should be made clear somewhere in a visible place  that Ubuntu 16.04  is slow even for quite capable 64 bit computers with a  2 GHz processor and 4 GB RAM. Definitely not the speed of the CPU, the  RAM quantity or the fact that it is run from an USB stick are the main  culprits for this drawback.  

2) > It will help other users if you could change the thread title to *Installing on Acer Aspire One D270* or similar. The present title is misleading as you have 64 bit hardware.

I doubt I have a 64 bit hardware. I have just run the command **lscpu** and this is what it displays:

```
xubuntu@xubuntu:~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 54
Model name:            Intel(R) Atom(TM) CPU N2600   @ 1.60GHz
Stepping:              1
CPU MHz:               1600.000
CPU max MHz:           1600.0000
CPU min MHz:           600.0000
BogoMIPS:              3191.73
L1d cache:             24K
L1i cache:             32K
L2 cache:              512K
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr  pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe  nx lm constant_tsc arch_perfmon pebs bts nonstop_tsc aperfmperf pni  dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm  arat
```

Definitely, I can change the title to a more suitable one but first we  have to be sure what processor and architecture my computer has.
Yes, there is a parameter there, **CPU op-mode(s): 32-bit, 64-bit**, which I interpret that the processor is 64 bit?! but in the same time another characteristic, **Architecture: i686**, tells me I have a 32 bit computer.

3) Is it possible to install on the same USB stick a few versions of  Ubuntu (Xubuntu, Lubuntu, Kubuntu, etc.,) and select the one I want to  try each time I start the computer? I have a 16 GB USB stick which has  space enough for a few Ubuntu-s. Unfortunately, with Rufus, each time i  try a new version I have to delete the previous one.

---

### Post by Geoffrey_Arndt on 2017-02-08
Why not dual-boot versus running a Live OS?    Much faster, simpler and more viable (Live OS even with persistence . . .  not really maintainable in the same degree as an installed system (lack of kernel updates, security & bug fixes, etc. - - the updater does not really function on Live systems).

Look at the lightest distros on Distrowatch.com such as "Antix . . . . Bodhi . . . . Lubuntu" etc.    Antix is based on debian, and the other two are based on Ubuntu core but with much ligher components (Desktop Environments)?

Are you concerned about the dual-boot install process ??? . . . (on a non-uefi machine, it's pretty straightforward, especially on an all Intel machine like yours).

You're just not going to have a good experience (imho) going down the road you've chosen so far.   (even with a persistent Xubuntu on usb. . . . Live OS's are a dead-end . . . really meant only for testing, recovery, installing OS or running "temporarily").

---

### Post by simplex1 on 2017-02-08
Before installing Xubuntu, I want to evaluate it for about one month or more. I do not really need Ubuntu now. When I decided to put it on an USB stick I was just curios about how it works, what features it has, etc. My Windows 7 has been working well on my laptop since 2012 when I bought the computer. I do not want to take risks and install an OS that is of no real use for me now.

---

### Post by Geoffrey_Arndt on 2017-02-09
There in fact, is an easy way to install any linux distro without changing your pc at all.   And that is to do to _a full install (not Live OS)_ on a fast usbv3 quality brand flash-stick (sandisk, kingston, lexar) . . . OR . . . much better yet, to do a full install on a device such as the San Disk 500 Extreme usbv3 SSD.   

Runs as fast as a full HDD install, and if you know how to do this, . . . is quite safe (low risk of messing with Win7) . . . IF . . . repeat . . . IF you install the Linux bootloader on the San Disk 500 versus the HDD of the PC.   Requires a standard usbv2 or v3 installer usb flash-stick, and the San Disk 500 SSD.

[http://omahatechconnect.org/2016/07/04/sandisk-extreme-500-portable-ssd/](http://omahatechconnect.org/2016/07/04/sandisk-extreme-500-portable-ssd/)

---

### Post by simplex1 on 2017-02-09
My computer is an USB v2 and a SSD will cost me at least $100 ([the cheapest I have found is $80 without Taxes]("http://www.bestbuy.com/site/searchpage.jsp?st=SanDisk+Extreme+500+240GB+External+Solid+State+&_dyncharset=UTF-8&id=pcat17071&type=page&sc=Global&cp=1&nrp=&sp=&qp=&list=n&af=true&iht=y&usc=All+Categories&ks=960&keys=keys")).

Xubuntu 16.04 LTS installed with Rufus (the one non-persistent) runs so well. Firefox is loaded from the USB stick only the first time I use it. After that, even if I close this browser and open it after some time, the LED of the stick does not blink.

There should be some settings, for the case in which Xubuntu is put on the stick with the Universal USB installer, that optimize Firefox and make it not to work so much with the USB drive, a thing that transform Xubuntu with persistence in an useless OS.

---

### Post by Geoffrey_Arndt on 2017-02-10
Does Firefox open & run faster on your Windows Live usb-stick? . . . . As it's been over 3 years since I've had any need at all for windows, maybe a valid "apples to apples" comparison would be educational.

---

### Post by Autodave on 2017-02-10
You need to remember that you are running it form a USB stick and not a hard drive. And, probably USB 1.  You have a slower machine, running an operating system from slower USB hook-up, and you are trying to run the fanciest Ubuntu there is.  Try dowloading the Lubuntu and run that from your USB......I think you might be shocked.

I have a 900MHZ, 1 gig net book that runs Xubuntu quite well.  Came with WinXP on it that was just horribly slow. Even Xubuntu 16.04 blows away the XP.

---

### Post by simplex1 on 2017-02-10
> **Geoffrey_Arndt said:**
> Does Firefox open & run faster on your Windows Live usb-stick? . . . . As it's been over 3 years since I've had any need at all for windows, maybe a valid "apples to apples" comparison would be educational.

Firefox runs from the RAM memory and is extremely fast (if it boots from an Xubuntu 16.04 USB-drive made with Rufus, so a non-persistent one). As I said, even if I close and open it repeatedly it stays there in the RAM and loads or activates quickly, when I reopen Firefox. If it runs faster than in Windows 7, I do not really know. I have to do more tests. What I can tell is that, for sure, it does not run more slowly.

> **Autodave said:**
> You need to remember that you are running it  form a USB stick ... . And, probably USB 1. .. .  Try dowloading the  Lubuntu and run that from your USB......I think you might be shocked.
I have a 900MHZ, 1 gig net book that runs Xubuntu quite well.  Came with  WinXP on it that was just horribly slow. Even Xubuntu 16.04 blows away  the XP.

My computer is USB 2, 1.6 GHz, 32 bit, 2GB RAM and it runs Xubuntu 16.04 (not Ubuntu) from a 16 GB USB (non-persistent) drive. It is fast with Xubuntu. This was not the case with Ubuntu. Unfortunately, this rapidity drops an order of magnitude if I make Xubuntu persistent. The LED of the USB-stick blinks all the time. 

**Question**: Will Lubuntu run faster if installed as ***persistent*** because this is my big problem now. Each time I start the computer all the settings, I made in a previous session, are lost.

---

### Post by mörgæs on 2017-02-11
> **simplex1 said:**
> 
I doubt I have a 64 bit hardware.

I don't. You do have 64 bit. The output posted indicates that your hardware is also capable of running a 32 bit operative system. In other words: 64 bit hardware is backwards compatible.

What I don't understand is that you post in a forum and still seem reluctant to take the advice given. I would expect that the very reason for posting was to harvest as much advice as possible.

---

### Post by simplex1 on 2017-02-11
> **mörgæs said:**
> I don't. You do have 64 bit. The output posted indicates that your hardware is also capable of running a 32 bit operative system. In other words: 64 bit hardware is backwards compatible.
What I don't understand is that you post in a forum and still seem reluctant to take the advice given. I would expect that the very reason for posting was to harvest as much advice as possible.

Somebody (see this link: [http://unix.stackexchange.com/questions/77718/32-bit-64-bit-cpu-op-mode-on-linux](http://unix.stackexchange.com/questions/77718/32-bit-64-bit-cpu-op-mode-on-linux)) had the same doubts as me and finally he found out he can run just the [32-bit PC (i386)]("http://releases.ubuntu.com/16.04/ubuntu-16.04.1-desktop-i386.iso") package of Linux.
I have noticed that some users on this forum tell me to do wrong things.

---

### Post by verymadpip on 2017-02-11
I'm running 64 bit Lubuntu 16.04 on an MSI U180 with an N2600 Atom CPU, GMA3600 graphics, 2Gb RAM.
I do this because I want 64bit Google Chrome for Netflix.
It works just fine here. (Kinda - see earlier comment about "infinite window borders").
It's the only OS on the machine & is installed to the hard drive.

Intel's Ark also indicates the N2600 is a 64 bit capable CPU, down in the "Advanced Technologies" section.
[http://ark.intel.com/products/58916/Intel-Atom-Processor-N2600-1M-Cache-1_6-GHz](http://ark.intel.com/products/58916/Intel-Atom-Processor-N2600-1M-Cache-1_6-GHz)

---

### Post by simplex1 on 2017-02-11
[QUOTE=verymadpip;13606155]I'm running 64 bit Lubuntu 16.04 on an MSI U180 with an N2600 Atom CPU, GMA3600 graphics, 2Gb RAM. ...
It works just fine here. ...
Intel's Ark also indicates the N2600 is a 64 bit capable CPU ...

Open a Terminal window and run the command **lscpu**, like this:

```
xubuntu@xubuntu:~$ lscpu
Architecture: i686
CPU op-mode(s): 32-bit, 64-bit
...
```

Post the result on this topic. What architecture do you have? Is it i686 or something else?

---------------------

UPDATE

I installed Ubuntu 16.04, the 64 bit package. [COLOR=#b22222]**It works**[/COLOR]. I run the same command **lscpu** and now it displays:

```
ubuntu@ubuntu:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
```

Unfortunately, after doing a test with Ubuntu 16.04, 64 bit on the same computer and in the same conditions as with its 32 bit version (see this link: [https://ubuntuforums.org/showthread.php?t=2351832&p=13604110#post13604110](https://ubuntuforums.org/showthread.php?t=2351832&p=13604110#post13604110) ) I got no visible improvement in speed. Ubuntu 16.04, 64 bit just requires more resources than its 32 bit version. see the attached picture and compare it with the one from [here]("https://ubuntuforums.org/showthread.php?t=2351832&p=13604110#post13604110"). I have not compare yet the 32 and 64 versions of Xubuntu 16.04 but I guess that I will get the same results. Xubuntu 16.04, 64 bit will just require more resources.

---

### Post by verymadpip on 2017-02-12
Hi again.
For me lscpu yields the same result as your second code box. (Showing 64 bit architecture).
Yes, 64 bit uses more resources, but as I'm not doing a gazillion things at once with my low end netbook I don't really notice.

---

### Post by simplex1 on 2017-02-12
In the meantime I also tested Xubuntu 16.04 - 64 bit package. On my computer its performance is below the 32 bit version. Firefox became unresponsive, with one occasion, also only LibreOffice was also active together with Firefox. Unless you run a software that really requires Xubuntu 64 bit, this version brings no advantage at all, at list in my case.

According to the discussion you can read [here]("http://stackoverflow.com/questions/607322/what-are-the-advantages-of-a-64-bit-processor") the main advantage of a 64 bit processor is that it can directly address more than 4 GB RAM. As my PC has only 2 GB, 32 bits are enough to directly address its entire RAM memory.

---

### Post by verymadpip on 2017-02-12
Hi again.
I have another machine - a Compaq CQ58 Presario (AMD E300 APU, dual core @1.6GHz, 4Gb Ram) which also runs Lubuntu 16.04.2.
I stopped using Firefox on that machine as it was pretty sluggish, moved over to Chromium Chrome for Netflix.  The CQ58 is still fairly sluggish.  I probably need to take it apart & give it a good clean, but that's not happening anytime soon to be honest.

This is getting a little off the beaten track & I'm unsure about what we're trying to solve now.  Anyway:
1. The N2600 is a 64 bit capable CPU.
2. Running from a live usb will always be a poor reflection of an OS (unless it's designed to run that way, like Puppy etc).
3. There are browsers other than Firefox available.

Good luck dude.

---

### Post by simplex1 on 2017-02-12
> **verymadpip said:**
> Hi again.
Running from a live usb will always be a poor reflection of an OS (unless it's designed to run that way, like Puppy etc).


Just install, with Rufus, a non persistent Xubuntu 16.04, 32 bit (or 64 bit) on an USB drive, and boot from it. I bet that Firefox will run faster or at least as fast as in the case when Xubuntu runs from the HDD.

---

### Post by verymadpip on 2017-02-12
Hi again.
I've no experience with Rufus, nor am I about to embark on that journey, sorry.
I generally use Unetbootin for creating Live USBs. (It will make a USB with persistence).
I also occasionally use the startup disk creator bundled with *buntu, but I dislike the way it partitions my sticks these days, so...Unetbootin.

---

### Post by simplex1 on 2017-02-12
No experience is needed to use Rufus. You press a button, select the iso image of Xubuntu (for example) and press Start.

Step by step instructions for installing Ubuntu on an USB drive, with Rufus:
[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by verymadpip on 2017-02-12
Hi again.
Perhaps I'm not being clear.
I've never used Rufus & have no intention of using Rufus.
I make my install USBs using either Unetbootin (available on Windows) or Startup Disk Creator.
These tools work well for me, I currently see no reason to change.  (It isn't broken, so I'm not fixing it).

Again, I'm at something of a loss as to what we're trying to solve at this point.

---

### Post by simplex1 on 2017-02-12
> **verymadpip said:**
> Hi again.
I have another machine - a Compaq CQ58 Presario (AMD E300 APU, dual core @1.6GHz, 4Gb Ram) which also runs Lubuntu 16.04.2.
I stopped using Firefox on that machine as it was pretty sluggish, moved over to Chromium Chrome for Netflix.  The CQ58 is still fairly sluggish.  I probably need to take it apart & give it a good clean, but that's not happening anytime soon to be honest.
[B]If you run a non persistent Xubuntu 16.04 - 32 bit, on your computer, Firefox will be incredibly fast. This is the reason I told you to install Xubuntu 16.04 on an USB drive with Rufus and then boot from the USB stick.

[/B]UPDATE

I have installed Xubuntu 16.04 on an USB drive, using UNetbootin. The LED of the USB stick blinks most of the time and Firefox is slow, it does not perform well. It works miserably. 

When Xubuntu is installed with Rufus, Firefox flies.

---

### Post by verymadpip on 2017-02-14
Oh I see, my bad, sorry.
I don't think I can help you with the firefox thing.  It's outside my sphere of knowledge.
Sory man, good luck.

---

