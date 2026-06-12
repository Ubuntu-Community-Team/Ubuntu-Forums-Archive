---
title: "New Linux/Ubuntu User, looking for help on a few things?"
date: 2024-08-16
forum: New to Ubuntu
---

### Post by superwookie68 on 2024-08-16
Hey everyone, 
 [IMG]https://y.yarn.co/e9c5568c-5c45-4e71-a6ca-47a9d97032b8_text.gif[/IMG] hahaha

I’m trying to figure out how to do some things that are so far, not working out for me and it's becoming very frustrating. Meaning, run a Linux distro on my Windows 10 PC, be able to customize that distro to have a very aesthetically pleasing DE, yet fast and smooth operating and with my very nice computers RGB fans/aio cooler running. And so far, I can’t really seem to figure out a way to do that. 


I built my own all white, super clean PC last winter. It was really fun learning about all the parts, how and why each part does what it does and where to spend more money and where to just get stuff that’s “good enough”, etc. It runs Windows 10, and is the following specs: AMD Ryzen 5 5600G 3.9GHz 6 core chip, Gigabyte B550 Vision D-P ATX mobo, Corsair RGB RT 32 GB DDR-4 3600 Memory, Samsung 970 Evo Plus 1 TB NVME M.2 SSD and a Gigabyte RTX 3060 GPU. While running Windows 10 it runs CRAZY fast and smooth compared to any computer I’ve ever used. It’s so cool and even better knowing that I built it myself. 




[B]ISSUE 1
[/B]But, I’ve caught the Linux bug recently after seeing some videos on youtube. I really love how customizable it is, how it’s such a vast community of like minded but individual people (all helping each other out to make computing more fun and better), love the lack of bloat ware on the OS’s, love how it's open source so that super smart people out there can make corrections or fix things (while the big guys just let BS pile up) and of course appreciate how secure it is in so many ways over Windows. So I thought I could just download some ISO’s of Ubuntu, Kubuntu, Pop and Zorin and start messing around using them no problem on my VMWare 16 workstation player. But it’s not going to plan :(


So Zorin and Pop OS, while nice and work smoothly and quickly on my VMWare player, don’t seem very customizable compared to Ubuntu or Kubuntu (which use Gnome and Plasma as their DE’s as far as I can tell from doing research). And when I see what you can do with Ubuntu or Kubuntu platforms on youtube, it blows my mind and I WANT to be able to do that. Create and customize my entire DE how I want. I'm much more of a visual/aesthetic person in general. Everything I have or get into, has to be amazing looking and look how I want. It makes me happy. So seeing what Gnome and Plasma DE's can become is DEFINITELY my thing. 


Yet, when I try to run Ubuntu or Kubuntu on the VMWare hypervisor, they have all sorts of problems right off the bat! They both load VERY slow. They both freeze or crash VMWare almost every time I try to use them. The screen is super small and has all this black space around the edges, while Zorin and Pop OS do not. It’s just not working for some reason. And I have the exact same VMWare settings for all 4 distros. Something like 8GB of ram, 40GB of HD space. And yet they just don’t work, while Zorin and Pop work flawlessly.  


So that’s problem no 1 I’m trying to solve. How do I get Ubuntu or Kubuntu (possibly even Mint Cinamon) to run fast, smooth and with full screen on VMWare (all with moderate to heavy customizations)? 



[B]ISSUE 2
[/B]Then the other issue I’m running into is related to the first one. I’m doing lots of reading, research etc, and understanding some of what I’m reading, but not getting a lot of answers that are lining up about this next issue. And that thing I’m kicking around the idea of trying is just loading a Linux distro straight onto my SSD. So setting up a dual boot. Windows 10 on one side, a Linux distro on the other. Some people are saying that Ubuntu or Kubuntu would work flawlessly and very fast if I just did this. But then, when I look around the internet about this, I’m seeing quite a few people saying that my white RGB lights on the Lian Li fans and AIO cooler will not work and not be controllable if I use Linux in a dual boot format?! That the only way I can have my lights on and working is if I run Linux as a VM inside of my Windows 10? So that is also super annoying and frustrating to find out. So how in the heck are Linux people supposed to have fans, lights and AIO’s work? It seems really lame and is super confusing. 

