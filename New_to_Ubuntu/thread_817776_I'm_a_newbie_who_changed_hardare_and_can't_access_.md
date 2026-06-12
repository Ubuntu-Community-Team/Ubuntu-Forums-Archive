---
title: "I'm a newbie who changed hardare and can't access Ubuntu now..."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Paratech on 2008-06-03
I had just upgraded my PC and now have a 2.6 GHZ Dual Core with 2 Gygs RAM, a Nvidia 8600, SB Live! and USB Robotics USB Modem. I have 3 partitions of hard drives, the main drive is partitioned into two ~14 gyg hard drives, one booting to Ubuntu 7.10 64 bit and the other to Windows XP SP2. The second hard drive is 500 GB.

When I installed Ubuntu, I was using *shudder* onboard video which was worse than the Raedon 9200, think the ATI 9200 WITHOUT Pixel shaders. Now I have a decent card, but Ubuntu crashes when I try to boot into Linux. I can go into safe mode, but I'm clueless in command prompt like areas.

I'll admit I've been spoiled by Windows, since Windows 98SE, I haven't used the command prompt on my computer and I have no clue about Linux commands.

I want to learn. I've already tried reinstalling Ubuntu, but it froze when it went to a GUI. I really could appreciate some help in getting started.

I'm primarily interested in emulation, but I'm not asking for any emulation help here, just help understanding how to set up the hardware on my PC. I want to learn how to get around Linux as well as play games, but playing games is the priority.

I'm hoping the modem can be used in Linux as my video card ate 2 slots and I only have 1 PCI slot and it's for my Sound Blaster Live. I don't want to mess with my onboard sound. I couldn't get it running on my PC when it was set up and I'm uninterested in trying. I prefer the SB Live! anyways.

So where do I get started.

Thanks to everyone willing to help me.

-Chris "Paratech" Cummins

---

### Post by rraj.be on 2008-06-03
to understand about terminal you can go here.


[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")







for games you can get here.

[https://help.ubuntu.com/community/Games]("https://help.ubuntu.com/community/Games")

[www.ubuntugames.org/en/UbuntuGames]("www.ubuntugames.org/en/UbuntuGames")


[linux.about.com/od/ubuntu_doc/a/ubuntu_games.htm]("linux.about.com/od/ubuntu_doc/a/ubuntu_games.htm")

[linuxgames07.blogspot.com/2007/11/top-ubuntu-linux-games.html]("linuxgames07.blogspot.com/2007/11/top-ubuntu-linux-games.html")

---

### Post by Paratech on 2008-06-04
When I get into the terminal, how will I find my way to changing the drivers that Linux needs? Can I download them *Linux drivers* onto my 500 gyg hard drive and access them from Linux?

I printed the text from the first link you sent me. I appreciate the help.

Thank you.

---

### Post by rraj.be on 2008-06-04
I cant get what you are asking for DRIVERS.

For 90 % you dont need any drivers including for your motherboard or sound card.

And for thanking there is a Medal symbol at the bottom of every post,near quote, quick reply buttons. so that you can click it to thank.

just do if you are really helped and you want to be thank full.


Further avoid using the terms like newbie, i am a nob.,, tired of etc.

your heading should contain something that tells every one whats the problem so that those who know about it can help you immediately and clearly.

and also mark your thread as solved if your problem is solved.

loot at the link in my signature

---

### Post by jualin on 2008-06-04
so did u get everything to work? or do you need more specific information of how to boot up ubuntu with the new hardware?

---

### Post by Paratech on 2008-06-04
I don't understand how I let Ubuntu know the hardware has changed? If it doesn't see the drivers have changed, doesn't it require I manually reconfigure the settings of the hardware?

I mentioned I was new at this so people might talk to me like I have no understanding of Linux. I'll try to be more clear in future posts...

From what I gather Ubuntu is setting the graphics/video for an ATI setting and I'm using an NVIDIA 8600, how do I tell Linux what hardware I'm using on my PC?

---

### Post by jualin on 2008-06-04
Boot up your computer in failsafe mode and when ask to log in, just log in, you first have to put your username and then it will ask you for your password. After you are log in (command line logged in), try this > sudo dpkg-reconfigure xserver-xorg. This will ask you a few questions and then it will reconfigure the hardware recognition for you. Tell me how that goes, good luck!

---

### Post by rraj.be on 2008-06-04
see this

but i dont have any experience in using that card.Sorry dude.

[ubuntuforums.org/showthread.php?t=460765]("ubuntuforums.org/showthread.php?t=460765")

---

### Post by Paratech on 2008-06-11
I've managed to get Linux up and running but I need drivers to use the 3D capability of my video card. I'll try and look for the drivers but I may need help finding and installing them.

:confused:

---

### Post by stalkier on 2008-06-11
> **Paratech said:**
> I've managed to get Linux up and running but I need drivers to use the 3D capability of my video card. I'll try and look for the drivers but I may need help finding and installing them.

:confused:

Goto System - Administration - Hardware Drivers
Click enable on your video chipset. You may need to restart the PC.

---

