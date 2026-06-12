---
title: "hi guys new to ubuntu having issues with graphic card"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by dbranston4 on 2015-03-04
hhi guys im new to ubuntu at the moment the ionly thing i seem to be struggling with is the graphics card which is an intel hd 3000 this is the setup it has given me and try as i might to change the driver it wont let me so its currently on 

CPU: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz (2656.97 MHz)
Memory: 3994 MB
OS Version: Linux 3.16.0-31-generic #41~14.04.1-Ubuntu SMP Wed Feb 11 19:30:43 UTC 2015 i686
Graphics Card Vendor: Intel Open Source Technology Center
Graphics Card: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL Version: 1.4 (3.0 Mesa 10.5.0-devel)

so i tried running this [http://askubuntu.com/questions/87090/how-do-i-install-drivers-for-an-intel-hd-graphics](http://askubuntu.com/questions/87090/how-do-i-install-drivers-for-an-intel-hd-graphics) from this link in terminal although it gave the impression it had installed it when i went back to check the driver it is the same as previously mentioned above i cann use the 3d graphic software ( secondlife ) but it is nowhere near as effective as it is in windows i want to pull completley away from windows and this is realistically the only issue stopping me from doing it 

your wisdom and knowledge is greatly appreciated in advance 

pickles

ps i have been backwards and forwards with ubuntu previously this time i want it to be for keeps please help again many thanks in advance

---

### Post by Autodave on 2015-03-04
Have you tried going to SOFTWARE & UPDATES --> ADDITIONAL DRIVERS and seeing if that comes up with a suggestion?

---

### Post by dbranston4 on 2015-03-04
> **Autodave said:**
> Have you tried going to SOFTWARE & UPDATES --> ADDITIONAL DRIVERS and seeing if that comes up with a suggestion?

yeah tried that it isnt bringing up anything at all just says no additional drivers

---

### Post by Vladlenin5000 on 2015-03-04
Intel drivers are open source, already included, and for that reason alone they won't show up in "additional drivers"., This tool is intended to deliver proprietary drivers/firmware that can't be included in the installation media due to legal issues (so they say...).
There's no need to add PPAs or whatever.
The drivers already included may not be the latest version but should work fine anyway.

---

### Post by ajgreeny on 2015-03-04
Do you actually have any problems with your graphics?  Generally the open-source drivers for Intel integrated graphics are good, and there are no additional drivers available for Intel cards so you probably have got the best driver that you can have with that card in your version of Ubuntu.

If you enabled the xorg-edgers repository and have since updated and upgraded the packages, that will have given you the best driver from Ubuntu repos; or did you download the installer direct from Intel as shown on that askubuntu link?  I have never tried that and I am unsure how safe it is to do so or how likely the dependency problems they mention might add to your difficulties.

---

### Post by dbranston4 on 2015-03-04
yes i do have problems on second life as in it is lagging more so than it would on for example windows i went back to the intel graphics installer and i am currently updating as it seems there is an update for it hopefully this will help

---

### Post by ajgreeny on 2015-03-04
I am not a gamer but I presume "Second Life" is a game?

I suspect that unless it is a game that runs on low graphics systems you may be unlucky with that setup in Linux, but I may be talking out of turn here, because, as I say, I don't play games much, and those I do dabble in don't need much graphic power.

---

### Post by dbranston4 on 2015-03-04
> **ajgreeny said:**
> I am not a gamer but I presume "Second Life" is a game?

I suspect that unless it is a game that runs on low graphics systems you may be unlucky with that setup in Linux, but I may be talking out of turn here, because, as I say, I don't play games much, and those I do dabble in don't need much graphic power.

i think your more than likley right well i will just have to dual boot for the time being til i get a desktop or another laptop then its seeya bye to windows for good

---