I just don't know what to do here? I want to make Ubuntu or a Linux distro my everyday driver OS. And if I can't run my fans, lights and AIO while using Linux, then I would need to run it in a VM. But then how do I get Ubuntu or Kubuntu to run fast, smooth, full screen etc? This has been very exciting and fun to discover Linux and how easy it is to use and all of it's great benefits over Windows. But then VERY disappointing and confusing trying to get my lights, fans and AIO to run while also being able to run Linux fast and smooth. So just looking for help.


Thanks everyone



[IMG]https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Flnv56xgpdol21.jpg[/IMG][IMG]https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Flnv56xgpdol21.jpg[/IMG]

---

### Post by TheFu on 2024-08-16
Some DEs demand direct hardware access.  Gnome and Plasma are 2 like that, so they will seldom run great inside a VM unless you setup GPU passthru.  That means the hostOS cannot use the GPU at all.

You do realize that all DEs are bloated, right?  You don't need a DE at all to have a GUI on Linux.  Also, DEs have certain constraints to make them work. They have to since there are more interfaces and programs can only use interfaces that are created to do things.   Learn about how the GUI layers of Unix-like OSes work and know that you don't need a DE.  Imagine how fast and customizable your systems will be without all that bloat?  Look up "Suckless" and my favorite WM, fvwm.

Don't get too stuck on any specific distro.  Try some non-Ubuntu and non-ubuntu-based distros too.

And how do I say this nicely.  VMware Player is one of the least good hypervisors that can be used.  Consider using a better option.  Also, consider making Windows run inside a VM that runs Linux on the hardware, not MS-Windows.  Then a huge world of capabilities opens up.  The Linux Gurus run KVM/qemu + libvirt  to manage their VMs.  It has been stable since 2010, so it isn't "new". Also, it is part of the Linux kernel, so it is constantly maintained by those experts.

Always remember, that the GUI you use is just another setup of programs on Unix-like OSes. They are NOT the OS.  There's no need to wipe an OS just to use a different GUI.  You are welcome to have 10+ GUIs on a single Linux OS.  However, due to short-sighted choices, it is best to have a different userid for each GUI/DE used to prevent configuration collisions.  Linux has been a multi-user OS since the beginning, so this isn't any issue. Take advantage of it as you search for the GUI you like best.

Just some thoughts for your consideration.

---

### Post by Dennis N on 2024-08-16
Most of the customizing of gnome-desktop systems is done with gnome shell extensions and gnome-tweaks. Are you using those? You can find recommendations on these in many places on the web.

---

### Post by Holger_Gehrke on 2024-08-16
Regarding issue 2: on all modern operating systems direct access to any hardware is not allowed. The only part of the system that can do it is the kernel. That's why drivers for any kind of hardware are loaded into the kernel. If the makers of your fans/lights/coolers don't either keep to some kind of well established standard for which drivers exist or develop drivers of their own for any and all operating systems including Linux, then your beautiful and expensive hardware is completely useless.

---

### Post by superwookie68 on 2024-08-16
> **TheFu said:**
> Some DEs demand direct hardware access.  Gnome and Plasma are 2 like that, so they will seldom run great inside a VM unless you setup GPU passthru.  That means the hostOS cannot use the GPU at all.

You do realize that all DEs are bloated, right?  You don't need a DE at all to have a GUI on Linux.  Also, DEs have certain constraints to make them work. They have to since there are more interfaces and programs can only use interfaces that are created to do things.   Learn about how the GUI layers of Unix-like OSes work and know that you don't need a DE.  Imagine how fast and customizable your systems will be without all that bloat?  Look up "Suckless" and my favorite WM, fvwm.

Don't get too stuck on any specific distro.  Try some non-Ubuntu and non-ubuntu-based distros too.

And how do I say this nicely.  VMware Player is one of the least good hypervisors that can be used.  Consider using a better option.  Also, consider making Windows run inside a VM that runs Linux on the hardware, not MS-Windows.  Then a huge world of capabilities opens up.  The Linux Gurus run KVM/qemu + libvirt  to manage their VMs.  It has been stable since 2010, so it isn't "new". Also, it is part of the Linux kernel, so it is constantly maintained by those experts.

Always remember, that the GUI you use is just another setup of programs on Unix-like OSes. They are NOT the OS.  There's no need to wipe an OS just to use a different GUI.  You are welcome to have 10+ GUIs on a single Linux OS.  However, due to short-sighted choices, it is best to have a different userid for each GUI/DE used to prevent configuration collisions.  Linux has been a multi-user OS since the beginning, so this isn't any issue. Take advantage of it as you search for the GUI you like best.

