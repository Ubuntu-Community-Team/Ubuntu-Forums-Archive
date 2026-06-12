---
title: "Computer won't load after updating from 12.04 to 12.10"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by Chomby on 2014-06-09
Hi, guys :) I've seen questions like this asked before, but none of the solutions worked for me, so I thought I would ask myself. A few weeks ago, I got a hand-me-down laptop with Ubuntu 12.04 LTS already installed (I'm not sure what means it was installed by, but if it was via CD, I don't have it). A few days ago, I was updating everything with Update Manager, and saw a box with an option to update me when a new upgrade is available, so I checked it, and right away it alerted me that 12.10 was available. So I followed all the steps to complete the upgrade, and everything seemed to be going well. Then finally, it said something like "reboot to finalize the changes," so I turned the laptop off, turned it back on, got the purple Ubuntu screen, then... the screen went black right before anything could load, and in the top left corner of the screen was what looked like a cursor to let you type, but you can't (I thought it might have been a terminal), and this screen doesn't change or go away.

So, is there any way I can fix this? I am an absolute newbie when it comes to Linux (I never used it before I got this laptop), so please explain anything to me like I'm a kid.
Thanks in advance!

---

### Post by coffeecat on 2014-06-09
It's odd that your 12.04 update manager was offering you an upgrade to 12.10 when 12.10 went end of life on May 16th. It should have only offered you an upgrade to the latest LTS version, 14.04. Which makes me wonder if there was something awry with how your installation was configured, but more of that in a moment. Since you are new to Ubuntu – and welcome to the forum, by the way! - a brief aside.

Ubuntu version numbers are based on year and month of release. Hence 12.04 = 2012 April, 12.10 = 2012 October, 14.04 = 2014 April. 12.04 and 14.04 are LTS (long-term support) versions, supported for 5 years on desktop and server. The intermediate versions, 12.10, 13.04, 13.10 were supported for only 18 months (12.10) or 9 months for 13.04 and later.

Which all means that even if you had not started the upgrade to 12.10, I would have advised not doing so – 12.04 is supported for just under 2 years yet. And by support, I mean bug-fix and security patch updates.

And back to how the system is configured. Since this is a hand me down, you don't know what the previous user may have done in terms of 3rd party software and configuration tweaks. If I had inherited that machine, I would want to make a clean install of Ubuntu and start afresh.

And the practical matter is that version upgrades that go sour, as yours seem to have done, are almost always very difficult if not impossible to fix. 

So – I suggest you think about making a fresh install for yourself of either the 12.04 version you have already been using, or the latest 14.04. Tell us what you want to do and we can point you in the right direction. The principle is fairly simple. You download an ISO file of the relevant release (all for free) and burn this to DVD or to a flash USB drive – you can do all this in Windows or MacOS. Also, post some details of the specifications of the laptop. And old one with limited RAM might be better off with one of the lighter Ubuntu variants such as Xubuntu or Lubuntu. If you have enough bandwidth you can download a variety of ISOs, burn them all to DVD/CD and try them all out live. That's one advantage of Linux – live CDs. Try before you don't have to buy! :)

---

### Post by Chomby on 2014-06-09
Thank you so much for all this info, I really appreciate it! My laptop is a Lenovo B570, which originally had 8 GB of RAM, but honestly, once I got the computer, I never bothered to check how much RAM was available. I'd like to install 14.04, so I would need to burn that to a DVD or CD? Pardon my ignorance, but say I got the disc with 14.04, how would I be able to actually download it to my computer if it won't completely load in the first place?

---

### Post by sandyd on 2014-06-09
> **coffeecat said:**
> It's odd that your 12.04 update manager was offering you an upgrade to 12.10 when 12.10 went end of life on May 16th. It should have only offered you an upgrade to the latest LTS version, 14.04. Which makes me wonder if there was something awry with how your installation was configured, but more of that in a moment. Since you are new to Ubuntu &#8211; and welcome to the forum, by the way! - a brief aside.

