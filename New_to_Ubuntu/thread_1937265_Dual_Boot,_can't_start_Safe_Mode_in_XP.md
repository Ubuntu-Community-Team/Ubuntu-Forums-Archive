---
title: "Dual Boot, can't start Safe Mode in XP"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by mrag on 2012-03-07
I installed latest Ubuntu last year on my Win XP. All things seem fine in either OS. But the other day I wanted to start XP in Safe Mode and could not. PC starts and I get menu to select Ubuntu or Windows. I select Windows and press F8 for Safe Mode, I get a very quick  view of blue screen, system shuts down. On restart I select Windows it gives screen saying "system did not properly shut down, how do you want to restart." I select Safe Mode, screen crashes again. So I can't get to Safe Mode. Is this me? Or am I missing something? Thanks.

---

### Post by lechien73 on 2012-03-07
I've come across this before in my previous job. I don't think it's anything to do with Ubuntu, but more a sign of malware infection or corrupted drivers on your Windows PC.

Safe Mode uses certain drivers, which are not used in normal mode. I've never used it, but this company claims to have a "Safe Mode fixer": [http://www.moonvalleysoft.com/safe-mode-fixer-p-29.html](http://www.moonvalleysoft.com/safe-mode-fixer-p-29.html)

---

### Post by ajgreeny on 2012-03-07
In the days when I had XP I could never get it to boot to safe mode either.  I tried many things to get it running that way without success, even booting to the XP install CD and running "repair", but still no go.

The only reason I wanted to run in safe mode was to perform a really good defrag prior to installing Ubuntu 5.04 as a dual boot, not because of a problem with XP.  Having now been using Ubuntu since then and after deciding that I only ever booted to XP in order to update it and the virus checker, I deleted XP about 3 or 4 years ago.  My system used to get to the same point in the safe mode boot and then just sit there saying "loading ??" (I can't remember what) and I would have to pull the plug and start again normally.

Never did find the reason; now I don't even care.

---

### Post by mrag on 2012-03-08
Thanks for the replies. Perhaps a more accurate description is on 'tapping F8 key' it seems my system tries to start Windows Safe Mode like normal, but then there is a glimpse of a BSOD message (too fast to read), it shuts down and then on restart I get the normal routine notice that Windows did not shut down properly, would I like to start normally or in Safe Mode. When I select Safe Mode then, it ignores me.

I guess my immediate question at this point is, on a dual boot pc with XP and 11.10, can anyone boot into Safe Mode?

---

### Post by lechien73 on 2012-03-08
I removed Windows from my computer some time ago, but used to have no problems booting into safe mode (which - being Windows - was something I needed to do often!)

I've done a quick search, and haven't found anyone else linking a dual-boot installation with failure to boot into safe mode.

---

### Post by mrag on 2012-04-04
At this point I have a very simple question for anyone using Ubuntu 11.10 and XP (SP3) in a dual boot setup. Can you boot into XP's Safe Mode ( a la the F8 or other route) ?

I am trying to narrow down where I might be having the problem so this becomes the critical first step. Thank you.

---

### Post by oldfred on 2012-04-04
I cannot easily boot into XP as I have changed to AHCI and my XP does not have the drivers. It behaves something like what you are reporting. 

Did you change BIOS to use AHCI?

I have to boot into BIOS can change back from AHCI to get Windows to boot. Which is part of my effort to wean myself from the one application I was running, which I had promised for at least a couple of years.

---

### Post by mrag on 2012-04-07
Thank you for your answer however, I have NO problem booting into regular Windows XP or Ubuntu. I just CANNOT boot into Windows Safe Mode. This has gotten a little more important as I am now getting an occasional BSOD PF_LIST_CORRUPT notice. To resolve that I will need to get into Safe Mode.

(I do not understand AHCI, but it would seem applicable only IF I had a trouble booting to regular Windows also)

---

### Post by oldfred on 2012-04-07
I know they say it is hard to get to from grub as it is quick, but if you are getting any part of the safe mode screen then it is a Windows issue. If you were booting from MBR directly, I think you would have the same issue. You can relatively easily test that by reinstalling the Windows boot loader, just that you then have to use Ubuntu liveCD to reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by mrag on 2012-04-07
Please do not take this the wrong way, but every so often it strikes me that I am not nor will I ever be a computer expert and maybe for $300 I should just go to Staples and come back and just sledgehammer my 5 year old XP ;-)

Thank you for your suggestions. I took a video of trying to get into XP's Safe Mode (see 38 sec mark) just to check if it is Windows as the problem.
[http://www.youtube.com/watch?v=L539-X2nYs0](http://www.youtube.com/watch?v=L539-X2nYs0)
Just after selecting Safe Mode, there is a very, very quick blue screen that displays briefly and reads: PAGE_FAULT_IN_NONPAGED_AREA
which then suddenly takes me back to the 'normal' Windows boot process and which proceeds quite normally. I googled this Page_Fault but left more confused than ever. As a side note, I have also received just two BSOD's over the last month: PFN_LIST_CORRUPT. I have noticed nothing while using Ubuntu and in Windows, in both cases, only after the pc was on for several DAYS.

---

### Post by oldfred on 2012-04-07
We are Ubuntu and can somewhat help on Windows issues with dual booting but are not experts, you may do better on a Windows forum.

One of the suggestions seems to relate to memory. Have you run the memory test from the grub menu?

Some also just remove memory (if they have more than 1 memory module) to see if that solves the issue or just clean memory contacts. You can use eraser and then alcohol to clean eraser bits off before reinserting memory module.

---

### Post by mrag on 2012-04-08
Thanks. I saw the bit about possible bad memory as a possible cause. Will try the eraser trick. Don't know a thing about the "memory test." Is that a menu option at start up?

The PFN_LIST_CORRUPT bsod has only shown up twice. Once around March 21 and then again April 4 and only while in WIndows. That last time 'only' FireFox was running and I was watching The Masters.org video channel. Boom, crash.

The PAGE_FAULT_IN_NONPAGED_AREA 'bsod' only shows for a split second and only when trying to get into Safe Mode. That only flashes on screen before XP starts normally-it does not 'freeze up' the pc. This bsod I thought was something in the dual boot menu, now I don't. agree?

I have not noticed any issues with Ubuntu although I use it much less :-( than I do XP. I have "Docky" with a widget that reports CPU and Mem. Right now they say 26% and 56% and the icon is green (good?). I have seen that go red now and again, but have not noticed any issues while running Ubuntu.

Now if only Ubuntu could run Netflix and Freemake Video.....

I have had a lot of success using [www.Aumha.org]("http://www.Aumha.org") for pc problems (mostly malware) so I will give them an 'opportunity' ;-)  Additional suggestions welcomed.

update: I ran the memory test via the Grub menu "Pass complete, no errors"

---

