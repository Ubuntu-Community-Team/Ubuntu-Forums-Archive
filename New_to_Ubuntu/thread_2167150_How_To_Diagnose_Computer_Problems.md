---
title: "How To Diagnose Computer Problems?"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by MPeezy on 2013-08-12
I recently had to leave my abusive relationship with Windows, but not before my PC got the performance knocked out of it. Now that I'm on Ubuntu, my computer is running smoother, but I'm still having issues. Most commonly, half the time I click to search my computer, Ubuntu freezes, gets all scrambly, and I'm forced to reboot. Occassionally this happens when I have a program such as Open Shot or Audacity open, and click on Firefox or another program. In addition, Audacity, Firefox, and Open Shot (the programs I mostly use), are often subject to crashing. I'm not sure if its a hardware or software issue, if I inherited a virus from Windows, or what, but I would like to figure it out. I have 2 GiBs of RAM, 2.2 GHz speed if that means anything for my problem.

Does anyone have any tips or ideas for how I can figure out what the issue is. I have had the occassional system error message, as well as an internal error message that specifies a problem with a particular file, but I haven't been able to save them. Of course, I know this would help immensely, so if I see them again, I will post them here. So what do you guys think? Any advice?

---

### Post by slw210 on 2013-08-12
What are the Complete Specifications for your computer? What Graphics card?

---

### Post by Gilad_Pellaeon on 2013-08-12
Could be several things. First thing that comes to my mind is maybe you're hard drive is starting to go belly up and it might be time to try and copy all the important data off it and replace it. Or if it's an older computer when was the last time you opened it up and cleaned all the dust out of it? I'm relativly new to Lubuntu myself but anytime you start getting file errors like this in any OS then you have to wonder if the hard drive is developing bad sectors that have worn out physically on the drive platter(s) from age.

---

### Post by oldos2er on 2013-08-12
I'd suggest you run smartctl on your hard disk(s), and memtest on your RAM. See [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) for help with smartctl. Memtest can be run from the grub menu, and it would probably best to let it run overnight.

---

### Post by zealibib slaughter on 2013-08-12
The first thing that I see is 2Gb ram.  That is really the bare minimum ram for Unity or KDE.  Your system may work better with a lighter desktop.

---

### Post by 3rdalbum on 2013-08-13
> **zealibib slaughter said:**
> The first thing that I see is 2Gb ram.  That is really the bare minimum ram for Unity or KDE.

No it's not! I run Unity on a gig of RAM, it works well. Even being at the minimum level of RAM would not cause a freeze, it would cause low performance and hard disk thrashing but not a crash.

However I strongly recommend a RAM check. Try taking a stick of RAM out of the computer and see if you still have problems. If you do, put it back in and take out the other stick.

Memtest is good but it doesn't always pick up bad RAM sticks.

the other possibility is your graphics card. Which one is it, and have you installed any drivers for it?

---

### Post by mastablasta on 2013-08-13
yes, 2 GB is more than enough. Just tried (waiting to find some time to install) 2GB and Kubutnu full effects. it works really fast. and i havent even loaded the proprietary drivers yet.

---

### Post by MPeezy on 2013-08-14
This is what I see when I check my system settings:

Memory: 1.8 GiB
Processor: AMD Phenom(tm) 9500 Quad-Core Processor x 4
Graphics: Gallium 0.4 on NV4C
OS type: 32-bit
Disk: 243.3

If I need anything more detailed, you guys are going to have to hold my hand to show me how to do it.
Just out of curiosity, how would I detect and eliminate a virus on Ubuntu? Since you control everything, can you just manually seek out and destroy malicious files? Or do you still need anti-virus software to help you?

---

### Post by waynefoutz2 on 2013-08-14
> **MPeezy said:**
> This is what I see when I check my system settings:

Memory: 1.8 GiB
Processor: AMD Phenom(tm) 9500 Quad-Core Processor x 4
Graphics: Gallium 0.4 on NV4C
OS type: 32-bit
Disk: 243.3

If I need anything more detailed, you guys are going to have to hold my hand to show me how to do it.
Just out of curiosity, how would I detect and eliminate a virus on Ubuntu? Since you control everything, can you just manually seek out and destroy malicious files? Or do you still need anti-virus software to help you?


There virtually are no viruses when running Ubuntu. Your hardware specs are more than adequate to run Ubuntu. Your best bet is to check your hard disk and RAM for problems as Oldos2er posted above. If you have a failing hard drive, that could have been your problem with Windows as well. I once had an old Dell laptop, Windows ran fine on it, but when I installed Ubuntu, smartmontools told me my hard drive was in bad health. I ignored the warning. Sure enough, a few weeks later the drive died. You can check your ram by choosing memtest in the GRUB menu at boot-up. 

I assure you the problem is not a virus.

---

### Post by coldraven on 2013-08-15
For a quick look at possible disk errors run the "Disks" utility. In the dash start typing "disk".
Near the top of the window is an assessment of your disk, mine says "Disk OK, one bad sector (36° C/97° F)".

---

### Post by slw210 on 2013-08-15
My WAG would be your Graphics card and/or the drivers for it.

Which OS and version are you running?

---

### Post by crazymonkey05 on 2013-08-15
just out of curiosity why are you using a 32-bit OS on a 64-bit processor?

---

### Post by Easy Limits on 2013-08-17
> **crazymonkey05 said:**
> just out of curiosity why are you using a 32-bit OS on a 64-bit processor?  This

---