Ubuntu version numbers are based on year and month of release. Hence 12.04 = 2012 April, 12.10 = 2012 October, 14.04 = 2014 April. 12.04 and 14.04 are LTS (long-term support) versions, supported for 5 years on desktop and server. The intermediate versions, 12.10, 13.04, 13.10 were supported for only 18 months (12.10) or 9 months for 13.04 and later.

Which all means that even if you had not started the upgrade to 12.10, I would have advised not doing so &#8211; 12.04 is supported for just under 2 years yet. And by support, I mean bug-fix and security patch updates.

And back to how the system is configured. Since this is a hand me down, you don't know what the previous user may have done in terms of 3rd party software and configuration tweaks. If I had inherited that machine, I would want to make a clean install of Ubuntu and start afresh.

And the practical matter is that version upgrades that go sour, as yours seem to have done, are almost always very difficult if not impossible to fix. 

So &#8211; I suggest you think about making a fresh install for yourself of either the 12.04 version you have already been using, or the latest 14.04. Tell us what you want to do and we can point you in the right direction. The principle is fairly simple. You download an ISO file of the relevant release (all for free) and burn this to DVD or to a flash USB drive &#8211; you can do all this in Windows or MacOS. Also, post some details of the specifications of the laptop. And old one with limited RAM might be better off with one of the lighter Ubuntu variants such as Xubuntu or Lubuntu. If you have enough bandwidth you can download a variety of ISOs, burn them all to DVD/CD and try them all out live. That's one advantage of Linux &#8211; live CDs. Try before you don't have to buy! :)
Not sure if its related, but on some computers, ive noticed that it refuses to upgrade to trusty unless you add the development flag.


Demo on one of my servers:
```

root@MaisieWilliams:/srv/redmine# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise
root@MaisieWilliams:/srv/redmine# do-release-upgrade
Checking for a new Ubuntu release
No new release found
You have new mail in /var/mail/root
root@MaisieWilliams:/srv/redmine#

```

However,
```

root@MaisieWilliams:/srv/redmine# do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,148 kB]                                                  
Fetched 1,148 kB in 0s (0 B/s)                                                 
authenticate 'trusty.tar.gz' against 'trusty.tar.gz.gpg' 
extracting 'trusty.tar.gz'
[screen is terminating]

```

Odd behaviour tbh

---

### Post by coffeecat on 2014-06-09
> **sandyd said:**
> Thats because on some computers, ive noticed that it refuses to upgrade due to point releases.

For example, 12.04.4 wont update to trusty, because trusty is at 14.04 - though it will update whenever trusty ever reaches 14.04.4

Yes, thanks. I remember now. 12.04 won't offer to upgrade to 14.04 until July, if I remember correctly. Offering to upgrade to 12.10 after 16th May must be a bug. I'm surprised.

> **Chomby said:**
> Thank you so much for all this info, I really appreciate it! My laptop is a Lenovo B570, which originally had 8 GB of RAM, but honestly, once I got the computer, I never bothered to check how much RAM was available. I'd like to install 14.04, so I would need to burn that to a DVD or CD? Pardon my ignorance, but say I got the disc with 14.04, how would I be able to actually download it to my computer if it won't completely load in the first place?

You need another computer to download the ISO and burn the disk. 8GB is more than enough for Ubuntu. Here's something to get you started:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

That's both your download link and links in that page to burn the ISO to disk, or USB stick. Once you've burned the DVD, or prepared the USB stick, you set your BIOS to boot from it, and it will boot into a choice between "try Ubuntu" and "install Ubuntu". Select try and you can tryout the live session without committing yourself to installing. It will be a bit sluggish but it's a useful exercise to see if your hardware is working out of the box.

---

### Post by Chomby on 2014-06-09
> **coffeecat said:**
> Yes, thanks. I remember now. 12.04 won't offer to upgrade to 14.04 until July, if I remember correctly. Offering to upgrade to 12.10 after 16th May must be a bug. I'm surprised.



You need another computer to download the ISO and burn the disk. 8GB is more than enough for Ubuntu. Here's something to get you started:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

