---
title: "[SOLVED] Drivers for Dell Inbuilt Webcam?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-23
I hope someone can help i have a Dell SP2208WFP flat screen monitor which has a built in webcam which i would like to be able to use on Ubuntu...are there any drivers available? (i presumed as it's dell that they would have official drivers...how silly of me :)) maybe some generic drivers?

Thanks in advance

---

### Post by halitech on 2008-07-23
open a terminal and post the output of
```
lspci
```
and
```
lsusb
```
so we can see if Ubuntu is even seeing the webcam

---

### Post by kamitsukai on 2008-07-23
_First command_
```
carl@carl-bedroom:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```
[U]
Second one:)[/U]
```
carl@carl-bedroom:~$ lsusb
Bus 002 Device 003: ID 062a:0204 Creative Labs 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 05ac:0221 Apple Computer, Inc. 
Bus 003 Device 004: ID 05ac:1006 Apple Computer, Inc. Hub in Apple Aluminum Keyboard
Bus 003 Device 003: ID 0424:2514 Standard Microsystems Corp. 
Bus 003 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 003 Device 001: ID 0000:0000  

```

Thanks for the help:KS

***Edit***
```
Bus 002 Device 003: ID 062a:0204 Creative Labs 
```

Is that my webcam? (i don't own anything made by creative unless it's the webcam in the monitor...lol)

---

### Post by halitech on 2008-07-23
I was looking at that and thinking it is a creative labs webcam so hopefully we are both right :)

the good thing is Ubuntu is seeing the hardware. I have a creatice cam as well and if I remember right, all I did was plug it in and it worked. Do you have any software installed yet that can use the cam?

---

### Post by kamitsukai on 2008-07-23
I've tried cheese and amsn but both ask simmilar things in there error messages asking if the webcam is correctley plugged in and installed...

---

### Post by halitech on 2008-07-23
ok, looks like it needs the spca5xx drivers. you can get them from here:

[http://mxhaard.free.fr/](http://mxhaard.free.fr/)

---

### Post by kamitsukai on 2008-07-23
OK I've never compiled anything....:D do you have any info on how i would go about this?

Thanks for all the help!

---

### Post by kamitsukai on 2008-07-23
> **halitech said:**
> ok, looks like it needs the spca5xx drivers. you can get them from here:

[http://mxhaard.free.fr/](http://mxhaard.free.fr/)

Hmmm... I've just spotted something on the ubuntu wiki pages it says that since gutsy the spca5xx driver has been replaced by gspca which comes already installed on ubuntu:confused:

so i tried what the wiki tells you to do which is to run:

```
lsmod | grep gspca
```
to see if the module has been loaded..which it hadn't so i then ran:

```
sudo modprobe gspca
```

now according to the wiki pages this should fix it well it hasn't:(

I'm really confused do i need the spca5xx driver if it's predecessor is built into ubuntu...?

Wiki page in question: [https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

---

### Post by halitech on 2008-07-23
ok, I forgot about it now being included so don't need to compile it but not sure why its not working...

---

### Post by kamitsukai on 2008-07-23
so i still need the spca5xx driver? sorry about all the questions but ive already borked my vista install today...

---

### Post by halitech on 2008-07-23
no, shouldn't need them at all. trying to remember what else I did to get mine working

---

### Post by kamitsukai on 2008-07-23
I thought i might of found away to get my webcam working but it appears it doesent work for me...

i was trying this: [http://ubuntuforums.org/showthread.php?t=593231](http://ubuntuforums.org/showthread.php?t=593231)

but as it didn't work can you be so kind as to tell me how to restore what i changed (the commands i need to input..lol)?

"Note: You have a backup of the original driver located at "/lib/modules/uvcvideo.ko", in case the upgrade turned out
for the worst. You only need to copy it back to /lib/modules/$(uname -r)/ubuntu/media/usbvideo/
to restore the original driver. You can try to upgrade again at later date after the developers release some updates."



Thanks for all your help so far i think I'm off to bed now, as it's roughly 4am in the UK...

---

### Post by halitech on 2008-07-24
I honestly don't know, normally when you move a file you back it up first but looking at the instructions, it doesn't show any backup being made...

okay, looking at it more I see what they did. open a terminal and type these 2 commands and it should restore the file

```

sudo cp -av /lib/modules/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko

sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko &&
sudo depmod -ae $(uname -r)

```

---

### Post by kamitsukai on 2008-07-24
Thanks seeems to work :)...i've been looking into getting the webcam working and i dont think it is really going to be possible at the momment there's so many conflicting reports saying that such and such way works or do this or that but none of which seem to work :(  maybe when the monitor gets a little older and more people have one support might get better :D

---

### Post by halitech on 2008-07-24
webcams are one of those things that seem hit or miss and I've been lucky with mine, not that I use it very often. Hopefully you'll be able to get it working down the road.

---

### Post by kamitsukai on 2008-07-28
OMG:KS OMG:KS OMFG!!!:KS It's a miracle! I was reading a post about someone else trying to get there webcam sorted and then I kinda felt sad that mine still wasn't working so I typed in

```
sudo modprobe gspca

```

on the off chance, that I might get lucky and....it works!!!!:shock: don't you just love it when something suddenly works and you have absolutely no idea how?

Oh on a side note will Gspca load at boot or will I need to do something to make it do that?\\:D/

as you can tell I'm over the moon!

---

### Post by halitech on 2008-07-28
I know what you mean, I've had those moments myself where just clicking the right thing at the right time makes everything fall into place :)

with doing the modprobe it basically puts it into the kernal as a module to load so you shouldn't have to load it each time you boot.

---

### Post by LibertyShadow on 2008-07-28
You could add it to /etc/modules to ensure it is loaded at boot time.

---

### Post by halitech on 2008-07-28
I thought doing the modprobe would add it to /etc/modules ??

---

