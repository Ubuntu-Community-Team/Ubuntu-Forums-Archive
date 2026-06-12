---
title: "Only low res with w/845GL on board graphics"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by rockyroadnz on 2008-07-21
Well I have got Ubuntu 8.04.1 installed using safe mode whihc defaulted to 640 x 480 resolution. All the applications I have tried out seem to work, and I can get onto the internet using Firefox - so that's the good news
THe bad news is the graphics - I can't get the PC to run in anything but 640x480. 
Ubuntu can;t seem to detect the w/845GL on board graphics in the HP Pavilion 522a. 
Can anyone tell me what to do next?

Here's what I have done so far...

I tried the 'fix' in
[http://ubuntuforums.org/showthread.p...t=845gl&page=2](http://ubuntuforums.org/showthread.p...t=845gl&page=2)
By using the instructions in that thread I copied the following into my xorg.conf replacing what was already there:

Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
ModelName "Dell 1024x768 Laptop Display Panel"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "i810"
VendorName "Videocard vendor"
BoardName "Intel 845"
VideoRam 10000
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection


That made the machine hang after the first logon, then on the second try it gave me a message that I was running in "640x480 and did I want to adjust that or continue?" After going through that I ended back in 640x480.
At one point it gave the opportunity to pick the video driver so I chose i810 (because it was referred to in other threads) then is said it couldn't detect the video and reset the xorg.conf back to generic settings

I also tried System/Preferences/Screen Resolution which says 'Unknown '640x480 86hz with no other choices. 'Detect Displays' does nothing that I can see.

I suppose the good news is that I had to learn how to use a few linux commands and gedit so some would argue that I am a better person for it

But how do I get this darned video to go properly???

---

### Post by overdrank on 2008-07-21
Hi and welcome, what is the amount of memory on the system? How much is being shared with the intel graphics?
The link you posted does not include the "how to"
Have you tried to boot into recovery mode and use the xfix option?

---

### Post by rockyroadnz on 2008-07-22
> **overdrank said:**
> Hi and welcome, what is the amount of memory on the system? How much is being shared with the intel graphics?
The link you posted does not include the "how to"
Have you tried to boot into recovery mode and use the xfix option?

Absolutely wonderful. Many thanks from a happy Kiwi.
The xfix tool solved the problem. When I ran it the PC froze with a blank screen, but after power off and reboot it all came right. The monitor is now running 1024 x 768. The System>Preferences>Monitor Resolution says the monitor is HP 16" when it is actually HP 17" but because it works I don't care about that.
BTW - Where is a new user meant to look to find out about useful things like xfix?
Thanks again.

---

### Post by overdrank on 2008-07-22
> **rockyroadnz said:**
> Absolutely wonderful. Many thanks from a happy Kiwi.
The xfix tool solved the problem. When I ran it the PC froze with a blank screen, but after power off and reboot it all came right. The monitor is now running 1024 x 768. The System>Preferences>Monitor Resolution says the monitor is HP 16" when it is actually HP 17" but because it works I don't care about that.
BTW - Where is a new user meant to look to find out about useful things like xfix?
Thanks again.

HI and the forums is a good place to start, the sticky's at the top of the beginners forums has a abundance of info for new users. Feel free to ask questions but you may find the answer if you search the forums first. :)

---

