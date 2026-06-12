---
title: "Boot problems after usb removal - isolinux disk error 01, AX=0201 drive 80"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by InkyDinky on 2008-07-17
I have an PIII 750MHz running 8.04.  I rebooted the system after a system update with a 512 mb usb drive plugged in. Now when I reboot I get "isolinux disk error 01, AX=0201 drive 80".  I originally had the usb drive plugged in and it booted up but froze with the default brown of the log in screen (no log in prompt or anything else).  I unplugged the usb figuring that was the problem and now get the isolinux error.  I tried using the 7.04 livecd to rescue but wasn't sure where to start.  I tried to use grub but find /boot returned nothing. Nothing else has changed and the system was working fine up to the reboot. Although I did have to reboot because the system froze and I couldn't get to any other terminals.
Any help would be appreciated.

---

### Post by phidia on 2008-07-17
> **InkyDinky said:**
> ied using the 7.04 livecd to rescue but wasn't sure where to start.  I tried to use grub but find /boot returned nothing. 
Any help would be appreciated.

can you get to a grub prompt? the command in grub is find /boot/grub/stage1
that command should return some output. Based on that output you would do setup (hdx,y) where x=the actual drive. and y= the install partition.It all depends how you have grub installed though. 
There is also a great tool called [super grub disk]("http://www.supergrubdisk.org/") which might help you.

---

### Post by InkyDinky on 2008-07-17
I *think* that I also tried find /boot/grub/stage1 command although it might've been find /boot/stage1 and that returned nothing.
Part of my concern is why did leaving the usb plugged in cause the problem.  What change was made because of the USB drive being plugged in.
Once I get back home I'll try "find /boot/grub/stage1" and report back.

---

### Post by InkyDinky on 2008-07-17
Problem solved: 
So before I rebooted with the LiveCD I figured that I'd try rebooting with the USB flash drive plugged in.  This time grub loaded flawlessly.  There was a longer than expected boot time.  Also the bios was a bit confused as it loaded the configuration utility.  I just saved the configuration and plugged on.  I believe that somehow the unejected usb was causing problems or that the boot order was causing problems.  I only received the isolinux errors when I didn't have the usb stick plugged in.

---

### Post by InkyDinky on 2008-07-17
Well it seems like there is actually more to this story than just that.  The problem cropped back up.  My research had hit upon various areas such as the HDD dying as well as some type of problem with a 40? pin cable vs 80 pin.  So when the problem cropped back up again and by screwing around with pluggin and unplugging the usb in the back I decided to crack open the case.  So I crack it open and notice that through all my moving of the pc around that the hdd has wiggled loose and the ide cable may have gotten loose with it.  So I gave a push on the ide cable and gave a push to the power cable as well and she booted up fine.  I was a bit perplexed as occasionally the HDD would show up in the bios and other times it would disappear.  I didn't think that the hdd was dying so put opening the case off to the last moment.
HTH someone else who ends up with this problem.

---