Just some thoughts for your consideration.


Ok, lots to digest and understand here. First pt taken. Gnome and Plasma probably will not run well inside a VM. That sucks. But good to know. But, explain more about this GPU passthru? I hardly EVER use my PC for gaming or use the GPU. I played Zelda BOTW on and off for about a year and then I just saw that Ghost of Tsushima got released for PC, so I'm definitely going to have to get that and play it. But other than that, I don't use my GPU all that often. So when you say I can passthru my GPU to the Linux distro running in a VM, is that a permanent setup? Will that help Gnome or Plasma work a lot better and run faster and smoother? Is it pretty quick and easy to change back and fourth from having the GPU in Windows to the Linux VM? I could potentially pass the GPU through to the Linux VM, and IF or WHEN, I want to play a game on the Windows side, I can just set it back to the Windows? 

Second pt, I did not realize DE's are bloated. But also don't know if you mean bloated as in, they contain lots of extra programs and crap I don't need or want? Or if they are just large and take up a lot of resources? And as far as "you don't need a DE to have a GUI on Linux", I think I do. Like I mentioned, I've seen some absolutely STUNNING DE's from people that create and share on YouTube, such as LinuxScoop and LinuxFam. SUPER customized, amazing looking, semi transparent windows with blurring, a trillion choices of amazing looking icons for your programs, docks, desktop widgets, folder colors and styles, just ENDLESS amazing looking mods. And as far as I can tell (which as I said, I'm new to all of this) only can be accomplished with the two better more in depth DE's which are Gnome and Plasma? So meaning, I DO really want to use them to be able to create and customize my own individual aesthetically pleasing desktop environment. I looked into that Suckless and then FVWM and those definitely look out of my league and like something I wouldn't be interested in. But thank you for the suggestion. 

Third pt, I did a lot of research online and it's pretty unanimous from most people and websites saying that VMWare is the best hypervisor for what I want to do and just in general. But if you think it's not great, what do you suggest? 
Then onto the next pt of this and hopefully the best part? You're suggesting I run Windows in a VM, that runs on a Linux base system? So my first question is, will this allow me to have Linux run fast and smoothly (because it's on the hardware and not on a VM) but also then be able to turn on the VM of Windows and control my fans, lights and AIO?!?! If so, then this is 100% what I need to do. 

Fourth pt, I'm not following this part very well and this might be out of my knowledge base. You might have to explain in simpleton terms. I know what a GUI is. I know what OS's are. But I don't know what you mean by "there's no need to wipe an OS just to use a different GUI. You are welcome to have 10+ GUIs on a single Linux OS." So I did some research and it seems that there are Linux OS's and then Linux GUI's. Not sure how Linux "distros" come into play for all of this. When you look up Linux Distros, all of these OS's and GUI's come up as a "distro." So that's confusing. But it looks like some of the OS's are Ubunutu, Debian, Mint, Fedora, Red Hat, Elementary, Arch and Manjaro. But, upon further reading, most of those are based on Ubuntu. So it seems like Ubuntu and maybe only a few others are TRULY their own OS? I don't know, just asking for clarification. Then it looks like some of the GUI's are: KDE, GNOME, XFCE, LXDE and MATE. But again, I'm sure there are others, just don't know. So it sounds like what you might be saying is that you can chose one OS, but then have many different GUI's running off of that one OS? Obliviously not at the same time (maybe you select one, when you fire up your computer?). And if that is correct, how does one go about setting your Linux OS up to do that easily? I've never heard of that before. Sounds interesting. 

One thing that you did not address, which is the biggest issue I'm facing with whether or not to try and continue with my plan of using Linux as my everyday OS, is how to integrate or use and control my fans, lights and AIO. I know to you and lots of other "power users" (people that are using their computers for work, coding, hacking, etc) don't care about aesthetics that much or at all. And just listening to your tone and way of speaking in your answer, makes me think you are one of those types of people. And there's obviously nothing wrong with that. But I 100% need and want to use my fans, lights and AIO as it is extremely aesthetically pleasing to my eye (plus I spent a lot of money on it) and that is also the main reason I'm considering using Linux. For its ability to customize and change virtually anything about how it looks and works. And if I can't have my fans, lights and AIO on and controllable, while using Linux in some way (whether that be through a VM or actually on my HD), then I will not be moving forward with using Linux. It's as simple as that. And that is really what I'm looking for help with here. HOW can I run Linux, customize it, have it run quickly and smoothly with little to no problems, WHILE being able to run and control my fans, lights and AIO. 

