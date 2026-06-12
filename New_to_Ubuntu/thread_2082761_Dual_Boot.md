---
title: "Dual Boot"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by HakimMalagasy on 2012-11-10
Hello,
I'm new on Ubuntu, and I have a little problem.
My problem is, I have Windows OS on my PC.
I installed an Ubuntu in another partition of my disk (not alongside windows). when the installation was finished, and I restart my computer, I couldn't see the Ubuntu I installed.
So help me to fix this issue.
Thank you.

---

### Post by 2F4U on 2012-11-10
What do you mean by installed in another partition but not alongside Windows? Alongside Windows usually means dual boot. Did you install through Wubi?

---

### Post by Bartender on 2012-11-10
Never mind.  +1 on 2F4U's comments - did the OP try and fail to do a true dual-boot, or is this Wubi, or maybe even virtualization?

---

### Post by El Tito on 2012-11-10
Have you installed grub and made de partition bootable?, I never have had problems installing alongside windows. Can you be more specific?

---

### Post by greatsirkain on 2012-11-10
in windows (if you have a usb stick)  make it bootable with Sardu selecting ultimate boot cd etc  (you can also add Ubuntu, SUSE and windows, among others, so you have live OS's on there too) then when you boot from your usb stick use grub or supergrub2 (from the utilities menu I think) to detect all operating systems then just select the one you want to use. A bootable usb stick with as many tools as you can get on there will always come in handy for fixing your computer.

---

### Post by HakimMalagasy on 2012-11-10
Thank you so much for your reply.
I mean with "not alongside windows", when you install Ubuntu, it asks you to install Ubuntu alongside windows or replace windows with Ubuntu or something else.
Me, I choose "Something Else" and I putted it in another partition of my disk (because I've already partitioned my disk via windows). And After I just follow the instruction.
Finally, it asked me to restart my computer, I did so, and the PC run directly with windows without asking me any choose.

---

### Post by 2F4U on 2012-11-10
Where did you install the bootloader Grub? It looks as if it went into the wrong place.

[http://ubuntuguide.org/wiki/Ubuntu:All#Installing_multiple_OS_on_a_single_computer](http://ubuntuguide.org/wiki/Ubuntu:All#Installing_multiple_OS_on_a_single_computer)
[http://askubuntu.com/questions/148881/dual-boot-windows-xp-and-ubuntu-12-04](http://askubuntu.com/questions/148881/dual-boot-windows-xp-and-ubuntu-12-04)

---

### Post by #1udancqSHv% on 2012-11-10
> **HakimMalagasy said:**
> Thank you so much for your reply.
I mean with "not alongside windows", when you install Ubuntu, it asks you to install Ubuntu alongside windows or replace windows with Ubuntu or something else.
Me, I choose "Something Else" and I putted it in another partition of my disk (because I've already partitioned my disk via windows). And After I just follow the instruction.
Finally, it asked me to restart my computer, I did so, and the PC run directly with windows without asking me any choose.

Hi Hakim, I've had a similar problem in the past, and although there are many possible fixes, this is one tactic that's worked for me. I've installed EasyBCD (not open source, unfortunately, but personal use version is free) and used the config to select the Linux partition. Then I went to the boot screen tab and created/edited entries in there, I think I checked the other tabs to see if there were any other settings to change, then went to the 'BCD Deployment' tab. You can then choose whether to deploy a Win Vista/7/8 bootloader or Win XP, and write it to the MBR. I've currently got it installed on my desktop PC until I can work out how to reconfigure GRUB-2 so it picks up Windows 7, and the three Linux distros I've just installed (Ubuntu, Mint and Mageia) - my family is new to Linux so we're all testing the three of them! Good luck, and hope you get this working!

---

### Post by HakimMalagasy on 2012-11-11
Hi guys, I can use Ubuntu now. Thank you for all your advices.
@jfj33, you were right. thanks:)

---

### Post by #1udancqSHv% on 2012-12-02
You're welcome! :)

Incidentally, you may well have already cracked this, but once I managed to get back into Ubuntu, I ran 'sudo os-prober' then 'sudo update-grub', which seemed to get grub back in charge again. Then I went back into Windows and uninstalled/removed EasyBCD.

Personally, I'd rather have Grub2 looking after the boot process as I intend to remove Windows after I'm fully comfortable about never needing to go back into the Win7 partition for any reason...

I found the following guide useful: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

