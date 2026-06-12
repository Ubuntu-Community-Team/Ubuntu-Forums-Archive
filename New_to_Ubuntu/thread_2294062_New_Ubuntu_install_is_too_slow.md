---
title: "New Ubuntu install is too slow"
date: 2015-09-09
forum: New to Ubuntu
---

### Post by davi3p on 2015-09-09
I installed a 14.04 ubuntu version in a HP 18 all-in-one that came with Windows, formatted the whole drive. The problem is that it's too slow and with clunky animations, both on unity and gnome, it takes time to load and open everything, and ALL animations are clunky, and it froze with me once. Looking at the graphics in the system monitor the two cores often peak at 100% of usage, and mostly stay above 50%, which is weird since I'm only using the browser. There seems to be no memory leak, both memories stay in low percentages all the time.

The "details" in "system configurations" gives me that this is an AMD E1 1500 APU with built in Radeon 7310.

I searched for other situations like mine and most of them seem to be related to the graphic drivers, in some cases people were advised to use the proprietary, in some cases people advised to use the Open Source ones, in some cases people were advised to uninstall the proprietary. I went to "additional drivers" and tried all three (open source, fgrlx and fgrlx-updates), all three were listed there so I didn't have to download anything from AMD's site, and none of them solved my problem, with the open source being particularly bad since it didn't allow any resolution above 800x600. I didn't try the uninstall proprietary drivers option.

So, how can I know what exactly is happening with my PC?
Is it possible that it also has something to do with that legacy/UEFI thing in the BIOS? I messed around there before installing until I found the option to deactivate the safe boot so I could remove the then installed Windows, I don't remember how I left things there.

---

### Post by Geoffrey_Arndt on 2015-09-09
Well, often by installing multiple video drivers, they "walk-over" each other and conflict especially if the prior drivers are not completely purged.    The best place to start would have been just to install the most likely proprietary driver. . . reboot and test it out.    If no improvement then completely remove or purge the old driver, move to the next and ditto all the way through.

UEFI/BIOS etc. is not likely a cause for initial or follow-up graphics issue.    

Best to use main google search to check linux compatibility for your specific device (see below for starters)

[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+7310+Ubuntu+Compatibility&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+7310+Ubuntu+Compatibility&ie=utf-8&oe=utf-8)

---

### Post by Geoffrey_Arndt on 2015-09-09
One additional note, if you continue to have difficulties installing the driver(s) and having a fast-usable PC, I would suggest considering:

>   Installing Ubuntu-Mate version OR
>   Installing Linux Mint Mate version OR
>   Installing Xubuntu 14.03.3 or Xubuntu 15.04 and then upgrading in 3 or 4 months to next versin (15.10)

The default video drivers often work better "out-of-the-box" with these versions of Ubuntu or Mint - - however, this info just included as another option you do have.   While I personally don't prefer non-Unity Ubuntu, sometimes it's needed.    Ultimately, the very best way to run the latest and greatest Ubuntu with Unity is to order a "pre-installed" version such as those from System76 or similar Linux computer vendors.

