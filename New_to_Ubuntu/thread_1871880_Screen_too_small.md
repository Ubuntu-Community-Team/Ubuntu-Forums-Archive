---
title: "Screen too small?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by rhedin on 2011-10-29
Hi. I've installed Ubuntu 11 on a Dell netbook 910. It has a 1024x600 screen. 
 
Before I installed 11 (it used to run 8) I had a row of menu items at the top of the screen. Now, I can see that the menu items are still there if I look at the teeny-tiny facsimile of the screen you see when you change workspaces. But the menu items are not visible when I go to any one workspace. I assume the screen doesn't have enough pixels vertically, and the menu items are off the screen. 
 
Does a 1024x600 screen meet Ubuntu's requirements? If not, is there an "Ubuntu light" I can install? 
 
Or have I mis-diagnosed the problem? 
 
 
Regards, 
 
Rick

---

### Post by rhedin on 2011-10-29
That smiley got created where I typed an 8 and a right paren.  I moved from version 8.

---

### Post by khelben1979 on 2011-10-29
Make a ```
lspci
``` and cut and paste the output to this thread. It's the graphics driver which will determine how well it handles your monitor resolution.

If you got a non-free driver installed from either AMD or nVidia, you should have a graphics control center where you can easily switch between different monitor resolutions. For AMD based video hardware it's called [AMD Catalyst]("http://en.wikipedia.org/wiki/AMD_Catalyst").

---

### Post by rhedin on 2011-11-01
KHelben, sorry to be so slow to respond.  I didn't realize until today I had a reply. 

That was really difficult!  I couldn't get a terminal up.  I tried /bin/bash.  Finally I found /usr/bin/gnome-terminal.

Anyway, here's the output:

rick@RicksNetbook:/usr/bin$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
rick@RicksNetbook:/usr/bin$

---

### Post by rhedin on 2011-11-04
So, what does this mean?  I can't interpret the output.     Regards, Rick   :p

---

### Post by 3rdalbum on 2011-11-04
> Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

You have Intel graphics, which should be fine. As a test I'll just get you to log out (go to the Unity Dash and type "log out" and it's the first item that appears. At the login screen, next to your name, click on the little cog icon and choose "Ubuntu 2D" or "Unity 2D", whichever one it's called. Log in and tell us if the little top bar appears now.

It should appear no matter what graphics card you have, but maybe Unity 2D works better.

---

### Post by rhedin on 2011-11-05
Hi, 3rdalbum.  It was "Ubuntu 2D."  
 
The behavior was the same.  I can't see the row of menus, but I can see them in the little pictures when I go to choose a different workspace. 
 
I notice that in the little pictures the menu items are in a gray band at the top.  On my regular window, there is a gray band at the top that says "Desktop".  I suspect that the Desktop gray band is obscuring the menu items gray band.  
 
Is this a reasonable conclusion?  Does it lead to a plan of action? 
 
 
               Regards, Rick

---

### Post by rhedin on 2011-11-14
I solved this problem.  I saw that Kubuntu offers specific "plasmas" for netbooks.  I installed Kubuntu, and I can see everything. 
 
I still can't get my wireless to work, but that's a different problem! 
 
Thanks for all the help. 
 
 
             Regards, 
 
             Rick

---

### Post by 3rdalbum on 2011-11-14
If you're talking about the program's menus not being visible in the bar at the top of the screen, then note that you just need to move your mouse to that bar to show the menus. The old "Applications Places System" menus from Gnome 2 are no longer available, if that's what you are talking about.

---

