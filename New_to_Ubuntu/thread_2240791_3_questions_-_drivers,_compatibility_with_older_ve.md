---
title: "3 questions - drivers, compatibility with older versions, installation problems"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by mr-bzyk on 2014-08-22
Hello,
I have few questions from beginner. Maybe some of them should be separate threads but probably answers are simple for more experienced users.
1st I'm using Ubuntu 14.04 LTS 64 bit and AMD A10-7850k APU - from the driver list I can choose open source drivers or property drivers but there is no updates for property drivers is it possible that this update will work automatically or I should do it manually?

2nd How to launch software that is compatible with Ubuntu 12.04 and there is no support for 14.04? I was using splashtop on Ubuntu 12.04 but it doesn't work on 14.04. I was trying with this [https://support-splashtoppersonal.splashtop.com/entries/43459488-Splashtop-personal-can-t-be-installed-on-ubuntu-14-04?page=1#post_25375757](https://support-splashtoppersonal.splashtop.com/entries/43459488-Splashtop-personal-can-t-be-installed-on-ubuntu-14-04?page=1#post_25375757)

3rd I can't install Ubuntu 12.04 LTS (both 32 and 64 bit) since I've changed my hardware (AMD A10-7850k APU & MSI A88XM-E45 motherboard) - the installation interface doesn't start (in normal use the software ask about do I want to tray or install Ubuntu - I don't get there).
I will be grateful for any kind of help.

---

### Post by grahammechanical on 2014-08-22
If only the answers were simple! I would give a lot more help on this site than I do.

Updating proprietary video drivers? Go to System Settings>Software and Updates and in the Ubuntu Software tab make sure that the box labelled Proprietary Drivers for Devices (Restricted) is ticked. An update to a proprietary video driver might break the loading of Ubuntu. The Ubuntu developers cannot make adjustments to proprietary software. All the Ubuntu developers can do is pass on bug reports to the owners of the software. Whether the bugs get fixed is out of the control of Ubuntu developers.

You can say the same thing about the software that people install in Ubuntu. It is the responsibility of the software developers to keep their software up to date with the development of Ubuntu if they want people to use their software. This is especially true of software that is not available in the Ubuntu Software Centre.

Go down to section 6 - F6 options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Knowing the answer is one thing. But giving the answer is not a simple process. Accuracy is important, Research is necessary. And time is used up.

Regards

---

### Post by mr-bzyk on 2014-08-22
Thanks for your answer.
Most important thing for me are drivers so maybe I will describe it more clearly:
In softwear center I've marked like in picture below
[https://imageshack.com/i/iqSPrOjgj](https://imageshack.com/i/iqSPrOjgj)

but my drivers are version 13 something (like on screen - sorry that it is in Polish I have system language english but catalyst is in Polish and I can't change it)
[https://imageshack.com/i/pbPRr5gaj](https://imageshack.com/i/pbPRr5gaj)

and on AMD web site the newest version is 14 something
[https://imageshack.com/i/ipENPunfj](https://imageshack.com/i/ipENPunfj)

I didn't install drivers manual. I've marked option in software center (like in a first picture) so I'm curious do I get automatic updates (I don't think so but maybe I should wait) or I should update it manually?

---

### Post by sotiris2 on 2014-08-22
Why do you want the latest version? Are you for example having specific issues? Also nowadays opensource radeon and catalyst are very very close in performance. I used to use catalyst for my 7770 pci card but after making a system with an 6600k apu I saw that open source driver was much better than before, and most importantly NO TEARING. 

If you want the latest catalyst here's a good [guide](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide). Be sure to unistall the catalyst version you have now first (switching to open source driver via software and updates and rebooting should do it).

---

### Post by mr-bzyk on 2014-08-22
Thanks for the link, I don't understand half of it but if I'll decide to install this drivers I'll search for explanation of some things :)
Why I want to install latest version of drivers? - I like to play some games from time to time and I have problems with graphic in The Witcher 2, and in the description on AMD website there is information that they solve some issues with this game. Also I thought that I can change how many memory is assigned to video card (but now I have no idea where and how to change it). Last thing is that I always try to be up-to-date with my software.
I didn't test open source drivers on this hardware but maybe I should.

---

### Post by ian-weisser on 2014-08-22
> **mr-bzyk said:**
> from the driver list I can choose open source drivers or property drivers but there is no updates for property drivers is it possible that this update will work automatically or I should do it manually?

It will update automatically.
Do not expect it to update a day or two after upstream release. Only important bugs are fixed in current packages between releases.
Ubuntu generally updates most packages every six months. Look for driver updates then.

---

### Post by mr-bzyk on 2014-08-23
Thanks for all answers. I think that I get some basic knowleadge - especialty about drivers updates and it was most important for me.

---

