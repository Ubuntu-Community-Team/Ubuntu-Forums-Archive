---
title: "Need To Install My ATI Catalyst Graphics Drivers"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by DoctorVarney on 2012-07-09
I've just got up and running with Ubuntu and now it's time to install my ATI Saphire Graphics card and Catalyst centre.   I put the disc in, that came with my card, but nothing is happening.  I tried opening the directory and running the setup.exe but again, no dice.

Are there special drivers needed for Ubuntu that I can download or another version of this available somewhere?  I've looked on the internet but can't seem to find any.

---

### Post by coffeecat on 2012-07-09
The disc that comes with the card only has Windows drivers. You may find that the default open source driver is perfectly adequate for you. My Radeon HD6450 gives me Unity and dual-monitor support just fine in 12.04 with the open source driver. Which chipset is your card?

If not, install the proprietary driver from the Additional Drivers utility.

---

### Post by DoctorVarney on 2012-07-09
I can't get the same high resolution settings or dual monitor support with just the Ubuntu drivers.  The Catalyst Control Centre gives me extra control, whereas the Ubuntu control panel is just bog standard.  My monitor and card are capable of some very high resolutions, so I want the proper software for my card.

I already ran the proprietary drivers scan from the Additional Drivers utility and nothing came up. 

Sorry, I have no idea what exact chipset this card uses.  It's the ATI Saphire and should use the Catalyst Driver Suite, Verson 5.8.

---

### Post by coffeecat on 2012-07-09
> **DoctorVarney said:**
> 
Sorry, I have no idea what exact chipset this card uses.

Open a terminal and post the output of this command:

```
lspci | grep VGA

```

---

### Post by ortermagic on 2012-07-09
Hi there,
 I too have the ATI Radeon Sapphire HD 6800, recently I have had an almighty struggle with the ATI catalyst Additional drivers. Involving several clean installs. I am using Ubuntu 12.04 with a dual monitor setup. I am responding to your post to warn you that in my experience there is some sort of conflict between the provided driver and the additional one. I have reluctantly resorted to using the onboard driver in order to get both monitors to work as I want them to.
I will follow your progress with this issue and make comments whenever I feel I can help.
I have not noticed much degradation in graphic out-put by using the OS driver, but at least I have a working system now.
I hope you will be able to achieve a successful outcome, but be prepared for problems and don't accumulate too much stuff that might be any sort of serious loss until you are sure you have  stable graphics, that way its not so bad when you have to reinstall.

---

### Post by QIII on 2012-07-09
DoctorVarney's issue is likely related to whether or not his card is too old to be supported by the proprietary driver, which is what coffeecat is looking for.  (Not finding a suggested additional driver may indicate that.)

If you used the "Additional Drivers" installation, you may be among those for whom it inexplicably fails.  Often that is remedied by installing from the command line.  Look at the wiki in my sig for the section about alternate command line installation with hardware acceleration.

But the open source driver is really quite good and if it works for your purposes there is no reason not to use it.

---

### Post by ortermagic on 2012-07-09
Thanks QIII,
I will study your wiki and maybe try it (amdcccle) again, sometime. It would be good to get full potential out of my card, I have followed your prescription and downloaded the script from the AMD site...
So far. I got the (amd-driver-installer-12-6-x86_64) version FYI.

---

### Post by DoctorVarney on 2012-07-09
> **coffeecat said:**
> Open a terminal and post the output of this command:

```
lspci | grep VGA

```

Certainly

```
05:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV370 5B60 [Radeon X300 (PCIE)]
```Thanks.  I'm surprised it is AMD.

---

### Post by DoctorVarney on 2012-07-09
I must admit, I can't complain about the resolution and picture quality with the open source drivers.  I think the main concern is when I come to increase my screen real estate on this rig.  I actually went to a LOT of trouble to get dual-head interfaces because one monitor is seldom enough for my workflow in graphics.

My main reason for switching to Linux was for internet tasks though.  Windows is simply a filth magnet when it comes to online nasties.   Even with anti-virus (AVG Basic) it ends up as decrepit nag with flies plundering at the nostrils within a matter of months and has to be put down like a sick animal.  The hope is this will be the last mercy killing.  I still have Windows XP to run the heavier graphical tasks on.  For sound, I have an audio (Daw) Intel rig which I reserve for audio recording and sequencing tasks running Win XP.  It never touches the internet and all files are quarantined before reaching it.  It ONLY runs software applicable to one task.   It boots within seconds and runs like a dream, proving that the internet is the bane of the computer.  I would like to think that Linux is more powerful and elegant than Windows by virtue of what it doesn't need, though the trade off is the complexity and steep learning curve to do basic stuff.   At the end of the day,  I have to remain objectively open minded during this experiment or nothing will be learned.

