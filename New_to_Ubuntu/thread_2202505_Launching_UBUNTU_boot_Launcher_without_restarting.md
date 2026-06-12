---
title: "Launching UBUNTU boot Launcher without restarting"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by campcreekdude on 2014-01-29
I dont know if its possible but it would be cool if I could launch the BOOT Launcher without having to physically restart my computer.

Lets say I load Ubuntu then decide in 1 hour that I'd like to launch into my windows 7 Install.
I actually have to restart my computer and get the ubuntu boot loader up to select windows 7.

It would be neat to have an option alongside of restart,shutdown and call it boot-launcher.
Then as soon as you exit ubuntu you go straight into boot launcher instead of restarting the mobo initialization and what not.

Is this possible to just launch boot launcher without having to restart and select the Ubuntu hard=drive.
Just an idea would be cool if it was that way. It would save time.

I dont want to use Virtual Box which is a solution to this because i need my video card in windows to  play games.

---

### Post by Frogs Hair on 2014-01-29
The question has been asked many times and the answer is no unless Windows or other operating system is run in virtual box or similar software. Success depends on your hardware .

---

### Post by Eric_Sysak on 2014-01-30
I read this question and I had a different idea for what the requestor wanted and I'd like to see if this makes sense and maybe has already been done.  It would seem that a GRUB2 tool could help in this request.  The idea is to have a pair of utilities, one Win and one Linux that you could toggle the GRUB2 configuration quickly and easily.  Essentially in Linux, you'd choose, Restart in Windows, and in Windows you'd choose Restart in Linux.  This seemingly would allow you to restart in the desired OS and minimize the newbie mangling of the config.  I know that I'd appreciate such a utility as editing GRUB2 is not too newbie friendly.

Just a thought, and if someone has already developed this solution, please pass it along.

---

### Post by campcreekdude on 2014-01-30
I think something like that would be interesting but I am hoping to avoid the entire restart as well. Like the motherboard bios boot screen. Just a kill switch for Ubuntu and an on switch for Windows through GRUB. 
without needing to post the motherboard. 
 The reason to want to avoid this restart is because  its really stressful on the hardware and it also would save time.
Thanks for the replys.

---

### Post by squakie on 2014-01-30
The one thing the restart does for you when it reinitializes your PC is that it resets the hardware.  I don't know about going from Ubuntu to say Windows, but I know it can be a "blessing" sometimes when going from Windows to Ubuntu - or even just rebtooting either.  You can avoid strange things like the occasional wireless adapter that doesn't cooperate at some point real well,  *hopefully* have done a clean close of open devices prior to the reset, etc..

---

