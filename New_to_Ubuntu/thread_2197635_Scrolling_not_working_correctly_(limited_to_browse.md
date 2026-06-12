---
title: "Scrolling not working correctly (limited to browsers)"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by wwwho on 2014-01-04
Hi,

**This is Me**
20 years on Windows. Some attempts on Linux about 10 years ago.

**My Setup**
I running the 12.04 in VMWare Player (6.0.1 build-1379776) on Windows 7 SP1. The host is a Lenovo Thinkpad X201 with 4 GB RAM and a 128 GB SSD. Virtualization extensions of the CPU have been enabled in the BIOS. I am using the integrated pointing device (Ultranav). The Ubuntu guest has peen provided with 1 CPU, 1 GB RAM and 25 GB hard disk space. VMWare Tools have been installed on the guest. Latest Ultranav driver installed on host as a troubleshooting step.
[B]
The Issue
[/B]I apologize in advance in case my description is not very clear which might be due to the fact that I am a non-native English speaker. 

The issue is with scrolling web pages in browsers. When I scroll web pages using the mouse, the scrolling behavior is erratic. It surfaces only in browsers but not in other applications like Libra Writer. There are three variations of it which I will describe below. 

[I]Dragging the scroll-bar handle
[/I]Dragging the scroll-bar handle starts out working fine but after a bit down the page the scrolling stops for a while, then jumps down the rest of the way. 

[I]Clicks on the scroll-bar not registering 
[/I]Something similar is happening when I click on the scroll bar, which should do a page-down or page-up operation. Again, this always works for the first click and sometimes also for one or two subsequent clicks. After that, the browser will stop responding to the clicks for a a few seconds, and then, will jump down to the end of the page. 

*Clicks on the scroll bar registering as multiple clicks*
A third behavior pattern is that some clicks on the scroll bar seem to trigger multiple page-up or page-down steps in the browser; that is I click once and the page scrolls far beyond the point where it should usually stop. This last pattern convinced me that this is not a performance issue like when the virtual machine would hang because the CPU is busy and then would execute the queued actions when it is available again.

The issue seems to occur only in browser windows. Libra Writer, for example, does not seem to show this behavior, which is another cue that this is not related to performance.

**Troubleshooting Steps**
[LIST]
[*]Installed Chromium to exclude Firefox as problem. Chromium has the same problem. 
[*]Tried varios combinations of the CPU virtualization optimizations in VMWare Player. At the moment it is set to Automatic. 
[*]Added a second CPU in VM Player 
[*]Installed latest Ultranav driver on host 
[*]Monitored Windows Task Manager to see if there were any CPU spikes. There were none. CPU was always below 20% no matter how many CPUs I added to the virtual machine. 
[/LIST]

Thank you very much in advance for reading this far and even more for considering to answer back :-)

---

### Post by wwwho on 2014-01-05
Bump

---

### Post by MrMichaelHill on 2014-01-05
Check the graphical side of things?

Does VMWare have things like 3D/2D Acceleration?

---

### Post by wwwho on 2014-01-06
It does but I cannot configure it. Help states "Accelerated graphics  capabilities apply to Windows XP, Vista, and, 7 guests". So that seems  to be the end of this route :-/

However, I found that my host-graphics driver (Intel) allows to choose between different power modes. Since it was set to save power, I changed that to performance mode, which seems to have gotten rid of most of the hanging. 

The other issue with mouse clicks being multiplied. Is still present however. I just did another test with Opera. Firefox seems to show the issue the least, followed by Chromium and the by Opera, which is the worst. It is really funny to look at. I click on the scroll bar (not the scroll buttons) and the page scrolls all the way down or up by it self. As sso as I move the pointer from the scroll bar, the scrolling stops.

Cheers!

---

### Post by MrMichaelHill on 2014-01-06
Hmmm its a strange one!

My guess would be at something to do on the graphical end. Do you have any of the additions installed? I'm not sure what it is in VMWare but in VirtualBox when you have installed an OS next you must install the **Guest Additions**, this configures things like graphics drivers, mouse integration etc... 

Does VMWare have something similar? and is it installed? :)

---

### Post by newb85 on 2014-01-06
I don't have VMWare experience (I use VirtualBox myself), but I believe the package open-vm-toolbox is somewhat analogous to VB's virtualbox-guest-utils.

---

