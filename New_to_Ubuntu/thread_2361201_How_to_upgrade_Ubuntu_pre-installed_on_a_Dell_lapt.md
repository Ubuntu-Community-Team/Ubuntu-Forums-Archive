---
title: "How to upgrade Ubuntu pre-installed on a Dell laptop?"
date: 2017-05-13
forum: New to Ubuntu
---

### Post by the-dreams-wind on 2017-05-13
[SIZE=2][FONT=arial]Hello, Ubuntu community. 
I have the laptop [DELL Inspiron 5759]("https://certification.ubuntu.com/hardware/201507-18601/"). The laptop has Ubuntu 14.04 LTS out of the box, but I really new in Ubuntu and don't have any idea how to deal with it properly. 
So there is a weird issue with it - when I open _**About this computer**_ settings, it randomly freezes. I hopefully decided to update the system to solve the problem. I don't know exact reason for that, but all 4 common repositories are disabled by default on this laptop. In the meanwhile there are a number of **_Other Software_** sources specified beforehand (please see attachments). So, to update the system, I turned on all the Ubuntu repositories and executed the command [/FONT][/SIZE][COLOR=#696969][FONT=courier new]sudo apt-get dist-upgrade[/FONT][/COLOR]. Eventually it brought me 16.04 LTS Ubuntu, but all the Other Software sources were turned off, some of **_Additional Drivers_** were disabled and I was not able to enable them back (it just was causing some error and refusing to work). My sound disappeared completely, and despite the [FONT=courier new][COLOR=#696969]lsb_release -a[/COLOR][/FONT] command was showing me 16.04 LTS Ubuntu, About this computer setting still was showing 14.04 LTS. The system was broken and I recovered it. Now I have 14.04 LTS factory image and everything but the freezing issue looks fine. 
As I mentioned above, I'm new in Ububntu, so I was looking for help on the [askubuntu]("https://askubuntu.com/questions/912611/should-i-update-certified-ubuntu") and [DELL]("http://en.community.dell.com/support-forums/software-os/f/3525/t/20012307") forum without much luck. Somebody [told me]("https://askubuntu.com/questions/914562/how-to-get-other-software-updates") that there should not be any compatible problems in case of clean-install of 16.04 LTS, but i'm not sure he is correct.

I'm still looking for advice, is there any specific steps for updating the laptop Ubuntu? How can I tell if the kernel contain any specific for the laptop piece of code? Should I update it at all? Should I change default settings in _**Software & Update**_ section? Should I update the system entirely or the kernel only? Are there the thresholds for updating? 
I don't really need to have the most recent system, but fully working and stable one. Any advice to provide me with right direction will be really appreciated.

Thanks in advance,

_**UPD:**_
Sorry for being late with it. I also want to provide details about my model. First, I can't find exact configuration of my laptop on the DELL site. On the other hand if I provide my service tag on the [DELL support-site]("http://www.dell.com/support/home/us/en/04"), it shows me the correct one.
Here is my configuration according to the [FONT=courier new]sudo lshw[/FONT] command:
```
**_Product:_** Inspiron 5759 (06B2)
**_Vendor:_** Dell Inc.
**_CPU:_** Intel(R) Pentium(R) CPU 4405U @ 2.10GHz
_**RAM:**_ SODIMM DDR3 Synchronous 1600 MHz (0.6 ns) 4 Gib 
_**HDD**_: Seagate ST500LT012-1DG14 500 GB
**_WiFi_**: Qualcomm Atheros QCA9565 / AR9565 
_**Ethernet**_: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express
_**DVD-ROM**_: PLDS DVD+-RW DU-8A5LH
**_Battery_**: DELL VN3N047
**_Other_**: USB 3.0 x1, USB 2.0 x2, Media-card reader, HDMI port
```

---

### Post by Autodave on 2017-05-13
Wow....lotsa questions.  Let's start with what I consider the most important one: the laptop needs to be running 16.04. 16.04 is the most current long-term release: 14.04 is almost dead now: no more updates will be issued including security updates.

Now, having said that, I have rarely ever got a distribution upgrade to work properly: it either has a lot of errors or just doesn't work at all.  IF you can d-l 16.04: whether Ubuntu, Xubuntu, or whatever, you would probably be best off doing a clean install.

Whatever version you d-l, it has to be put on a DVD or a USB stick as an executable: you cannot simply transfer it like you would a file.

I am sure you will get other answers that may differ from mine.

What are the specs on that machine? That may lead to a better answer as to what version (Ubuntu, Xubuntu, ?) to go after.

---

### Post by Autodave on 2017-05-13
I found one site that states that machine is a 2.5 dual core with 16 gig RAM and an AMD Radeon R5 GPU. Does that sound right? If so, Ubuntu would certainly run fine with that set up.

