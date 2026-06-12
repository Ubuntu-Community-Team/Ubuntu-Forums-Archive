---
title: "Trying to hang in there.......usb tether to net not working. HELP! Pretty Please"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by shortie2 on 2014-03-22
For over a month now I have been trying to dual boot win 8 and 12.04 lts.  I gave up.  I attempted to dual boot my Dell with win7 and ubuntu 12.04 lts.  
After a few attempts at different guides, I found one that worked for me [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/) with no problems and everything went smoothly. Now I cannot connect to the net.  

I use pdanet on my sprint note 2 4g  on windows.
I downloaded easytether for ubuntu and it says its connected but I cannot browse to web.  I also tried to connect to open wifi and nothing was detected.  If anyone has any insight.......I am typing this from win7 but i will boot back into Ubuntu to run any commands i need to.

---

### Post by squakie on 2014-03-23
What type of wireless adapter are you using when you try to attempt to connect to wifi?  If it's something like a USB dongle then post back the output of:

lsusb

If it's internal in the machine, post back the output of:

lspci

---

