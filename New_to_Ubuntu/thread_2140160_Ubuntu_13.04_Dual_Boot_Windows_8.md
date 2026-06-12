---
title: "Ubuntu 13.04 Dual Boot Windows 8"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by Eersfanpilot on 2013-04-28
So far I am impressed! 13.04 is running way better on my Windows 8 dual boot set up than 12.04 and 12.10. Keep up the good work Dev's!!

Earlier versions I have tried could not pick up my wifi in my house. 13.04 shows a signal strength out of the box at 61% (I am still running a Belkin USB antenna to get 100%) but 12.04, 12.10 and Fedora 18 all had issues picking up the signal. My Broadcom card is showing up in the wireless drop down options and works, just weak. Step in the right direction as far as I am concerned. 

So far 13.04 seems quicker than 12.10. I like that. I am getting used to Unity and even got Cinnamon installed but it kept freezing up on me, so back to Unity. 

Still having the issue where I can not close my laptop lid and go into standby. I can, but the screen still can not wake from it. 

Some things to note (maybe? I am a Noob so just trying to help):

Once, I hit standby from the drop down menu, It flashed to a log in screen, then the screen went black. Computer woke back up, but screen remained black (The same old situation I have been having with 12.04, 12.10, and Fed18)

Whenever I boot up 13.04 I get an error message stating no "Backlight Controller" (Something to that effect) 

Just thought I would throw those out there and maybe help?? Not sure if it helps for not though. Mainly wanted to say Great Job to those who worked on 13.04!

---

### Post by 0N3 on 2013-04-28
The backlight problem is it a samsung laptop by any chance? had same issue with a samsung laptop

---

### Post by Eersfanpilot on 2013-04-28
Shoot,  I'm sorry,  forgot to post laptop info.  That would have been helpful. 

 Lenovo Z585 A10

---

### Post by 0N3 on 2013-04-28
When installing Ubuntu did you install a swap partition? I had similar issue when I didn't install a swap partition. I could be completely wrong I am no genius basing my replies on personal experience

---

### Post by Eersfanpilot on 2013-04-28
Well I installed along side Windows 8 and let the installer do the work. I had already created a 100G partition for it to put Ubuntu into and according to Gparted I am showing a 95G partition (ext4) and a linux swap of 5.4G

This suspend/wake issue seems (from Google searches) to be a universal Linux problem that has been ongoing for a few years. I have seen posts as far back as 2009 dealing with the same issue. I have tried changing to proprietary drivers on the graphics cards to installing other drivers for the Broadcom 4313 card (which I have). Since upgrading to 13.04, that is the first time I have seen an actual error message regarding the inability to find a Backlight Controller. 

There have been posts from previous years with people thinking it was a backlight issue since the computer wakes, but not the screen. So I thought I would throw it out there.

---

