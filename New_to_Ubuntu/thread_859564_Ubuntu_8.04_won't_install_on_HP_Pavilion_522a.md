---
title: "Ubuntu 8.04 won't install on HP Pavilion 522a"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by rockyroadnz on 2008-07-14
Hi, I am trying to install Ubuntu on an HP Pavilion 522a, so the neighbours kids can have a PC to surf the net and share music.
There install fails with no hints as to what is wrong. Can anyone help 

I downloaded ubuntu-8.04.1-desktop-i386.iso, burned a CD and booted  it OK.
Selected English language (the default)
Selected 'Install Ubuntu'
Watched the progress bar move up and down for a few minutes.
Screen then switched to blank then faint raster a few times.
Machine then froze with faint raster displayed.
At this point I can't alt/ctrl/delete to reboot and can't eject the CD.
Only way is to force power off.
I've tried this a few times with same result.

I have run 'Check CD' OK and 'Check Memory' OK. I don;t think there's anything wrong with the PC because it boots up Windows OK.
I'm starting to wonder if the HP Pavilion 522a is not good enough to run Ubuntu?

I'm lost - no idea what to do next and don't want to go back to Windows.
Any advice appreciated.
Keep in mind when offering advice that I am a total novice. Until recently I thought Unix were people that protected harems.
Thanks.

---

### Post by LowSky on 2008-07-14
Well I tried to look around but no luck.. what are the specs of the computer

from ubuntu.com

"System Requirements 
Ubuntu is available for PC... At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space. " What isn't said is that you need about a 1Ghz Processor as well

I think the Xubutu is a better choice as it can run on older hardware and use the Alternative CD is a better Option to try, you can download it here
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/xubuntu-8.04.1-alternate-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/xubuntu-8.04.1-alternate-i386.iso)


If that doesn't wrk may I suggest Puppy Linux, it can run on nearly anything
[http://www.puppylinux.org/downloads](http://www.puppylinux.org/downloads)

---

### Post by braddcadd on 2008-07-14
I would try the alternate install CD.  It has a text based installer.  If the GUI causes the hangup, maybe textbased can force through the issue.  Just a guess.

Maybe try one of the older versions of Ubuntu (6.06 or 7.10) as a last resort.  (Get Ubuntu on and drop the window$ !!)

Good Luck

---

### Post by SunnyRabbiera on 2008-07-14
Hmm, it should work, as HP's are usually good with linux... but it can still be a bad burn.

---

### Post by Pastortom on 2008-07-14
> **rockyroadnz said:**
> Hi, I am trying to install Ubuntu on an HP Pavilion 522a, so the neighbours kids can have a PC to surf the net and share music.
There install fails with no hints as to what is wrong. Can anyone help 

I downloaded ubuntu-8.04.1-desktop-i386.iso, burned a CD and booted  it OK.
Selected English language (the default)
Selected 'Install Ubuntu'
Watched the progress bar move up and down for a few minutes.
Screen then switched to blank then faint raster a few times.
Machine then froze with faint raster displayed.
At this point I can't alt/ctrl/delete to reboot and can't eject the CD.
Only way is to force power off.
I've tried this a few times with same result.

I have run 'Check CD' OK and 'Check Memory' OK. I don;t think there's anything wrong with the PC because it boots up Windows OK.
I'm starting to wonder if the HP Pavilion 522a is not good enough to run Ubuntu?

I'm lost - no idea what to do next and don't want to go back to Windows.
Any advice appreciated.
Keep in mind when offering advice that I am a total novice. Until recently I thought Unix were people that protected harems.
Thanks.


It seems like there are MANY users on this forum who has the EXACT same problem as you, mate..

And Im one of them..

Ive tried several installation methods, but each time Ubuntu tries to run its GUI (not text based) it freezes.. after many trial and errors during install Ive managed to install Ubuntu and managed to get it to boot up, but every time it tries to load the GUI it freezes.. 

Im betting theres a graphic card error, but I dont know enough about linux to avoid that..

anyone got a clue?

---

### Post by SunnyRabbiera on 2008-07-14
depends on the card, if its an ATI it can cause serious bugs.

---

### Post by kansasnoob on 2008-07-14
> Watched the progress bar move up and down for a few minutes.
Screen then switched to blank then faint raster a few times.
Machine then froze with faint raster displayed.

How long did you wait?

I've honestly seen this dozens of times and if I just waited 15 or 20 minutes, and then just moved the mouse around a bit, NO PRESSING BUTTONS, the screen resumes and I learn that "things" have been happening.

You are after all installing an OS! It takes normally 20 to 25 minutes for my computer to complete the initial install (depends on hardware) and then another 10 to 30 minutes to run updates, then I can begin installing my preferred "stuff".

OTOH I have found sometimes that installation just "stalls" for no apparent reason and I have to use the text based Alternate CD to install. I suspect it's a hardware conflict.

Sorry, I'm getting yelled at! Time to kill more chickens.

---

### Post by brnetonboy on 2008-07-14
it sounds to me like that blank screen was the screensaver. i dunno why they have a blank screensaver go on during install, it's stupid. but if you hit ctrl-alt-del, you may have done it at an inopportune time and messed something up.

try reinstalling again and this time move the mouse around if the screen goes black.

you also might want to try downloading another copy of the newest version of linux (8.04.1) and re-burning it, just so you can be confident it wasn't the disc.

i had trouble installing linux because of the way the discs were burned, even though i did a disc check and it came out OK. i used a different burner and it worked fine.

---

### Post by cariboo on 2008-07-14
If you try the LiveCD in Safe Graphics Mode:

With "Try Ubuntu Without Changing Anything" highlighted hit F4 and select Safe Graphics Mode, then hit return to select that mode and then start Ubuntu. 

Jim

---

### Post by rockyroadnz on 2008-07-14
> **LowSky said:**
> Well I tried to look around but no luck.. what are the specs of the computer

from ubuntu.com

"System Requirements 
Ubuntu is available for PC... At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space. " What isn't said is that you need about a 1Ghz Processor as well

I think the Xubutu is a better choice as it can run on older hardware and use the Alternative CD is a better Option to try, you can download it here
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/xubuntu-8.04.1-alternate-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/xubuntu-8.04.1-alternate-i386.iso)