Thank you for your starting information and help, I appreciate it very much!

---

### Post by superwookie68 on 2024-08-16
> **Dennis N said:**
> Most of the customizing of gnome-desktop systems is done with gnome shell extensions and gnome-tweaks. Are you using those? You can find recommendations on these in many places on the web.

I have not even been able to get past the desktop screen! It freezes or crashes the second I click on any app or setting. I have tons of youtube videos bookmarked, to help me use Extension and Tweaks to customize, but as I said, when running Ubunut or Kubuntu on VMWare, they freeze or go super slow and/or crash almost right away. Yet Zorin and Pop run very fast and smooth. It's super weird and I'm trying to google why this is happening and how to fix it, but as I said, I get a million different responses with different answers to the same question. It's very frustrating

---

### Post by superwookie68 on 2024-08-16
> **Holger_Gehrke said:**
> Regarding issue 2: on all modern operating systems direct access to any hardware is not allowed. The only part of the system that can do it is the kernel. That's why drivers for any kind of hardware are loaded into the kernel. If the makers of your fans/lights/coolers don't either keep to some kind of well established standard for which drivers exist or develop drivers of their own for any and all operating systems including Linux, then your beautiful and expensive hardware is completely useless.

So I'm not really following what you're trying to explain to me. But my best guess is that you are saying that the makers of the fans, lights and AIO are the only ones that can make drivers? And since I don't see any Linux drivers for any of my fans, lights or AIO, I'm basically sh*t out of luck?! Which means that people that use Linux can't and don't use RGB fans, lights or AIO's? Is that what you are trying to say?

---

### Post by hessajee on 2024-08-16
I'm also somewhat new to UNIX/Linux/Ubuntu having dabbled in it a long time ago (as one can see from when I created my account here). 

Just one thought - you could create a bootable USB, run your Ubuntu flavour from there, see how it works and if you like it etc. It might be possible to run a VMWare equivalent from there with Windows and see if your fans, lights or AIO work. You seem to have the hardware spec to be able to do it. I think you need a large capacity USB memory stick (USB SSD with USB 3.2 capabilites) so you're not limited by speed and see if you can simulate what you want to do.

If it does what you want it to do, then you can follow the suggestions above, install your choice of Linux/Ubuntu and run Windows from a VMWare equivalent.

---

### Post by TheFu on 2024-08-16
> **superwookie68 said:**
> So I'm not really following what you're trying to explain to me. But my best guess is that you are saying that the makers of the fans, lights and AIO are the only ones that can make drivers? And since I don't see any Linux drivers for any of my fans, lights or AIO, I'm basically sh*t out of luck?! Which means that people that use Linux can't and don't use RGB fans, lights or AIO's? Is that what you are trying to say?

People using Linux do have lots of lights.  They are just careful which hardware they buy, to ensure it is either already supported via existing kernel drivers or drivers are available from the hardware maker.  Linux has less than 5% of the desktop/laptop market share, so most hardware vendors ignore it.  IME, Gigabyte completely ignores Linux.  I used to buy Gigabyte equipment, then I tried to get support for a small issue and they simply said "we don't support linux".  I take my money elsewhere now.  I don't want to encourage bad behavior from vendors.  

All hardware vendors have to decide how much they will or will not support Linux.  Some are definitely better than others.

Sorry, I can't answer all your questions.  We are different people at different places in life with different needs. Many things you ask aren't anything on my list of things to care about.  I don't care about blinking lights.  My systems are usually in a different room, so nobody sees them. 

I'm a trained engineer. In general, I disable all RGB-like lights. They are distracting to me. There are 4 lights on the front of my systems.  These are tied to a disk caddy, so I can see if the disks are working or not.  That's it.  External arrays also have lights to show power and which disks are installed/working.

VMware makes at least 6 different hypervisors.  Player is the lowest-end offer they make.  There are others from other projects.  With Linux, as the hostOS, then there are others, including those made by VMware, Oracle.  I use the built-in hypervisor that is part of the Linux kernel.  I didn't always. Around 2010, due to issues with 3 other hypervisors, including 3 from VMware, I and my company switched.  We ran tests for nearly a year before the switch.  I use kvm/qemu + libvirt since then. Sometimes our choices turn out to be mistakes.  This is one I've never regretted, but I'm mostly interested in server-on-server virtualization.  I care very little about desktops, but I do run my main desktop inside a VM and access it from anywhere in the world either using ssh or x2go or remote X11 (via an ssh-tunnel).  This web browser I'm typing into is actually running on a different system, inside a VM, with just the browser window being displayed, not the full desktop.  Also running on the desktop VM is a fat email program, and about 5 other things. The windows for each different program are displayed on my local workstation with fvwm as the WM. No DE used.  I've been customizing fvwm for nearly 30 yrs now.  

