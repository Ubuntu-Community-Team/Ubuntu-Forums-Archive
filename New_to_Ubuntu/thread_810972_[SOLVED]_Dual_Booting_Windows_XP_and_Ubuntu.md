---
title: "[SOLVED] Dual Booting Windows XP and Ubuntu"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by ben32b on 2008-05-28
I currently have two SATA hard drives in my computer. One hard drive has Windows XP installed on it. The other hard drive has Ubuntu installed on it.

Whenever I turn on my computer (with the way it is set up at the moment), a menu comes up telling me to select either Windows XP or Ubuntu to load.

I want to make it so that when I turn my computer on, no menu comes up, and instead Windows XP loads instantly and automatically by default.
I want to make it so that if I want to load Ubuntu instead, I just press a button while the BIOS is still loading, to get in Ubuntu for that session instead (rather than the default I want of loading automatically to XP).


It would be very helpful if someone could post a download link to something which can do this, and explain how to set it up.

Any help will be greatly appreciated.

---

### Post by SunnyRabbiera on 2008-05-28
Eh, what you ask for is mostly possible but not advisable.
I suggest leaving things the way they are, I know its an extra screen to go through but its only there for a short time.

---

### Post by markbuntu on 2008-05-28
Ahhh.. top secret Ubuntu. There is probably some way to do that with grub. Making XP the default with a 1 second timeout but you would have to be extremely quick on the keyboard to intercept that.

There is a way to intercept the bios, usually F1 or F4 to change the default boot configuration to look for the Ubuntu drive instead of the XP one but you would need to reboot and change it back at the end of your session.

That said, it is not really a good idea to be messing around with the bios all the time. Bad things can happen.

---

### Post by ben32b on 2008-05-28
**SunnyRabbiera:**
Other people who use this computer are not good with computers and get confused when the menu comes up asking them if they want Ubuntu or Windows.
I know it won't be extremely easy to do what I want, but it will make it much less confusing for these other people who use this computer.

Can you please go ahead and explain in detail the possible but not advisable method?

All of my files are already backed up just for if something goes wrong.


**markbuntu:**
It's not meant to be secret, just to make it so that other people who use this computer won't be confused.



I want to try to replace the default BIOS OS loading menu with XP as default & Ubuntu when pressing a certain button.
I won't even need a "OS select screen" if XP is default and one button loads Ubuntu instead.

---

### Post by Golem XIV on 2008-05-28
Hmmm

Never tried this, but it may just work:

Boot, enter BIOS, set SATA0 as boot drive.  Install Windows on SATA0 (C: )
Reboot, enter BIOS, set SATA1 as boot drive.  Install Ubuntu on SATA1 and put GRUB on sdb (in the Advanced option at the last dialog during installation)

Reboot.  During POST, press button to bring up BIOS boot menu.  Select SATA0 to boot to Windows, SATA1 to boot to Ubuntu.

If Windows is already installed on SATA0 then you just need to get rid of GRUB on sda (Windows recovery console, fdisk /mbr) and instal it on sdb.

---

### Post by ben32b on 2008-05-28
> **Golem XIV said:**
> 
During POST, press button to bring up BIOS boot menu.  Select SATA0 to boot to Windows, SATA1 to boot to Ubuntu.


Currently the BIOS boot menu automatically comes up because it detects two different operating systems in the hard drives.
It then does what you said, where you select which drive.

Here's a slightly different thing than what I originally thought of.


So this is what I want the computer to do:
1. If F12 is not pressed while the BIOS is loading, do NOT load the BIOS boot menu, and instead load Windows.
2. If F12 is pressed while the BIOS is loading, go to the BIOS boot menu where I can select Ubuntu as the OS for that session.
**^  ^  ^  How can I do this?  ^  ^  ^**

---

### Post by impert on 2008-05-28
Oops

---

### Post by starcannon on 2008-05-28
I'd just edit the /boot/grub/menu.lst file, set windows to default, set the timeout down to 1 second *you'll have to hit the escape key quick to catch it at 1 second* and call it good.

---

### Post by inportb on 2008-05-28
I would do that too.

But you say your BIOS shows you a boot menu automatically? If so, what's your BIOS?

---

### Post by ben32b on 2008-05-28
> **inportb said:**
> 
But you say your BIOS shows you a boot menu automatically? If so, what's your BIOS?
Yes, the boot menu comes up automatically because it finds more than one OS
My BIOS is Dell Dimension 8400's A09 BIOS

---

### Post by ben32b on 2008-05-28
bump

---

### Post by ben32b on 2008-05-28
In the default boot loader, how can I do the following:
1. Set windows xp to selected by default (ubuntu is currently default because it is in alphabetical order).
2. Change timeout to 3 seconds.

I am not sure how to get into something that lets me edit the boot loader.

---

### Post by frayalejandro on 2008-05-28
> **starcannon said:**
> I'd just edit the /boot/grub/menu.lst file, set windows to default, set the timeout down to 1 second *you'll have to hit the escape key quick to catch it at 1 second* and call it good.

I also have multiple users in this computer, and I set the timeout down to 3 sec; usually, no one asks what is this menu for (they dont even have the time to read it), and it gives me enough time to boot from Ubuntu.

The instructions are here:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by starcannon on 2008-05-28
> **frayalejandro said:**
> I also have multiple users in this computer, and I set the timeout down to 3 sec; usually, no one asks what is this menu for (they dont even have the time to read it), and it gives me enough time to boot from Ubuntu.

The instructions are here:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

aye I just leave mine at the default here, everyone here knows what the menu is for on the onliest dual boot box, and that link is great, I just figured the comments at the top of the menu.lst file were pretty complete so assumed that would work for most peoples needs.

Anyway yeah I agree, 3 seconds is plenty fast while still allowing time enough to hit an arrow key.

---