If that doesn't wrk may I suggest Puppy Linux, it can run on nearly anything
[http://www.puppylinux.org/downloads](http://www.puppylinux.org/downloads)

Thanks for the reply's so quickly from all of you. 
The PC only has 256Mb Ram, so I will download the Alternate CD you referred to and try it tonight.

Machine specs are:
The HP Pavilion 522a with Intel 1.7ghz processor (Celeron I think)
256MB Ram
80GB drive
'Intel Extreme 3d Graphics' (HP website says Integrated w/845GL Chipset)

---

### Post by Xerp on 2008-07-14
Xubuntu is great on low spec machines too :)

---

### Post by Pastortom on 2008-07-14
> **rockyroadnz said:**
> Hi, I am trying to install Ubuntu on an HP Pavilion 522a, so the neighbours kids can have a PC to surf the net and share music.
There install fails with no hints as to what is wrong. Can anyone help 

I downloaded ubuntu-8.04.1-desktop-i386.iso, burned a CD and booted  it OK.
Selected English language (the default)
Selected 'Install Ubuntu'
Watched the progress bar move up and down for a few minutes.
Screen then switched to blank then faint raster a few times.
Machine then froze with faint raster displayed.
At this point I can't alt/ctrl/delete to reboot and can't eject the CD.
Only way is to force power off.
I've tried this a few times with same result.

I have run 'Check CD' OK and 'Check Memory' OK. I don;t think there's anything wrong with the PC because it boots up Windows OK.
I'm starting to wonder if the HP Pavilion 522a is not good enough to run Ubuntu?

I'm lost - no idea what to do next and don't want to go back to Windows.
Any advice appreciated.
Keep in mind when offering advice that I am a total novice. Until recently I thought Unix were people that protected harems.
Thanks.

Mate, while trying to find a solution for the same problem on my own computer I found the same solution for your problem.

When you boot your computer with the Ubuntu install CD highlight "Install Ubuntu" and push F6 then hook off ALL additional options.. or at least "ACPI=off".. I had the 100% exact same issues as you with all kinds of Ubuntus trying to load GUI (after seeing the loading bar fill up and you see the screen flicker).. but when I added ACPI=off at the end it fixed my problem..

At the moment I also remove the tag "splash" and add the tag "vga=773" to make sure the video resolution isnt the problem during bootup..  if you're still having problems you might wanna try "Safe Graphic Mode" which is under F4 at Ubuntu bootup menu.. 

Good luck mate, and I hope this saves you 12 hours of hard work which Ive been through to accidently find this out..

---

### Post by rockyroadnz on 2008-07-15
Ok, Thanks again to all. 
I really appreciate all you help and advice.
It was (is) a graphics driver problem. Installing in Safe Graphics mode got it going. I can now boot Ubuntu from the hard drive. Yippee...  :) 
The graphics look fairly lousy but I'm not going to bother about that for the moment. I now have to investigate why the ethernet network won't work. That might have to be a problem for me to solve tomorrow night.

---

### Post by rockyroadnz on 2008-07-17
Well the network problem was easy to overcome - the network is not being enabled at startup. So I just start it manually. I can live with that.

But back to the original problem - the graphics :mad: I can't get the PC to run in anything but 640x480. Ubuntu can;t seem to detect the w/845GL on board graphics. I tried the 'fix' in 
[http://ubuntuforums.org/showthread.php?t=30235&highlight=845gl&page=2](http://ubuntuforums.org/showthread.php?t=30235&highlight=845gl&page=2)
I copied the following into my xorg.conf replacing what was already there

Section "Device"
       Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
       Driver          "i810"
       BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
       Identifier      "Generic Monitor"
       ModelName       "Dell 1024x768 Laptop Display Panel"
       HorizSync       31.5 - 48.5
       VertRefresh     59.0 - 75.0
       Option          "DPMS"
EndSection

Section "Device"
       Identifier      "Videocard0"
       Driver          "i810"
       VendorName      "Videocard vendor"
       BoardName       "Intel 845"
       VideoRam        10000
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
       Monitor         "Generic Monitor"
       DefaultDepth    24
       SubSection "Display"
               Depth           1
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           4
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           8
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           15
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           16
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           24
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
       Screen          "Default Screen"
       InputDevice     "Generic Keyboard"
       InputDevice     "Configured Mouse"
EndSection


That made the machine hang after the first logon, then on the second try it gave me a message that I was running in "640x480 and did I want to adjust that or continue?"   After going through that I ended back in 640x480.
At one point it gave the opportunity to pick the video driver so I chose i810 then is said it couldnt detect the video and reset the xorg.conf back to generic settings

I also tried System/Preferences/Screen Resolution which says 'Unknown '640x480 86hz with no other choices. 'Detect Displays' does nothing that I can see.

I suppose the good news is that I had to learn how to use a few linux commands and gedit so some would argue that I am a better person for it :-)

But how do I get this darned video to go properly???

---