---

### Post by ian-weisser on 2017-05-13
> **Autodave said:**
> 14.04 is almost dead now: no more updates will be issued including security updates.

Er, 14.04 will continue to receive security upgrades until April 2019. The release is supported for two more years.

> **Autodave said:**
> I have rarely ever got a distribution upgrade to work properly: it either has a lot of errors or just doesn't work at all.  IF you can d-l 16.04: whether Ubuntu, Xubuntu, or whatever, you would probably be best off doing a clean install.

Okay, let's prevent some confusion here:
'Distribution-upgrade' is a Debian term, and it does something very different in Debian than in Ubuntu.
A distribution upgrade is a proper way to migrate from one release of Debian to another.
However, if you try it in Ubuntu, you will likely break your system...as perhaps you have discovered.
Ubuntu uses 'do-release-upgrade' to migrate to another release of Ubuntu

In Ubuntu, you CAN use do-release-upgrade quite safely if you purge the non-Ubuntu software that causes conflicts, returning your system to as close to stock condition as possible before starting. I have upgraded systems every six months since 2006, with only one problem in eleven years...my own fault, I didn't remove the non-Ubuntu software first.

Looking over the AskUbuntu thread, I think the OP has already caused enough package management problems to make a do-release-upgrade risky, and that agree that a clean install is the best option.

---

### Post by yancek on 2017-05-13
What does "out of the box" mean?  Did you buy the laptop from Dell with Ubuntu pre-installed?  If that's the case, they probably have made changes to settings for the machine.  If you did get Ubuntu pre-installed, contacting Dell would have probably been your first best step.  

Just to clarify, support for 12.04 ended last month, your 14.04 which you had will be supported for two more years.
Your original problem seems very unusual, I've never hears of anything like that in my years of using Linux.

---

### Post by milkness on 2017-05-13
Firstly, you are very sensible for asking the community first, (something I wouldn't do because I'm a idiot).

So take some advice for an idiot who has broken many things and back up you computer.

Do you have a external drive or a different computer you could back it up  to? If so, a quick search online or on yout-be can show you how.

Personally I think that the laptop will run fine if you update it. I am sure that Autodave is correct in that a clean install would be smoother approach, but just in-case there is additional propitiatory software, it think it would be worth updating the system, just to see if that additional software manages to survive or is crucial for the computer to run because it is always worth a try.

So this is what to do:

