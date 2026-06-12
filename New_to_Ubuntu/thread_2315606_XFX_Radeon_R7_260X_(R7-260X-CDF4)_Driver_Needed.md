---
title: "XFX Radeon R7 260X (R7-260X-CDF4) Driver Needed"
date: 2016-02-29
forum: New to Ubuntu
---

### Post by HaoleBoy1975 on 2016-02-29
XFX Radeon R7 260X (R7-260X-CDF4) Driver Needed

Yeah so like 22 installs later of Ubuntu I have not yet had any luck getting the right information from Google searches about how to install the correct drivers so that when I do updates or need to restart my computer, I do not have to wonder how I am going to get back into my desktop because the display drivers are all fouled up. I want very much to make this work, and give Ubuntu an honest chance but this is getting rather aggravating.

The model Number of my card is: R7-260X-CDF4

I bought this card for gaming, and if I had had a brain & waited a little longer I could have bought myself an R9 instead... But in any case, Ubuntu seams to hate ATI with a passion same as I seam to hate AMD with a passion but its affordable.

So any any way. I went & downloaded the so called display driver from AMD's site. I have no idea how to open or run the .run file. Nothing seams to open it in Ubuntu, and the things I installed that seamed like they might open a run file in Software Center, didn&#8217;t. Any ideas?

Downloaded,
AMD Radeon Software Crimson Edition 15.12 Proprietary Linux Graphics Driver

Download Location,
[http://support.amd.com/en-us/kb-articles/Pages/AMDRadeonSoftwareCrimsonEdition15-12LINReleaseNotes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDRadeonSoftwareCrimsonEdition15-12LINReleaseNotes.aspx)

The closest thing to an installer is,
amd-driver-installer-15.302-x86.x86_64.run

I have the pdf but not seeing how to use this file, and it has mention of deb files but there are none in this archive. Perhaps I missed something...

---

### Post by QIII on 2016-02-29
Hello!

You need not download and install the driver from AMD.  You may install it from Canonical's repositories. 

Simply use the Additional Drivers functionality.  Remember to do 

```
sudo amdconfige --initial
```

in the terminal before you reboot.

Take a look at Section 3.1 in the ATI wiki in my signature for a complete run-down on how to do it manually.

---

### Post by HaoleBoy1975 on 2016-02-29
```
lspci -vvnn | grep VGA
```

returned the following in terminal,

```

awfordjr@A88XM-Gaming:~$ lspci -vvnn | grep VGA
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics] [1002:130f] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X/360] [1002:6658] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
awfordjr@A88XM-Gaming:~$

```

I feel so lost with Linux... Now I know how people feel that ask me questions about Windows.

```

awfordjr@A88XM-Gaming:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
[sudo] password for awfordjr: 
cp: cannot stat &#8216;/etc/X11/xorg.conf&#8217;: No such file or directory
awfordjr@A88XM-Gaming:~$ 

```

I dont have a clue what I am doing here. Would it be so hard for things to just install like they do in Windows? ffs

I feel there may be a little brain activity yet. I think I get it now, so I was supose to download all those files. Well that makes a little sence now.

```

Package 'fglrx-glx' is not installed, so not removed
Package 'fglrx-control-qt2' is not installed, so not removed
Package 'xfree86-driver-fglrx-dev' is not installed, so not removed
Package 'xorg-driver-fglrx-dev' is not installed, so not removed
Package 'libfglrx' is not installed, so not removed
Package 'fglrx-pxpress' is not installed, so not removed
Package 'boinc-client-fglrx' is not installed, so not removed
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-core' is not installed, so not removed
Package 'fglrx-dev' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
Package 'fglrx-updates-core' is not installed, so not removed
Package 'fglrx-updates-dev' is not installed, so not removed

```

I will go do that now then.

---

### Post by QIII on 2016-02-29
```
awfordjr@A88XM-Gaming:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
[sudo] password for awfordjr: 
cp: cannot stat &#8216;/etc/X11/xorg.conf&#8217;: No such file or directory
awfordjr@A88XM-Gaming:~$
```

```

Package 'fglrx-glx' is not installed, so not removed
Package 'fglrx-control-qt2' is not installed, so not removed
Package 'xfree86-driver-fglrx-dev' is not installed, so not removed
Package 'xorg-driver-fglrx-dev' is not installed, so not removed
Package 'libfglrx' is not installed, so not removed
Package 'fglrx-pxpress' is not installed, so not removed
Package 'boinc-client-fglrx' is not installed, so not removed
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-core' is not installed, so not removed
Package 'fglrx-dev' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
Package 'fglrx-updates-core' is not installed, so not removed
Package 'fglrx-updates-dev' is not installed, so not removed

```


This is normal if you have not installed the driver before.  Just keep following the instructions.

---

### Post by HaoleBoy1975 on 2016-03-01
When it was time to restart it froze my screen again, and I was not able to get back into the desktop not even with use of the restore menu which I figured out was shift. So for now I have given up & reinstalled Windows 10. I will give it a go again later as I have been at it all day. Thank you very much for the help.

---

### Post by mastablasta on 2016-03-02
i am not sure what you are doing and what the code is supposed to show us. 

but you are supposed to run additional drivers app, select the driver you want/need and install it. it's 3 clicks with a mouse.

you can also do it in CLI if you want to: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

installing form .run file also Works and it works just like in windows. you make the file executable and run it. the issue is that you will then need to do this all the time when there is a kernel upgrade.

---

### Post by Bucky Ball on 2016-03-02
> **mastablasta said:**
> ... run additional drivers app, select the driver you want/need and install it. it's 3 clicks with a mouse.

Often that easy, depending on the GPU. On your next attempt, after install, update and immediately check 'Additional Drivers'. Ubuntu doesn't install things like Windows because it isn't Windows and sometimes it's not easy because hardware manufacturers don't create neat little GUIs to install their drivers for Linux like the bother to do for Windows.

Generally nothing to do with Ubuntu. A lot of the time it is down to the hard, unpaid work of a volunteer who is interested enough to bother that some hardware works at all. 

I encourage people to email manufacturers if their hardware doesn't work with Linux, but I encourage users more strongly to use hardware that is known to be compatible with Linux. Admittedly, this is not always easy, but it does encourage manufacturers that bother to play nice with Linux users.

Good luck on your next attempt. :)

---

