---
title: "Error: linux-image-extra-3.16.0-60-generic (not installed)"
date: 2016-02-01
forum: New to Ubuntu
---

### Post by LDRoamer on 2016-02-01
I am new to Linux (haven't used it in quite a few years) I got an message that something had failed when doing updates using the Software Updater tool.  There was an automatic error report generated and this is a bit more of what is in it:



ProblemType: Package
DistroRelease: Ubuntu 14.04
Package: linux-image-extra-3.16.0-60-generic (not installed)
ProcVersionSignature: Ubuntu 3.16.0-59.79~14.04.1-generic 3.16.7-ckt20
Uname: Linux 3.16.0-59-generic i686
ApportVersion: 2.14.1-0ubuntu3.19
Architecture: i386
Date: Mon Feb 1 16:43:07 2016
DuplicateSignature: package:linux-image-extra-3.16.0-60-generic:(not installed):cannot copy extracted data for './lib/modules/3.16.0-60-generic/kernel/drivers/isdn/hardware/mISDN/hfcsusb.ko' to '/lib/modules/3.16.0-60-generic/kernel/drivers/isdn/hardware/mISDN/hfcsusb.ko.dpkg-new': unexpected end of file or stream
ErrorMessage: cannot copy extracted data for './lib/modules/3.16.0-60-generic/kernel/drivers/isdn/hardware/mISDN/hfcsusb.ko' to '/lib/modules/3.16.0-60-generic/kernel/drivers/isdn/hardware/mISDN/hfcsusb.ko.dpkg-new': unexpected end of file or stream

I was asked if I wanted to report this bug. I wasn't sure if I should but I did anyway. Its probably related to something I did or didn't do.  This is a new install of Ubuntu 14.04 (about four days old). I am not sure if I need to worry about and this and for certain I don't know what to do to fix it. Since this is a new install and I have no data on the computer it would be easy enough to simply blow away the installation and try again.  Computer is an ancient Acer Aspire One netbook with a 32 bit atom processor and 1.5 gigabytes of ram.

---

### Post by sandyd on 2016-02-01
Give this a try
```

sudo apt-get clean
sudo rm /var/cache/apt/archives/linux-image-extra-3.16.0-60-generic_3.16.0-60.80~14.04.1_amd64.deb
sudo apt-get -f install

```

---

### Post by LDRoamer on 2016-02-01
Don't bother trying to help me with this. I had to reinstall as the system was totally screwed.  I could log in but had no usb support, no network, graphics were goofy and all it would do is keep telling me there was a system error and do I want to report it. Pretty much nothing else worked. No sense in trying to sort it out when I have nothing to lose at this point and so reinstalled. What does trouble is that is the third time in a week that the Ubuntu has choked on an update and become totally unusable (and required a reinstall to fix).  

This old netbook came with Windows XP (which continues to run just fine on it) but with the end of XP support and not wanting to spend any money purchasing Win 10 I thought linux would be a great way to give the old girl some new life.  But if it continues to be a problem it is obviously not going to be a solution and I may just end up having to retire this machine (which would kind of **** me off - in a minor way).

As a point of interest everytime I have installed the installation gets to the point where it says you need to restart and at that point it freezes requiring a hard reset (power off).   Each time though it has succesfully booted to the desktop and I have been able to run programs without incident (such as firefox, the included office software and even Skype).

This latest installation locked  while I was on the phone and when I came back  there was a triangle in the password box, said wrong password, and then wouldn't let me log in again even though I entered the proper password. N password had been previouly entered and this appears to have just happened randomnly when the comuter locked. I am writing this from this latest Ubuntu installation so I did get back in after a reboot but I have pretty mucy zero confidence that Ubuntu and this machine will reliably work together. Windows XP works fine and the last time I reinstalled it was probably 6 years ago. 

It could be that the hardware is starting to fail on this old girl (she has been rode hard and put away wet lots of times) but you would think that it would show up in Windows which it doesn't.

I might try one of the other distributions but I am sort of running out of road on this. I was hoping I could get this thing working so I could carry it on my motorcycle trips and the like (and not worry about it since it basically has no value) but so far that doesn't seem likely given I have installed three times and the evidence is that none of these installations has been stable.

Any suggestions as to how I might improve my experience would be appreciated.

---

### Post by Bashing-om on 2016-02-01
LDRoamer; Hey;

I have had good results :

Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

on older hardware . 

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by LDRoamer on 2016-02-02
I will give lubuntu a try. My concen is that Lubuntu is just a variant of Ubuntu and if Ubuntu won't run in a stable fashion on this pc then Lubuntu probably won't either. But I have nothing to lose but time (although that is a bit of a precious commodity) and if things work out I will gain a working PC that I can use for email and the like. However my enthusiasm has waned considerably after three failed attempts. In each case it only worked for a few days and then total blew up when it tried to install updates. Also I really hadn't installed all that much or done anything really wacky with the system. Basically was just trying to use it for normal things (email, web browsing etc.).  Anyway will give it one more bash before giving up.

---

### Post by Bashing-om on 2016-02-02
LDRoamer; Welp; ,,,

My experience; (u)buntu is a resource hog, and it takes the hosses to run it .. needs at least 2 Gigs of ram and a better than a single processor for a good experience . One's video card has a lot to do with how the system performs . How much ram is video taking away from the CPU ?
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)
Even (l)ubuntu wants 1 Gig of ram at the minimum - in my experience.

One can go much lighter. I value functionality and speed above all other considerations in my computer . I do run on old hardware on a minimal install in a very tight environment. I boot to terminal and IF I want a GUI I start the lightweight xfce4 desktop .
However, building from minimal takes some familiarity with this our operating system by choice; But anyone who has the want to - to learn - can do it .

Then again, there are many other linux spins that are very light ! My preference due to familiarity is 'buntu in some shape, form or factor .

[INDENT][INDENT]old hardware, no biggy
[INDENT][INDENT][INDENT]just gets re-purposed
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by LDRoamer on 2016-02-02
Thanks all for the help and comments. I have removed Ubuntu and installed Lubuntu and so for so good (but its only been about two hours so will keep my fingers crossed that this installation will be stable).  For the record I wasn't that unhappy with Ubuntu. It seemed to run pretty well on this machine all things considered. Had it not blown up three times I would probably still be using it.  Lubuntu does seem a bit quicker though and ultimately that may be a better a system for this old net book (which I think if it is not the original acer net book then close to it).  If all goes well for the next couple of weeks then I will remove windows. I have a dual boot setup with Windows XP but don't see the point in keeping XP now that support is ended. 

Thanks and again and I hope this time it all goes smoothly.

---

### Post by Bashing-om on 2016-02-02
LDRoamer; Uh Huh .. :)

Looking forward to conclusion ; Let us know how it goes.

[INDENT][INDENT]dirty jobs
[INDENT][INDENT][INDENT]done dirt cheap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by LDRoamer on 2016-02-08
Lubuntu has been stable on this old net book and pretty fast given the relatively low powered hardware.  So I think I am over my initial woes and on to more productive things. I was going to delete Windows but I haven't done that in case I run into the odd application that doesn't run under linux.  If I find that I don't have anything that I can't do in Linux I will take windows off completely.  One concern I have though is that this machine has a 32 bit processor and the support for 32 bit Chrome is ending which I have to say is disappointing to me. I understand why they would do that as 32 bit processors are a thing of the somewhat dim dark past but I am hoping that this thing won't become an orphan. I am fine with Firefox and so long as it continues in 32 bit form then I will be good.

---

