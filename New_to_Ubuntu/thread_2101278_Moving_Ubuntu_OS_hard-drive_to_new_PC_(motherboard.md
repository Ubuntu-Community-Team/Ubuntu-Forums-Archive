---
title: "Moving Ubuntu OS hard-drive to new PC (motherboard/processor)"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by chamira on 2013-01-04
Hello, my old PC died, RAM/motherboard failure or something and I cannot find the parts to upgrade it where I am located.

So I bought a new bare bones system and installed my Ubuntu 11.10 OS drive (from the old PC) in the new PC.

But I am not progressing beyond the Grub menu, the system just hangs after the Grub screen. Once it managed to get to the Ubuntu red dot splash page but that was it.

I am sure this is something to do with the new PCs hardware configuration, may be the new built-in graphics card on the motherboard is not recognized?

As the old PC is dead, I cannot un-install the graphics drivers and any other proprietary drivers from Ubuntu. 

The old PC was an AMD 32 bit processor with an Asus motherboard. The new PC is Intel 64bit with an Intel motherboard. Would this cause issues as well?

Is there anything I can do to make Ubuntu check the configuration and update any necessary drivers?

Any advice is appreciated.

---

### Post by El Tito on 2013-01-04
Yes, this is due to a mismatch between your old kernel config files and your new hardware. In your old installation you have different components and thus different modules, so I suppose if you simply install your old hard disk in a new computer, it will not work.
You could copy your home folder, to save your personal files. The problem are the programs in your old machine. Don't really know if copying your /usr folder, or some parts of it, would solve your problem.

Good luck!!

---

### Post by chamira on 2013-01-04
Thanks for the reply. 

But there surely must be an established sequence of commands to help people in this situation?

I can imagine this is quite a common situation: As hardware becomes obsolete over a period of few years, it is impossible for me to re-create my old PC configuration and I had to buy a new system.

---

### Post by Pletched on 2013-01-04
The instructions are as follows.
[LIST]
[*]pop in live disc
[*]create a partion so you can recover some files
[*]recover some files
[*]install a new version of ubuntu 12.04
[/LIST]

---

### Post by mastablasta on 2013-01-04
the problem are only proprietary drivers (likely the graphics card). the opensource ones are built into kernel. and linux check for hardware and then loads the necessary modules on boot. 
 
so what GPU do oyu have now and which one you had before?
 
you can see how to remove and reinstall the opensoruce drivers here: [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver")
 
another option could be that you need to use a boot parameter in grub to get the new hardware to boot and then solve the drivers issue after you get into the desktop:
 
have a look here: [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver)
 
ofcourse if your new otherboard has UEFI then the Pletched's solution is best and probably easiest. otherwise oyu would need to manually create and add boot partition.
 
when you get to red dot screen hit esc (it should drop the splash screen and you will see old fashioned boot commands running...) maybe it will give you a clue in term of error message. if you can see it,  write it down or take a photo of it and post here. people can help more easilly if they know exactly what the error is.

---

### Post by chamira on 2013-01-08
Thank you everyone for all the advice. 

I am going to document the full saga here just in case it may prove useful for others:

From the Grub screen, when I select to run in recovery mode, I get to a terminal login screen. 

Running 'xstart' gave me an error about the nvidia modules not loaded and no devices found.

(On my old PC I had one graphics card Nvidia GeForce 6600 (PCIEx16 256MB) which I used to run two monitors. 

In my new PC, I have installed the nvidia from the old machine and the new motherboard also comes with a built-in Intel card. 

But at this stage the hardware configuration is 'seen' as having only the nvidia card, I presume.

Why the drivers were missing, I don't know.)

So, I decided to upgrade the 11.10 installation to 12.04 via the terminal, in the hope that all relevant modules for the hardware might be loaded on upgrade.

The upgrade was sucessful but I got 'no such device' on selecting any options on the Grub screen - possibly a boot loader problem. 

This was solved by following the instructions here:
[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

So I got my o/s drive from my old PC installed, updated and working on my new PC!

The monitor on the built-in Intel motherboard is working correctly, but the one on the nvidia card is not working. In fact, the nvidia card does not seem to be recognized at all. (This is another post!)

Thanks again for all the advice and support.

---

