---
title: "Need update help"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by phil56 on 2014-12-24
I first installed Ubuntu on  laptop a year or so ago, worked great, but gave laptop to my son so limited experience with Ubuntu.
I have just reassembled a PC with parts I had laying around. Basically an AMD Athlon 64X2 which was too slow to run WIN7. Had XP on it but that was unsupported and slow.
For the past few days I had many attempts at installing Unbuntu (and Linux Mint and Zorin). The Zorin and Mint would hang up, I could install Unbuntu but every time I updated it would not reopen. I tried and read the fixes but they are too complicated for this senior with limited time. I want to get this install stable, play with it a while and then give to a deserving youngster.

I installed it to formatted HDDs each time. I do not want to mess around with Grub loader, command lines or the like. Do I just not upgrade ever or is there a simple solution. Can I download other software to use in the meantime?

Thanks

---

### Post by Mark Phelps on 2014-12-24
> Had XP on it but that was unsupported and slow.

Sorry to tell you this, but any processor that was "slow" in XP, is going to be just as "slow" in Ubuntu -- Unity or Mate.

You might be able to get decent performance in Xubuntu, but most likely, it's going to be Lubuntu -- as best.

Please post the specs of your machine, especially the amount and speed of system memory.

---

### Post by sammiev on 2014-12-24
Hi phil56 and welcome,

What are the specs of your renewed new computer including video?

---

### Post by phil56 on 2014-12-24
> **Mark Phelps said:**
> Sorry to tell you this, but any processor that was "slow" in XP, is going to be just as "slow" in Ubuntu -- Unity or Mate.

You might be able to get decent performance in Xubuntu, but most likely, it's going to be Lubuntu -- as best.

Please post the specs of your machine, especially the amount and speed of system memory.

I should not have said it was necessarily slow on XP. It just was not Win7 ready.
I need to learn a lot more, I am lost except for running things in Dash. I can't find anything that says it is installed software. Like HW Monitor.

But I have an Athlon 64X2, 2X512MB DDR2, and a Radeon 8450 (I think that's it, old GPU for sure)

Linux may be too command intensive for me. But I will put some effort into trying to learn over the next week or so and see if I can learn enough to get by.

Thanks

---

### Post by Mark Phelps on 2014-12-24
The Athlon 64X2 is not bad, nor is the Radeon 8450 -- but the 1GB of memory is going to hold back performance -- regardless of what Linux distro you install.

You should see if the machine can be upgraded to at least 2GB of memory -- 4GB would be even better.

---

### Post by phil56 on 2014-12-24
> **Mark Phelps said:**
> The Athlon 64X2 is not bad, nor is the Radeon 8450 -- but the 1GB of memory is going to hold back performance -- regardless of what Linux distro you install.

You should see if the machine can be upgraded to at least 2GB of memory -- 4GB would be even better.

I understand, I may just not want to put money into this rig. I just built a  i7-4790 w/GTX 970 as a graduation/Christmas gift for my son w/2X4 GB Ram so I will need to curb computer spending for a while. My main desktop is an AMD A8 with 2X4GB and it is a good all purpose web and office app machine (no gaming required).

I am already starting to read more to learn. But in the meantime, why all the crashes after people upgrade? And this issue seems to go back into early 2014. The fixes are many and complicated. For now I am afraid to upgrade anything. Is it known which upgrades cause the issues or is it just the act of upgrading? I am tlking about the large upgrade suggsted just after installing or done while installing by checking the upgrade box. Either way, it crashes if updated, will not restart.

---

### Post by Bashing-om on 2014-12-24
phil56; Hi !


+1 ^ .

I also run dual AMD 64 athlon board with 
> 
sysop@1404mini:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon
06:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1404mini:~$ 

I do have 4GB of ram AND ->
system is fine good and dandy. Runs well and absolutely no problems.

The amount of ram makes the difference.

[INDENT][INDENT]don't worry about the hosses - add more
[INDENT][INDENT][INDENT][INDENT]load the wagon
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by phil56 on 2014-12-27
Just an update on my update issues. After another set of failed updates I decided to try Zorin and see if it too had issues. Downloaded and installed the 32 bit full version. After it worked I downloaded and burned an ISO of the 64 bit using the 32 bit system. Am now running Zorin 64 bit and installed all updates.

Not sure what the issue was, but I am now playing in the Linux world. Have no idea what I am doing. Will try and learn within Zorin and then try Ubuntu again if and when I get comfortable.

Thanks

---

### Post by Bashing-om on 2014-12-27
phil56; OK ;

The wagon is loaded. That is the good thing.

Even though I know little of Zorin, we are still here for assistance when needed.

[INDENT][INDENT]it's open source
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

