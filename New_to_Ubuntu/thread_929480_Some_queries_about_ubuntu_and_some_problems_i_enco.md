---
title: "Some queries about ubuntu and some problems i encountered"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by ajsup on 2008-09-25
I have been using Ubuntu for about a week now.. As told to me, its really an awesome operating system.. with lots of things to do.. no doubt about that.. Now, considering the fact that i am relatively new to this OS.. i would like to pose some queries regarding the OS.. if u could so kindly pls answer them without much delay, it would be really great..

1) Due to some unwanted reasons, the system seems to stop operating ie hangs it self.. Apart from shutting it down forcebly what else can I do? how can i restart without causing damage to my computer.. are there any hot keys or short cut key for restarting the comp..  I tried using the On/Off Key but that only stops the music player.. i looked up in the keyboard shortcuts also.. but there is no short cut key for restarting or shutting down.. except for the mouse click shut down button at the top right corner of the desktop screen, no other option..

2) Once i shut down forceably, i log back in.. i would want to perform a disc scan to check for bad sectors and all.. where & how can i do that, and is it necessary to do that in ubuntu..

3) The music player is good.. But sometimes it tends to stop playing music or video, for that matter.. why does that happen.. i usually restart the player.. it works.. else restart the comp..

4) can u suggest some other internet browser than mozilla and seamonkey.. 

5) i tried to install 3D desktop compiz.. but it says the gfx card in not sufficient.. but again.. if a laptop can work with windows vista and play games like splinter cell.. i doubt it is the gfx card.. last attempt.. can u suggest sumthing..

---

### Post by Peter09 on 2008-09-25
1. Ubuntu should not hang, so you have a problem there. Try <ctrl><Alt><BkSp> to get you back to a login prompt. We will need more information to understand what is happening.

---

### Post by prshah on 2008-09-25
> **ajsup said:**
> 
1) the system seems to stop operating ie hangs.. Apart from shutting it down forcebly what else can I do? how can i restart without causing damage to my computer.. are there any hot keys or short cut key for restarting the comp.. 

2) Once i shut down forceably, i log back in.. i would want to perform a disc scan to check for bad sectors and all.. 


3) The music player is good.. But sometimes it tends to stop playing music or video, for that matter.. why does that happen.. i usually restart the player.. it works.. else restart the comp..

4) can u suggest some other internet browser than mozilla and seamonkey.. 

5) i tried to install 3D desktop compiz.. but it says the gfx card in not sufficient.. 

1) You can (as a last resort) restart the computer safely, even from a hang condition by pressing the following keys in sequence:

Alt+SysRq+R (Remove keyboard control from X)
Alt+SysRq+E (End all running tasks)
Alt+SysRq+I (kIll remaining (hanging) tasks)
Alt+SysRq+S (Sync unwritten data to disk)
Alt+SysRq+U (Unmount filesystems)
Alt+SysRq+B (instant reBoot)

The keys sometimes _may_ not work, if the hang is hardware based.

2) If you restart after an improper shutdown, the disks are immediately checked. Not for bad sectors though; that has to be done manually. 

3) Check if you have setup [pulseaudio properly]("http://ubuntuforums.org/showthread.php?t=776739").

4) You can try Galeon / Opera / lynx (text only). Opera has to be downloaded from the opera website, Galeon and lynx are available from Applications-Add/Remove

5) You may not be running the correct drivers for your graphics card, or it may not be setup properly. Check the following, then post back for resolutions:
[indent]a. Press Alt+F2, give the command ```
displayconfig-gtk
``` Click on the "Graphics Card" tab, and note which driver is in use.
b. Now open a terminal (Applications-Accessories-Terminal) and post the output of the below command```
lspci -v | grep -E -A 5 -B 1 -i vga\|graphics
```
[/indent]

---

### Post by ajsup on 2008-12-22
thanks to both of you..

---

