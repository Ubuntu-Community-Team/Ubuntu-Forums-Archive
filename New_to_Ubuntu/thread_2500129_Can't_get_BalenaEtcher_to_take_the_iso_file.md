---
title: "Can't get BalenaEtcher to take the iso file"
date: 2024-08-23
forum: New to Ubuntu
---

### Post by keltkitty on 2024-08-23
I set up a laptop with Linux-- Ubuntu probably-- at least a decade ago and it went kinda smooth. But now I'm hoping to set up a Surface laptop with Ubuntu and all seems to go sideways. Did initial downloading on the Surface itself, and suddenly the BitLocker grabbed it and shut me out. Now trying to set up a thumb drive to boot the machine, but I can't build the USB drive to do that. Downloaded BalenaEtcher and clicked on the downloaded iso and an error alert popped up: "(0,h.requestMetatdata) is not a function" But I'm following the instructions as I see them. Also tried grabbing from the URL, but another error alert came up.

What am I doing wrong?

Thanks

---

### Post by Rubi1200 on 2024-08-25
If you are attempting to write the ISO to USB in Windows, then you could also try with either Rufus or Ventoy.

If it works, then boot the computer and go into BIOS to change the boot order to let your USB stick get to the live desktop.

---

### Post by keltkitty on 2024-08-25
BitLocker is a Windows thing I never encountered before, but it locked up the computer. I bought a Ubuntu USB that was already loaded and it kicked out BitLocker and brought Win11 back up. But I can't get it to load Ubuntu by clicking many recommended control keys. And I don't see a way to show you a jpg of windows explorer showing what's on the USB. 

Feeling kinda dumb here. If this is a normal Ubuntu looking thing shouldn't I see a .exe?

Keltkitty

---

### Post by nicolasdentremont on 2024-08-25
Your posts are a little confusing but that's alright I'm sure someone here can set you in the right direction.

It might be important to note where you got the pre-loaded drive and what version of Ubuntu it has.

If you bought a pre-loaded Ubuntu USB drive, you shouldn't need to use Balena Etcher. Balena Etcher is used to write an image file to a removable drive to create a bootable drive.

If Ubuntu is already loaded on that drive you should be able to boot it by plugging it into your device and restarting it. It should boot from the USB when your device starts up.

If not...

You may need to change the boot order in your BIOS menu. You'll need to find out how to enter that on your device because the method varies from device to device. On my laptop I need to press F12 as soon as it starts.

In the BIOS menu, there should be a boot tab that will show a list of devices and the order that they are booted. You'll want to move the USB drive to the top of the list.

I'm not sure how bitlocker works but you should be able to at least boot and try Ubuntu right from the USB.

---

### Post by keltkitty on 2024-08-25
Thanks all,

I have moved forward and Ubuntu is "installed" on the snarling laptop, black screen comes up and says, "Error: 0x80370102 The virtual machine could not be started because a required feature is not installed." Which I can only fix if I get into the BIOS, which I have tried dozens of times now. I get the impression Microsoft is fighting me. It used to be so easy to get into BIOS. I've restarted with most of the F keys, as well as shift and escape. Win ignores.

In Linux code now. Moving to a different questions, unless I find the answer in a form search. 

Thanks for the info here.

---

### Post by nicolasdentremont on 2024-08-26
Are you trying to install Ubuntu as a virtual machine?

Also Google says this:

> **To load the BIOS firmware settings menu:**


[LIST]
[*]Shut down your Surface.
[*]Press and hold the volume-up button on your Surface and at the same time, press and release the power button.
[*]When you see the Surface logo, release the volume-up button. The BIOS menu will display within a few seconds.
[/LIST]


---