1. Back up the hardrive (not just drag and drop but properly done with some software) - just in case.
2. Select all of the unchecked boxes on the "Ubuntu Software" panel bit in the "Software & Updates" program.
2a. If the next step doesn't work properly then comment out / delete some or all of the dell proprietary repository links in the "Other Software" panel and replace it with the Ubuntu ones (search for online - use most recent) - if you want - isn't really that important.
3. On the desktop press, Ctrl + t , this will open a terminal (you probably know this already and sorry if you do but this will help other people later on who don't know how to do that), and type the "sudo do-release-upgrade" if that doesn't works try "sudo apt-get dist-upgrade", along with "sudo apt-get update" and "sudo apt-get upgrade".

If that all fails then either try a clean install of the new Ubuntu 17.xx from a usb drive or something (there are thousands of tutorials online) or restore from the backup you did.

I am sorry you are having trouble with your laptop - it's just what happens when private corporations can't bothered to keep their stuff updated/progress.

That should hopefully work and if I am giving bad advice please do not hesitate to question/tell me off. 


Have fun!

---

### Post by Dennis N on 2017-05-13
> I'm still looking for advice, is there any specific steps for updating the laptop Ubuntu? How can I tell if the kernel contain any specific for the laptop piece of code? Should I update it at all? Should I change default settings in Software & Update section? Should I update the system entirely or the kernel only? Are there the thresholds for updating? 

The special repository at [http://dell.archive.canonical.com/dists/](http://dell.archive.canonical.com/dists/) can be examined, and contain what seem to be custom Dell packages apparently to optimize your system. I would leave these repositories enabled (note that there is nothing in that repository for the last two releases, 16.10 and 17.04. What that implies, I'm not sure.)

The 4 ubuntu software repositories (thumbnail 2) should be enabled, otherwise no way to update most packages, including security updates. After enabling, open software updater, and check for any updates.

You should otherwise update when you are notified of available updates, but check the 'updates' tab (thumbnail 2) to be sure it is actually set up to check for updates. 

You could consider not opening the "about this computer" and therefore avoid the freeze problem.

---

### Post by Geoffrey_Arndt on 2017-05-14
Just install the latest LTS (16.04.2).   Don't waste time on 17.xx anything.

Get the layout of your system first though . . . run gparted program and jot down your partition layout, disks, etc.

As already indicated, copy your important data from PC to a USB drive first. 

If you're uncertain how to get the iso, create a bootable usb and then do the install - ask first or view some of the many excellent tutorials on the youtube linux channels.

---

### Post by the-dreams-wind on 2017-05-14
> **Autodave said:**
> I found one site that states that machine is a 2.5 dual core with 16 gig RAM and an AMD Radeon R5 GPU. Does that sound right?
> **Autodave said:**
> What are the specs on that machine? 
My laptop has some specific config you can't find on the DELL site.. Forgot to specify it, sorry:
Here is my configuration according to the [FONT=&amp]sudo lshw[/FONT] command:
```
**_Product:_** Inspiron 5759 (06B2)
**_Vendor:_** Dell Inc.
**_CPU:_** Intel(R) Pentium(R) CPU 4405U @ 2.10GHz
_**RAM:**_ SODIMM DDR3 Synchronous 1600 MHz (0.6 ns) 4 Gib 
_**HDD**_: Seagate ST500LT012-1DG14 500 GB
**_WiFi_**: Qualcomm Atheros QCA9565 / AR9565 
_**Ethernet**_: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express
_**DVD-ROM**_: PLDS DVD+-RW DU-8A5LH
**_Battery_**: DELL VN3N047
**_Other_**: USB 3.0 x1, USB 2.0 x2, Media-card reader, HDMI port
```

In accordance with most of the answers, the 'clean-install' of 16.04 LTS still seems to be the best option. However, to mitigate update impact, I was looking for approach to make kind of minor updates first and look if it helps. I'll try Dennis N approach first, and see if it helps.If there is no luck with it, I'll try 'clean-install' and will get back here with my result :) If i will not, thanks anyway for your help!

---

### Post by steven60 on 2017-05-14
i agree on the fact a clean install is the best way to upgrade your system.
one question is do you have a home partion? 
if not, you should its definitely alot easier to do the clean install upgrade as you can keep almost all the same settings this way.
as well as your files on the home partition will be safe.
this was one of the first lessons i learned when i started out with linux.
i cant tell you how many times i screwed up my system.
and had to fresh install.
a home partion will save u time if you break your system.

---

### Post by ian-weisser on 2017-05-14
> **the-dreams-wind said:**
> to mitigate update impact, I was looking for approach to make kind of minor updates first and look if it helps.

That approach usually doesn't work in our world of Debian-based Linux distros. A specific upgrade to one package might fix a problem, but might not...while it breaks your system by introducing dependency conflicts.
It's possible to do, but you must have good package management skills.
Definitely not for beginners.

---

### Post by the-dreams-wind on 2017-05-18
Hey,
Fortunately, I've got back :) After the clean install everything appears to work. Only one issue I can mention now is that an error occurs each time I launch the system (you can find it in attachment), however I can't see if it breaks anything. 
Although some questions were unanswered for me:
[LIST]
[*]How can I install drivers and programs were originally installed with the DELL repositories?
[*]Taking into account the fact that minor system updates can break the system, how can I prevent them?
[*]Is it a decent approach to use the 'Software Updater' to keep my software updated?
[*]Is there a built-in way in Ubuntu to make a snapshot of the system to be able to get back as needed?
[/LIST]

Thanks for your help guys. It is appreciated :)

---

### Post by the-dreams-wind on 2017-06-03
Hello everyone again,
Unfortunately the 16.04 LTS works not very well with the laptop. I decided to get back to 14.04. So the only question remains for me now is - how to _**get important security updates**_ and keep the system consistent, i mean, to not update system core or any other part of the system that was not tested well by DELL? 
I see only one option - to enable Ubuntu and DELL repositories, but set the option 'Notify me of a new Ubuntu version' to 'Never'.
Please correct me if I'm wrong with my conclusion.
Thanks in advance.

---

### Post by ian-weisser on 2017-06-03
> **the-dreams-wind said:**
> Unfortunately the 16.04 LTS works not very well with the laptop

Sorry to read that.
What does this mean?
This is very vague. Can you provide details?

---

### Post by the-dreams-wind on 2017-06-11
> **ian-weisser said:**
> Sorry to read that.
What does this mean?
This is very vague. Can you provide details?
Primarily it's still related to the sound. When I plug my headset in the laptop, i can't even reboot it without having a problem. At best it may switch sound output to another existing device, that just doesn't work for some reason. More often it causes some unknown HDMI outputs to emerge from nowhere. The same issues arise when the laptop is woken up after suspending. And when the headset is plugged i always have 3 microphone inputs... (the same for 14.04 LTS actually) Eventually sound disappears at all, showing me only dummy output (or no outputs) in the sound settings. Many UI glitches and artifacts also make me think it's kind of bad idea to switch to 16.04 LTS, but people tell me that it's ok for any Ubuntu versions :)

---