I can only hope that what I learn pleases me.  To be quite honest, I think Ubuntu is quite sexy, for what it  is.

---

### Post by QIII on 2012-07-09
@otermagic

Doing it from AMD's website may be more trouble than it is worth, unless you think there is enough difference between 12.4 and 12.6 that makes you think you must have the latter.  12.4 is in the Precise repo and it is easier to install from the repo.

---

### Post by QIII on 2012-07-09
@DoctorVarney

Unfortunately, that chipset is in the AMD legacy bin.  The Linux driver that would work with it, the legacy driver, will not work with X server versions post 2008.

Use the open source Radeon driver (the default, which you are using) and enjoy.  If you attempt to install the proprietary driver, you'll end up staring at a blinking cursor and throwing things.

The open source driver should be quite serviceable for you, even though you won't have the fine-grained control of CCC.

---

### Post by mastablasta on 2012-07-10
more info on opensource driver here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
dual monitor setting should work but i am not sure how well it works with Unity interface. 
 
If you are experiencing lag you might want to look into other DE that use different way to draw windows. I have ATI9600XT from about same age and haven't tried it with Unity yet but it works very good with KDE (Kubuntu).
 
As menitoned in the link - an upgrade can be made via development PPA (but only if necessary). normally it is not needed as Opensource drivers should work fine.

---

### Post by coffeecat on 2012-07-10
> **mastablasta said:**
> more info on opensource driver here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
dual monitor setting should work but i am not sure how well it works with Unity interface. 

It works just fine with my AMD card, but it is a much newer chipset than the OP's. Whether or not the legacy X300 card might struggle with the large amount of screen space, I don't know, but System Settings -> Displays gives me all the control I need to set up dual-monitors in Unity with the open source Radeon driver.

@DoctorVarney, good luck with using Ubuntu.

---

### Post by Bucky Ball on 2012-07-10
@DrVarney: Have you looked at Ubuntu Studio? By the sounds of what you're into might suit:

[http://ubuntustudio.org/](http://ubuntustudio.org/)

You can install apps from there into a regular Ubuntu install from the repositories . So you can just add audio and/or video apps by adding:

ubunstudio-audio and/or ubuntustudio-video

... or if you want to go the whole hog:

ubuntustudio-desktop

---

### Post by DoctorVarney on 2012-07-10
Thanks.  I think I'll call this one resolved for the time being and move on.  The graphics are working well enough, without any issues that aren't just in my own mind.  My other machines run Windows XP with dual monitors.  So when the time comes to attach another monitor on this or if I move other machines over to Linux, then I think I will need to address it, if there's any chance they won't be detected.  I know Linux supports multi monitor support, because I've seen other people's machines set up in this way.  I would have thought though, that any driver that's working correctly with my card would be offering me greater choice of resolutions and some of the features hitherto offered by the Catalyst Control Centre.

---

### Post by Bucky Ball on 2012-07-10
If solved, (satisfactorily) please mark as solved from 'Thread Tools' at top right to help others. Good luck. ;)

---

### Post by DoctorVarney on 2012-07-11
Well, yes, but not exactly "solved" as there will soon come a time when I start hooking up secondary monitors to this machine.  The quick answer is, we don't know yet if the issue is solved or not.

---

### Post by ortermagic on 2012-07-13
I have set amdcccl it seems to be working well...however the annoying thing is that my left screen is designated no2 and the right screen is no1... I wonder how to change them over to make primary screen show up on left hand screen. Can anyone help?
See enclosed screenshot attatchment

---

### Post by QIII on 2012-07-13
You might actually get a better response, and the community an easier solution to see, if you start a new thread.

---

### Post by ortermagic on 2012-07-13
> **QIII said:**
> You might actually get a better response, and the community an easier solution to see, if you start a new thread.
Thanks, I have "hopefully" started a thread in general. Basicaly c/p the above!

---

### Post by Bucky Ball on 2012-07-13
> **qiii said:**
> you might actually get a better response, and the community an easier solution to see, if you start a new thread.

+1.

---

