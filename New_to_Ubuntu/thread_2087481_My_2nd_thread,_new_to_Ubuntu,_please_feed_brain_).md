---
title: "My 2nd thread, new to Ubuntu, please feed brain :)"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by HarlanT on 2012-11-23
Finally up and Ubuntu'd
Do I need an Antivirus program and if so which one please?
Is Wine preinstalled? "WOW" "Shaiya" "Diablo II III"??
Then later I will get serious, and begin application installing. ughhh work stuff.
I forgot to wish everyone a Happy Turkey Tossing day! so a Belated HTTD
Thanks for the help

Harlan

---

### Post by lisati on 2012-11-23
Q: Do I need antivirus software with Ubuntu?
A (short): It depends on who you talk to.

You might find the information at [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) helpful.

I generally only use antivirus on Ubuntu to scan emails that might be sent to or received from Windows users. For one thing, my boss might be less than amused if I accidentally forward a file to my colleagues that won't hurt my Ubuntu installation(s) but causes mischief on the computers at work. My choice of AV product on my server is based around ClamAV.

---

### Post by 73ckn797 on 2012-11-23
Wine has to be installed. You can find it in the Software Center. I would recommend using Virtual Box, also in Software Center. Install Windows in it and not have to mess with Wine issues. [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by RoosterHam on 2012-11-23
Welcome to the world of Ubuntu, and by extension the worlds of opensource and unix. (unix-likes)

VirtualBox is great for compatibility with Windows. But if you have slightly higher gaming performance expectations you may be much more satisfied with the results of some efforts of configuring wine, which you'll have to install yourself.

I'd recommend you install a firewall setup tool, such as Firestarter or such. like [[COLOR=#DD4814]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635") said, antivirus is more about protecting windows systems you'll communicate with. But firewall rules are important for all networked computers.

---

### Post by HarlanT on 2012-11-23
Thank you Thank you for the wonderful fast replies
Since I care about my friends, family and colleagues, I will heed the advice here, and get a AV protection going. Very good point on passing along to others, not my cup of tea (Java now huh!)

lisati: ty for the link and wisdom, on my way to do reading there. Is ClamAV good for Desktop? or is this a server style.
My use is personal PC and only networking to access old system, and to create internet access.
73ckn797: ty for the link and thoughts. I will install Wine if it isn't already installed, and will research this virtual box you mentioned.

RoosterHam: ty for the heads up advice here. Gaming is rather intense on this end......I work hard so I have to play hard to get over the work damages! must keep system balanced! Work some... Play MORE! I will investigate the Virtual vs Wine ways to play MMORPG games and cross my fingers for compatibility too.
Thank you for the welcome :)
Ill post back later as I progress,  digress or as it happens.
Once I am feeling like I am in the drivers seat, rather than in the back seat, Ill try to post a thoughts for others to read, hopefully helpful, things to expect or something.

Cheers

Harlan

---

### Post by DuckHook on 2012-11-23
For me, one of the unalloyed pleasures of Linux is the fact that I don't need anti-virus. It just bloats and crufts up the OS and I'm happy to leave that problem to Windows. My Windows installations invariably spend the first 15 minutes of every boot-up downloading virus signatures, checking for engine updates, plugging up my network, checking my entire HDD and generally slowing my system down to a crawl.

The downside of Linux is that no mainstream games are compiled for it. WINE is a brave attempt to bring Windows games to the Linux OS, but it is finicky, quirky and won't run most of the games out there without lots of tweaks and at least a few missing features. And if your games are anywhere near bleeding edge, you will not be happy running them in a virtual machine. The overhead incurred in running a VM on top of Linux is so great that the demands made by modern games will choke the VM, to say nothing of the fact that none of the higher end functions of your GPU will be available to you.

I run Diablo 2 in WINE quite happily, but have not even bothered to try D3, because my old box would probably die trying to run it in Windows much less WINE.

