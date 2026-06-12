---
title: "[AMD] fglrx-core failed to build Xubuntu 15.04 HD 6370m"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by plonide on 2015-08-31
Hello all
I'm having trouble installing the AMD catalyst drivers on my laptop. The video card is supported by AMD for Catalyst driver.
No matter what method I try I get the same result, AMDCCCLE failed to run and tells me there is a problem with my driver or GPU, when I reboot my system I get a black screen and some troubleshooting manager that tells me it can't find my display and gpu and I have to reinstall.
[IMG]https://i.imgur.com/WNPF9Rv.png[/IMG]
The error message is in German for some reason, my locale is English. It also gives this error in the terminal when running it
```
sh: 1: gnome-session: not found
```
When building the packages manually following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Utopic_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Utopic_Installation_Guide) it tells me fglrx-core failed to build or is missing and the same happens, amdcccle can't launch. I'm guessing the same thing happens when using the additional drivers method (tried fglrx and fglrx-updates) but it doesn't display the fglrx error message.

uname -a
lspci -nn | grep VGA
```
Linux X72JT 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:32 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] [1002:68e4]
```
laptop: [https://www.asus.com/Notebooks/K72JT/specifications/](https://www.asus.com/Notebooks/K72JT/specifications/)

I hope I can one day install it successfully with some help. If you need any more info or logs please let me know. I don't mind installing it again a couple more times if it means it will finally be working.

---

### Post by mastablasta on 2015-08-31
use this page as instructions to install them: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

installing it via GUI is an easier option but i guess you had a failure with that method?

is there another GPU chip on computer? purge them and reinstall using CLI and post any errors you may encounter.

this is how you install it:
```
sudo apt-get install fglrx
```

---

### Post by plonide on 2015-08-31
I have an i5 480M cpu which has the Intel Graphics Media Accelerator HD Graphics / Intel HD Graphics. I don't think it's being used or even detected (see picture)

[IMG]http://i.imgur.com/C20jV1u.jpg[/IMG]

I'm guessing the bottom one is the intel graphics?

When I execute : lspci -vvnn | grep VGA

```
zo@X72JT:~$ lspci -vvnn | grep VGA
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] [1002:68e4] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

```

sudo apt-get install fglrx terminal log:
[http://pastebin.com/ghKDqH3v](http://pastebin.com/ghKDqH3v)

Now, I am confused as to which one I should execute

> Generate a fresh xorg.conf BEFORE REBOOTING! 

sudo amdconfig --initial 
If you are using multiple AMD graphics cards or AMD dual graphics (i.e.: notebook users), use: 
sudo amdconfig --adapter=all --initial
Pretty sure that if I execute sudo amdconfig --initial, I will have a black screen upon reboot

---