That's both your download link and links in that page to burn the ISO to disk, or USB stick. Once you've burned the DVD, or prepared the USB stick, you set your BIOS to boot from it, and it will boot into a choice between "try Ubuntu" and "install Ubuntu". Select try and you can tryout the live session without committing yourself to installing. It will be a bit sluggish but it's a useful exercise to see if your hardware is working out of the box.

That sounds great. Sorry for all the questions (I didn't know I didn't know this stuff, hehe), but how would I set the BIOS to boot from it?

---

### Post by coffeecat on 2014-06-09
> **Chomby said:**
> how would I set the BIOS to boot from it?

That varies according to the make and model. I have no experience of Lenovo so I can only guess. Seeing as the Lenovo B570 is a discontinued model that originally ran Windows 7, it probably (hopefully!) has a traditional BIOS and not the newer UEFI that comes with Wndows 8 machines. The POST screen (the initial splash when you first turn on) may prompt you to press a key for setup - often DEL or one of the function keys. Or with some makes of machine, one of the F keys pops up a menu which allows you to select which device to boot from. You'll need to check the manual for the machine if none of those help.

---

### Post by Chomby on 2014-06-09
Alright, I think I've got this :) Again, thank you so much for all of your help. Now I have to go run out and buy some blank DVDs. I'll come back later if I have any more questions.

---

### Post by Chomby on 2014-06-09
Okay, I downloaded 14.04 to a DVD, installed it on my computer, and rebooted. Now, instead of loading, it comes up with a window that says Boot Menu|App Menu, and once again, I'm totally lost. I'll include pictures of the Boot/App Menu window, so hopefully that will help. Am I on the right track at all with this?

Boot Menu-
[IMG]http://i59.tinypic.com/1zqf2wo.jpg[/IMG]

App Menu-
[IMG]http://i59.tinypic.com/i6b4i8.jpg[/IMG]

---

### Post by Vladlenin5000 on 2014-06-09
Choosing option #2 from the boot menu whenever you need to boot from a CD or DVD should be kinda obvious...

---

### Post by Chomby on 2014-06-09
Choosing any of those options just takes me to a black screen... 
Just rebooted again, now it brings up a GNU GRUB (?) menu, that gives options to either (1) Try Ubuntu without installing, (2) Install Ubuntu, (3) OEM install, and (4) Check disc for defects. I've already installed 14.04 with the disc, so I am really at a loss :(

---

### Post by Vladlenin5000 on 2014-06-09
> **Chomby said:**
> Choosing any of those options just takes me to a black screen... 
Just rebooted again, now it brings up a GNU GRUB (?) menu, that gives options to either (1) Try Ubuntu without installing, (2) Install Ubuntu, (3) OEM install, and (4) Check disc for defects. I've already installed 14.04 with the disc, so I am really at a loss :(

Indeed. It booted again from the installation DVD. If that wasn't what you want then you could've tried the HDD option. If that fails it doesn't hurt to try to install it again. Take note of any errors and post them here. Then, someone may be able to suggest something.

---

### Post by Chomby on 2014-06-09
Reinstalled again, rebooted, and the Boot/App menu came up again. I selected #2 on the Boot Menu (CD/DVD), it quickly flashes text that says something like "could not open," and then it takes me to a black screen again. I'm about to give up technology all together and go live in the woods. Thank you all for your suggestions, though!

---

### Post by coffeecat on 2014-06-10
> **Chomby said:**
> Reinstalled again, rebooted, and the Boot/App menu came up again. I selected #2 on the Boot Menu (CD/DVD), it quickly flashes text that says something like "could not open," and then it takes me to a black screen again. I'm about to give up technology all together and go live in the woods. Thank you all for your suggestions, though!

The screenshots you posted in your post #9 show a menu that your machine's BIOS is putting up. I don't know why. Perhaps your BIOS is now configured to show that menu every time. Most BIOS setups will only show a menu like that if you press a certain function key. 

If you select #2, you will simply boot up from the DVD every time even if you have installed to the hard drive. If you have installed Ubuntu to the hard drive you need to select #1, "ATA HDD..." That's your internal HD.

---

