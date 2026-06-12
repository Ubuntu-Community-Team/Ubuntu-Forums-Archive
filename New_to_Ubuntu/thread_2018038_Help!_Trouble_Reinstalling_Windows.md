---
title: "Help! Trouble Reinstalling Windows"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by Jeff9 on 2012-07-05
I've decided after 3 weeks that I prefer to run Windows on my laptop (although keeping Ubuntu on desktop!). I made a bootable USB (which I've confirmed to work)to reinstall Windows.

The problem: When I go to the boot menu in bios, I see Ubuntu, my HDD, the USB, and one more option. When I select anything but "Ubuntu", nothing happens. 

Help! I'm trapped.

---

### Post by |{urse on 2012-07-05
What version of windows?

---

### Post by Jeff9 on 2012-07-05
Windows 7 Pro (64 bit, if that matters)

---

### Post by |{urse on 2012-07-05
Go into your bios and see if there are any boot to usb options, also set the boot order to boot the flash drive first. The version would matter if it was xp, because it sucks at life on usb bootability lol. Plus the fact that it never works even if it boots.

---

### Post by Jeff9 on 2012-07-05
In my BIOS I can set which device I want to boot from temporarily or permanently. 

When go to the temporary menu, I simply select my USB drive. The screen goes blank and then goes back to the device selection screen. The options listed are ubuntu, my HDD, the USB, and PCI LAN.

When I alter the boot order via the permanent menu, Ubuntu boots regardless (even if it's last behind EVERYTHING).

---

### Post by |{urse on 2012-07-05
Oh gotcha, almost seems like youll need to remake that usb drive bootable on that system, did you make it on this computer or another one? Also are all other usb ports exhibiting the same behavior?

[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html) <-- 
i know that guide works under ubuntu, just used it today.

---

### Post by Jeff9 on 2012-07-05
I made the original USB on another computer. Out of curiosity,why does it matter? 

Hmmm...I have a Windows 7 DVD, but no optical drive on my laptop. I'll need to think of how to get an ISO on that computer.

---

### Post by |{urse on 2012-07-05
Ive had it happen to me that windows on flash will be bootable on one sys and not on others. have you done a cmos reset? Maybe the cmos isnt saving boot priority settings when you f10?

-edit- nah that wouldnt matter because youre also selecting the usb from the boot menu..

---