My suggestion: dual boot for now. If and when you find yourself rarely touching Windows, then you can nuke it and recover the disk space. Until then, you will have the full convenience of using whichever OS is best for your need of the moment.

---

### Post by monkeybrain2012 on 2012-11-23
Antivirus is basically for protecting Windows users (clamAV only detects Windows virus and is rather useless for that purpose) I don't run AV on any of my Linux installs, it is not my responsibility to babysit Windows users and I assume they would have the good sense to run AV on their ends. If not even if I scan all my emails it is not going to save them. 

Instead of running old Windows games on WINE you may also want to check out some native Linux games. [http://www.lgdb.org/list_games](http://www.lgdb.org/list_games) The developers work hard for them and the worst thing is that people don't even know their existence. Maybe you will find a few that catch your fancy. :)

---

### Post by HarlanT on 2012-11-23
> **DuckHook said:**
> For me, one of the unalloyed pleasures of Linux is the fact that I don't need anti-virus. It just bloats and crufts up the OS and I'm happy to leave that problem to Windows. My Windows installations invariably spend the first 15 minutes of every boot-up downloading virus signatures, checking for engine updates, plugging up my network, checking my entire HDD and generally slowing my system down to a crawl.

The downside of Linux is that no mainstream games are compiled for it. WINE is a brave attempt to bring Windows games to the Linux OS, but it is finicky, quirky and won't run most of the games out there without lots of tweaks and at least a few missing features. And if your games are anywhere near bleeding edge, you will not be happy running them in a virtual machine. The overhead incurred in running a VM on top of Linux is so great that the demands made by modern games will choke the VM, to say nothing of the fact that none of the higher end functions of your GPU will be available to you.

I run Diablo 2 in WINE quite happily, but have not even bothered to try D3, because my old box would probably die trying to run it in Windows much less WINE.

My suggestion: dual boot for now. If and when you find yourself rarely touching Windows, then you can nuke it and recover the disk space. Until then, you will have the full convenience of using whichever OS is best for your need of the moment.

DuckHook:
TY for the thoughts here.
As I was afraid of, and yes am prepared to dual boot (ALT Boot for me keeping drives dedicated to OS) 
On my other side, (non gaming and serious) I must use Autocad, and other serious windows based audio analysis software, and worry that the new Windows will also have issues here, so once I get my rear behind the Ubuntu wheel, I will have to do some serious research of linux based programs, to find "ALL" that I can migrate to, and leave "ONLY" those I can not change over to Ubuntu on the Alternate Boot.
This is the main reason I did not switch 3 years ago, let alone 7 years ago.
What will replace Adobe Premier? Cooledit Pro? Autocad 2005/8/9?
I cringe at the thought of the learning curve here, to find the flow from old ways to new ones, since there is a good work flow "now" being able to work with all the aspects of sound analysis, import to photo-shop, export to premier, export to cooledit, reimport... and so on. But we will see!
I'll remain optimistic for now and forge on through here.
Net is to find drivers for my Vid card now. Learn the update process.
Thanks again for all help!

Harlan

---

### Post by DuckHook on 2012-11-23
> **HarlanT said:**
> I must use Autocad, and other serious windows based audio analysis software

If you use AutoCAD, then you simply have no choice but to stick with Windows at least to some degree. It will work nicely up to all of the 2D features in a VM provided that you have the hardware horsepower, but it will not work at all in WINE. Have not tried the 3D features in a VM, but would not hold my breath. 3D tends to be bad on VMs.

> What will replace Adobe Premier? Cooledit Pro?

AutoCAD is your biggest problem. Linux tends to have decent alternatives for most other proprietary stuff, but CAD is so specialized and tethered to proprietary formats that there is sadly no other choice. Moreover, CAD files have to be absolutely and utterly precise from consultant to client or you risk operational and liability issues. Many users are already picky about subtle changes in MSWord docs but the need for absolute veracity in CAD is orders of magnitude higher than in anything else save, perhaps, accounting.

> I cringe at the thought of the learning curve here...

I'm not going to try selling you a half-truth. It won't be easy and some days you will ask why you bothered trying to make the change. What I will tell you is that the end result is worth it. When you are standing at the office supply store adding up the cost of all those proprietary apps and coming to the conclusion that you could purchase a small car for what you would have to pay in aggregate, and then realize that you are paying nothing in the Linux world except some time and sweat, there is a real sense of satisfaction and achievement. And when you slowly grow from the uncertain user to the comfortable user to one who has enough knowledge to advise new users on a forum like this, then you not only feel satisfaction, but a sense of being a part of something bigger than oneself. I'd better stop now before I get too maudlin.:redface:

---

### Post by HarlanT on 2012-11-23
> **DuckHook said:**
> If you use AutoCAD, then you simply have no choice but to stick with Wi....

I'm not going to try selling you a half-truth........:redface:

Thank you DuckHook for your words
I appreciate brutal honesty above all and so it seems........ I have some testing to do.
I still have 3 days to get things sorted out and will install a few Virtual Machine programs and test things in each one. Is the best scenario for now, and maintain a boot drive for the what's needed for all else.
I can not move away from Auto-Cad the same goes for a few other programs still.
But optimistically speaking, the future might change many issues as well.
I first have to learn "WHAT" is available and decide on use/ compatibility and go from there. 
Thanks monkeybrain2012: nice link for games :) Ill check them out! 
I will post back once I test the VM machines out and share my thoughts....... probably take a few hours (12) and a nap too.

