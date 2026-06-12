---
title: "Looking to try Ubuntu"
date: 2016-02-15
forum: New to Ubuntu
---

### Post by hoffmann2 on 2016-02-15
Hey there,

I'm new here and I'm looking to try Ubuntu but I have some questions before I go ahead and get things rolling here.

First off, where do I find drivers and other support for my current hardware? 

My current hardware that has necessary drivers are as follows:

Motherboard: ASUS ROG Maximus VII Hero
CPU: Intel Core i7-4790K
GPU: ASUS ROG MARS 760 x 2 (Dual GPU GTX 760 Card)

Additionally, does Ubuntu have cross-platform support for software? 
There are definitely a few program I hope that I can bring with me since they're fairly useful (ex. ROG Gamefirst III, Logitech Gaming Software) and I can't seem to find any "Ubuntu" or Linux versions, so I wasn't sure if that means they just don't exist or don't need to have a separate version.

Lastly, 

I am currently running Windows 10 and am hoping that I can dualboot Ubuntu on the same SSD. 
Is this possible with Windows 10 and Ubuntu? 

I appreciate your help in the matter,

Thanks,

Hoffmann

---

### Post by Bucky Ball on 2016-02-15
Drivers and support for your current hardware are more than likely already included in the Ubuntu 'kernel' so you don't need to do the Windows thing of installing a driver for every bit of hardware. Drivers can generally be added manually if required (very new hardware, for instance, or problematic and the manufacturers of it don't play nice with the open-source community). 

If you [download the Ubuntu ISO]("http://www.ubuntu.com/download/desktop") and create bootable install media, boot from that, choose 'Try Ubuntu' at the options screen and this will take you to a desktop running from the install media, not the hard drive. This is called a 'live' session and will not alter your hard drive in any way (unless you do so manually from the live session). That will give some idea of how things will go. 

(A note: LTS (long-term support) release are supported for five years from release (14.04 LTS=April, 2014 release), all other releases, interim releases, are supported for nine months (15.10 released October, 2015). LTS releases can skip all the interims and be upgraded via the net to the next LTS (14.04> 16.04 LTS due in April). All releases, LTS and interim, can be upgraded via net to the next newest release (for instance, 15.04>15.10>16.04 LTS). So, go for 14.04 LTS (most stable) or 15.10.)

Cross-platform as in does it run Windows programs? No. Not natively. Ubuntu is NOT a drop in replacement for Windows. You can use software like 'WINE' which will allow you to run some Win programs nicely, others poorly and some not at all. If you are looking for a drop-in replacement for Windows and want to use a lot of Windows programs, stick with Windows. Ubuntu, and Linux generally, is not it (albeit some 'distros' are very customisable and can be made to *look* like Windows, but that is where most similarities end). 

Dual-booting with Ubuntu and any Win is not only possible but practised by the majority of users here. No problem.

Hope that helps, welcome to the forums, and maybe Ubuntu. :)

