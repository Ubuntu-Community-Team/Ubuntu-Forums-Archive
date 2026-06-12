---
title: "Blank screen after ubuntu upgrade to 11.10"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by aditi12 on 2012-11-17
Hi,

I have recently upgraded from Ubuntu 11.04 to 11.10 via the Upgrade Manager. The process went smoothly until the point it came to "Restarting system". At this point the terminal came up with some commands and hex codes. The last command was something with "restart" and nothing happened after that. I had to wait for 5 mins and then I restarted my computer. Since then every time I load linux I get a blank screen. Any help would be greatly appreciated.

I am using a ThinkPad E420 with dual boot - Win7 & Unbuntu (64 bit). I tried booting via the ISO image for 11.10 through a USB stick but then it says "BOOTMGR is missing, press ctrl+alt+del to restart".

Thanks!
Aditi.

---

### Post by Bartender on 2012-11-17
In my opinion the simplest, most straightforward thing to do is to download an Ubuntu install .iso.  I'd suggest the 12.04 LTS download unless you like upgrading more frequently.

You can use a Windows PC to get the download and make the bootable CD.  Just use ImgBurn as the program to make a bootable disc.  It'll recognize the download as an .iso if I recall correctly and burn a disc properly so that it's bootable.

Boot from that disc.  When you get to the stage in the installer where it asks what you want to do, choose "Replace Ubuntu".  I don't know whether it'll say "Replace Ubuntu 11.04" or "Replace Ubuntu 11.10" since it sounds like the upgrade didn't finish correctly.

EDIT: Booting from USB is much less reliable than CD/DVD.  There are many USB sticks for sale that simply won't work as an installer.  The ones that come with their own Windows-centric firmware are the obvious losers, but I've got one or two that are just plain old USB sticks and they don't work, even when I did exactly the same thing as with the USB stick that DID work.

---

