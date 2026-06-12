---
title: "Self-Inflicted First-Time Ubuntu Problem"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by SiddharthaWolf on 2012-04-17
Hi, I'm having a bit of a problem with Ubuntu and think I know what the cause is, but need a little guidance getting round it. As a little background, I've been meaning to move to Ubuntu for a while, and finally converted after I started having problems with Windows Vista (which seemed to be software, rather than hardware-related).

I downloaded and burnt the ubuntu.iso (latest version), rebooted with CD in the drive, and followed the installation instructions. I realise that I did it all a little hastily, but felt inclined to do so because I need my computer at the moment for work-related purposes (I'm a teacher) and prior to this it was almost impossible to use (increasingly slow and had started refusing to load Windows except in Safe Mode, recently even refusing to load in Safe Mode).

So I wasn't sure about the amount of space I had available for install, but (in hindsight I think incorrectly) thought it was around 10gb. I ultimately want to be completely reliant on Ubuntu and stop using Windows entirely, but I chose to install Ubuntu next to Windows, since I didn't have a back-up of some files I wanted to keep (and due to the slowness of windows, had no way of accessing them). After this, installation seemed to go ok. That is, until a strange error popped up near the end. I forget the exact wording, but after doing some research found that apparently it correlates with not having enough hard-disk space during install.

It allowed me to use the Ubuntu OS, which I assume from the sluggishness and constant DVD-drive whirring was just loading from the DVD. I was hoping to take advantage of the opportunity to delete some items from my hard-drive, so I could begin a fresh full re-install as soon as possible. Unfortunately, I had to go to bed due to early morning work commitments. 

When I got back from work, I started Ubuntu up, but it just stalled on the purple load-up screen and showed a lack of hard-drive activity on the indicators (I've done the same thing again just now and it's still on the same loading screen 30 minutes later, if I press CTRL + ALT + F1, it goes to a black screen). 

If I restart with the disc in the drive (hoping for a "reinstall Ubuntu" option), it goes to a loading screen (which seems to take forever) accompanied by DVD-drive activity. After a while it loads Ubuntu (or, strangely, it does this time, but hadn't previously, so now I'm going to have to slightly change my query). So now that I know it can load with the Ubuntu CD (but not reinstall), how can I begin afresh and be able to make enough room for full reinstall, transfer all my important files from Windows, and delete the Windows OS completely? As I type this Ubuntu has crashed on the pre-desktop screen (with the background but no ability to control anything/taskbar etc.). If I press CTRL + ALT + F1, it goes to the command screen, but I'm not sure what commands I can run to progress.

Finally, if I restart and go to "Ubuntu... (recovery mode)" it goes through the commands series (terminating with "...doing nothing") before going to the Recovery Menu:

[LIST]
[*]If I click FSCK, it posts some stuff I can't interpret, mentioning 140298/172368 files (0.1% non-contiguous) and 638863/688128 blocks [93.505494] etc. OPTS: errors=remount-ro
[*]If I click "Clean" it says "Finished, please press ENTER" without doing anything.
[*]If I click "DPKG" , it says "cannot remove '......partial/*", and something else I don't have time to write before it goes through a series of processes and finishes with "373 upgraded, 4 newly installed, 0 to remove and 0 not upgraded". Then, it says "Need to get 257MB of archives. After this operation, 225MB of additional disk space will be used." followed by "E: You don't have enough free space in /var/cache/apt/archives/"
[*]I have no idea how to use the two root tools
[/LIST]

If I click ESC or the option I forget the name of basically returning to a normal Ubuntu start-up, it says "Warning: Fake initctl called, doing nothing".

I would be very grateful to anyone able to help me fix this error, with the ideal final situation being:
[LIST=1]
[*]Ubuntu fully installed.
[*]All important files transferred from Windows to Ubuntu.
[*]Windows uninstalled
[/LIST]

Thanks in advance :)

---

### Post by Bucky Ball on 2012-04-17
Welcome.

Are you using 12.04 LTS by any chance? Please provide release number. ;)

---

### Post by SiddharthaWolf on 2012-04-17
I'm fairly certain it's 11.10, definitely not 12.04.

---

### Post by cottfcfan on 2012-04-17
Can you still boot into windows?
Do you have a separate drive to back up all your files to?

---

### Post by dawnboat on 2012-04-17
can you get into vista safe mode with networking? does your computer have some malware loaded into it possibly?

---

### Post by JC Cheloven on 2012-04-17
Hi, a colleague here. Welcome :)

Windows Vista stands for one of the worst operating systems ever. Some people around me had the same exact symptoms as you. I installed Ubuntu for them, of course ;) 

I'm not yet clear of whether you pc boots with the live ubuntu cd or not. 

First off, please let us know what your hardware is. The better way to do it is, if you can boot from live cd:
- open a terminal (ctrl-alt-t should do) 
- run the following commands (one at a time)
```
sudo fdisk -l
lspci
free -m
```
- copy the output of each (you can select text dragging with the mouse, then ctrl-shift-c)
- paste back here (ctrl-v while you are editing your answer).

