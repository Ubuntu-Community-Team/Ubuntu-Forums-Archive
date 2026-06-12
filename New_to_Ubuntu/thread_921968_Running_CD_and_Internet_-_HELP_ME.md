---
title: "Running CD and Internet - HELP ME"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Maxiimillian on 2008-09-16
Ok so im doing a project for my Net2 class to just get ubuntu working on a pc. Right now i run from the cd (When i boot my pc it gives me an option to run Windows or Ubuntu). I log in perfectly fine but once at the desktop, i cannot connect to any type of internet (Running N1 Mimo Wireless Desktop Card and my router is a N1 Vision. Both made from Belkin) and also when i try to run a CD it does not autorun, so i went to the cd directory and just tried to double click the .exe and nothing happens.  I read some guides on Ubuntu but cannot find anything specifically there to help me.

I am using the latest ubuntu version btw to.

MS-7181 Mobo
Mobile AMD Athlon 2800+ 64 ~1.8Ghz
1028 Ram

If ya need anything else just let me know. Right now im running the same pc from windows option.

---

### Post by Tatty on 2008-09-16
.exe files are windows executables and will not run natively in linux.  However there is an application called wine which attempts to simulate the windows API to allow windows applications to run.

Wine is far from perfect though so dont expect anything to work straight away.  What windows .exe's are you trying to run?

---

### Post by Maxiimillian on 2008-09-16
Well my wireless N1 adapter came with a cd, so i tried to run that and nothing happened.

---

### Post by Tatty on 2008-09-16
Do you have a specific model number for your wireless card?

can you open a terminal and post the output from the following two commands:
```

lspci
lsusb
```

> **Maxiimillian said:**
> Well my wireless N1 adapter came with a cd, so i tried to run that and nothing happened.

No that wont work directly in Ubuntu, there is a utility called ndiswrapper which may help you install your windows drivers in linux, but it depends on the model of your card

---

### Post by Maxiimillian on 2008-09-16
Ok, i have to reboot my pc and run Ubuntu that way, give me a sec and i will get you what you need.

---

### Post by jualin on 2008-09-16
> **Maxiimillian said:**
> Well my wireless N1 adapter came with a cd, so i tried to run that and nothing happened.

Follow the above suggestion since you cannot install the drivers for your Wireless card in Linux using the Windows CD that your card came with. As the person above me said, .exe files are only for Windows. Even though you can run some of those .exe files using Wine in Linux, you cannot install the drivers using Wine. 
In my signature there is a tutorial of how to install Wireless drivers using the Windows Drivers (Ndiswrapper). Hope this helps!

---

### Post by Maxiimillian on 2008-09-16
Ok this is what i got when i ran those 2 commands in a terminal

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)


Bus 005 Device 003: ID 050d:805c Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 06a3:8000 Saitek PLC 
Bus 001 Device 001: ID 0000:0000

---

### Post by Maxiimillian on 2008-09-16
Is that what you need?

---

### Post by Tatty on 2008-09-16
Im pretty sure you will need to use ndiswrapper to install as your card is the same model as in this thread:
[http://ubuntuforums.org/showthread.php?p=5716527#post5716527](http://ubuntuforums.org/showthread.php?p=5716527#post5716527)

I have never installed drivers with ndiswrapper so i cant help you in detail.  Try following the instructions in the link in jualin's signature:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Maxiimillian on 2008-09-16
Thank you Tatty i will try it right now. I will report back in a little.

---

### Post by Maxiimillian on 2008-09-16
Ok i tried for a good hour and i couldent get anything working

---

### Post by Tatty on 2008-09-16
Well how far did you get and where did it go wrong?

---

### Post by Maxiimillian on 2008-09-17
I went to install NDISWRAPPER and it was a success and thats about how far i got because i didnt know what to do next.

---

### Post by nothingspecial on 2008-09-17
Install ndisgtk
```

sudo apt-get install ndisgtk
```

This will give you a nice little gui to put your .inf file in.

---

### Post by jualin on 2008-09-17
Did you check the tutorial on my signature? In what part of the process did you get stuck on?

---