I ran using DEs for about 11 yrs, then got frustrated with having to learn a new GUI every time there was a new release and some new GUI team decided to make it "better" ... which usually meant more bloated, slower, used 2-10x more RAM and I'd have to learn how to access programs I've been using nearly 20 yrs.  For me, it was a waste of time.  I completely understand that people want "pretty" and don't care how much RAM and CPU and GPU that needs.  That isn't me.  I want to get the most from my hardware.  On one system, I have 10 VMs and Linux containers running. Not bad for a $120 3 yr old CPU with $80 of RAM. 
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        22Gi       1.4Gi       196Mi       7.2Gi       7.9Gi
Swap:         4.1Gi       2.4Gi       1.7Gi
```
Plenty of RAM still available in the system.  OTOH, that system doesn't have any GUI running on the hardware.

It is fine for your needs to be different from mine.  That's pretty common.

For GPU passthru, the GPU can only be used by 1 system at a time, exclusively.  Most people that do that have 2 GPUs in their system. They use the low-end GPU for the host OS and use the expensive GPU for 1 of the VMs.  Switching this has been non-trivial, but I suppose it gets a little easier every release.  IDK. I haven't bothered trying in 15 yrs.

---

### Post by superwookie68 on 2024-08-16
> **hessajee said:**
> I'm also somewhat new to UNIX/Linux/Ubuntu having dabbled in it a long time ago (as one can see from when I created my account here). 

Just one thought - you could create a bootable USB, run your Ubuntu flavour from there, see how it works and if you like it etc. It might be possible to run a VMWare equivalent from there with Windows and see if your fans, lights or AIO work. You seem to have the hardware spec to be able to do it. I think you need a large capacity USB memory stick (USB SSD with USB 3.2 capabilites) so you're not limited by speed and see if you can simulate what you want to do.

If it does what you want it to do, then you can follow the suggestions above, install your choice of Linux/Ubuntu and run Windows from a VMWare equivalent.


Hmmm, interesting. I do have two 64GB USBs and two 128GB USBs. Looks like from some initial research that it probably won't be a good option for me though. Sounds like it only works and saves info onto the USB, which is obviously nowhere near as fast as my SSD. And that not all features work when running off of a USB. But that might be an option? I'll have to look into that and see how that would work. 

Thanks for the suggestion

---

### Post by Dennis N on 2024-08-16
> **superwookie68 said:**
> I have not even been able to get past the desktop screen! It freezes or crashes the second I click on any app or setting. I have tons of youtube videos bookmarked, to help me use Extension and Tweaks to customize, but as I said, when running Ubunut or Kubuntu on VMWare, they freeze or go super slow and/or crash almost right away. Yet Zorin and Pop run very fast and smooth. It's super weird and I'm trying to google why this is happening and how to fix it, but as I said, I get a million different responses with different answers to the same question. It's very frustrating

Well then, you need to solve the VM problem first. I think you might get better results with kvm/qemu virtualization with Ubuntu host if you can do that. I use it on my vms, and the performance is not perceptibly different than I get in a standard install. I can't recall ever having a problem. I don't use a separate gpu. Streaming video works fine. I imagine graphics intensive games might not, but I don't have any. Also, there is no Windows installed on my computers. I stopped using that back in 2007.

---

### Post by hessajee on 2024-08-20
The bootable USB option was more to just try things out and if you're happy with the results then make it 'permanent' and install it onto your SSD. Saves you formatting your system just in case things don't work out the way you want it to. 

Alternatively and/or in addition to the bootable USB option, install your choice of Linux alongside your current Windows installation, then go with installing another copy of Windows virtually as suggested in this thread and see if it is faster and it works as intended. 

Then you can decide to format your SSD and make your final choice 'permanent'. 

FYI - I purchased a 1TB Portable SSD USB 3.2 which in theory should provide faster speeds. I've yet to test it but it could give comparable results if you have a USB 3.2 port etc.

---

### Post by TheFu on 2024-08-20
Any SSD, even SATA, connected to USB3 or higher will be so fast as to not matter. I doubt you'll notice.  However, USB storage has different storage commands than SATA, SCSI, eSATA and SAS connected storage.  I consider USB connections for "emergency use only" ... sometimes those emergencies last a week as I await a new HDD/SSD to be shipped.

OTOH, a few friends DO run Linux only from USB3 connected devices and they seem happy.  They travel that way to prevent any important data on the internal storage from risk. They pop out the SSD inside their laptop and leave it at home.  Can't lost sensitive data if you don't have it with you.

Storage in my systems have a flow.  They start out as primary storage, then move to backup storage, then to Sneaker*Net storage and finally shelf storage - which means they are in line for destruction in a pit with 3000 deg heat (fun for the whole family!).  Nobody actually knows how to completely wipe SSD storage, so it is best NOT to sell it or trash it if it ever contained anything that may have been sensitive.  I consider encrypted passwords "sensitive", so I never trash any SSDs before they are slagged or the county has a free digital shredding day. On those days, you get to watch them put your SSD/HDD into a huge metal shredder and see what comes out the other side.  Data won't be recovered from those things.

---

### Post by TheFu on 2024-08-21
FWIW: [https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/](https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/)
MSFT update seems to have screwed many dual boot systems.

---

### Post by oldfred on 2024-08-21
On the SBAT issue posted above by TheFu.
A new shimx64.efi was released. Only required if UEFI Secure boot on.


Since November 2022, several Linux distributions, including Ubuntu 22.04.2 and 20.04.6, have upgraded to shim 15.7, which provides a critical security update to address various vulnerabilities in the boot stack. o address this issue, it is recommended that users switch to newer installer media, such as Ubuntu 22.04.2, Ubuntu 20.04.6, and equivalent updated media from other distributions. 
[https://discourse.ubuntu.com/t/sbat-revocations-boot-process/34996](https://discourse.ubuntu.com/t/sbat-revocations-boot-process/34996)
Sbat Windows update stops old Linux shim from working 
[https://support.microsoft.com/en-us/topic/august-13-2024-security-update-kb5041160-3e8026f2-bb4c-4c1c-9855-d41e1b5b1bd9](https://support.microsoft.com/en-us/topic/august-13-2024-security-update-kb5041160-3e8026f2-bb4c-4c1c-9855-d41e1b5b1bd9)

You can check version of shim you have installed. 15.7 required to resolve issue, noble showing 15.8 update.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ dpkg -s shim-signed | grep Version [/COLOR]
[COLOR=#ff5454]**Version**[/COLOR][COLOR=#000000]: 1.58+15.8-0ubuntu1[/COLOR]
[/FONT]
```

