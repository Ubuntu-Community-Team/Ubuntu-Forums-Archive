---
title: "After update VESA is new driver &amp; Launcher is gone!"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by megatron prime on 2013-02-25
People of Earth I require your best scientists fix my computer.

Until the Ununtu 12.10 update (about 4 days ago)everything was fine. I did the update (Using software centre)When I restarted, the Launcher bar was gone and the screen resolution is something ridiculous like 3000 x 2065! I can't activate any programs. All I could do was right click properties to get the All Settings are and while there, I saw two things. Under Display: I was set to Laptop mode (I have a desktop) and the resolution below that reads 640 x640) Go figure that one. I can change the drop down menu below to apply to more than one monitors. It doesn't seem to recognize my Toshiba 32". It did before.

1. I have tried that flgrx recommendation of removal. It didn't even find it,but I am sure I insatelled it a few days ago by command line.
2. I did not try this one because he has a Radeon card which is diffrenet than mine: [http://ubuntuforums.org/showthread.php?](http://ubuntuforums.org/showthread.php?)
t=2119220&highlight=fglrx
3. I found a third article which talks about Nvidia cards, but it did not look hopeful.
4. I have a recently downloaded driver for Nvidia GdForce 6150 LE but gedit doesn't seem to work the screen goes blank and i'm unsure how to proceed.

I do not to have to re-install my entire system, but because an update went wrong. I wish I had checked it more thoroughly,but because the update appeared on the Laucher as a safe update, I trusted it. I'm mad because I just jumped ship from Fedora for exactly this type of reason, too many problems with updates and software that wasn't tested. From what I read the Ubuntu forums and community work well; but I'm annoyed when I hear people bragging about linux when both failed constantly (I've only had Ubuntu working 2 months and after a simple update it broke. update. 

Skill Level: Beginner
I can open a terminal and figure how to edit using gedit,
and execute commands by command line, but only if I cutting and
pasting what some other genius has already written, so writ it as it literally should appear in the command line area.
I am running:
Ubuntu 12.10
with: Nvidia GdForce 6150 LE
HP 4200 AMD Dual Core 3.7MB RAM

I give you 24hrs to fix my computer problem or I destroy
your puny little planet!

Megatron Prime

---

### Post by DuckHook on 2013-02-25
There's something quite admirable about the ability to still find humour when approaching something as cussed and frustrating as these problems tend to be. So, even though you are thoroughly evil and intent on subjugating the universe, we must assist in the faint hope that you can yet be redeemed.

Your video card is an nVidia. It does not use the fglrx driver, which is an AMD driver. nVidia uses the nvidia driver instead. The instructions for installing/troubleshooting are [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

It may be possible to solve your problem simply by uninstalling, rebooting, then reinstalling the nVidia driver.

Do not take this help as a sign of weakness. The people of Ubuntu are ever-vigilant and strong. If you try to crush us, you will only destroy yourself. You have been warned.

-Optimus-

---

### Post by grahammechanical on 2013-02-25
I am assuming from this that you can get to System Settings

> All I could do was right click properties to get the All Settings are and while there, I saw two things. Under Display: 

If so open Software Sources (or Software & Updates - whatever it is now being called). Open the Additional Drivers tab and experiment activating one of the drivers on offer.

We do need to experiment because Nvidia drivers have not been up to standard lately. What you seem to be experiencing happened to me when I was testing 12.10 before its release. A faulty Nvidia driver could not work out the width of the screen and was placing the Launcher outside the physical left edge of the screen.

There are other ways to try to get to a working desktop. At the Grub boot menu select Advanced Options for Ubuntu and select either an earlier kernel to boot or select Recovery mode. At the Recovery mode menu select Resume.

Regards - and watch out for solar flares.

---

### Post by megatron prime on 2013-02-27
> **grahammechanical said:**
>  At the Grub boot menu select Advanced Options for Ubuntu and select either an earlier kernel to boot or select Recovery mode. At the Recovery mode menu select Resume.

Regards - and watch out for solar flares.

Thanks grahammechanical.
I tried that before I posted here, I forgot to mention that. It didn't make any difference unfortunately.

It's clear to me the launcher is pushed outside the visible window. I found the software settings area by some miracle (not easy without a launcher) fortunately I used the search function in the All Settings area (because a Software Updates icon was not visible)
Initially I was unable to change the video driver in the Additional Drivers area. There were several available including the most recent one Nvidia-173 with Legacy support (I think that's what you call it) for my GeForce 6150 LE graphics card.

So I selected the Nvidia-173 proprietary driver and selected Apply & restarted the computer. Now when it loads, on start up a tiny warning graphic is shown (that I can't read). I thought if it was listed here then the driver was already installed, or this would initiate and install the driver. Now things are a little worse. What happened?

---

### Post by megatron prime on 2013-02-27
> **DuckHook said:**
> 

Your video card is an nVidia. It does not use the fglrx driver, which is an AMD driver. nVidia uses the nvidia driver instead. The instructions for installing/troubleshooting are [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

It may be possible to solve your problem simply by uninstalling, rebooting, then reinstalling the nVidia driver.

-Optimus-

Thanks DuckHook,
I realize Nvidia is my video card. I installed the fglrx driver because I had tried all else and hoped (like a non-religious person about to die and praying to god he would save them) that because my machine is an AMD 64 that maybe, fingers crossed this would perform some kind of miracle. It didn't.

I followed the page you sent me. Nvidia-173 is the latest driver. I have an older version I originally installed and which was working, but I guess I have to install this new one. I know about the Nouveau Driver and its low performance we are old enemies, right from the beginning when I installed Fedora years ago. I switched from Fedora to Ubuntu understanding that it was more stable. I have downloaded. The Nvidia-173 version from the website, before I followed the page link you suggested. In Ubuntu there is a restricted driver link, but there are 3 files to install, do I have to install all 3? Also the file size is quite larger than the download I got from the Nvidia site, why is that? it's supposed to be the same driver.

---

### Post by windscape on 2013-02-27
Hi,

Something you might want to consider it starting over with Ubuntu 12.04.2 LTS, where LTS stands for Long-Term Support. The LTS versions of Ubuntu tend to be more conservative and more stable when it comes to software updates. That is the version that I run myself and I have yet to run across an update that caused any issues. *knocks on wood*

---

### Post by megatron prime on 2013-02-27
> **windscape said:**
> Hi,

Something you might want to consider it starting over with Ubuntu 12.04.2 LTS, where LTS stands for Long-Term Support. The LTS versions of Ubuntu tend to be more conservative and more stable when it comes to software updates. That is the version that I run myself and I have yet to run across an update that caused any issues. *knocks on wood*

Tnanks for the advice. I am considering a re-install. But I would rather not because I would still have the same problem. When I originally installed Ubuntu 12.10; right from the beginning the screen only displayed snow. I found this fix [http://ubuntuforums.org/showthread.php?t=2083868](http://ubuntuforums.org/showthread.php?t=2083868)

I have tried running the istall CD while my Ubuntu 12.10 is installed, it didn't work. I think there is something wrong with the recovery mode part, not sure. It didn't reboot the same way as when I was started from a blank hard drive.

Don't use the word 'issue' it is NOT a synonym for the word PROBLEM, and I definitely have a PROBLEM on my hands.

Current status:
Time invested: 5-7 hours.
Level of frustration: About 7 on 10.
Method of communication: Via my Windows XP netbook (which amazingly has never required a re-install or encountered an update problem in the 4 years I've owned it, congratulations Microsoft you finally got it right). 
Desktop computer running Ubuntu 12.10: AMD 64 HP Pavillion a1710n (steam driven)with Nvidia Graphics card GeForce 6150 LE(built into the motherboard) is non-functional.
Bootup in current Kernel: Displays screen with super small warning graphic I can't read, perhaps because the resolution is something massive like 3000 X 2065.
Bootup in older Kernel version: Prompts me to login, then I am left with a command prompt and I am not comfortable with command line stuff unless I know it's going to work.

Status before Ubuntu forum changes were implemented. I looked into the xorg.conf file using gedit. In the Service "Monitor" section I noticed the monitor type resolution etc. were not recognized. Same for the "Device" area with regards to board name.
1. I am familiar with the xrandr command.
2. I don't want to mess around with the xorg.conf file in terminal view, since I am not good at that unless the instructions are clear. 
3. I am unsure if the changes implemented in GUI mode took place
and the desired Nvidia-173 download is now the default driver or not.

What now??

---