Anticipating some points: 
- it's better to resize windows from within windows, prior installing ubuntu
- 10 Gb is a bit scarce for an operative ubuntu install, but it should largely suffice for testing purposes.

---

### Post by SiddharthaWolf on 2012-04-17
JC Cheloven, thanks for your response. My computer didn't load with the Ubuntu CD, but I think that might be due to some damage to the CD. I just downloaded Ubuntu again on my gf's laptop and have just tried it again on my laptop. Surprisingly, it loaded up perfectly, offering me a trial version of Ubuntu - which I started using as an opportunity to delete and transfer some files - for about 30 minutes before it bizarrely faded out and the screen turned into some kind of 70s psychedelic arts fest with alternating patches of colour obscuring the text behind. When I tried to restart again, it didn't recognise the boot CD and just went straight to the menu. None of the options work any more.

As for the commands you requested:

**<SUDO FDISK -L>** 
disk 160.0gb
255 heads, 63 sectors/tracks, 19457 cylinders, total 312581808 sectors

Device Boot       Start        End        Blocks     ID       System
/dev/sda1          2048    3074047       1536000     27   HiddenNTFS/WinRE
/dev/sda2       3074048  158722047      77824000      7   HPFS/NTFS exFAT
/dev/sda3     158722048  305240919      73259436      7   HPFS/NTFS exFAT
/dev/sda4     305242110  392580095       3668993      5      Extended
/dev/sda5     305242112  310759231       2754560     83         Linux
/dev/sda6     310753280  312580090        913408     82  Linuxswap/Solaris

**<FREE -M>  **
      Total          Used          Free       Shared     Buffers    Cached
Mem     873           37           835          0           6         15 
Buffers/Cache         13           860
Swap      0            0            0

The other command you suggested I try gave me results I wasn't sure exactly what to give you (and since I had to handwrite this stuff as my computer won't load to any OS, was unable to C + V). I got this info from the "Ubuntu [recovery]" menu btw, as I can't get on Ubuntu any more.

I'll also add the specs as written in the BIOS setup:

CPU TYPE: AMD ATHLON 64x2 TK-87
SPEED:   1.9Ghz
HDD: WDC WD1600BEVT-00ZCT0(S1)
Total Mem: 1024MB

> Can you still boot into windows?
Do you have a separate drive to back up all your files to?

I can't boot into windows at all. I don't know how to boot into safe mode either, since the option no longer appears at boot up as it goes to that purple menu that Ubuntu presumably installed instead.

I have two hard-drives, but both are being used. I would ideally like to be able to access them purely to delete some files and transfer the rest over the the main hard-drive.

> can you get into vista safe mode with networking? does your computer have some malware loaded into it possibly?[QUOTE][/QUOTE]