This bug suggests that 15.8 is required.
[https://bugs.launchpad.net/ubuntu/+source/cd-boot-images-amd64/+bug/2076929](https://bugs.launchpad.net/ubuntu/+source/cd-boot-images-amd64/+bug/2076929)

More discussion:

[https://tech.slashdot.org/story/24/08/21/0031243/something-has-gone-seriously-wrong-dual-boot-systems-warn-after-microsoft-update](https://tech.slashdot.org/story/24/08/21/0031243/something-has-gone-seriously-wrong-dual-boot-systems-warn-after-microsoft-update)

---

### Post by Holger_Gehrke on 2024-08-21
> **superwookie68 said:**
> So I'm not really following what you're trying to explain to me. But my best guess is that you are saying that the makers of the fans, lights and AIO are the only ones that can make drivers? And since I don't see any Linux drivers for any of my fans, lights or AIO, I'm basically sh*t out of luck?! Which means that people that use Linux can't and don't use RGB fans, lights or AIO's? Is that what you are trying to say?

Not really S.O.L., there are controller chips for led lighting out there and the Linux kernel has drivers for some of them. If your lights use one of these controllers then you will find directories named for the LEDs in the directory /sys/class/leds/. You can find some documentation on the supported chips and how you can 'talk' to the drivers at [www.kernel.org/doc/html/latest/leds/index.html]("http://www.kernel.org/doc/html/latest/leds/index.html"). There's also OpenRGB, a controller software which allows you to graphically control LEDs on all the supported devices including some USB devices which aren't supported by the Kernel directly. AFAIK it should be in the repositories for 24.04, if not there's both an Appimage and a .deb package available from openrgb.org.

Holgerf

---

