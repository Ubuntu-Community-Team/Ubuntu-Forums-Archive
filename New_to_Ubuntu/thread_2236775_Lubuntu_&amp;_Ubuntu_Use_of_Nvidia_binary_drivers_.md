---
title: "Lubuntu &amp; Ubuntu: Use of Nvidia binary drivers causes system to freeze."
date: 2014-07-28
forum: New to Ubuntu
---

### Post by kira-yamato-2008 on 2014-07-28
After searching high and low for an answer and have come up empty on solving this problem.
OS: Lubuntu 14.04 64-Bit and Ubuntu 12.04 64-Bit

The Hardware:
HP G60-120US Laptop
CPU: AMD Turion X2 64-Bit @ 2.00GHZ
RAM: 3GB DDR2 (Shared with GPU)
GPU: Integrated nvidia GeForce 8200M G
Other: External VGA Hanns-G 19 inch 4:3 aspect ratio LCD Monitor. (Needed because the Laptop's LCD is broken, cracked and only a third of the screen actually works on it. It makes a handy keyboard light though.)

The issue in detail: When ever I load up any nvidia binary driver Lubuntu 14.04 will freeze during OpenGL games, videos, flash videos; and just for the sake of it, randomly when no apps are open. It's even worse in Ubuntu 12.04 which freezes rather quickly just with the Unity DE running, mostly it just freezes on start up before I can even do anything. Nothing works after either happens, nothing. I have to do a hard reset on the machine. Now then the reason I want to use the nvidia binary drivers is becuse the Nouveau display driver causes tearing in OpenGL games, on Ubuntu's Unity DE, and on Hulu's browser video player (although not the pop-out one.) Generally the binary drivers will work up to a minute in an application that uses OpenGL in Lubuntu before a freeze occurs, and I know that the nvidia drivers fix any issue I have with tearing, because on Nouveau the tearing starts as soon as any OpenGL application starts. Windowed mode on the app doesn't help, neither does full screen.

I'd really like to solve this problem. I'd like to be able to play Open Arena, Source Engine games, and few others. The games I want to run are compatible with Linux/OpenGL and I know this PC has enough muscle to run them without issues. So with that in mind ANY input would be helpful.

Side note #1: Nouveau driver causes graphical tearing in 3d OpenGL regardless of monitor settings. Nvidia binary drivers cause the freezing regardless of the settings. Even if one monitor is off. 
Side note #2: On the Ubuntu 12.04.4 64-Bit LiveDVD there was no graphical tearing with the Nouveau drivers, on the Unity DE; however, after the Install there started being graphical tearing.

---

