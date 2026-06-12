---
title: "NVIDIA issues NOT displaying Nav Bar"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by enj on 2013-03-09
I am new to Ubunto... now loading 12.04...
on HP XW8000 d530 CMT Xeon CPU 3.06 GHz 3.12 GB RAM... NVIDIA Quadro FX 1100 Driver 5/26/2008 6.14.11.6996...

I have read this link [https://help.ubuntu.com/community/Bi...erHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") ... and have the 173 drivers loaded... see below...

The user sign-in screen comes up but after signing in all I get is a blank background screen...
When I LEFT Click and select "Change background settings" I can then get access to the entire SETTINGS menu... still no side bar...

I went to "Additional Drivers" and got a screen with a message consistent with the above link on NVIDIA...
specifically "NVIDIA accelerated graphics driver (post-release update)(version 173-updates)" ...with the note "This driver is activated and currently in use."

However when I go to the System Details I see" Memory 3.7Gib Processor Intel Xeon CPU 3.06GHz x 2 GRAPHICS "UNKNOWN" OS type 32-bit Disk 0 bytes... System Up-To-Date
Under Sub-Menu Graphics: Driver: Unknown   Experience  Standard...

When booting in Safe Mode in the log I can see numerous attempts to load NVIDIA drivers and the load is unsuccessfull...

I'm not sure what to try next...
Thanks in advance...
Ed

---

### Post by gifford on 2013-03-09
I would suggest if you are able, to use the regular NVIDIA driver, not the post-release update to see if this does not correct your problem. You change it by going to "Additional Drivers" and select it instead of the post-release version. Also, when you go to background settings, under behavior, make sure that auto-hide launcher is set to off. 

Welcome to the forums and to Ubuntu.

Another thing you might consider, since I assume this is a fresh install, is to use the 64 bit version of Ubuntu as your hardware will support it.
In my own xwHP8600 workstation, I ended up changing my video card to an AMD ATI FirePro V4800 as the NVIDIA card and drivers were too troublesome.

---

### Post by enj on 2013-03-09
I gave it a shot... I de-Activated the 173-version and then searched for additional drivers...
It only presented one option to select... the same 173...!!!

Any other suggestion please...
Thanks
Ed

---

### Post by gifford on 2013-03-09
Here is a older thread which addresses the problem: [http://ubuntuforums.org/showthread.php?t=1986601](http://ubuntuforums.org/showthread.php?t=1986601)
Several of the posts indicate the 32 bit version has a problem loading the "glx" module. The 64 bit version does not have the problem.

Did you make sure auto-hide launcher is set to off?

---

### Post by enj on 2013-03-12
Gifford...
Took a while to get back, I've been experimenting...
Yes... Auto-Hide is OFF...

I was using Wubi to install and I didn't see an option for 12.04 64 bit... so I downloaded 12.10 32 bit and installed it...
I did get into GRUB and modified "nomodeset" and the desktop now works... but it is SLOW... particularly when typing in terminal or search modes... do you think it is machine or software issue with SLOWNESS...?

Now under System Details: ubuntu 12.10 Mem 3.7 Gib Processor Intel Xeon CPU 3.06GHz x 2 GRAPHICS: VESA: NV36 Board - p192-0o  OS: 32 bit  Disk 90.0 GB... as least it sees a Graphics card now...!!!
 
I should probably remove 12.10 and download and reinstall 12.04 (not with Wubi) or maybe not... are you sure the 64 bit will work on my 32 bit machine...?

The only method I see for removing 12.10 is to simply delete the partition...
I assume that will also delete /etc/default/grub... since I no longer see the Windows XP Boot Loader Menu now... will I have a problem here with no Windows Dual BLM or will it reappear...?

Not exactly sure which way to go at the moment...
What do you suggest...???
Thanks in advance...
Ed

---

### Post by Frogs Hair on 2013-03-12
There are some dual boot suggestions for restoring boot loader selections for Windows at the link. 64 bit  be fine but the need for it is based on memory. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Wubi downloads 64 bit which almost all modern machines can handle by default and is for trial use with a 30 GB max size limit . Pick either a Wubi installation or a traditional  dual boot.

---

