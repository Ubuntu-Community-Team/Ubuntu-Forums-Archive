---
title: "100% n00b question on installation"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by scottaa1 on 2008-08-29
Hello All,

First time listener, first time caller.  I decided to give ubuntu a try on a spare laptop (Toshiba Satellite, P4 1.8 GHZ, 512MB RAM, no internal ROM drive because it died).  A friend said I could use wubi to do the installation seamlessly.  I DL'd that, it DL'd the 700MB files, was processing along nicely, then hung at 98%, at a message that I believe was 'removing language pack gnome' (sorry, that was an hour ago, I don't remember exactly what it said).  After it had been hung for almost an hour (altho the mouse still worked, so the laptop hadn't frozen), I forced a reboot.  If I select the ubuntu boot option, it gets to where it asks for my login and then password, but then I get a bunch of denied access messages and can't go any further.

This is my first foray into this type of thing, so nothing is too n00b to point out to me.  I searched in the forums and saw a post from 2007 saying wubi required Windoze... I have no idea what that is.   It's entirely possible my friend overlooked that requirement, he's not exactly detail oriented.

I'm not sure what I should do to try to re-run the installation, or if I should start over, or if I should just download the .iso, burn it, and run it from a USB drive.  Any input to help this totally uninitiated person would be appreciated. 

Thanks,
Scott

---

### Post by drs305 on 2008-08-29
Wubi installs into the windows file system, so you have to start with a Windows OS. You access wubi, once installed, via the windows boot manager.

If you are trying to make this the only OS of the computer or a truly dual-boot system you need to install it via the LiveCD or AlternateCD.

To download the iso's:
[Get Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by caljohnsmith on 2008-08-29
> **scottaa1 said:**
> I searched in the forums and saw a post from 2007 saying wubi required Windoze... I have no idea what that is.
Hi Scott, welcome to the forums. :) "Windoze" is just a derogatory term that many Linux geeks use when referring to Microsoft Windows.:biggrin: Wubi is used to install Ubuntu inside Windows so that you don't have to do any repartitioning of your HDD. Do you have Windows on that computer all ready or is that computer meant to be 100% Ubuntu? Some people may feel differently, but my personal opinion is if you can, definitely install Ubuntu to its own partition, as opposed to using Wubi; Wubi just adds another layer of complexity that can sometimes cause things to go wrong.

---

### Post by scottaa1 on 2008-08-29
> **drs305 said:**
> Wubi installs into the windows file system, so you have to start with a Windows OS. You access wubi, once installed, via the windows boot manager.

If you are trying to make this the only OS of the computer or a truly dual-boot system you need to install it via the LiveCD or AlternateCD.

To download the iso's:
[Get Ubuntu]("http://www.ubuntu.com/getubuntu/download")
Thanks.  I got wubi via windows, ran it, and it did its thing and then said reboot was required.  I then went into the ubuntu boot, where it appeared to be completing a normal installation, with checking stuff, deleting stuff, setting stuff up, etc.  As I said, got to 98% complete of the installation and then stopped.   

I'm now planning to download the iso and burn it, try it that way.  Thanks for your fast reply.  I'll be back to let you all know how things are going!

Scott

---

### Post by scottaa1 on 2008-08-29
> **caljohnsmith said:**
> Hi Scott, welcome to the forums. :) "Windoze" is just a derogatory term that many Linux geeks use when referring to Microsoft Windows.:biggrin: Wubi is used to install Ubuntu inside Windows so that you don't have to do any repartitioning of your HDD. Do you have Windows on that computer all ready or is that computer meant to be 100% Ubuntu? Some people may feel differently, but my personal opinion is if you can, definitely install Ubuntu to its own partition, as opposed to using Wubi; Wubi just adds another layer of complexity that can sometimes cause things to go wrong.

Hi, and thanks.  Yes, that laptop has WinXP on it.  The installation seemed very logical and I didn't have any questions about it along the way, it just stopped at 98%.  I want to eventually make it 100% ubuntu, but I was advised that my first attempt should be with Windows still on it.  I want to eventually have it entirely non-Windows, but I want to get some familiarity first with how this all works.

Thanks again,
Scott

---

### Post by drs305 on 2008-08-29
It sounds like there was a problem on the wubi install. If it installed successfully on windows boot you should get an option to either start windows or wubi. Wubi is designed to allow a user to try out ubuntu without making a specific partition, as was stated earlier by caljohnsmith.

You can either try to reinstall wubi or make a dual-boot system, which is what I would recommend. During the installation it will ask how you want to set up the partitions. Just make sure you don't wipe out your windows partition. 

If you have access to another computer during the install and you have questions just come on back and people here will help you out.

Welcome to ubuntu.

---

### Post by scottaa1 on 2008-08-29
> **drs305 said:**
> It sounds like there was a problem on the wubi install. If it installed successfully on windows boot you should get an option to either start windows or wubi. Wubi is designed to allow a user to try out ubuntu without making a specific partition, as was stated earlier.

You can either try to reinstall wubi or make a dual-boot system, which is what I would recommend. During the installation it will ask how you want to set up the partitions. Just make sure you don't wipe out your windows partition. 

If you have access to another computer during the install and you have questions just come on back and people here will help you out.

Welcome to ubuntu.

Thanks.  Yes, it gave me the dual-boot option.  Perhaps my mistake was when it first told me it needed to reboot that I selected the ubuntu option too early?  It did seem to progress in to what looked like a very normal and proper installation (and I think I was doing the right thing; it literally hung on what said it was deleting gnome language file, or something, at 98% of system setup).  I have this other laptop right next to it, so I'll be able to ask along the way.  Going to give it another try, thanks for everyone's input!

Scott

---

### Post by Tatty on 2008-08-29
Sometimes wubi-related problem can be hard to solve on these forums as wubi is still fairly new and most people here tend to be used to more traditional ubuntu installations.

Im not sure why the installation failed, it may be that the download was corrupted somehow, it may be worth trying to re-download and re-install it from scratch.
If you could post the *exact* error messages which are appearing, that may help someone figure out whats going wrong.


Personally though, i would reccommend a more traditional ubuntu installation with a live CD.  You should partition your drive so you can dual-boot both ubuntu and windows (best not to get rid of windows, at least until you are comfortable with ubuntu, so you always have a fallback)
These websites will help you with this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Backup all your valuable data first, and make sure you pay close attention to the part on partitioning, as this is the only point where if you dont read it carefully you could accidentally break you windows install.

---

### Post by scottaa1 on 2008-08-30
Hi again!  I got the install to work on my second attempt and can boot into ubuntu.  However, when I actually try to do anything it locks up.  Actually, I was able to play a game of chess, but when I tried to go in and look around the network settings, or open firefox, or the word processor, it freezes.  

I'm going to search on 'lockup' on the forums to see if I can find anything that sounds like a likely candidate.  If anyone has any thoughts, I'd love to hear them.

Thanks,
Scott

---