Harlan

---

### Post by Mark Phelps on 2012-11-24
BEFORE you install Wine and try running Diablo III, suggest you read the details at the WineHQ site:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13484]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13484")

Regarding GAMING, now that MS is switching to Direct X v11+ for new games, that make Linux gameplay under Wine even  more uncertain.  So, for Windos gaming, a Windows setup is becoming even more of a requirement.

Regarding Windows apps like Autocad, while the situation might improve down the road, the problem with using any high-end Windows apps in Wine is that they are constantly being upgraded over time, and the newset versions tend NOT to work, or you have to wait months until folks figure out how to make them work.

So basically, as long as you are tied to Gaming and MS only apps, you will also be tied to retaining a dual-boot system (like so many of us).

---

### Post by HarlanT on 2012-11-24
> **Mark Phelps said:**
> BEFORE you install Wine and try running Diablo III, suggest you read the details at the WineHQ site:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13484](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13484)

Regarding GAMING, now that MS is switching to Direct X v11+ for new games, that make Linux gameplay under Wine even  more uncertain.  So, for Windows gaming, a Windows set up is becoming even more of a requirement.

Regarding Windows apps like Autocad, while the situation might improve down the road, the problem with using any high-end Windows apps in Wine is that they are constantly being upgraded over time, and the newest versions tend NOT to work, or you have to wait months until folks figure out how to make them work.

So basically, as long as you are tied to Gaming and MS only apps, you will also be tied to retaining a dual-boot system (like so many of us).

Thank you Mark for the thoughts.
Yep I agree, and in fact am installing the Wine, VMWare, and Virtual box to play with.
I suppose soon Ill be asking how to UNINSTALL in Ubuntu LOL
So far I have the Vbox installed, and a WINXP virtual up and running. Pretty nice really! First test was the Shaiya game....... it downloaded, it installed and it ran right up to the the standard boot screen, and........ the failure is the game, not the VM as the new release of the game is NOT "VM" Compatible, Clearly stating that for the error message, no matter what OS you are based on.
I am fairly sure this change was for the gaming industry and security issues, so this has nothing to do with the compatibility and operation of the programs VM and foundation OS.
I will be installing Autocad shortly and do a test run, but am rather encouraged by the smoothness of the VM.
I can say I recommend Virtual Box as far as install, setup and basic operation.
After Autocad will be a test of some audio apps.

Fun Fun Fun

Harlan

---

### Post by philinux on 2012-11-24
Glad you're having fun. Please take time to read this for future threads.


[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