No Safe Mode at all (see above) :( I had done extensive scans for all kinds of potential problems - from malware/viruses to registry errors, hard-drive issues to cpu - but none had suggested anything was out of the ordinary. The only problem appeared to be the amount of time needed to load start-up applications (some took ~10 mins), and a recurring error from Malware Bytes that suggested some problem with it (but I think there might have been an incompatibility with the relatively recently installed ESET iirc).

Hope this helps narrow down the possibilities. Any help would be much appreciated, thanks for all you've tried so far.

---

### Post by JC Cheloven on 2012-04-17
> **SiddharthaWolf said:**
>  (...) I just downloaded Ubuntu again on my gf's laptop and have just tried it again on my laptop. Surprisingly, [COLOR="Red"]it loaded up perfectly, offering me a trial version of Ubuntu[/COLOR] - which I started using as an opportunity to delete and transfer some files - for [COLOR="Red"]about 30 minutes before it bizarrely faded out and the screen turned into some kind of 70s psychedelic arts[/COLOR] fest with alternating patches of colour obscuring the text behind. When I tried to restart again, it didn't recognise the boot CD and just went straight to the menu. None of the options work any more.

Ufff... works for a while, then crashes... this makes me think in a hardware failure. Most likely your ram or your graphics card. Perhaps something heating-related. I'd wish I'm not correct. If your bios has some built-in ram test (or hardware test in general), it could be a good idea to run it. Also, please try running the live ubuntu session in your gf's laptop for a while, to discard any damage on the cd.
[COLOR="RoyalBlue"]EDIT: in a second thought, the problem could be that you were moving many (large) files from the live session, which relies only on ram, and you got out of ram. So let's not panic for a while about the hardware possibility.[/COLOR]

Anyway, I'll carry on answering your post, just in case it helps.

> 
As for the commands you requested:

**<SUDO FDISK -L>** 
disk 160.0gb
255 heads, 63 sectors/tracks, 19457 cylinders, total 312581808 sectors

Device Boot       Start        End        Blocks     ID       System
/dev/sda1          2048    3074047       1536000     27   HiddenNTFS/WinRE
/dev/sda2       3074048  158722047      77824000      7   HPFS/NTFS exFAT
/dev/sda3     158722048  305240919      73259436      7   HPFS/NTFS exFAT
/dev/sda4     305242110  392580095       3668993      5      Extended
/dev/sda5     305242112  310759231       2754560     83         Linux
/dev/sda6     310753280  312580090        913408     82  Linuxswap/Solaris

- You said elsewhere you have two discs. It reports you have only one. Perhaps you thought that two partitions in the same disc (which you actually have, of similar size) were two different discs. 
- You said you accesed "the discs" from a live cd ubuntu session, at least for 30 min, and recovered some files. I hope you took the files to an external disc: if you just moved them from one partition to another, I'm afraid it will be of little help if the present situation (can't access disk) continues.
- Your Ubuntu partition (where you installed ubuntu, not the live session which doesn't use your disk) is very small, just about 2.6Gb. Much smaller than the 10 Gb you stated. It's well under the recommended requirements, so it's not surprising that your installed ubuntu system doesn't work!

> 
**<FREE -M>  **
      Total          Used          Free       Shared     Buffers    Cached
Mem     873           37           835          0           6         15 
Buffers/Cache         13           860
Swap      0            0            0

Ok, you have about 1Gb ram. It surprises me the small ram footprint of your ubuntu live session. I think it simply can't be true. But let's put that aside for now. (ah ah, as I carry on reading I see you have been using the ubuntu recovery, so it's less strange; it's ok).

> 
The other command you suggested I try gave me results I wasn't sure exactly what to give you (and since I had to handwrite (...) 

Regarding the [COLOR="Blue"]lspci[/COLOR] command, I was interested in the line that says something as "VGA compatible controller".

> 
I have two hard-drives, but both are being used. I would ideally like to be able to access them purely to delete some files and transfer the rest over the the main hard-drive.

As said, I think you had two partitions, on the same disc. Also, what are you considering your "main drive"?

> 
No Safe Mode at all (see above) :( I had done extensive scans for all kinds of potential problems - from malware/viruses to registry errors, hard-drive issues to cpu - but none had suggested anything was out of the ordinary. The only problem appeared to be the amount of time needed to load start-up applications (some took ~10 mins), and a recurring error from Malware Bytes that suggested some problem with it (but I think there might have been an incompatibility with the relatively recently installed ESET iirc).

Sorry, what is that thing? If it's some hardware, have you tried to unplug it?
> 
Hope this helps narrow down the possibilities. Any help would be much appreciated, thanks for all you've tried so far.
You're welcome!

---

### Post by Scott Baker on 2012-04-17
A few things here. First, what is the EXACT version of Ubuntu that you downloaded and burned to disk. There have been some radical changes between the last few releases, so it would help to know what we're all dealing with here. Next, in burning to a disk, you may have a corrupted burn, and not know it. If you are in a position to do it, load the Ubuntu ISO to a >4Gig flash drive. All of the specs that you've provided so far indicate that a complete install should not be a problem on your machine (I've 11.10 on older machines with very few issues). Try the flash drive, check the results, and let us know what your progress is like. Thanks.

---

### Post by JC Cheloven on 2012-04-18
> **SiddharthaWolf said:**
> I'm fairly certain it's 11.10, definitely not 12.04.
"he said..."

Anyway, and just in case, could you please (SiddharthaWolf), when you're in live mode with that cd, be it at your computer or your gf's, issue this command at terminal? ```
lsb_release -a

```

As for this:
> **Scott Baker said:**
>  All of the specs that you've provided so far indicate that a complete install should not be a problem on your machine
Please note: he's been trying to install to a little more than 2.5Gb partition. This could indeed be a problem.

---

### Post by Bucky Ball on 2012-04-18
> **JC Cheloven said:**
> "he said..."

Anyway, and just in case, could you please (SiddharthaWolf), when you're in live mode with that cd, be it at your computer or your gf's, issue this command at terminal? ```
lsb_release -a

```As for this:

Please note: he's been trying to install to a little more than 2.5Gb partition. This could indeed be a problem.

+1. Agree on both. But is the OP a he? ;)

---

### Post by SiddharthaWolf on 2012-04-18
Dear all, thanks for your assistance. The problem mainly came about and was exacerbated by the fact that I was trying to do too much too quickly. Last evening I came across a post somewhere mentioning that you can delete the Ubuntu partition from within Windows (which I had just been able to access in Safe Mode). I did this, reinstalled Ubuntu and chose to create a new partition of 50GB. I am now writing this grateful response to your suggestions from within Ubuntu. :) Again, thanks, if I have any further problems, I'll know who to ask.

---

### Post by Bucky Ball on 2012-04-18
Great news! Enjoy Ubuntu and the learning curve. Please mark thread as 'Solved' from thread tools to help others. ;)

---

### Post by JC Cheloven on 2012-04-18
> **Bucky Ball said:**
> Great news! Enjoy Ubuntu and the learning curve. Please mark thread as 'Solved' from thread tools to help others. ;)
+1 Congrats!
Last word of advice: if version 11.10 works fine for you, stick with that for at least some months. You'll be given the option to update to version 12.04 in a few days, but you don't have to. New versions may not come out sometimes as polished as one would desire, but improve soon afterwards, as the community (we) provide wider testing.

---