PS: You'll be doing a bit of research if you get into it so [have a read of this]("http://linux.oneandoneis2.org/LNW.htm"). Old, but many points still very relevant. If you get into Ubuntu, do so with an open mind, don't expect it to be exactly the same as Win (because it isn't), remember you didn't learn how to use Windows in a day and enjoy the learning curve. There's a ton of info out there to help you along and a heap of friendly support here and elsewhere to help you through any issues you might encounter on your journey ... and there's the pre-requisites. 

Good luck. :D

---

### Post by hoffmann2 on 2016-02-15
That definitely does help,

I'm not necessarily looking for a "drop in replacement" as you say, I was more so just curious if these things will be available since some of them are quite useful. 
Is there somewhere that I can check to see what software is available? Most software I can live without but not having VeraCrypt would make it essentially useless. 


Thanks,

Hoffmann

Edit:

Oh nice, I didn't realize there was a live version. I'll go give that a try right now.

---

### Post by Bucky Ball on 2016-02-15
> **hoffmann2 said:**
> That definitely does help,

I'm not necessarily looking for a "drop in replacement" as you say, I was more so just curious if these things will be available since some of them are quite useful. 
Is there somewhere that I can check to see what software is available? Most software I can live without but not having VeraCrypt would make it essentially useless. 


Thanks,

Hoffmann

Edit:

Oh nice, I didn't realize there was a live version. I'll go give that a try right now.

Yes, give it a try is the best way. Once at a desktop, make sure you are online with a cable or wireless (some wireless will not work 'out of the box') check 'Software Centre'. You can search for software in there in various categories and quite easily. There is another package manager called 'Synaptic Package Manager' which I find preferable. You can install it via the Software Centre (but be aware that anything you do on a 'live' session will be lost on reboot as it is not a hard drive install and saves everything to RAM, not hard drive).

Also, no, it's not a drop-in replacement for Windows, BUT, there are many alternatives to Windows programs out there: Libreoffice for Office (LO comes default with Ubuntu), Gimp for Photoshop, Thunderbird for whatever Win uses, Firefox for IE. 

As for Veracrypt. A disk encryption tool? Never used one, but you can encrypt your disk as part of the Ubuntu install. Not sure if it does the same as Veracrypt. [I had a quick look using 'ubuntu veracrypt']("https://duckduckgo.com/?q=veracrypt+ubuntu"). Get used to doing that! When looking for an alternative or information, just search for what you're looking for, then add 'ubuntu'. You'll find plenty.

(Just another thought: Ubuntu can be fairly 'hands on' in the beginning as you get to know it and get your machine the way you want it (there are many alternatives in the Linux world), but once things are right and the machine is stable, that's it. I run only LTS releases (generally, designed for production, server and work environments where machines are on for long periods and downtime is not an option) and I just use it. My laptop is rarely switched off and it just works. I haven't had a problem with it (14.04 LTS) in probably a year or so (that I haven't either caused myself or some hardware issue, not fault of OS).

What people say is, in part, true. Ubuntu just works, once you have it set up properly, that is. No six monthly reinstalls to clean out the cruft, no viruses, no hassle, at least for many of us. :D

---

### Post by hoffmann2 on 2016-02-15
> **Bucky Ball said:**
> As for Veracrypt. A disk encryption tool? Never used one, but you can encrypt your disk as part of the Ubuntu install. Not sure if it does the same as Veracrypt. [I had a quick look using 'ubuntu veracrypt']("https://duckduckgo.com/?q=veracrypt+ubuntu"). Get used to doing that! When looking for an alternative or information, just search for what you're looking for, then add 'ubuntu'. You'll find plenty.

Yeah that looks like the one. It's essentially the successor to TrueCrypt since it stopped being updated in 2015 and much more preferable to Windows' BitLocker (and their potential backdoors) and something I'll need to be able to access my other drives if and when I get Ubuntu installed. 

Admittedly, I have used Ubuntu once before a lonnnngg time ago (I think it was Ubuntu 9 or something along those lines) but I've since forgotten anything that I learned in my brief time there. I was too young to really get a good grasp of it and spent most of my time playing games on Steam which wasn't as supported in Ubuntu back then as I understand it is now. I do know it's not Windows and I'm not looking for a dressed up Windows imitator. I'm looking to get away from Windows which is why I'm coming back to Ubuntu. 

Thanks for all your help Bucky Ball, I'll keep your advice in mind for any future questions.

---

### Post by Bucky Ball on 2016-02-15
> **hoffmann2 said:**
> Admittedly, I have used Ubuntu once before a lonnnngg time ago (I think it was Ubuntu 9 or something along those lines) but I've since forgotten anything that I learned in my brief time there. I was too young to really get a good grasp of it and spent most of my time playing games on Steam which wasn't as supported in Ubuntu back then as I understand it is now. I do know it's not Windows and I'm not looking for a dressed up Windows imitator. I'm looking to get away from Windows which is why I'm coming back to Ubuntu. 

Thanks for all your help Bucky Ball, I'll keep your advice in mind for any future questions.

You're part way there, then. :) Yes, Steam is a happening concern in Linux now and sounds like you have a good understanding of the conceptual and practical differences between Ubuntu and Windows so you're not expecting a replica (many do and are well disappointed when that's not the case).

No probs with the help. That's why I hang around this joint! :D

---

### Post by mastablasta on 2016-02-16
you might have issues with live session having 2 GPU cards. the live session can not store the NVidia drivers installation needed to run the cards. you may need to unplug one card, install OS, install closed source proprietary drivers, reboot and then plug in the other card.

as long a so you don't expect windows and everything to work then you can investigate it. from the software you talk about - it seems you are into gaming. if so windows is a better platform as it is much better supported with the software as well as with drivers.

if you want to just explore Linux then it might be better to have a look at virtualbox or similar where you should be able to easily install and run Linux to see how it looks like. for example you can use this guide: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Ubuntu doesn't have "cross platform support". just like windows only supports windows software. hey they even dropped their DOS programme support. many older games do not work on latest windows.
still there are plenty of software alternatives available in Ubuntu. just nowhere near as many as in Windows. especially games part is underfed. luckily some windows software and games work in wine. but not that many.

Ubuntu software repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

wine application database: [https://appdb.winehq.org/](https://appdb.winehq.org/)

---

### Post by hoffmann2 on 2016-02-16
> **mastablasta said:**
> you might have issues with live session having 2 GPU cards. the live session can not store the NVidia drivers installation needed to run the cards. you may need to unplug one card, install OS, install closed source proprietary drivers, reboot and then plug in the other card.

as long a so you don't expect windows and everything to work then you can investigate it. from the software you talk about - it seems you are into gaming. if so windows is a better platform as it is much better supported with the software as well as with drivers.

if you want to just explore Linux then it might be better to have a look at virtualbox or similar where you should be able to easily install and run Linux to see how it looks like. for example you can use this guide: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Ubuntu doesn't have "cross platform support". just like windows only supports windows software. hey they even dropped their DOS programme support. many older games do not work on latest windows.
still there are plenty of software alternatives available in Ubuntu. just nowhere near as many as in Windows. especially games part is underfed. luckily some windows software and games work in wine. but not that many.

Ubuntu software repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

wine application database: [https://appdb.winehq.org/](https://appdb.winehq.org/)


I did manage to get Ubuntu to install properly. 

The card I have is not two video cards, it is two GPUs built into one card so removing one of the GPUs kills the crab. I haven't had TOO many problems thus far.

Thank you for that info though, much appreciated.

---

### Post by buzzingrobot on 2016-02-16
When the Linux kernel boots, it detects the hardware components in a system and automatically loads the appropriate drivers. It's very good at this. When you boot an Ubuntu install image, you're given the option to try it in live mode. That's an easy way to check out hardware compatibility.

Sometimes issues arise with very new hardware if the vendors do not release open source drivers and Linux developers haven't yet written their own.

The kernel will default to using an open source driver for the video card it detects.  The open source driver for Nvidia is called the Nouveau driver. Because it's a reverse-engineered effort, Nouveau may not handle some things -- demanding games, etc. -- as well as the proprietary drivers Nvidia releases. Those drivers can be installed in Ubuntu with the "Additional Drivers" tool. This lets you select a recommended proprietary driver and then downloads it, installs it and sets your system up to use it. (Can takes several minutes to get that done.) The web is full of how-to pieces outlining other ways to install Nvidia's proprietary drivers.  **Don't** use them. Use the Additional Drivers tool.

As already mentioned, look for Linux software that lets you do what you want to do, rather than Linux versions of Windows software. If you have a specific reliance on Windows, it's best to stay with Windows or set up a dual boot system. For example, if you need to create documents in a format that only MS Office can do, then, of course, you need to use Office. Photoshop and other Adobe tools are a good examples of this, as well.  Several very capable graphics tools exist in Linux, but if you need to live and work in the Adobe universe, you can't do that in Linux.

---