See this for more info:  [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

### Post by davi3p on 2015-09-09
Thanks for the reply, Geoffrey.
> Well, often by installing multiple video drivers, they "walk-over" each  other and conflict especially if the prior drivers are not completely  purged.    The best place to start would have been just to install the  most likely proprietary driver. . . reboot and test it out.    If no  improvement then completely remove or purge the old driver, move to the  next and ditto all the way through.

I've found many replies in other places saying similar things. I don't remember which driver the OS was using at the beginning, I think it was the open source one. How then would I proceed to remove all of them and trying one per time since I'm not going to have any GUI to help me in the process? Specially because I don't know how I can know if the drivers have been completely purged.

> >   Installing Ubuntu-Mate version OR
>   Installing Linux Mint Mate version OR
>   Installing Xubuntu 14.03.3 or Xubuntu 15.04 and then upgrading in 3 or 4 months to next versin (15.10)

I'd like to stay with ubuntu on gnome because this PC is for my parents, and they learned to operate on gnome almost intuitively (actually better than what they did on windows), I've tried xfce, mate, cinnamon KDE and unity before and I don't think it would be so easy for them.
> 
Best to use main google search to check linux compatibility for your specific device (see below for starters)
As I said in the first post, the very softwares in ubuntu automatically recognized the processor and the GPU, already listing the proprietary drivers for me to download in the "additional drivers" if I wanted to. So I don't think compatibility is an issue, but from what I've seen in other places, AMD/ATI drivers seem to be a history of problems with ubuntu.

What I wanted to know at first was whether there was any way of knowing what's going on at all, some kind of log to check for example, I'm not even sure if the CPU/GPU is the problem. But the uninstalling drivers thing is worth checking.

---

### Post by Geoffrey_Arndt on 2015-09-09
OK . . first things first.   The Ubuntu-Mate distro uses the classic gnome2 desktop.    Mint-Mate uses (imho), an even nicer version of gnome2 with an excellent custom start menu and other intuitive system tools (it doesn't get an easier than Mint).

For what it's worth, _if that were my PC, I would download (post-haste) the Mint-Mate and Ubuntu-Mate iso's_, burn both to dvd or thumb-drive.   Then, as your parents are used to gnome, start with Ubuntu-Mate and see how that goes . . .

---

### Post by NathanRodriguez on 2015-09-09
You can try Lubuntu also, a variant focused on performance for "old" hardware. Works very fine here, even with Mate desktop installed, it's way more responsive than Win7.

---

### Post by mastablasta on 2015-09-10
here is how you remove them and install them in cli: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

use proprietary ones. the chip is supported. you might need to set it up properly. and remove any bad xorg.conf files.

there is no need for Mint and Xubuntu and Lubuntu and whatever other distros were suggested. Ubuntu should work with this chip. and if it doesn't chances are you will have same problems with other versions.

edit: another thing - i am not sure when the chip came out but you might need hardware enablement stack: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
or you can use a newer version of Ubuntu and see if it works better or not.

the reason for this is that in Linux drivers are part of kernel. newer kernel means newer drivers. so with newer hardware newer kernel is better (even if you don't use the default opensource drivers).

---

### Post by davi3p on 2015-09-10
Mastablasta, I uninstalled the fglrx through purge while using the  fgrlx-updates. Then I switched (reinstalled) to the fgrlx so I could  uninstall the fgrlx-updates, not sure if this is how it's supposed to be  done. Then I restarted the computer so the OS could switch to the new  driver, and when I initiated it it reported to me this problem (I'm  translating from my native language, not sure if this is how the message  also appears in english): "I'm sorry, an error occurred during the  installation of the program: packet fgrlx 2:5 200-0ubuntu0.5" and then a  HUGE log and I can't understand anything in it. I don't know if this is  the first time this message appears during initialization since this is  the first time I'm the one initializing this PC on ubuntu. But like I  said, **I am using the fgrlx right now**, and it's working fine except for the problems of sluggishness and clunkyness reported before.

I  don't know whether this whole instal-uninstall thing is working since I  have to be using one driver while uninstalling the other (or so I  assume), like I was doing: use fgrlx-updates, uninstall fgrlx, switch to  fgrlx, uninstall fgrlx-updates. And I don't know whether I should also  uninstall the OSS one and at what moment I should remove the xorg.conf. I can't just uninstall all three drivers (or at least the two fgrlx) and remove the xorg.conf at once, right? I wouldn't have any driver to run my GUI then.

About the new kernel thing, I did as the link in your post suggested and it told me that it was alreadu up to date so it didn't install anything.

edit: I did it just as the link you posted (the first one) while using the open source driver, it didn't work, the error message during initialization is gone, but the processor cores are still peaking at 100% very often, the animations are clunky, everything is slow. One of the things that are being made slow in the system is the openning of any new software, any software, even light stuff such as the terminal, takes a considerable time to open.

---

