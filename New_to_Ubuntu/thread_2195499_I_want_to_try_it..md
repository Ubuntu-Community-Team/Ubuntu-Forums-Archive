---
title: "I want to try it."
date: 2013-12-24
forum: New to Ubuntu
---

### Post by bgast7851 on 2013-12-24
I have tried to boot live DVD/CD of several distros but I only want to use Ubuntu or Mint. Ubuntu gets further for me in the boot process but still won't boot. I have changed everything in Bios that I needed to change that I know of. I have even tried to enter text at the splash screen. Something like ro quiet splash and  ro nomodeset and that did not work. Here are the distros that I have attempted to try Linux Mint Petra based on Ubuntu Saucy, that says won't load x-server to me. I have the latest Ubuntu, I have Elementary, I have Lubuntu. Anyway, I'd like to pick one and give it a try, but they won't let me and I am absolutely clueless.

My computer is a Gateway, AMD E1-2500 APU with Radeon HD 8240 graphics on the chip (I guess), 500 GB Hard drive, 4 GB DDR3 Memory, DVD-Super Multi-drive, Card Reader(whatever that means), and Integrated LAN 10/100/1000 (I don't know if this is any good or not.) I also have another external hard drive I think 250 or 300 GB. My printer is HP F4180 All in one.

I have used Ubuntu and Mint on older computers without any problems whatsoever. Well, I should say once I get all the packages that allow me to watch DVD's and download music from eMusic and Amazon. Could not watch Netflix though. 

I am frustrated I spent the better part of 2 days just trying to get Ubuntu to boot and the thread that I had originally had up got moved because I did not title it correctly and asked whether I should switch. I can't even try it on this machine so I can't even make that determination. Of course if you all can help me get booted then I may need some help getting it going the way it supposed to get going with drivers etc. 

I have bookmarked this thread so I can keep track of replies. I am determined now because of all of the time invested to get some flavor of Ubuntu or Mint installed. 

I hope I have given you enough information and I am actually embarrassed having to ask all these questions. I really don't know where to even search it out.

---

### Post by yaoyao on 2013-12-24
Maybe you can go into your BIOS, check an option about SATA or Serial something, and try to turn it off(or on), my laptop cound't boot any windows system installation DVD versions after win xp.
I don't have my laptop beside, so can't help you for more details, go have a check on your bios and good luck bro.

---

### Post by DuckHook on 2013-12-24
Hi bgast7851 and welcome to the forums.

No need to be embarrassed about anything. That's why the community exists in the first place.

Just a few more questions:

1. Are you dual booting with Windows 8?
2. If so, is secure boot and fastboot turned on? They must be off for another OS to run.
3. Have you tried actually installing instead of LiveDVD?
4. Have you tried running/installing through USB instead of DVD?
5. When you say you've tried entering text at the splash screen, please describe in detail. Is it at LiveDVD "Try Ubuntu" screen? To my knowledge, you do not preface "nomodeset" with "ro".

If we cannot chase down your problem, it may be worthwhile to try a different non-Ubuntu-based distro. Arch-derived distros would be Manjaro or Chakra. You could also try Mageia or Fedora. The idea would be to at least get a working system so that we can probe HW (you may also end up liking these distros just as they are). From there, we can try installing Ubuntu or dual booting. The critical element is: tell us if Windows co-resides on your system.

---

### Post by grahammechanical on 2013-12-24
How far in the boot process do you get? Please describe what you see as the live session starts to load. That will give some clues. Oh, by the way, Ubuntu can handle secure boot. Ubuntu 12.04.3, 13.04 and 13.10 have a signed kernel that a secure boot motherboard will accept. You do need fast boot turned off and if the other OS is Windows 8 then there is a certain way that you need to load the live session and install Ubuntu. There are plenty of threads on this forum with advice on how to install Ubuntu on a machine with Windows 8.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by Mark Phelps on 2013-12-24
You're telling us what is NOT happening -- but to get help, you need to tell us what IS happening, as well.

You say Ubuntu gets farther in the boot process, but you need to tell us what happens when it stops working.

Also, you need to tell us what OS you have on the machine at present.

---

### Post by bgast7851 on 2013-12-24
Ok, give me a bit of time and I will create another flash drive with Ubuntu. I am also printing out the helps from the reply above and will attempt to get it sorted out with that. If so, I will come back in and say [solved]. I just put windows 8.1 on my machine a couple of minutes ago. Prior to that it was just windows 8...I am making a big assumption here that I will like Linux better.  I think for now I would like a dual boot and to actually put Linux on my external hard drive unless that is not such a good idea. The reason I want to try Linux so bad is because I constantly receive high CPU warnings and the machine bogs down a lot. I had Norton installed for anti virus but now I have ESET and that seems to help with regard to speed. 

I have been able to Fedora to boot. However when I want to install it, it does not recognize the available space on either of my hard drives and I don't know how to solve that problem. 

I tried Manjaro also and did not even get as far as Ubuntu. Same with PCLOS. 

Ultimately I would rather use Mint. 

I apologize for not being more specific as to what was happening because I was going from memory from several days ago, when I had almost given up.

---

### Post by bgast7851 on 2013-12-24
I made a bootable USB drive. I tried to boot. Secure boot is disabled. Fast Boot is disabled. Quiet Boot is enabled. When I tried to boot I said try Ubuntu without installing. Then I got a screen that said the system is running in low graphics mode with some choices to make. I chose to run in low graphics mode just one session. Then I got 

*Starting LightDM Display Manager
*Stopping send an event to indicate Plymouth is up

after that nothing happened and I did not know what to do.

---

### Post by bgast7851 on 2013-12-30
I am still trying when I get time just to try Ubuntu or Mint. Neither one works booting from a live DVD or USB....See above comment...that is where I left off.  I did a google and I found this:

Type Alt+Ctrl+F1
Then 
```
sudo apt-get remove Ubuntu-desktop
           
sudo apt-get install Ubuntu-desktop
```

after I did this I got :

```
Ubuntu@Ubuntu:~$

```

I don't know what to type there. Also what was said when I googled the above code was that it would install the missing x.org dependencies. My graphics is Radeon HD 8240. I have been at this for more than 2 weeks with no success. I would prefer Mint but if I can get Ubuntu booted in the live version then I would try to install on an separate USB hard disc attached to my computer.  All I want to do is determine if I would be better off with Linux. My other thread got moved but this is all about solving a very vexing problem.

Google really gets me no where. Maybe I just don't really know how to do a proper search. My windows 8.1 machine is running kind of OK. After I got rid of Norton for anti-virus and I am trying ESET, but I am hoping Linux will be better.

---

